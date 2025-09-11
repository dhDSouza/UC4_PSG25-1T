# 🛡️ Aula 4 - Programação Orientada à Objetos: Pilar do Encapsulamento

## 🤔 O que é Encapsulamento?

Encapsulamento significa **proteger os dados de um objeto**, controlando como eles podem ser acessados ou modificados.

👉 Pense em uma **conta bancária**:

* Você pode **depositar** ou **sacar dinheiro**.
* Mas você **não pode abrir o cofre e mexer diretamente** no saldo — precisa usar os métodos autorizados.

Esse controle garante **segurança** e **organização** no código.

---

## 📦 Encapsulamento na prática

Em TypeScript, usamos **modificadores de acesso** para controlar quem pode acessar os atributos/métodos de uma classe:

* **`public`** → acessível de qualquer lugar. *(Padrão no TS)*
* **`private`** → acessível **somente dentro da própria classe**.
* **`protected`** → acessível dentro da classe **e nas classes filhas**.
* **`readonly`** → só pode ser lido, não alterado.

---

## 👨‍💻 Exemplo com Conta Bancária

```ts
class ContaBancaria {
  private saldo: number;

  constructor(saldoInicial: number) {
    this.saldo = saldoInicial;
  }

  // Método público para depositar
  public depositar(valor: number): void {
    if (valor > 0) {
      this.saldo += valor;
      console.log(`Depósito de R$${valor} realizado!`);
    } else {
      console.log("Valor inválido para depósito.");
    }
  }

  // Método público para sacar
  public sacar(valor: number): void {
    if (valor <= this.saldo) {
      this.saldo -= valor;
      console.log(`Saque de R$${valor} realizado!`);
    } else {
      console.log("Saldo insuficiente!");
    }
  }

  // Método público para consultar saldo
  public consultarSaldo(): void {
    console.log(`Saldo atual: R$${this.saldo}`);
  }
}

const minhaConta = new ContaBancaria(1000);
minhaConta.depositar(500);     // Depósito de R$500 realizado!
minhaConta.sacar(200);         // Saque de R$200 realizado!
minhaConta.consultarSaldo();   // Saldo atual: R$1300

// 🚫 Não funciona (saldo é privado)
// console.log(minhaConta.saldo);
```

👉 Repare que o **`saldo` é privado**, então só pode ser manipulado pelos métodos da classe. Isso protege contra usos incorretos.

---

## 🐱 Exemplo com Gato

```ts
class Gato {
  private energia: number;

  constructor() {
    this.energia = 100; // começa descansado
  }

  public brincar(): void {
    if (this.energia > 0) {
      this.energia -= 20;
      console.log("O gato brincou e ficou mais cansado.");
    } else {
      console.log("O gato está sem energia. Ele precisa dormir!");
    }
  }

  public dormir(): void {
    this.energia = 100;
    console.log("O gato dormiu e recuperou a energia!");
  }

  public mostrarEnergia(): void {
    console.log(`Energia atual do gato: ${this.energia}`);
  }
}

const gato = new Gato();
gato.brincar();          // O gato brincou e ficou mais cansado.
gato.mostrarEnergia();   // Energia atual do gato: 80
gato.dormir();           // O gato dormiu e recuperou a energia!
```

👉 Aqui o atributo **`energia` está protegido**. Se fosse público, alguém poderia bagunçar o estado do gato, por exemplo: `gato.energia = -999`.

---

## ⚖️ Vantagens do Encapsulamento

* ✅ **Proteção dos dados** contra alterações incorretas.
* ✅ **Regras claras de acesso** (somente métodos permitem manipulação).
* ✅ **Flexibilidade para mudar a implementação** sem afetar quem usa a classe.
* ✅ **Código mais confiável e seguro**.

---

## 📝 Exercícios

### 🔎 Pesquisa

1. O que acontece se todos os atributos de uma classe forem `public`?
2. Qual a diferença entre `private` e `protected` no TypeScript?
3. Dê exemplos reais de coisas do cotidiano que precisam de **encapsulamento** (como o saldo bancário).

### 💻 Prática

1. Crie uma classe `Pessoa` com:

   * Atributo privado `idade`.
   * Método público `fazerAniversario()` que aumenta a idade.
   * Método público `mostrarIdade()` para exibir a idade.

2. Crie uma classe `Celular` com:

   * Atributo privado `nivelBateria`.
   * Métodos públicos `carregar()` e `usar()` (que diminuem a bateria).
   * Método `mostrarBateria()` para exibir o nível atual.

---

## 🎯 Resumindo

* **Encapsulamento = proteger os dados internos do objeto**.
* Usamos **modificadores de acesso** (`public`, `private`, `protected`, `readonly`).
* Os dados são acessados **através de métodos controlados**.
* Isso deixa o código **mais seguro, organizado e fácil de manter**.
