# 📌 Atividade de Comunicação Assertiva no Ambiente Dev

## 🎯 Objetivos

* Exercitar **comunicação assertiva** (clareza, objetividade e respeito).
* Fixar os conceitos de **classe, objeto e encapsulamento** em TypeScript.
* Simular um ambiente real de **passagem de requisitos** entre times.

---

## 🧩 Contexto

Vocês fazem parte de **duas empresas de tecnologia diferentes**.
Uma será a **empresa contratante** (que explica a necessidade).
A outra será a **empresa contratada** (que implementa o código com base no que entendeu).

Se a comunicação for clara e assertiva, a implementação estará correta.

---

## 📌 Passos da Atividade

### 1. Formação dos Grupos

* Organizem-se em equipes de **3 a 5 alunos**.
* Cada grupo será, alternadamente, **contratante** e **contratado**.

---

### 2. Definição da Classe (10 min) – Contratante

O grupo contratante deve escolher uma classe para solicitar.
Exemplos: `Carro`, `ContaBancaria`, `Aluno`, `PersonagemDeJogo`.

A classe deve ter:

* Pelo menos **3 atributos**.
* Pelo menos **2 métodos**.
* Uso de **encapsulamento** (atributos `private` com `get/set`).

> [!IMPORTANT]
>  O grupo **não mostra o código**, só explica.

---

### 3. Comunicação Assertiva (10 min) – Contratante → Contratado

O grupo contratante deve **explicar como a classe funciona** para o grupo contratado:

* Usem **exemplos claros e do cotidiano**.
* Não utilizem jargões técnicos.
* Confirmem entendimento:

  > "Vocês conseguem imaginar como isso funcionaria em código?"
  > "Querem que eu repita de outro jeito?"

> [!TIP]
> "Queremos uma `ContaBancaria`. Pensem nela como um cofre: o dinheiro dentro (`saldo`) não pode ser acessado diretamente.
> Para colocar dinheiro usamos o método `depositar()`.
> Para retirar, usamos `sacar()`.
> Só conseguimos ver o valor atual com uma chave (`getSaldo`)."

---

### 4. Implementação em TypeScript (10–15 min) – Contratado

O grupo contratado deve **implementar a classe** baseada apenas na explicação recebida.

Modelo para referência:

```ts
class ContaBancaria {
  private saldo: number;

  constructor(private titular: string, private numero: string) {
    this.saldo = 0;
  }

  public depositar(valor: number): void {
    this.saldo += valor;
  }

  public sacar(valor: number): void {
    if (valor <= this.saldo) {
      this.saldo -= valor;
    } else {
      console.log("Saldo insuficiente!");
    }
  }

  public getSaldo(): number {
    return this.saldo;
  }
}
```

---

## ✅ Critérios de Avaliação

* **Clareza na comunicação** (o grupo explicou de forma compreensível).
* **Aplicação de POO** (classe, objeto, encapsulamento).
* **Trabalho em equipe**.
* **Fidelidade ao que foi solicitado**.

---

⏱️ Tempo total: \~40 minutos   
👥 Trabalho em grupo   
📌 Linguagem: **TypeScript**
