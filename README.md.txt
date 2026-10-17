# 📊 Simulador de Investimentos em FIIs

Ferramenta desenvolvida no Excel com **interface estilo aplicativo (App UI)** para simulação de acúmulo de patrimônio e dividendos mensais através de **Fundos de Investimento Imobiliário (FIIs)**.

---

## 💡 Pergunta e Estrutura do Negócio

A ferramenta foi projetada para ser simples e intuitiva, permitindo que qualquer pessoa simule seus investimentos sem necessidade de conhecimentos técnicos no Excel. Ela responde diretamente a **5 perguntas centrais de negócio**:

1. **Quanto investir por mês?**  
   👉 *Onde aparece:* Na célula **C9** (ou `aporte`), onde o usuário digita o valor desejado ou usa a sugestão de 30% do salário.
2. **Por quantos anos?**  
   👉 *Onde aparece:* Na célula **C10** (ou `prazo_anos`), onde se insere o tempo da aplicação.
3. **Qual a taxa de rendimento mensal?**  
   👉 *Onde aparece:* Na célula **C11** (ou `taxa_mensal`), informada pelo usuário (ex: 0,80%).
4. **Quanto de patrimônio vai acumular?**  
   👉 *Onde aparece:* Nos **Resultados Principais (C14)** e na tabela de **Projeção de Cenários (F7:H12)** para prazos de 2 a 30 anos.
5. **Quanto vai receber de dividendos por mês?**  
   👉 *Onde aparece:* Nos **Resultados Principais (C15)** e ao lado de cada cenário de tempo na coluna H.

---

## 📐 Fórmulas Utilizadas: VF e PROCV

* **`VF` (Valor Futuro):**  
  Utilizada para calcular o crescimento do patrimônio com aportes mensais recorrentes sob juros compostos.  
  *Exemplo:* `=VF(taxa_mensal; prazo_anos*12; -aporte; 0; 0)`

* **`PROCV` (Procura Vertical):**  
  Utilizada na aba principal para buscar dinamicamente na aba `Apoio` o percentual de alocação de cada tipo de FII com base no perfil selecionado. Utiliza uma **Chave Composta** (`Perfil + Tipo de FII`).  
  *Exemplo:* `=PROCV($D$18 & B21; Apoio!A:D; 4; FALSO)`

---

## 🏷️ Intervalos Nomeados Criados

Para tornar as fórmulas legíveis e evitar erros com referências de células, foram definidos os seguintes intervalos nomeados no Excel:

| Nome do Intervalo | Célula de Origem | Descrição |
| :--- | :--- | :--- |
| `aporte` | `C9` | Valor em R$ que o usuário escolheu aportar mensalmente |
| `prazo_anos` | `C10` | Período total em anos da simulação |
| `taxa_mensal` | `C11` | Rentabilidade média mensal esperada (%) |

---

## 🎯 Divisão da Carteira por Perfil de Investidor

Na aba de apoio (`Apoio`), a alocação foi distribuída garantindo que **a soma de cada perfil resulte sempre em 100%**:

| Tipo de FII | Conservador | Moderado | Arrojado |
| :--- | :---: | :---: | :---: |
| **Tijolo** | 50,0% | 40,0% | 25,0% |
| **Papel** | 30,0% | 35,0% | 35,0% |
| **FOF** | 20,0% | 15,0% | 10,0% |
| **Desenvolvimento** | 0,0% | 5,0% | 15,0% |
| **Infraestrutura** | 0,0% | 5,0% | 10,0% |
| **Outros** | 0,0% | 0,0% | 5,0% |
| **TOTAL** | **100%** | **100%** | **100%** |

*Nota: Os percentuais acima são meramente ilustrativos para a simulação e não constituem recomendação de investimento.*

---

## 🛠️ Melhorias e Ajustes em Relação à Versão do Expert

1. **Design App UI sem Gridlines:** Removidas as linhas de grade padrão para dar um aspecto de aplicativo executável.
2. **Ajuste de Alinhamento e Espaçamento:** Ajuste nas colunas centrais e mesclagem de cabeçalhos para eliminar "buracos" e espaços em branco na visualização.
3. **Gráfico Dinâmico Integrado:** Inclusão de um gráfico de pizza automatizado que reflete instantaneamente a alteração de perfil selecionada pelo usuário.
4. **Padronização de Chaves Compostas:** Normalização dos nomes entre a aba do simulador e a aba de apoio (ex: alinhando o termo `Infraestrutura`) para eliminar erros do tipo `#N/A`.

---

## 📸 Evidências de Funcionamento (Prints)

### 1. Simulação com Perfil **Moderado**
*(Insira a imagem aqui)*
`![Simulação Perfil Moderado](./prints/simulacao_moderado.png)`

### 2. Simulação com Perfil **Arrojado** / **Conservador**
*(Insira a imagem aqui)*
`![Simulação Perfil Arrojado](./prints/simulacao_arrojado.png)`