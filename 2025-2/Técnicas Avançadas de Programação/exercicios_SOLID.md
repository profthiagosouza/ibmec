
# 🧪 Lista de Exercícios – Refatoração dos Princípios SOLID em Java

Este material contém exercícios práticos com **códigos prontos para refatoração**. Cada exemplo viola um ou mais princípios do SOLID. Sua tarefa é analisar e **refatorar o código** aplicando o princípio correto.

---

## 🧱 1. Single Responsibility Principle (SRP)

### 🧪 Exercício 1 – Classe com múltiplas responsabilidades

```java
public class Usuario {

    public void cadastrar(String nome, String email) {
        System.out.println("Usuário cadastrado: " + nome);
    }

    public boolean validarSenha(String senha) {
        return senha.length() >= 8;
    }

    public void enviarEmailBoasVindas(String email) {
        System.out.println("Enviando e-mail de boas-vindas para: " + email);
    }

    public static void main(String[] args) {
        Usuario u = new Usuario();
        u.cadastrar("Ana", "ana@email.com");
        u.enviarEmailBoasVindas("ana@email.com");
    }
}
```
✏️ **Tarefa:** Separe cada responsabilidade em classes distintas.

---

### 🧪 Exercício 2 – Relatório com duas funções

```java
public class Relatorio {

    public void gerar() {
        System.out.println("Gerando relatório de vendas...");
    }

    public void salvarEmArquivo() {
        System.out.println("Relatório salvo em arquivo .txt");
    }

    public static void main(String[] args) {
        Relatorio r = new Relatorio();
        r.gerar();
        r.salvarEmArquivo();
    }
}
```
✏️ **Tarefa:** Aplique SRP separando a geração e a persistência do relatório.

---

## 🏗️ 2. Open/Closed Principle (OCP)

### 🧪 Exercício 3 – Cálculo de desconto com if

```java
public class CalculadoraDesconto {

    public double calcular(String tipoCliente, double valor) {
        if (tipoCliente.equals("VIP")) {
            return valor * 0.8;
        } else if (tipoCliente.equals("REGULAR")) {
            return valor * 0.9;
        } else {
            return valor;
        }
    }

    public static void main(String[] args) {
        CalculadoraDesconto calc = new CalculadoraDesconto();
        System.out.println("Desconto VIP: " + calc.calcular("VIP", 100));
        System.out.println("Desconto Regular: " + calc.calcular("REGULAR", 100));
    }
}
```
✏️ **Tarefa:** Elimine os `if` usando polimorfismo e torne o código aberto para extensão.

---

### 🧪 Exercício 4 – Cálculo de área com verificações

```java
class CalculadoraArea {

    public double calcularArea(Object forma) {
        if (forma instanceof Circulo) {
            Circulo c = (Circulo) forma;
            return Math.PI * c.raio * c.raio;
        } else if (forma instanceof Retangulo) {
            Retangulo r = (Retangulo) forma;
            return r.largura * r.altura;
        }
        return 0;
    }
}

class Circulo {
    double raio;
    Circulo(double raio) { this.raio = raio; }
}

class Retangulo {
    double largura, altura;
    Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }
}

public class Main {
    public static void main(String[] args) {
        CalculadoraArea calc = new CalculadoraArea();
        System.out.println("Área do círculo: " + calc.calcularArea(new Circulo(5)));
        System.out.println("Área do retângulo: " + calc.calcularArea(new Retangulo(4, 6)));
    }
}
```
✏️ **Tarefa:** Use herança e polimorfismo para eliminar `instanceof`.

---

## 🧬 3. Liskov Substitution Principle (LSP)

### 🧪 Exercício 5 – Classe filha quebrando o contrato

```java
class Ave {
    public void voar() {
        System.out.println("Ave voando...");
    }
}

class Pinguim extends Ave {
    @Override
    public void voar() {
        throw new UnsupportedOperationException("Pinguins não voam!");
    }
}

public class Main {
    public static void main(String[] args) {
        Ave ave = new Pinguim();
        ave.voar();
    }
}
```
✏️ **Tarefa:** Reestruture as classes para respeitar o LSP.

---

### 🧪 Exercício 6 – Veículos com comportamentos diferentes

```java
class Veiculo {
    public void acelerar() {
        System.out.println("Acelerando veículo...");
    }
}

class Bicicleta extends Veiculo {
    @Override
    public void acelerar() {
        throw new UnsupportedOperationException("Bicicleta não acelera com motor!");
    }
}

public class Main {
    public static void main(String[] args) {
        Veiculo v = new Bicicleta();
        v.acelerar();
    }
}
```
✏️ **Tarefa:** Ajuste a hierarquia para respeitar o LSP.

---

## 🪶 4. Interface Segregation Principle (ISP)

### 🧪 Exercício 7 – Interface muito grande

```java
interface Funcionario {
    void trabalhar();
    void dirigir();
    void programar();
}

class Desenvolvedor implements Funcionario {
    public void trabalhar() { System.out.println("Trabalhando..."); }
    public void dirigir() { throw new UnsupportedOperationException("Não dirijo."); }
    public void programar() { System.out.println("Programando..."); }
}

public class Main {
    public static void main(String[] args) {
        Funcionario dev = new Desenvolvedor();
        dev.trabalhar();
        dev.programar();
    }
}
```
✏️ **Tarefa:** Divida a interface em interfaces menores e específicas.

---

### 🧪 Exercício 8 – Animais com métodos que não fazem sentido

```java
interface Animal {
    void voar();
    void nadar();
    void andar();
}

class Cachorro implements Animal {
    public void voar() { throw new UnsupportedOperationException("Cachorros não voam."); }
    public void nadar() { System.out.println("Nadando..."); }
    public void andar() { System.out.println("Andando..."); }
}
```
✏️ **Tarefa:** Crie interfaces específicas para cada comportamento.

---

## 🔄 5. Dependency Inversion Principle (DIP)

### 🧪 Exercício 9 – Dependência concreta

```java
class BancoDeDados {
    public void salvar(String dados) {
        System.out.println("Salvando no banco: " + dados);
    }
}

class RelatorioService {
    private BancoDeDados banco = new BancoDeDados();

    public void gerarRelatorio() {
        banco.salvar("Relatório de vendas");
    }
}

public class Main {
    public static void main(String[] args) {
        RelatorioService service = new RelatorioService();
        service.gerarRelatorio();
    }
}
```
✏️ **Tarefa:** Faça `RelatorioService` depender de uma abstração.

---

### 🧪 Exercício 10 – Leitura de dados fixa

```java
class LeitorArquivo {
    public String ler() {
        return "Lendo dados do arquivo...";
    }
}

class Processador {
    private LeitorArquivo leitor = new LeitorArquivo();

    public void processar() {
        System.out.println(leitor.ler());
    }
}

public class Main {
    public static void main(String[] args) {
        Processador p = new Processador();
        p.processar();
    }
}
```
✏️ **Tarefa:** Aplique DIP criando uma interface para a leitura de dados.

---

## 🧠 Desafio Final – Aplicação Completa

Implemente um sistema de pedidos aplicando **todos os princípios SOLID**:  
- Cadastro de clientes e pedidos.  
- Cálculo de descontos extensível.  
- Suporte a múltiplos métodos de pagamento.  
- Interfaces específicas e baixo acoplamento.

