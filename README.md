# Projeto Final - Predição de Óbito em Pacientes com SRAG

## Integrantes do Grupo
* **Pedro Medeiros**
* **Virginia Prettz**
* **Vinicius Henrique**

## Objetivo
Desenvolver um modelo preditivo capaz de identificar o risco de óbito em pacientes com Síndrome Respiratória Aguda Grave (SRAG), utilizando dados de sintomas e comorbidades.

## Subproblema Escolhido
Predição de Óbito e Fatores de Risco em Pacientes com SRAG.

## Base de Dados
* **Fonte:** OpenDataSUS
* **Período:** 2013 a 2018
* **Total de Registros:** 185.313 casos (após limpeza)

## Metodologia

### 1. Coleta e Unificação
Integração de 6 bases anuais (2013-2018) do INFLUD, tratando encoding `latin1` e separadores específicos do DataSUS.

### 2. Seleção de Variáveis
Filtro de variáveis relevantes em 4 grupos:
- Demográficas (idade, sexo, UF)
- Sintomas respiratórios (febre, tosse, dispneia)
- Comorbidades (cardiopatia, pneumopatia, obesidade)
- Desfecho (cura ou óbito)

### 3. Limpeza de Dados
- Remoção de colunas com 100% de valores nulos
- Conversão do formato codificado de idade
- Filtro de casos com desfecho definido (cura ou óbito)
- Criação da variável alvo binária `OBITO`

### 4. Pré-processamento
- Padronização de variáveis dicotômicas (sintomas e comorbidades)
- One-hot encoding para variável categórica (sexo)
- Imputação de valores ausentes na idade com mediana
- Escalonamento de features com `StandardScaler`

### 5. Modelagem
**Algoritmo:** Regressão Logística com `class_weight='balanced'`

**Divisão dos Dados:** 70% treino / 30% teste (estratificada)

## Resultados

### Modelo V1 (Limiar padrão 0.50)
- **AUC-ROC:** 0.79
- **Acurácia:** 73%
- **Recall (Óbito):** 72%
- **Precisão (Óbito):** 31%

### Modelo V2 (Limiar ajustado 0.60)
- **Acurácia:** 78% (+5%)
- **Recall (Óbito):** 61% (-11%)
- **Precisão (Óbito):** 35% (+4%)
- **Redução de Falsos Positivos:** 583 casos

## Conclusão
O modelo V2 demonstrou melhor equilíbrio entre sensibilidade e especificidade, sendo mais adequado para aplicação clínica ao reduzir alarmes falsos sem comprometer significativamente a detecção de casos graves.

## Tecnologias Utilizadas
- Python 3.x
- Pandas
- Scikit-learn
- Matplotlib / Seaborn

## Estrutura do Repositório
```
data-science-project/
├── Entrega_4_Virginia_Pedro_Vinicius.ipynb  # Notebook principal
└── README.md                                 # Este arquivo
```

---

**Disciplina:** Ciência de Dados  
**Ano:** 2024
