# 📘 Aula 1: Introdução ao TypeScript

---

## 🤔 O que é TypeScript?

* **JavaScript (JS)**

  * Linguagem dinâmica, flexível, interpretada.
  * Usada no **frontend** (navegadores) e **backend** (Node.js).
  * Não exige definir tipos — mas isso pode gerar erros difíceis de rastrear.

* **TypeScript (TS)**

  * Criado pela Microsoft como um **superconjunto do JS**.
  * Adiciona **tipagem estática** + recursos avançados.
  * É **compilado para JS**, logo roda em qualquer lugar que o JS roda.

👉 Em resumo: **todo código JS é válido em TS, mas nem todo código TS é válido em JS**.

---

## 🚀 Por que usar TypeScript?

1. **Menos bugs** 🐛

   * O compilador detecta erros antes de rodar o código.

2. **Autocompletar poderoso** ✨

   * IDEs como o VS Code conseguem sugerir funções, variáveis e tipos de forma mais precisa.

3. **Manutenção mais fácil** 🛠

   * Projetos grandes ficam mais organizados.
   * Evita problemas de “qual era mesmo o tipo dessa variável?”.

4. **Compatível com JS moderno** 🌍

   * Suporta recursos do **ES6+** (classes, async/await, etc.).

---

## 🧩 Tipos de Dados no TypeScript

| Tipo        | Exemplo                                              | Descrição                               |
| ----------- | ---------------------------------------------------- | --------------------------------------- |
| `string`    | `"Daniel"`                                           | Texto                                   |
| `number`    | `42`, `3.14`                                         | Números inteiros ou decimais            |
| `boolean`   | `true`, `false`                                      | Valores lógicos                         |
| `any`       | `let x: any = "pode ser tudo";`                      | Aceita qualquer tipo (evite usar muito) |
| `unknown`   | `let valor: unknown = 10;`                           | Parecido com `any`, mas mais seguro     |
| `null`      | `let n: null = null;`                                | Valor nulo                              |
| `undefined` | `let u: undefined = undefined;`                      | Variável não definida                   |
| `array`     | `let nums: number[] = [1,2,3];`                      | Lista de elementos tipados              |
| `tuple`     | `let pessoa: [string, number] = ["Ana", 25];`        | Estrutura fixa com tipos específicos    |
| `object`    | `let user: {id: number, nome: string}`               | Estrutura de dados com chaves tipadas   |
| `enum`      | `enum Cores { Vermelho, Azul }`                      | Conjunto de valores nomeados            |
| `void`      | `function log(): void {}`                            | Função que não retorna nada             |
| `never`     | `function erro(): never { throw new Error("..."); }` | Função que nunca retorna                |

---

## 👨‍💻 Exemplos de Código

### JavaScript (sem tipagem)

```javascript
function soma(a, b) {
  return a + b;
}

console.log(soma("2", 2)); // Resultado: "22" (bug escondido!)
```

### TypeScript (com tipagem)

```typescript
function soma(a: number, b: number): number {
  return a + b;
}

console.log(soma(2, 2)); // Resultado: 4
// console.log(soma("2", 2)); // Erro em tempo de compilação!
```

---

## ⚙️ Configuração do Ambiente no VS Code

1. **Instalar Node.js** (necessário para rodar TS)
   👉 [Download Node.js](https://nodejs.org)

2. **Criar um projeto**

   ```bash
   mkdir projeto-typescript
   cd projeto-typescript
   npm init -y
   ```

3. **Instalar o TypeScript**

   ```bash
   npm install -g typescript
   npm install -D typescript
   ```

4. **Gerar o arquivo de configuração (`tsconfig.json`)**

   ```bash
   npx tsc --init
   ```

---

## 📝 O que é o tsconfig.json?

É o arquivo que **configura o compilador TS**.
Exemplo de `tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "ES6",        
    "module": "commonjs",   
    "strict": true,         
    "outDir": "./dist",     
    "rootDir": "./src"
  }
}
```

* **target** → versão do JS para compilar
* **module** → sistema de módulos usado (Node = `commonjs`)
* **strict** → ativa todas as verificações de segurança
* **outDir** → pasta onde o JS compilado será salvo
* **rootDir** → pasta onde está o código-fonte TS

---

## 💻 Fluxo de Trabalho

1. Criar um arquivo `src/index.ts`:

   ```typescript
   let nome: string = "Daniel";
   console.log("Olá, " + nome);
   ```

2. Compilar:

   ```bash
   npx tsc
   ```

3. Rodar o JavaScript gerado:

   ```bash
   node dist/index.js
   ```

---

## 🏋️ Lista de Exercícios

1. Crie uma função `dobrar` que receba um número e retorne ele dobrado.
2. Crie uma função `saudacao` que receba um nome (`string`) e retorne `"Olá, <nome>"`.
3. Defina um **array de strings** com nomes de amigos e percorra ele com `forEach`.
4. Crie uma **tupla** que armazene `[nome, idade]`.
5. Crie um `enum` para representar **níveis de acesso**: `ADMIN`, `USER`, `GUEST`.
6. Crie um objeto `pessoa` com propriedades tipadas (`nome`, `idade`, `email`).
7. Escreva uma função que nunca retorna (`never`), lançando um erro.
8. Configure um projeto com `tsconfig.json` que tenha `src/` e `dist/`.
