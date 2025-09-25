# 🧙‍♂️ Trabalho: Criando um Livro-Jogo do Senhor dos Anéis com TypeScript

## 📚 O que é um Livro-Jogo?

Um **livro-jogo** é uma experiência interativa que combina elementos de literatura e gaming! 🤔✨   
Em vez de ler passivamente, você toma decisões que afetam o rumo da história. A cada página, surgem escolhas como:

* **"Se quiser investigar a caverna, vá para a página 47"** 🕵️‍♂️
* **"Se preferir seguir pelo rio, vá para a página 89"** 🚣‍♂️

Você será o **mestre do destino** dos personagens! E vamos implementar isso usando **Programação Orientada a Objetos** em TypeScript! 💻

## 🎯 Objetivo da Atividade

Criar um sistema modular de livro-jogo baseado no universo de **O Senhor dos Anéis** 🧝‍♂️⚔️, aplicando os **4 pilares da OOP**:

- **🔐 Encapsulamento**
- **👨‍👩‍👧‍👦 Herança** 
- **🔄 Polimorfismo**
- **📋 Classes Abstratas e Interfaces**

## 🏗️ Estrutura do Projeto

### 1. 📖 **Interface Base - `IPagina`**

```typescript
interface IPagina {
    id: number;
    texto: string;
    escolhas: IEscolha[];
    executar(): void;
}
```

### 2. 🧩 **Classe Abstrata - `PaginaBase`**

```typescript
abstract class PaginaBase implements IPagina {
    constructor(
        public id: number,
        public texto: string,
        public escolhas: IEscolha[] = []
    ) {}
    
    abstract executar(): void;
    
    protected mostrarEscolhas(): void {
        console.log("\n--- Suas Opções ---");
        this.escolhas.forEach((escolha, index) => {
            console.log(`${index + 1}. ${escolha.texto}`);
        });
    }
}
```

### 3. ⚔️ **Classes Específicas - Exemplos Criativos!**

```typescript
class PaginaBatalha extends PaginaBase {
    constructor(
        id: number,
        texto: string,
        public inimigo: Personagem,
        public recompensa: Item[]
    ) {
        super(id, texto);
    }
    
    executar(): void {
        console.log(`Enfrentando: ${this.inimigo.nome}!`);
        // Sistema de batalha aqui!
    }
}

class PaginaQuebraCabeca extends PaginaBase {
    constructor(
        id: number,
        texto: string,
        public solucao: string,
        public dica: string
    ) {
        super(id, texto);
    }
    
    executar(): void {
        console.log("Desvende o enigma élfico!");
    }
}
```

## 🎒 **Sistema de Inventário - Seja Criativo!**

```typescript
class Inventario {
    private itens: Item[] = [];
    
    adicionarItem(item: Item): void {
        this.itens.push(item);
        console.log(`${item.nome} adicionado ao inventário!`);
    }
    
    usarItem(nome: string): boolean {
        const itemIndex = this.itens.findIndex(item => item.nome === nome);
        if (itemIndex > -1) {
            this.itens[itemIndex].usar();
            this.itens.splice(itemIndex, 1);
            return true;
        }
        return false;
    }
}
```

## 💎 **Itens Mágicos - Sua Imaginação é o Limite!**

Crie itens únicos como:

- **🔮 Palantír quebrado** - Revela páginas secretas
- **🍃 Lembas especial** - Restaura HP extra
- **📜 Mapa de Thror** - Mostra caminhos alternativos
- **💍 Anel de Prata** - +10 de carisma nas negociações
- **🗡️ Adaga de Morgul** - Envenena inimigos gradualmente

## 🌍 **Jornada Épica - Ideias para Desenvolver**

### Capítulo 1: 🏞️ **As Terras Sombrias**

```typescript
const pagina1 = new PagiaExploracao(
    1,
    "Você está na Floresta de Fangorn. Árvores ancestrais sussurram segredos...",
    [
        { texto: "Seguir o som da água", proximaPagina: 2 },
        { texto: "Investigar os sussurros", proximaPagina: 15 },
        { texto: "Descansar sob a grande árvore", proximaPagina: 7 }
    ]
);
```

