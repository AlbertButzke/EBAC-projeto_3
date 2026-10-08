# 🛒 Análise Exploratória de Preços e Descontos no Varejo Supermercadista

Projeto de Análise Exploratória de Dados (EDA) focado na avaliação estatística de políticas de precificação, distribuição de descontos e identificação de anomalias em uma rede de supermercados.

---

## 📌 Visão Geral do Projeto

O objetivo deste projeto é aplicar conceitos de **estatística descritiva** e **visualização de dados** para extrair *insights* sobre o portfólio de produtos, entender a dispersão de preços normais entre categorias e mapear a estratégia de descontos aplicada por categoria e marca.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

- **Python 3.14**
- [**Pandas**](https://pandas.pydata.org/): Tratamento, limpeza, agrupamento e cálculo de métricas estatísticas.
- [**Matplotlib**](https://matplotlib.org/): Visualizações estáticas com foco em boas práticas de *Data Storytelling* e *DataViz*.
- [**Plotly Express**](https://plotly.com/python/): Gráficos interativos e mapas hierárquicos (*Treemaps*).

---

## 📂 Estrutura dos Dados

A base de dados contém informações sobre itens comercializados, incluindo:

| Coluna | Descrição |
| :--- | :--- |
| `Title` | Nome do produto |
| `Marca` | Marca do fabricante |
| `Categoria` | Categoria mercadológica (em espanhol) |
| `Preco_Normal` | Preço de venda regular (sem desconto) |
| `Preco_Desconto`| Preço final com desconto aplicado |
| `Preco_Anterior`| Preço de referência anterior à promoção |
| `Desconto` | Montante total descontado |

---

## 🔍 Principais Etapas e Análises

### 1. Medidas de Tendência Central (Média vs. Mediana)
- Cálculo da média e mediana do `Preco_Normal` por categoria.
- **Insight:** A maioria das categorias (`lacteos`, `congelados`, `frutas`, etc.) apresenta **assimetria positiva** (média > mediana), evidenciando a presença de itens de alto valor que distorcem a média para cima. Apenas `comidas-preparadas` apresentou mediana superior à média.

### 2. Dispersão e Variabilidade (Desvio Padrão)
- Avaliação da volatilidade dos preços intra-categoria.
- **Insight:** A categoria **`lacteos`** apresentou o maior desvio padrão do catálogo, com a média superando a mediana em cerca de 2,4 vezes.

### 3. Detecção de Outliers e Diagnóstico de Causa-Raiz (Boxplot & IQR)
- Aplicação da regra do Intervalo Interquartil ($IQR = Q_3 - Q_1$) e limite superior ($Q_3 + 1.5 \times IQR$) para a categoria `lacteos`.
- **Diagnóstico de Negócio:** Investigando os *outliers* extremos (ex: leites com preços muito acima da mediana), identificou-se uma inconsistência cadastral: **produtos comercializados em fardos/engradados cadastrados como unidades simples**. Foi recomendada a normalização por *pack size* para derivar o preço unitário real.

### 4. Intensidade de Descontos por Categoria
- Gráfico de barras horizontal ordenado e limpo, evidenciando quais departamentos operam com maiores concessões médias de desconto.

### 5. Visão Hierárquica e Portfólio (Treemap Interativo)
- Gráfico *Treemap* interativo relacionando **Categoria > Marca**, dimensionado pelo **volume de produtos** cadastrados e colorido pela **intensidade média de desconto**.

---

## 🚀 Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/AlbertButzke/EBAC-projeto_3.git
   cd seu-repositorio
   ```

2. Crie e ative um ambiente virtual (opcional, mas recomendado):
   ```bash
   python -m venv venv
   # No Windows:
   venv\Scripts\activate
   # No Linux/Mac:
   source venv/bin/activate
   ```

3. Instale as dependências:
   ```bash
   pip install pandas matplotlib plotly
   ```

4. Certifique-se de que o arquivo da base (`MODULO7_PROJETOFINAL_BASE_SUPERMERCADO.csv`) está na raiz do diretório e execute o notebook ou script Python.

---

## 👤 Autor

Desenvolvido por **Felipe Alberto Butzke**  
*Sinta-se à vontade para conectar-se comigo via [LinkedIn](https://www.linkedin.com/in/felipe-alberto-butzke-649986317/) ou abrir uma Issue para sugestões!*