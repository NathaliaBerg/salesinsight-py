# SalesInsight PY — Análise e Visualização de Dados de Vendas

## 🎯 Objetivo do Projeto

Este mini-projeto foi desenvolvido como parte da Avaliação M1.1 do curso SCTEC/SENAI-SC (Módulo 01). O objetivo é simular a rotina de um Analista de Dados Júnior em uma empresa de varejo: carregar, limpar, transformar, agregar e visualizar um dataset de vendas, gerando insights relevantes para uma reunião trimestral da diretoria.

O fluxo responde a perguntas de negócio como:
- Como as vendas se comportam ao longo do tempo (mês e trimestre)?
- Quais produtos e categorias geram mais receita?
- Quais regiões têm melhor desempenho?
- Quais clientes são mais valiosos (segmentação Bronze/Prata/Ouro)?
- Existe relação entre quantidade vendida e receita gerada por transação?

## ⚙️ Instalação e Execução

### Opção 1 — Google Colab (recomendado)
1. Faça upload do arquivo `.ipynb` para o [Google Colab](https://colab.research.google.com)
2. Execute as células em ordem (Ambiente de execução > Executar tudo)
3. O Colab já possui Pandas, NumPy, Matplotlib e Seaborn pré-instalados

### Opção 2 — Local (VS Code ou terminal)
```bash
pip install pandas numpy matplotlib seaborn
python salesinsight.py
```

O script gera automaticamente:
- `vendas.csv` — dataset de vendas (bruto ou limpo, conforme etapa)
- `relatorio_clientes.csv` — segmentação de clientes por nível de gasto
- `estatisticas.json` — métricas agregadas e relatório de limpeza
- `grafico_linha_receita_mes.png`, `grafico_barras_top_produtos.png`, `grafico_dispersao_qtd_receita.png`, `painel_subplots.png`

## 🧠 Conceitos de Python e Análise de Dados Aplicados

**Lógica e estruturas de dados**
- Condicionais (`if/elif/else`) para classificação de faixas e segmentos
- Listas, tuplas e dicionários (retorno de função de limpeza como tupla `(df, relatório)`)

**Manipulação de arquivos**
- Leitura e escrita de CSV (`pd.read_csv()`, `.to_csv()`)
- Leitura e escrita de JSON (`json.dump()`, `json.load()`)

**Datas e textos**
- Módulo `datetime` para extração de mês, trimestre e ano
- Expressões regulares (`re.sub()`, `re.compile()`) na padronização de textos e nomes de clientes

**Funções**
- Funções com parâmetros, retorno e docstring em todo o fluxo
- Funções `lambda` na segmentação de clientes (Bronze/Prata/Ouro)
- Função de ordem superior `processar_coluna()`, que recebe outra função (ex: `np.mean`) como argumento

**Pandas**
- Leitura, filtros, seleções e `groupby` (agregações por mês, produto, categoria e região)

**NumPy**
- Conversão de colunas para array com `.to_numpy()`
- Operações vetorizadas e broadcasting (sem laços `for`/`while`)
- Filtragem booleana sobre arrays
- Transformação condicional vetorizada com `np.select()` (coluna `faixa_receita_item`)

**Visualização (Matplotlib / Seaborn)**
- Gráfico de linha (receita por mês)
- Gráfico de barras (top 5 produtos)
- Gráfico de dispersão (quantidade × receita)
- Painel com `subplots()` 2×2 e `fig.suptitle()`
- Customização completa (título, rótulos, legenda, paleta, `figsize`) e exportação em PNG com `plt.savefig()`

**Orientação a Objetos**
- Classe `AnalisadorDeVendas` com `__init__`, atributos (`self.df`, `self.estatisticas`, `self.segmentacao`) e métodos que organizam o fluxo completo (`limpar`, `criar_colunas`, `segmentar_clientes`, `calcular_estatisticas_numpy`, `gerar_graficos`)

**Fluxo de execução**
- Função `main()` e bloco `if __name__ == "__main__":` como ponto de entrada único do projeto

## 📊 Estrutura do Fluxo

```
Carregar dataset bruto
        ↓
Limpar dados (nulos, datas inválidas, regex) → relatório de limpeza
        ↓
Criar colunas derivadas (receita_total, mes, trimestre, ano, faixa_receita_item)
        ↓
Segmentar clientes (Bronze / Prata / Ouro)
        ↓
Calcular estatísticas com NumPy (vetorizado, sem loops)
        ↓
Gerar visualizações (linha, barra, dispersão, painel 2x2)
        ↓
Exportar resultados (CSV + JSON) e reler JSON para conferência
```

## 🗂️ Organização do Projeto

- **Repositório:** https://github.com/NathaliaBerg/salesinsight-py
- **Kanban:** https://trello.com/invite/b/6a92518ed5e351ae0c4d1ea0/ATTIa45c851c74408f53376cd8cb0d5dd0aaB50116A0/backlogsalesinsight
- **Vídeo de demonstração:** https://youtu.be/a2rc0Y8TxmA

## 🚀 Possíveis Melhorias Futuras

- Implementar herança com `AnalisadorComProjecao` (subclasse com `super()`)
- Adicionar projeção simples de tendência por média móvel
- Enriquecer o dataset com tabela auxiliar via `merge` ou `pivot`
- Tratamento estatístico de outliers e normalização (conteúdo de semanas futuras do módulo)

## 👤 Autoria

Projeto desenvolvido individualmente como parte da Avaliação M1.1 — SCTEC/SENAI-SC, Módulo 01.
