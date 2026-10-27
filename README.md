# R.POO.G — RPG ASCII em C++

Jogo de RPG por turnos executado no terminal, desenvolvido em **C++** para praticar **Programação Orientada a Objetos (POO)**, separação de responsabilidades e organização do código em classes.

O jogador percorre cenários representados por arte ASCII, enfrenta quatro inimigos e, ao final, um chefe chamado **Necromante**.

## Funcionalidades

- Menu inicial com opções de jogar, sair e visualizar créditos.
- Sequência de batalhas contra **Goblin, Orc, Troll, Skeleton** e o chefe **Necromante**.
- Combate por turnos com três ações: **atacar, defender e utilizar poção de cura**.
- Atributos de vida (HP), dano e quantidade de poções.
- Ataques especiais dos inimigos, com preparação sinalizada ao jogador.
- Recuperação parcial de HP entre confrontos e telas de vitória ou derrota.
- Cenários e personagens desenhados em ASCII; uso de cores ANSI em alguns elementos do terminal.

> **Escopo atual:** o menu de combate oferece ataque, defesa e cura; não há opção de fuga implementada.

## Conceitos de POO aplicados

| Conceito | Aplicação no projeto |
| --- | --- |
| **Abstração** | `Character` representa características comuns dos personagens e declara o método abstrato `attackEnemy`. |
| **Herança** | `Player` e `Enemy` derivam de `Character`. |
| **Polimorfismo** | O método virtual `attackEnemy` é sobrescrito nas classes derivadas. |
| **Encapsulamento** | Atributos como HP e dano são acessados ou alterados por métodos das classes. |
| **Composição e organização** | `Game` coordena jogador, inimigos, cenas, menus e batalhas. |

## Estrutura do repositório

```text
.
├── CMakeLists.txt
├── README.md
└── src/
    ├── main.cpp
    ├── Character.h / Character.cpp
    ├── Player.h / Player.cpp
    ├── Enemy.h / Enemy.cpp
    └── Game.h / Game.cpp
```

- **`Character`:** atributos e interface comum dos personagens.
- **`Player`:** ataque do jogador e recuperação de HP.
- **`Enemy`:** dano, defesa e ataques especiais.
- **`Game`:** menu, cenas ASCII, fluxo narrativo, combates e reinicialização.
- **`main.cpp`:** ponto de entrada; configura UTF-8 no console do Windows.

## Como compilar e executar

### Opção A — Compilação direta com g++

Requisitos: compilador com suporte a C++20 e terminal.

```bash
g++ -std=c++20 src/main.cpp src/Character.cpp src/Player.cpp src/Enemy.cpp src/Game.cpp -o rpoog
```

No Linux/macOS, execute:

```bash
./rpoog
```

No Windows, o executável gerado normalmente será `rpoog.exe` (execute `./rpoog.exe` no terminal compatível).

### Opção B — CMake

O `CMakeLists.txt` do repositório declara **CMake 4.0** como versão mínima e **C++20** como padrão.

```bash
cmake -S . -B build
cmake --build build
```

Execute o binário `jogoascii` (ou `jogoascii.exe` no Windows) no diretório de saída criado pelo gerador do CMake.

**Observações:** as cores usam códigos ANSI, que podem variar conforme o terminal. O jogo usa comandos de limpeza de tela `CLS` (Windows) e `clear` (outros sistemas). Algumas entradas do menu são lidas como números inteiros.

## Melhorias possíveis

- Validar entradas inválidas de forma mais robusta.
- Adicionar testes automatizados para regras de combate.
- Separar efeitos de terminal da lógica de jogo, facilitando testes e portabilidade.
- Criar opção de fuga, se desejada no futuro.

## Créditos

O menu de créditos da aplicação identifica:
- Eduardo Braz de Oliveira
- Gihad Mohamad Mourad
- Jonatas Lopes de Sousa

---

**Repositório:** https://github.com/BrazTec/Game_ASCII-R.POO.G
