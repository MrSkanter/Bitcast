# BitCast  
Tentativa de construir um modelo preditivo aplicado ao mercado de criptomoedas, utilizando dados históricos do Bitcoin.

📚 **Sumário**
- [Descrição do Projeto](#descrição-do-projeto)  
- [Objetivos](#objetivos)  
- [Dados](#Dados)    
- [Modelagem](#modelagem)  
- [Resultados](#resultados)  
- [Como Executar](#como-executar)  
- [Licença](#licença)  

---

## 🧠 *Descrição do Projeto*  
**BitCast** é um projeto de análise de séries temporais financeiras que busca prever a volatilidade do Bitcoin através de:
- Análise exploratória de dados históricos  
- Engenharia de features específicas para mercados voláteis  
- Modelagem estatística com regressão linear  

### 🔄 **Fases do Projeto**  

#### **Fase 1 - Modelagem Preditiva**  
- Desenvolvimento de modelo de regressão linear  
- Análise comparativa entre períodos históricos
- Validação estatística com métricas financeiras  

#### **Fase 2 - Implementação Prática** *(Futuro)*  
| Módulo           | Funcionalidades Principais                     | Status       |  
|------------------|-----------------------------------------------|-------------|  
| **API REST**     | Previsões em tempo real, documentação Swagger | Planejado   |  
| **Telegram Bot** | Alertas automáticos, histórico de previsões   | Em design   |  
**Atenção**: Projeto com fins educacionais, não recomendado para decisões financeiras reais.

## 🎯 Objetivos  

### **Objetivo Principal**  
Prever a volatilidade dos retornos do Bitcoin em X períodos à frente usando regressão linear. 
1. Prever (ou tentar) o preço de fechamento do Bitcoin    
2. Aprender a avaliar modelos
3. Entender suas limitações estatísticas 

### **Metodologia**  

#### **Variaveis**  
📌 **Variáveis Preditoras:**  
- `Direção`: Tendência binária do dia anterior
- `Distancia`: Variação absoluta de preço
- `Volatilidade`: Amplitude de movimentação do retorno

Obs: estamos trabalhando a Volatilidade do Retorno

### 🎯 **Variável Alvo**
- `Alvo`: Volatilidade futura a ser prevista X períodos à frente 

### ✔ **Validação Cruzada**  
- `Holdout`: Divisão temporal (train: 70%, test: 30%)
- `Acuracia`: Acerta se volatilidade vai subir/descer?

### ⚠ **Limitações Técnicas**  
### 1. **Natureza Não-Linear dos Mercados**
- 📉 A regressão linear assume relações lineares, enquanto a volatilidade de criptomoedas:
  - Tem picos abruptos (*flash crashes*)
  - Responde a eventos não quantificáveis (ex.: tweets de Elon Musk)

### **Saídas Esperadas**  
📊 Modelo linear com:
- ✅ Gráfico comparativo previsão vs realidade
- 🔍 Diagnóstico estatístico completo

## 📊 *Dados*

### **Fontes**
- Dados diários do Bitcoin via Yahoo Finance (YFinance.jl)
- Períodos comparativos:
  - 2015-2025 
  - 2020-2025 

### **Variáveis**
| Coluna | Descrição | Tipo |
|--------|-----------|------|
| `open` | Preço de abertura | Float |
| `high` | Máxima do dia | Float |
| `low` | Mínima do dia | Float |
| `close` | Preço de fechamento | Float |
| `adjusted_close` | Fechamento ajustado | Float |

### **Pré-processamento**
1. Download automático com pacote do Yahoo Finance
2. Filtro de datas por período
3. Cálculo de variaveis
4. Remoção de missing values