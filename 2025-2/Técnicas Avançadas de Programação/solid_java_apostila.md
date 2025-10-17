
# Princípios SOLID em Java  
**Autor:** Professor Thiago Souza  

---

## 📚 Introdução

Os princípios **SOLID** foram propostos por Robert C. Martin (conhecido como *Uncle Bob*) e representam um conjunto de **boas práticas de design orientado a objetos** que tornam o código mais **legível, reutilizável, fácil de manter e escalável**.  

A sigla **SOLID** representa:

- **S** – Single Responsibility Principle (Princípio da Responsabilidade Única)  
- **O** – Open/Closed Principle (Princípio Aberto/Fechado)  
- **L** – Liskov Substitution Principle (Princípio da Substituição de Liskov)  
- **I** – Interface Segregation Principle (Princípio da Segregação de Interfaces)  
- **D** – Dependency Inversion Principle (Princípio da Inversão de Dependência)

Aplicar esses princípios ajuda a criar sistemas que crescem com facilidade e evitam problemas comuns como **código rígido, frágil e difícil de testar**.

---

## 🧱 1. Single Responsibility Principle (SRP)  
**Princípio da Responsabilidade Única**

> “Uma classe deve ter apenas uma razão para mudar.”

Esse princípio afirma que cada classe deve ser responsável por **um único propósito ou funcionalidade**. Isso torna o código mais fácil de manter, testar e reutilizar.

### ❌ Exemplo errado (violando SRP):

```java
public class Relatorio {

    // Esta classe faz duas coisas: gera o relatório e salva no banco
    public void gerarRelatorio() {
        System.out.println("Relatório gerado...");
    }

    public void salvarNoBanco() {
        System.out.println("Relatório salvo no banco de dados...");
    }
}
```

Aqui, a classe tem **duas responsabilidades**: gerar e salvar. Se a forma de salvar mudar, a classe precisa mudar mesmo que a geração não tenha mudado.

---

### ✅ Exemplo correto (aplicando SRP):

```java
// Classe responsável apenas por gerar o relatório
public class GeradorDeRelatorio {
    public void gerar() {
        System.out.println("Relatório gerado...");
    }
}

// Classe responsável apenas por salvar o relatório
public class SalvarRelatorio {
    public void salvar() {
        System.out.println("Relatório salvo no banco de dados...");
    }
}

// Classe principal que orquestra as operações
public class Main {
    public static void main(String[] args) {
        GeradorDeRelatorio gerador = new GeradorDeRelatorio();
        SalvarRelatorio salvador = new SalvarRelatorio();

        gerador.gerar();
        salvador.salvar();
    }
}
```

✅ Agora cada classe tem apenas **uma responsabilidade** e pode evoluir independentemente.

---

## 🏗️ 2. Open/Closed Principle (OCP)  
**Princípio Aberto/Fechado**

> “Entidades de software devem estar abertas para extensão, mas fechadas para modificação.”

Ou seja, você deve poder **adicionar comportamentos sem alterar o código existente**.

### ❌ Exemplo errado (violando OCP):

```java
public class CalculadoraDesconto {

    public double calcular(String tipoCliente, double valor) {
        if (tipoCliente.equals("VIP")) {
            return valor * 0.8; // 20% de desconto
        } else if (tipoCliente.equals("REGULAR")) {
            return valor * 0.9; // 10% de desconto
        }
        return valor;
    }
}
```

Se aparecer um novo tipo de cliente, você terá que **alterar o código da classe**, violando o OCP.

---

### ✅ Exemplo correto (aplicando OCP):

```java
// Interface para estratégias de desconto
interface Desconto {
    double aplicar(double valor);
}

// Implementação para cliente VIP
class DescontoVIP implements Desconto {
    public double aplicar(double valor) {
        return valor * 0.8;
    }
}

// Implementação para cliente Regular
class DescontoRegular implements Desconto {
    public double aplicar(double valor) {
        return valor * 0.9;
    }
}

// Classe que utiliza a abstração sem precisar ser modificada
public class CalculadoraDesconto {
    public double calcular(Desconto desconto, double valor) {
        return desconto.aplicar(valor);
    }
}

public class Main {
    public static void main(String[] args) {
        CalculadoraDesconto calc = new CalculadoraDesconto();

        System.out.println("Desconto VIP: " + calc.calcular(new DescontoVIP(), 100.0));
        System.out.println("Desconto Regular: " + calc.calcular(new DescontoRegular(), 100.0));
    }
}
```

✅ Para adicionar um novo tipo de cliente, basta criar uma nova classe que implemente `Desconto`, **sem alterar o código existente**.

---

## 🧬 3. Liskov Substitution Principle (LSP)  
**Princípio da Substituição de Liskov**

> “Subtipos devem poder substituir seus tipos base sem alterar o comportamento do programa.”

