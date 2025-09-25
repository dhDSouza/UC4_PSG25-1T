# 🎭 Aula 7 - Programação Orientada a Objetos: Pilar do Polimorfismo

## 🤔 O que é Polimorfismo?

A palavra vem do grego: **poli** (muitos) + **morfos** (formas).

🤔 Em programação, significa que **um mesmo método pode ter comportamentos diferentes dependendo do contexto**.

📌 Em outras palavras: é como se um personagem tivesse **várias transformações ou técnicas**, mas você o chama sempre pelo mesmo nome.

---

## 📚 Tipos de Polimorfismo

### 1️⃣ Polimorfismo de Sobrescrita (Override)

* Acontece quando **uma classe filha reimplementa** um método da classe pai.
* Exemplo: `Personagem` tem o método `atacar()`, mas `Mago` e `Guerreiro` atacam de formas diferentes.

👉 Analogia:

* Em **Dragon Ball**, o comando é sempre **“Kamehameha”**, mas o poder do **Goku criança** não é o mesmo do **Goku Super Saiyajin Blue**.
  O método é o mesmo, o efeito muda!

```ts
class Personagem {
  constructor(public nome: string) {}

  atacar(): void {
    console.log(`${this.nome} ataca normalmente 👊`);
  }
}

class Mago extends Personagem {
  atacar(): void {
    console.log(`${this.nome} lança magia de fogo 🔥`);
  }
}

class Guerreiro extends Personagem {
  atacar(): void {
    console.log(`${this.nome} golpeia com espada 🗡️`);
  }
}

const gandalf = new Mago("Gandalf");
const aragorn = new Guerreiro("Aragorn");

gandalf.atacar(); // magia de fogo 🔥
aragorn.atacar(); // espada 🗡️
```

---

### 2️⃣ Polimorfismo de Sobrecarga (Overload)

* Em algumas linguagens, você pode criar **várias versões do mesmo método** com parâmetros diferentes.
* O TypeScript **não tem sobrecarga real** (como Java ou C#), mas podemos simular com **assinaturas diferentes**.

* Pense no **Naruto**: o jutsu se chama sempre “Clone das Sombras”, mas ele pode fazer **2 clones, 100 clones ou 1000 clones**, dependendo do chakra disponível.

```ts
class Calculadora {
  somar(a: number, b: number): number;
  somar(a: string, b: string): string;

  somar(a: any, b: any): any {
    return a + b;
  }
}

const calc = new Calculadora();
console.log(calc.somar(10, 20));      // 30
console.log(calc.somar("Oi, ", "Daniel")); // "Oi, Daniel"
```

---

### 3️⃣ Polimorfismo por Interface

* Quando diferentes classes implementam a **mesma interface**, mas cada uma dá sua própria implementação.

* Em **Star Wars**, todos os Jedi usam a **Força**, mas cada um manifesta de formas diferentes:

  * Yoda levanta uma nave 🚀
  * Obi-Wan usa para influenciar mentes 🧠
  * Anakin... bem, ele usa para destruir jovens padawans 😬

```ts
interface Lutador {
  nome: string;
  lutar(): void;
}

class Jedi implements Lutador {
  constructor(public nome: string) {}
  lutar(): void {
    console.log(`${this.nome} luta com sabre de luz 🔵`);
  }
}

class Sith implements Lutador {
  constructor(public nome: string) {}
  lutar(): void {
    console.log(`${this.nome} luta com sabre vermelho 🔴`);
  }
}

const luke = new Jedi("Luke");
const vader = new Sith("Vader");

luke.lutar();  // sabre azul
vader.lutar(); // sabre vermelho
```

---

## 🌟 Vantagens do Polimorfismo

* **Reuso de código**: você chama o mesmo método, mas ele se adapta.
* **Extensibilidade**: fácil adicionar novos comportamentos.
* **Organização**: mantém a lógica mais clara.

📌 É como em **RPG**: você usa sempre o comando “Atacar”, mas o resultado depende da classe do personagem.

---

## 📝 Exercícios

### 🔎 De Pesquisa

1. Qual a diferença entre **sobrescrita** e **sobrecarga** no TypeScript?
2. O TypeScript realmente suporta sobrecarga de métodos como Java? Justifique.

### 💻 De Prática

1. Crie uma classe `Animal` com o método `falar()`.

   * Faça subclasses (`Cachorro`, `Gato`, `Pássaro`) que sobrescrevem o método de forma diferente.
2. Crie uma interface `Instrumento` com o método `tocar()`.

   * Implemente em classes (`Guitarra`, `Bateria`, `Flauta`) que tocam sons diferentes.
3. Simule sobrecarga criando uma classe `Mensagem` com o método `enviar()`, que pode receber **string** ou **número** (id de usuário).
