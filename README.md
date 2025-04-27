# Projeto de Aprendizado: Regressão Linear com Dados de Bitcoin

## 🎯 Objetivo

Este projeto foi desenvolvido como um exercício de aprendizado pessoal. O principal objetivo é aplicar e entender os passos básicos para implementar um modelo de Regressão Linear em R, utilizando dados financeiros reais (cotação do Bitcoin).

## 📖 Descrição

O código neste repositório realiza as seguintes etapas:

1.  **Coleta de Dados:** Busca dados históricos de cotação do Bitcoin (BTC-USD) usando a biblioteca `tidyquant`.
2.  **Engenharia de Features:** Cria novas variáveis (features) a partir dos dados brutos, como:
    * Retorno diário percentual (`Retorno`).
    * Série temporal suavizada de retornos percentuais (`Retorno_p`).
    * Proporção do movimento do preço diário (`Proporcao`).
    * Desvio padrão móvel dos retornos (`Desvio`), usado como proxy para volatilidade.
    * Variável Alvo (`Alvo`): A volatilidade futura (desvio padrão dos retornos) deslocada para `n` períodos no futuro. O objetivo é prever essa volatilidade futura.
3.  **Análise Exploratória:** Visualiza a distribuição da variável alvo e calcula a correlação entre as features e a variável alvo, incluindo um heatmap.
4.  **Preparação dos Dados:** Limpa dados (remove `NA` e `Inf`), divide o conjunto de dados em treino (até final de 2020) e teste (de 2021 em diante).
5.  **Modelagem:** Treina um modelo de Regressão Linear (`lm`) usando as features criadas para prever a variável `Alvo` nos dados de treino.
6.  **Previsão:** Utiliza o modelo treinado para fazer previsões nos dados de treino e teste.
7.  **Avaliação:**
    * Calcula métricas de erro como MAE (Mean Absolute Error) e RMSE (Root Mean Squared Error) para os conjuntos de treino e teste.
    * Calcula o R² (R-squared) para o conjunto de treino.
    * Compara as previsões com os valores reais através de gráficos (scatter plot e série temporal).
    * Analisa a capacidade do modelo em prever a *direção* do movimento da volatilidade e se ela está acima ou abaixo de um limiar.
8.  **Análise de Resíduos:** Examina os resíduos do modelo (diferença entre real e previsto) para verificar algumas suposições da regressão linear, usando gráficos como:
    * Resíduos vs. Valores Ajustados.
    * Q-Q Plot.
    * Gráficos de Regressão Parcial (Added Variable Plots).

## 🛠️ Ferramentas e Bibliotecas Utilizadas

* Linguagem: **R**
* Pacotes utilizados:
    * `tidyquant`: Para obter dados financeiros.
    * `ggplot2`: Para visualização de dados.
    * `dplyr`: Para manipulação de dados.
    * `zoo`: Para funções de janela móvel (`rollapply`).
    * `Metrics`: Para calcular métricas de erro (MAE, RMSE).
    * `reshape2`: Para manipulação de dados (usado no heatmap).
    * `scales`: Para formatação de eixos em gráficos.
    * `broom`: Para trabalhar com outputs de modelos.
    * `patchwork`: Para combinar múltiplos gráficos `ggplot`.

## 🚀 Como Executar (se desejar replicar)

1.  Certifique-se de ter o R e o RStudio (ou outro IDE) instalados.
2.  Instale as bibliotecas necessárias:
    ```R
    install.packages(c("tidyquant", "ggplot2", "reshape2", "scales", "zoo", "dplyr", "Metrics", "broom", "patchwork"))
    ```
3.  Execute o script R fornecido.

## ⚠️ Observações

* Este é um projeto **estritamente educacional** para praticar conceitos de regressão linear.
* O modelo gerado **não tem a intenção de ser usado para previsões financeiras reais** ou tomadas de decisão de investimento. Modelos financeiros reais exigem muito mais complexidade, validação rigorosa e consideração de outros fatores.
* O foco foi no processo de implementação e nos passos básicos da modelagem, não na otimização do modelo ou na obtenção de métricas de performance excepcionais.
