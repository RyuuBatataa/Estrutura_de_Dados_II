# Caderno do Estudante
# Projeto ConectaUDF: redes sociais com grafos
**Disciplina:** Algoritmos / Matemática Discreta / Ciência de Dados

**Alunos:** Isaque Kirmse / Liz Cristina

## 1. O desafio
Você faz parte da equipe que analisa a rede social fictícia **ConectaUDF**. Sua missão é representar as amizades em um grafo, realizar cálculos e usar Python para interpretar a estrutura da rede.

## 2. Conceitos essenciais
- **Vértice (ou nó):** representa um usuário.
- **Aresta:** representa uma amizade entre dois usuários.
- **Grau:** quantidade de conexões diretas de um usuário.
- **Caminho:** sequência de usuários em que cada par consecutivo está conectado.
- **Densidade:** proporção entre as amizades existentes e todas as amizades possíveis.

Neste projeto, a amizade é recíproca. Portanto, usamos um **grafo não direcionado**.

## 3. Conheça os usuários
| Código | Usuário |
|---|---|
| A | Isaque |
| B | Liz |
| C | Gabriel |
| D | Jamilly |
| E | Pedro |
| F | Eduarda |
| G | Vinicius |
| H | Ana |
| I | Fernando |
| J | Lucas |

As amizades são:
1. Isaque — Liz
2. Isaque — Gabriel
3. Isaque — Jamilly
4. Liz — Gabriel
5. Gabriel — Jamilly
6. Gabriel — Ana
7. Jamilly — Pedro
8. Jamilly — Eduarda
9. Jamilly — Ana
10. Pedro — Vinicius
11. Eduarda — Fernando
12. Vinicius — Fernando
13. Fernando — Lucas

---
### Resposta

![](imagem1.png)


---

## 4. Passo a passo: desenhe o grafo
1. Desenhe seis círculos, um para cada usuário.
2. Escreva o nome de cada pessoa dentro do círculo.
3. Para cada amizade da lista, desenhe uma linha entre os dois usuários.
4. Não desenhe duas linhas para a mesma amizade.
5. Confira se todas as oito amizades aparecem.

**Espaço para o seu desenho:** faça o grafo no caderno ou em uma ferramenta de desenho.
<img width="518" height="528" alt="WhatsApp Image 2026-11-08 at 22 27 27" src="https://github.com/user-attachments/assets/e3c6a8b6-5b19-4483-9e2e-abd18c4779dd" />

## 5. Passo a passo: calcule o grau
Conte quantas linhas chegam a cada círculo. Registre o resultado.

| Usuário | Amigos diretos | Grau |
|---|---|---:|
| Isaque | Liz, Gabriel, Jamilly | 3 |
| Liz | Isaque, Gabriel | 2 |
| Gabriel | Isaque, Liz, Jamilly, Ana | 4 |
| Jamilly | Isaque, Gabriel, Pedro, Eduarda, Ana | 5 |
| Pedro | Jamilly, Vinicius | 2 |
| Eduarda | Jamilly, Fernando | 2 |
| Vinicius | Pedro, Fernando | 2 |
| Ana | Gabriel, Jamilly | 2 |
| Fernando | Eduarda, Vinicius, Lucas | 3 |
| Lucas | Fernando | 1 |

**Pergunta 1:** quem tem mais conexões diretas?  
Resposta: Jamilly

## 6. Passo a passo: calcule o número de amizades
Some todos os graus. Como cada amizade conecta dois usuários, cada aresta é contada duas vezes.

**Fórmula:**  
`Número de arestas = soma dos graus ÷ 2`

1. Soma dos graus: 3 + 2 + 4 + 5 + 2 + 2 + 2 + 2 + 3 + 1 = 26
2. Divida por 2: 26 ÷ 2 = 13
3. Quantas amizades existem no grafo? 13

## 7. Passo a passo: calcule a densidade
A densidade compara as amizades existentes com o total de amizades possíveis.

Para um grafo simples não direcionado:

`D = 2 × E / (V × (V − 1))`

Em que:
- `D` = densidade;
- `E` = número de arestas;
- `V` = número de vértices.

Substitua os valores:
`D = 2 × 13 / (10 × (10 − 1))`

Resultado decimal: 0,2889  
Resultado percentual: 28,89%

**Interprete:** a rede tem poucas ou muitas das conexões possíveis? Explique com suas palavras.
**Resposta:** Possui poucas conexões possíveis porque o calculo mostrou que são quase 29% apenas das conexões possíveis.

________________________________________________________________

## 8. Passo a passo: represente o grafo em Python
A lista de adjacência registra, para cada usuário, os nomes de seus amigos. Digite o código em Python (por exemplo, no Google Colab ou em outro ambiente disponível).

```python
rede = {
    "Isaque": ["Liz", "Gabriel", "Jamilly"],
    "Liz": ["Isaque", "Gabriel"],
    "Gabriel": ["Isaque", "Liz", "Jamilly", "Ana"],
    "Jamilly": ["Isaque", "Gabriel", "Pedro", "Eduarda", "Ana"],
    "Pedro": ["Jamilly", "Vinicius"],
    "Eduarda": ["Jamilly", "Fernando"],
    "Vinicius": ["Pedro", "Fernando"],
    "Ana": ["Gabriel", "Jamilly"],
    "Fernando": ["Eduarda", "Vinicius", "Lucas"],
    "Lucas": ["Fernando"]
}

# Quantidade de usuarios
n = len(rede)

# Calcule o grau de cada usuario
for usuario, amigos in rede.items():
    print(usuario, "tem", len(amigos), "conexoes")

# A soma dos graus conta cada amizade duas vezes
soma_graus = sum(len(amigos) for amigos in rede.values())
arestas = soma_graus // 2

print("Total de usuarios:", n)
print("Total de amizades:", arestas)

# Densidade do grafo
densidade = (2 * arestas) / (n * (n - 1))
print(f"Densidade: {densidade:.2%}")
```

### Entenda o código
1. `rede` guarda os usuários e suas listas de amigos.
2. `len(rede)` conta os usuários.
3. `len(amigos)` calcula o grau de cada usuário.
4. `sum(...)` soma os graus.
5. `// 2` divide a soma por dois para contar cada amizade uma única vez.
6. A fórmula final calcula a densidade.

## 9. Passo a passo: encontre um caminho
Encontre um caminho de Ana até Felipe. Cada passagem por uma linha corresponde a uma aresta.

Exemplo de registro:
`Liz → Gabriel → Jamilly → Eduarda → Fernando → Lucas`

- Quantas arestas há no caminho? 5
- Você encontrou outro caminho com a mesma quantidade de arestas? Qual? Sim.
`Liz → Isaque → Jamilly → Eduarda → Fernando → Lucas`


________________________________________________________________

## 10. Desafio em grupo
Amplie a rede social:
1. Adicione pelo menos quatro usuários fictícios.
2. Crie no mínimo cinco novas amizades.
3. Atualize a lista de adjacência no Python.
4. Recalcule os graus, o total de arestas e a densidade.
5. Compare a densidade antes e depois da ampliação.
6. Identifique os usuários com mais conexões.
7. Explique como a rede poderia recomendar uma nova amizade.

## 11. Entrega
Entregue:
- desenho do grafo;
- tabela com os graus;
- cálculos de arestas e densidade;
- código Python executável;
- respostas às perguntas e breve conclusão.

## 12. Pergunta de reflexão
Duas pessoas ainda não são amigas, mas têm três amigos em comum. Como essa informação poderia ser usada para sugerir uma nova conexão? Quais cuidados de privacidade devem ser considerados ao analisar redes sociais?