Ou seja, qualquer subclasse deve poder ser usada no lugar de sua superclasse sem causar comportamentos inesperados.

### ❌ Exemplo errado (violando LSP):

```java
class Ave {
    public void voar() {
        System.out.println("Ave voando...");
    }
}

class Pinguim extends Ave {
    // Pinguim não voa! Isso quebra a expectativa do método herdado.
    @Override
    public void voar() {
        throw new UnsupportedOperationException("Pinguins não voam!");
    }
}
```

Aqui, `Pinguim` **não respeita o contrato** da superclasse `Ave`, violando o LSP.

---

### ✅ Exemplo correto (aplicando LSP):

```java
// Superclasse mais genérica
abstract class Ave {
    public abstract void mover();
}

class Andorinha extends Ave {
    @Override
    public void mover() {
        System.out.println("Andorinha voando...");
    }
}

class Pinguim extends Ave {
    @Override
    public void mover() {
        System.out.println("Pinguim andando...");
    }
}

public class Main {
    public static void main(String[] args) {
        Ave ave1 = new Andorinha();
        Ave ave2 = new Pinguim();

        ave1.mover();
        ave2.mover();
    }
}
```

✅ Agora, **qualquer subtipo pode substituir `Ave` sem quebrar o comportamento esperado.**

---

## 🪶 4. Interface Segregation Principle (ISP)  
**Princípio da Segregação de Interfaces**

> “Nenhum cliente deve ser forçado a depender de métodos que não utiliza.”

Em outras palavras, é melhor ter **interfaces pequenas e específicas** do que uma grande e genérica.

### ❌ Exemplo errado (violando ISP):

```java
interface Trabalhador {
    void trabalhar();
    void dirigir();
}

class Desenvolvedor implements Trabalhador {
    public void trabalhar() {
        System.out.println("Desenvolvendo código...");
    }

    public void dirigir() {
        // Desenvolvedor não precisa dirigir
        throw new UnsupportedOperationException("Não dirijo!");
    }
}
```

---

### ✅ Exemplo correto (aplicando ISP):

```java
// Interfaces pequenas e coesas
interface Trabalhador {
    void trabalhar();
}

interface Motorista {
    void dirigir();
}

class Desenvolvedor implements Trabalhador {
    public void trabalhar() {
        System.out.println("Desenvolvendo código...");
    }
}

class Caminhoneiro implements Trabalhador, Motorista {
    public void trabalhar() {
        System.out.println("Transportando cargas...");
    }

    public void dirigir() {
        System.out.println("Dirigindo caminhão...");
    }
}
```

✅ Agora, cada classe implementa **apenas o que realmente precisa**.

---

## 🔄 5. Dependency Inversion Principle (DIP)  
**Princípio da Inversão de Dependência**

> “Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.”

Esse princípio promove o uso de **interfaces ou classes abstratas** em vez de dependências diretas em implementações concretas.

### ❌ Exemplo errado (violando DIP):

```java
class Teclado {
    public String lerEntrada() {
        return "Digitando...";
    }
}

class Computador {
    private Teclado teclado;

    public Computador() {
        teclado = new Teclado(); // depende diretamente de uma implementação concreta
    }

    public void iniciar() {
        System.out.println(teclado.lerEntrada());
    }
}
```

---

### ✅ Exemplo correto (aplicando DIP):

```java
// Abstração
interface DispositivoEntrada {
    String lerEntrada();
}

// Implementação concreta 1
class Teclado implements DispositivoEntrada {
    public String lerEntrada() {
        return "Entrada via teclado...";
    }
}

// Implementação concreta 2
class Scanner implements DispositivoEntrada {
    public String lerEntrada() {
        return "Entrada via scanner...";
    }
}

// Classe de alto nível depende da abstração
class Computador {
    private DispositivoEntrada dispositivo;

    // Injeção de dependência via construtor
    public Computador(DispositivoEntrada dispositivo) {
        this.dispositivo = dispositivo;
    }

    public void iniciar() {
        System.out.println(dispositivo.lerEntrada());
    }
}

public class Main {
    public static void main(String[] args) {
        Computador pc1 = new Computador(new Teclado());
        Computador pc2 = new Computador(new Scanner());

        pc1.iniciar();
        pc2.iniciar();
    }
}
```

✅ Agora o `Computador` depende apenas da **abstração** `DispositivoEntrada`, e não de implementações específicas.

---

## 🎯 Conclusão

Aplicar os princípios **SOLID** no desenvolvimento em Java é essencial para construir sistemas:

- **Fáceis de entender** – cada classe tem um papel claro.  
- **Fáceis de manter e estender** – novas funcionalidades exigem menos mudanças.  
- **Fáceis de testar** – o código desacoplado facilita a criação de testes automatizados.  

Esses princípios não são regras rígidas, mas **guias poderosos** para projetar sistemas orientados a objetos mais robustos e evolutivos.
