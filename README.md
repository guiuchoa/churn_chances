# churn_chances

# 📉 Predição de Churn de Clientes com Regressão Logística

Este projeto consiste em um pipeline de Machine Learning para prever o cancelamento de clientes (Churn) em um serviço de assinatura fictício. O objetivo é identificar os principais fatores que levam um cliente a cancelar o serviço e calcular a probabilidade de saída.

## 📋 Sobre o Projeto

O projeto foi dividido em duas etapas principais:
1.  **Geração de Dados Fictícios:** Criação de uma base de dados realista simulando um cenário de telecomunicações/assinaturas.
2.  **Modelagem Preditiva:** Criação de um notebook de regressão logística para o cenário de *Churn*.

### 🔍 Estrutura dos Dados (`base_churn.csv`)
A base gerada contém 2000 registros com as seguintes colunas:
* `ID_Contrato` / `ID_Usuario`: Identificadores únicos.
* `Tipo_Plano`: Básico, Padrão, Premium, etc.
* `Canal_Venda`: Origem do cliente (App, Site, Loja).
* `Forma_Pagamento`: Cartão, Boleto, PIX.
* `Suporte_Acionado`: Quantidade de vezes que o cliente contatou o suporte.
* `Data_Inicio_Contrato` e `Data_Ultimo_Login`: Datas para cálculo de fidelidade (Tenure).
* `Cancelou`: Variável alvo (**Sim** ou **Não**).

## 🛠️ Tecnologias Utilizadas

* **Python**
* **Pandas & NumPy:** Manipulação de dados e engenharia de atributos.
* **Scikit-Learn:**
    * `LogisticRegressionCV`: Modelo linear com validação cruzada (Lasso).
    * `Pipeline` & `ColumnTransformer`: Pré-processamento robusto.
    * Métricas: Acurácia, AUC-ROC, Matriz de Confusão.
* **Matplotlib & Seaborn:** Visualização de dados e gráficos de performance.

## 🚀 Como Executar

1.  **Clone o repositório** (ou baixe os arquivos).
2.  **Instale as dependências**:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3.  **Execute o Notebook**:
    Abra o Jupyter Notebook ou script Python principal. O fluxo de execução é:
    * Carregamento e limpeza.
    * Engenharia de features (Cálculo de *Tenure* e Recência).
    * Treinamento do Pipeline.
    * Exibição das métricas e coeficientes.


## 📈 Resultados e Interpretação

O modelo utiliza **Regressão Logística com regularização L1 (Lasso)**, permitindo interpretar os coeficientes como *Odds Ratios*:

* **Fatores de Risco (Aumentam Churn):**
    * Alta frequência de contato com suporte (`Suporte_Acionado`).
    * Pagamento via Boleto Bancário.
* **Fatores de Proteção (Reduzem Churn):**
    * Planos do tipo "Premium" ou "Empresarial".
    * Maior tempo de contrato (Clientes antigos tendem a ser mais fiéis).
