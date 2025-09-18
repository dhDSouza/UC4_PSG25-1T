# 🧬 Aula 6 - Programação Orientada a Objetos: Pilar da Herança + Classes Abstratas e Interfaces

## 🤔 Revisando Herança

Herança é quando uma classe (filha) aproveita e estende os comportamentos de outra (pai).   
   
👉 Exemplo: `Hobbit` e `Elfo` herdam de `Personagem`.

---

## 🧩 Classes Abstratas

Uma **classe abstrata** é como um **molde incompleto**.

* Você não pode criar um objeto direto dela.
* Ela serve de **base** para outras classes.
* Pode conter métodos já implementados **ou** apenas a “assinatura” (métodos abstratos) que devem ser obrigatoriamente implementados pelas classes filhas.

📌 Analogia:

* Pense na classe abstrata como o **Clã Uchiha (Naruto)** → você não pode criar um “objeto Clã Uchiha”, mas todos os Uchihas herdam características em comum (Sharingan, por exemplo). Cada personagem (Itachi, Sasuke) vai implementar o uso desse poder de forma diferente.

### Exemplo em TypeScript:

```ts
abstract class Personagem {
  constructor(public nome: string, public poder: number) {}

  // Método abstrato (sem implementação)
  abstract atacar(): void;

  // Método comum (todas as classes filhas herdam igual)
  mostrarStatus(): void {
    console.log(`${this.nome} tem poder ${this.poder}`);
  }
}

class Mago extends Personagem {
  atacar(): void {
    console.log(`${this.nome} lança uma bola de fogo! 🔥`);
  }
}

class Guerreiro extends Personagem {
  atacar(): void {
    console.log(`${this.nome} ataca com sua espada! 🗡️`);
  }
}

const gandalf = new Mago("Gandalf", 95);
gandalf.atacar();
gandalf.mostrarStatus();

const aragorn = new Guerreiro("Aragorn", 85);
aragorn.atacar();
```

---

## 📜 Interfaces

A **interface** é como um **contrato**: ela diz **o que uma classe deve ter**, mas não implementa nada.

* Serve para **garantir que diferentes classes tenham os mesmos métodos/propriedades**.
* Diferente de classes abstratas, uma classe pode implementar **várias interfaces** (herança múltipla de contratos).

📌 Analogia:

* Pense nas interfaces como os **códigos Jedi (Star Wars)**.

  * Todo Jedi deve seguir o código, mas cada um interpreta/implementa de forma diferente (Yoda ensina de um jeito, Anakin ignora 🙃).

### Exemplo em TypeScript:

```ts
interface Lutador {
  nome: string;
  poder: number;
  lutar(): void;
}

class Saiyajin implements Lutador {
  constructor(public nome: string, public poder: number) {}

  lutar(): void {
    console.log(`${this.nome} solta um Kamehamehaaaa! 🔥`);
  }
}

class Ninja implements Lutador {
  constructor(public nome: string, public poder: number) {}

  lutar(): void {
    console.log(`${this.nome} usa um Jutsu secreto! 🌀`);
  }
}

const goku = new Saiyajin("Goku", 9000);
const naruto = new Ninja("Naruto", 8000);

goku.lutar();
naruto.lutar();
```

---

## 🧐 Diferença entre Classe Abstrata e Interface

| Característica                        | Classe Abstrata | Interface |
| ------------------------------------- | --------------- | --------- |
| Pode ter atributos implementados?     | ✅ Sim           | ❌ Não     |
| Pode ter métodos implementados?       | ✅ Sim           | ❌ Não     |
| Pode herdar de várias ao mesmo tempo? | ❌ Não           | ✅ Sim     |
| Pode instanciar direto?               | ❌ Não           | ❌ Não     |

📌 **Resumo nerd:**

* Classe Abstrata = “Clã Uchiha” (tem coisas já prontas + obriga métodos).
* Interface = “Código Jedi” (apenas o contrato, nada implementado).

---

## 📝 Exercícios

### 🔎 De Pesquisa

1. Qual a principal diferença entre classe abstrata e interface no TypeScript?
2. Em quais casos você escolheria uma classe abstrata ao invés de uma interface?

### 💻 De Prática

1. Crie uma classe abstrata `Animal` com o método abstrato `falar()`.

   * Crie duas subclasses (`Cachorro`, `Gato`) que implementam esse método de forma diferente.
2. Crie uma interface `Veiculo` com as propriedades `marca` e `modelo`, e o método `acelerar()`.

   * Implemente em pelo menos duas classes (`Carro`, `Moto`).
