# **Projeto de Previsão de Vendas com Transformers**

Este projeto tem como objetivo prever as vendas semanais da Walmart utilizando técnicas avançadas de aprendizado profundo, especificamente **Transformers**, para capturar padrões temporais complexos e dependências de longo prazo nos dados. O modelo é treinado em um dataset público de vendas da Walmart, que inclui informações como lojas, departamentos, feriados, temperatura, preço do combustível, CPI e taxa de desemprego.

## **Objetivo do Projeto**
O objetivo principal é desenvolver um modelo de previsão de vendas que seja capaz de:
1. Prever as vendas semanais com alta precisão.
2. Capturar padrões sazonais, tendências e eventos especiais (como feriados).
3. Ser robusto a outliers e variações nos dados.
4. Fornecer insights sobre quais fatores impactam mais as vendas.

## **Tecnologias Utilizadas**
- **Linguagem**: Python
- **Frameworks**: PyTorch, Scikit-learn, Pandas, NumPy
- **Visualização**: Matplotlib, Seaborn
- **Modelagem**: Transformers, Multi-head Attention, LSTM
- **Pré-processamento**: RobustScaler, Log-transform

## **Estrutura do Projeto**
```
TFT/
├── walmart_sales.csv          # Dataset de vendas da Walmart
├── best_model.pth             # Modelo treinado salvo
├──  TFT_Walmart.ipynb         # Notebook
├── README.md                  # Este arquivo
└── requirements.txt           # Dependências do projeto
```
## **Como Executar o Projeto**

### **Pré-requisitos**
1. **Python 3.8+** instalado.
2. **Git** para clonar o repositório.
3. **GPU** (opcional, mas recomendado para treinamento mais rápido).

### **Passos para Execução**

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/RianMBarreto10/TFT
   cd TFT
   ```

2. **Instale as dependências**:
   ```bash
   pip install -r requirements.txt
   ```

## **Descrição do Código**

### **1. Pré-processamento**
- **Tratamento de datas**: Conversão para o formato `datetime`.
- **Feature engineering**:
  - Criação de features temporais (mês, semana do ano, trimestre).
  - Interação entre features (temperatura × preço do combustível).
  - Lag features (vendas das últimas 4 semanas).
- **Normalização**: Uso de `RobustScaler` para reduzir o impacto de outliers.
- **Transformação logarítmica**: Aplicada nas vendas para lidar com a escala ampla.

### **2. Modelagem**
- **Arquitetura Transformer**:
  - Multi-head Attention para capturar dependências temporais.
  - Camadas LSTM para modelar sequências de longo prazo.
  - Camadas densas para a saída final.
- **Função de perda**: Huber Loss, que é robusta a outliers.
- **Otimização**: AdamW com agendador de taxa de aprendizado cíclico.

### **3. Treinamento**
- **Early Stopping**: Interrompe o treinamento se a perda de validação não melhorar.
- **Validação temporal**: Divisão dos dados em treino e teste preservando a ordem temporal.
- **Métricas**: MAE, RMSE e MAPE para avaliação.

### **4. Avaliação**
- **Análise de resíduos**: Verificação de padrões nos erros de previsão.
- **Visualização**: Gráficos comparando valores reais e previstos.

## **Resultados Esperados**
| Métrica | Valor Esperado |
|---------|----------------|
| MAE     | 100,000 - 150,000 |
| RMSE    | 120,000 - 180,000 |
| MAPE    | 20% - 30%         |

## **Resultados Obtidos**
| Métrica | Valor Esperado |
|---------|----------------|
| MAE     | 0.10  |
| RMSE    | 0.14  |
| MAPE    | 0.74% |

## **Melhorias Futuras**
1. **Adicionar mais features**:
   - Informações externas como eventos locais, campanhas de marketing.
2. **Testar outras arquiteturas**:
   - Temporal Fusion Transformers (TFT).
   - Modelos híbridos (CNN + LSTM).
3. **Implementar cross-validation temporal**:
   - Para garantir robustez do modelo.
4. **Deploy do modelo**:
   - Integração com APIs para previsões em tempo real.

## **Contato**
- **Nome**: [Rian Barreto]
- **Email**: [rianbbb1@gmail.com]
- **LinkedIn**: [www.linkedin.com/in/rian-barretoML]
- **GitHub**: [RianMBarreto10]
