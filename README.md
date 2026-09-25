# miniprojeto-cafe
Realizando a criação de um miniprojeto sobre café para análise de dados

## Sobre o projeto
Projeto de estudo de **limpeza e análise de dados** com Python e pandas, usando um dataset de vendas de uma cafeteria com dados propositalmente "sujos" (valores nulos, `ERROR`, `UNKNOWN` e tipos incorretos).

## Dataset
Arquivo original: `dirty_cafe_sales.csv` (10.000 linhas, 8 colunas)
Arquivo tratado: `miniprojeto-cafe-limpo.csv` (9.974 linhas)

| Coluna | Descrição |
|---|---|
| Transaction ID | Identificador da transação |
| Item | Produto vendido (Coffee, Cake, Salad...) |
| Quantity | Quantidade vendida |
| Price Per Unit | Preço unitário |
| Total Spent | Valor total da venda |
| Payment Method | Forma de pagamento |
| Location | Local da venda (In-store / Takeaway) |
| Transaction Date | Data da transação (todas de 2023) |

## Tecnologias
- Python
- pandas
- NumPy
- Matplotlib
- Jupyter Notebook

## Etapas realizadas

### Exploração
- [x] Leitura do CSV e exploração inicial (`head`, `info`, `describe`)
- [x] Verificação de valores nulos e linhas duplicadas
- [x] Diagnóstico dos tipos incorretos (valores `ERROR` e `UNKNOWN` misturados)

### Limpeza
- [x] Conversão das colunas numéricas (`to_numeric`) e de data (`to_datetime`)
- [x] Substituição de `ERROR`/`UNKNOWN` por `NaN` nas colunas de texto
- [x] Recuperação do `Price Per Unit` a partir do `Item`, já que cada item tem um preço fixo (`groupby` + `map`)
- [x] Preenchimento de `Quantity`, `Price Per Unit` e `Total Spent` pela relação `Total = Quantidade × Preço`
- [x] Remoção das 26 linhas irrecuperáveis (com 2 ou mais valores numéricos ausentes)
- [x] Recuperação do `Item` a partir do preço, só para preços exclusivos de um item (Coffee, Cookie, Salad e Tea)
- [x] Preenchimento das categorias restantes (`Item`, `Payment Method`, `Location`) com `"Unknown"`
- [x] Criação de uma cópia sem datas nulas (`df_datas`) para as análises temporais
- [x] Exportação do dataset limpo

### Resultado da limpeza
| Coluna | Nulos antes | Nulos depois |
|---|---|---|
| Item | 969 | 0 |
| Quantity | 479 | 0 |
| Price Per Unit | 533 | 0 |
| Total Spent | 502 | 0 |
| Payment Method | 3178 | 0 |
| Location | 3961 | 0 |
| Transaction Date | 460 | 460* |

\* Não é possível recuperar a data. Essas vendas ficam no dataset para as análises por produto, mas são excluídas das análises temporais (~4,6% das vendas).

### Análises
- [x] Faturamento e quantidade vendida por produto
- [x] Faturamento, unidades vendidas e número de vendas por mês
- [x] Gráficos: faturamento por produto (barras) e faturamento mensal (linha)

## Principais resultados (2023)
- **Salad** é o produto que mais fatura (19.095), por ter o maior preço (5.0).
- **Coffee** é o produto que mais vende em unidades (3.904), mas fatura menos por ser barato (2.0).
- O faturamento mensal é **estável**, entre ~6.600 e ~7.350, sem sazonalidade forte.
- ~58% das vendas não registram forma de pagamento ou local, o que indica uma falha no registro do caixa.

## Próximos passos
- [ ] Análises por forma de pagamento e por local
- [ ] Quantidade vendida por mês e por item
- [ ] Gráficos das demais análises

## Como executar
```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook miniprojeto-cafe.ipynb
```
