# System of Validation 
for the process of `selection` for learning and pratique **Java POO**
## Controle de Fluxo *Desafio*
```plaintext
/ControleDeFluxo-Desafio/
|
|--.idea
|--src/
|  |--Contador.java
|  |--ParametrosInvalidosException.java
|--.gitignore
|--ControleDeFluxo-Desafio.iml
```
## Sistema de Validação Processo *Seletivo*
```plaintext
/SistemaDeValida-oDIO/
|
|--.idea
|--src/
|  |--candidatura/
|     |--ProcessoSeletivo.java
|--.gitignore
|--SistemaDeValidacao.iml
```
## Conceitos Trabalhados
### Contador
`main` Recebe dois parâmetros via terminal e utiliza um try catch para soltar uma exceção caso o parâmetro um seja maior que o dois
```java
public static void main(String[] args) {
        Scanner terminal = new Scanner(System.in);
        System.out.println(" -_-_- Contador -_-_-");
        System.out.println("Digite o primeiro parâmetro : ");
        int parametroUm = terminal.nextInt();
        System.out.println("Digite o segundo parâmetro : ");
        int parametroDois = terminal.nextInt();

        try{
            contar(parametroUm, parametroDois);
        }catch (ParametrosInvalidosException exception){
            System.out.println("O segundo parâmetro deve ser maior que o primeiro");

        }
    }
```
`método`
utiliza um laço for utilizando os dois parâmetros e soltando a exceção caso a verificação seja inválida
```java
static void contar(int parametroUm , int parametroDois) throws ParametrosInvalidosException{
        if (parametroUm > parametroDois)
            throw new ParametrosInvalidosException();

        int contagem = parametroDois - parametroUm;
        for (int i = 0; i < contagem; i++){
            System.out.println("Imprimindo o número " + (i+1));
        }
    }
```
### Sistema de Validação Para Processo Seletivo
`main` contém um array com pseudos nomes de integrantes do processo seletivo, e utiliza um laço for para simular o chamado para cada candidato
```java
public static void main(String[] args) {
        String [] candidatos = {"FELIPE","MARCIA","JULIA", "PAULO", "AUGUSTO"};
        for(String candidato:candidatos){
            entrandoEmContato(candidato);
        }
    }
```
`métodos`
#### `entrandoEmContato` 
Tenta entrar em contato com um candidato até três vezes, dependendo da resposta.
```java
static void entrandoEmContato(String candidato) {
        int tentativasRealizadas = 1;
        boolean continuarTentando = true;
        boolean atendeu = false;
        do{
            atendeu = atender();
            continuarTentando = !atendeu;
            if(continuarTentando)
                tentativasRealizadas++;
            else
                System.out.println("CONTATO REALIZADO COM SUCESSO");
        }while(continuarTentando && tentativasRealizadas < 3);
        if (atendeu)
            System.out.println("CONSEGUIMOS CONTATO COM " + candidato + " NA " + tentativasRealizadas + "° TENTATIVA");
        else
            System.out.println("NÃO CONSEGUIMOS CONTATO COM " + candidato + ", NÚMERO MAXIMO TENTATIVAS " + tentativasRealizadas + " REALIZADAS");
    }
```
#### `ligarCandidato`
Itera sobre a lista de candidatos e tenta entrar em contato com cada um.
```java
static void ligarCandidato(){
        String [] candidatos = {"FELIPE","MARCIA","JULIA", "PAULO", "AUGUSTO"};

    }
```
#### `imprimirSelecionados`
Imprime a lista de candidatos com seu número de ordem
```java
static void imprimirSelecionados() {
    String[] candidatos = {"FELIPE", "MARCIA", "JULIA", "PAULO", "AUGUSTO"};
    System.out.println("Imprimindo a lista de candidatos informando os selecionados");
    for (int indice = 0; indice < candidatos.length; indice++) {
        System.out.println("O candidato de n° " + (indice + 1) + " é o " + candidatos[indice]);
    }
}

```

#### `atender`
Simula a resposta do atendimento com uma chance aleatória.
```java
static boolean atender() {
    return new Random().nextInt(3) == 1;
}

```

#### `selecaoCandidato`
Seleciona candidatos com base no salário pretendido em relação ao salário base.
```java
static void selecaoCandidato() {
    String[] candidatos = {"FELIPE", "MARCIA", "JULIA", "PAULO", "AUGUSTO", "MONICA", "MIRELA", "DANIELA", "JORGE", "RENATA"};

    int candidatosSelecionados = 0;
    int candidatosAtual = 0;
    double salarioBase = 2000.0;
    while (candidatosSelecionados < 5 && candidatosAtual < candidatos.length) {
        String candidato = candidatos[candidatosAtual];
        double salarioPretendido = valorPretendido();

        System.out.printf("O candidato " + candidato + " solicitou este valor de salário: " + salarioPretendido + "%n");
        if (salarioBase >= salarioPretendido) {
            System.out.println("O candidato " + candidato + " foi selecionado para a vaga");
            candidatosSelecionados++;
        }
        candidatosAtual++;
    }
}

```

#### `valorPretendido`
Gera um valor aleatório de salário pretendido entre 1800 e 2200.
```java
static double valorPretendido() {
    return ThreadLocalRandom.current().nextDouble(1800, 2200);
}

```

#### `analisarCandidato`
Analisa se deve ligar para o candidato com base no salário pretendido.
```java
static void analisarCandidato(double salarioPretendido) {
    double salarioBase = 2000.0;
    if (salarioBase > salarioPretendido) {
        System.out.println("LIGAR PARA O CANDIDATO");
    } else if (salarioBase == salarioPretendido) {
        System.out.println("LIGAR PARA O CANDIDATO COM CONTRA-PROPOSTA");
    } else {
        System.out.println("AGUARDANDO RESULTADO DE OUTROS CANDIDATOS");
    }
}

```
