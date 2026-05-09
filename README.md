[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/zHqjFsRx)
# Diagnóstico de retomada - Teoria da Computação
Esta atividade serve para mapear o que você já domina sobre linguagens formais, autômatos, gramáticas e computabilidade.
Responda individualmente. Use suas palavras. Se usar IA depois da primeira tentativa, registre o uso na seção 7.
## 1. Mapa do que eu lembro
Marque cada tópico como: lembro bem, lembro parcialmente, não lembro, nunca vi ou não tenho certeza.
- alfabeto: Bem
- cadeia: Bem
- linguagem: Parcialmente
- gramática: Parcialmente
- autômato finito: Bem
- linguagem regular: Bem
- linguagem livre de contexto: Não lembro
- linguagem sensível ao contexto: Nunca vi
- linguagem irrestrita: Não lembro
- hierarquia de Chomsky: Não lembro
- computabilidade: Lembro
- máquina de Turing: Lembro
## 2. Definições com exemplo
Explique, com suas palavras e com um exemplo simples, usando o alfabeto `Sigma = {a, b}`.
1. O que é um alfabeto? Um conjunto de símbolos que podem ser usados para dar contexto a algo. Por exemplo, Σ = {a, b} significa que só posso usar os símbolos a e b.
2. O que é uma cadeia? É uma sequência de símbolos do alfabeto. Por exemplo: "aba", "aab", "b" são cadeias formadas com {a, b}. A cadeia vazia (sem nenhum símbolo) também é válida.
3. O que é uma linguagem? É um conjunto de cadeias. Não tenho certeza de como delimitar exatamente quais cadeias entram ou não, mas sei que é um agrupamento de palavras que seguem alguma regra.
4. O que é uma gramática? É um conjunto de regras que define como formar as cadeias de uma linguagem. Não lembro os detalhes formais, mas a ideia é que você parte de um símbolo inicial e vai aplicando regras até chegar numa cadeia final.
## 3. Linguagens
Considere as linguagens:
```text
L1 = { w em {0,1}* | w termina com 01 }
L2 = { a^n b^n | n >= 0 }
L3 = { a^n b^n c^n | n >= 0 }
```
**L1 = { w ∈ {0,1}* | w termina com 01 }**

1. Três palavras que pertencem: `01`, `001`, `101`
2. Duas palavras que não pertencem: `10`, `00`
3. Classe:  linguagem regular.
4. Motivo: só preciso verificar o final da cadeia, um autômato finito consegue fazer isso sem precisar contar nada.

---

**L2 = { a^n b^n | n >= 0 }**

1. Três palavras que pertencem: `ab`, `aabb`, `aaabbb`
2. Duas palavras que não pertencem: `aab`, `abbb`
3. Classe: não lembro o nome certo, talvez livre de contexto.
4. Motivo: precisa contar quantos a's tem e garantir o mesmo número de b's, e não tenho certeza se um autômato simples consegue fazer isso.

---

**L3 = { a^n b^n c^n | n >= 0 }**

1. Três palavras que pertencem: `abc`, `aabbcc`, `aaabbbccc`
2. Duas palavras que não pertencem: `aabbc`, `abc`... espera, `abc` pertence. Então: `aabcc`, `abbc`
3. Classe: não sei dizer.
4. Motivo: parece mais difícil que L2 porque agora são três símbolos pra contar ao mesmo tempo. Não sei que tipo de máquina precisaria para isso.

## 4. Autômato finito
Considere o autômato abaixo, sobre o alfabeto `{0,1}`:
```text
Estados: q0, q1, q2
Estado inicial: q0
Estado final: q2
Transições:
q0 --0--> q1
q0 --1--> q0
q1 --0--> q1
q1 --1--> q2
q2 --0--> q1
q2 --1--> q0
```
1. Esse autômato parece reconhecer cadeias que contêm `01` em algum ponto, ou seja, termina com `01` como sufixo relevante. Cadeias onde aparece um 0 seguido de 1 e o autômato chega em q2.

2. Execução manual:
   - `01` → q0 -0→ q1 -1→ q2 ✅ **aceita**
   - `101` → q0 -1→ q0 -0→ q1 -1→ q2 ✅ **aceita**
   - `100` → q0 -1→ q0 -0→ q1 -0→ q1 ❌ **rejeita**
   - `1101` → q0 -1→ q0 -1→ q0 -0→ q1 -1→ q2 ✅ **aceita**
   - `111` → q0 -1→ q0 -1→ q0 -1→ q0 ❌ **rejeita**

3. Tabela de caminho:

| Cadeia | Passo 1 | Passo 2 | Passo 3 | Passo 4 | Resultado |
|--------|---------|---------|---------|---------|-----------|
| `01`   | q0 →(0)→ q1 | q1 →(1)→ q2 | — | — | aceita |
| `100`  | q0 →(1)→ q0 | q0 →(0)→ q1 | q1 →(0)→ q1 | — | rejeita |

## 5. Gramática
Considere a gramática:
```text
S -> aS
S -> b
```
1. Cinco cadeias produzidas:
   - `b`
   - `ab`
   - `aab`
   - `aaab`
   - `aaaab`

2. A linguagem é formada por zero ou mais letras `a` seguidas de exatamente um `b` no final.

3. Parece regular. As regras são simples: sempre adiciona um `a` na frente ou termina com `b`. Não precisa contar nem guardar informação do passado, o que lembra o funcionamento de um autômato finito.

## 6. Ponto de dificuldade
Tópico escolhido: **linguagem livre de contexto**

1. O que eu entendo: sei que existe essa classe e que ela fica entre as linguagens regulares e algo mais complexo. Acho que está relacionada a gramáticas com regras mais flexíveis.
2. Onde eu me confundo: não sei exatamente o que a diferencia da linguagem regular, nem que tipo de autômato a reconhece.
3. Que tipo de explicação ajudaria: um exemplo lado a lado com uma linguagem regular, mostrando por que uma é regular e a outra não, com um exercício guiado depois.

## 7. Uso de IA, se houver
```text
Em algumas partes que nao lembrava,principalmente em relacao ao funcionamento dos automatos finitos
```
## Submissão no Moodle
Depois de finalizar, copie no Moodle:
```text
Repositório:
Commit final:
Autoavaliação: nível atual, maior dificuldade e tópico que precisa ser retomado.
```
