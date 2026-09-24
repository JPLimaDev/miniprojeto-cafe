# miniprojeto-cafe
Realizando a criação de um miniprojeto sobre café para análise de dados

## Sobre o projeto
Projeto de estudo de **limpeza e análise de dados** com Python e pandas, usando um dataset de vendas de uma cafeteria com dados propositalmente "sujos" (valores nulos, `ERROR`, `UNKNOWN` e tipos incorretos).

## Dataset
Arquivo: `dirty_cafe_sales.csv` (10.000 linhas, 8 colunas)

| Coluna | Descrição |
|---|---|
| Transaction ID | Identificador da transação |
| Item | Produto vendido (Coffee, Cake, Salad...) |
| Quantity | Quantidade vendida |
| Price Per Unit | Preço unitário |
| Total Spent | Valor total da venda |
| Payment Method | Forma de pagamento |
| Location | Local da venda (In-store / Takeaway) |
| Transaction Date | Data da transação |

## Tecnologias
- Python
- pandas
- NumPy
- Jupyter Notebook

## Etapas realizadas
- [x] Leitura do CSV e exploração inicial (`head`, `info`, `describe`)
- [x] Verificação de valores nulos e linhas duplicadas
- [x] Diagnóstico dos tipos incorretos (valores `ERROR` e `UNKNOWN` misturados)
- [x] Conversão das colunas numéricas (`to_numeric`) e de data (`to_datetime`)
- [x] Substituição de `ERROR`/`UNKNOWN` por `NaN` nas colunas de texto
- [x] Criação de uma cópia sem datas nulas para análises temporais

## Próximos passos
- [ ] Recuperar `Price Per Unit` a partir do `Item`
- [ ] Preencher `Quantity`, `Price Per Unit` e `Total Spent` pela relação `Total = Quantidade × Preço`
- [ ] Preencher categorias ausentes com `"Unknown"`
- [ ] Remover linhas irrecuperáveis e exportar o dataset limpo
- [ ] Análises: faturamento por item, forma de pagamento, local e mês
- [ ] Visualizações com gráficos

## Como executar
```bash
pip install pandas numpy jupyter
jupyter notebook miniprojeto-cafe.ipynb
```