### Capítulo 2: 🏔️ **Minas de Moria**

```typescript
const pagina42 = new PagiaBatalha(
    42,
    "Um troll da caverna bloqueia o caminho! Seu machado brilha na escuridão...",
    new TrollCaverna(),
    [new AdagaMorgul(), new PocaoCura()]
);
```

## 🎨 **Exercícios Criativos**

### 1. **Crie Seu Próprio Personagem** 🧝‍♀️

```typescript
class ElfoCaçador extends Personagem {
    constructor() {
        super("Elfo Caçador", 80, new ArcoLongo());
    }
    
    habilidadeEspecial(): void {
        console.log("🏹 Flecha da Lua: Dano triplo à noite!");
    }
}
```

### 2. **Designe Um Item Mágico Único** ✨

Que tal um **"📖 Livro de Mazarbul"** que permite reler páginas anteriores? Ou um **"🔔 Sino de Erebor"** que atrai criaturas amigáveis?

### 3. **Crie Um Final Alternativo** 🌟

E se... **Gollum se redimisse**? Ou **Boromir sobrevivesse**? Suas escolhas determinam o destino da Terra-média!

## 📊 **Critérios de Avaliação**

| Conceito | 🎯 Obrigatório | 💯 Diferencial |
|:--------:|:--------------:|:---------------:|
| **Herança** | Classes de personagens e itens | Hierarquia complexa de criaturas |
| **Polimorfismo** | `executar()` se comporta diferente | Múltiplos tipos de batalha |
| **Encapsulamento** | Atributos privados no inventário | Getters/setters criativos |
| **Interfaces** | `IPagina`, `IItem` | Interfaces para efeitos especiais |

## 🚀 **Dicas para Brilhar**

1. **🎪 Seja Original**: Crie criaturas únicas como "**Aranha-Gêmea de Shelob**" ou "**Ent Adolescente**"
2. **🔗 Conecte Escolhas**: Uma decisão na página 5 afeta a página 50!
3. **🎵 Adicione Elementos Surpresa**: Itens que mudam o estilo narrativo
4. **🤝 Trabalho em Equipe**: Cada um cria um capítulo diferente

## 💡 **Exemplo de Fluxo**

```
Página 1: "O anel brilha...?" 
    → Escolha A: "Tocá-lo" (Página 2: Visão aterradora!)
    → Escolha B: "Guardá-lo" (Página 3: Hobbits curiosos aparecem!)

Página 2: "Sauron te vê!" 
    → Inventário: 🔮 Palantír pode salvar você!
    → Sem palantír? Game Over! 💀
```

## 🔥 **Conclusão**

Vocês não estão apenas codando - estão **moldando histórias**! Cada `class` é um novo personagem, cada `interface` uma nova mecânica, cada `herança` uma linhagem épica. 

**Lembrem-se**: Na Terra-média, até a menor pessoa pode mudar o curso do futuro... assim como a menor classe pode gerar o sistema mais incrível! 🧙‍♂️💖

**Que sua jornada em TypeScript seja tão épica quanto a da Sociedade do Anel!** ⚔️📖✨

---

*⌛ Tempo de desenvolvimento: 1 semana*  
*👥 Trabalho em grupos de 3-4 alunos*  
*📅 Apresentação: Demonstração ao "Conselho de Elrond" (professor e turma)*

<img src="https://imgs.search.brave.com/sviU496isxr1J4u3pV8se8fYOy_r5404Gu_EgUis3Fo/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tZWRp/YS50ZW5vci5jb20v/OThTRXkzLWE2WG9B/QUFBTS95b3Utc2hh/bGwtYmUtdGhlLWZl/bGxvd3NoaXAtb2Yt/dGhlLXJpbmcteW91/LXNoYWxsLWJlLmdp/Zg.gif">

**Boa sorte, jovens desenvolvedores!**
