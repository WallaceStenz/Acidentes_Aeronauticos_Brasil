# ✈️ Analise de Acidentes Aereos no Brasil

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Status](https://img.shields.io/badge/Status-Concluido-green)
![ML](https://img.shields.io/badge/Machine%20Learning-Random%20Forest%20%7C%20Gradient%20Boosting-orange)

## 📌 Sobre o Projeto

Analise exploratoria e preditiva de acidentes aereos ocorridos no Brasil entre **2008 e 2017**, utilizando dados do CENIPA (Centro de Investigacao e Prevencao de Acidentes Aeronauticos) obtidos no Kaggle.

O objetivo principal foi identificar padroes nas ocorrencias aereas e construir um modelo de Machine Learning capaz de **prever se um acidente resultara em fatalidade**.

---

## 📂 Dataset

- **Fonte:** [Kaggle — Acidentes Aereos no Brasil](https://www.kaggle.com)
- **Periodo:** 2008 a 2017
- **Registros:** 5.116 ocorrencias
- **Colunas:** 116 variaveis (classificacao, aeronave, fatores contribuintes, etc.)

---

## 🔍 Principais Insights da EDA

### Analise Temporal
- **2012 e 2013** foram os anos com mais ocorrencias (~625 cada)
- Tendencia de **queda consistente** a partir de 2013, sugerindo melhoria nas regulacoes
- **Junho e Agosto** sao os meses com menos ocorrencias
- **Janeiro** lidera em ocorrencias — periodo de ferias e maior trafego aereo

### Fatalidades
- **ACIDENTE** concentra praticamente 100% das fatalidades
- A fase de **CRUZEIRO** e a mais letal, mesmo nao sendo a mais frequente
- **DECOLAGEM** e a fase com mais acidentes no total
- **VOO REGULAR** tem taxa de letalidade de 1.0 — todo acidente vira tragedia
- **VOO PRIVADO** lidera em numero de acidentes mas com danos relativamente menores
- **VOO DE INSTRUÇÃO** tem a menor taxa de letalidade (~0.20)

### Analise Geografica
- **Sao Paulo** concentra o maior numero de acidentes e fatalidades do Brasil
- Importante ressaltar: SP tambem tem o maior volume de trafego aereo do pais

---

## 🤖 Machine Learning

### Objetivo
Classificacao binaria: prever se um acidente aereo resultara em fatalidade (`True/False`)

### Desafio
Dataset **desbalanceado** — apenas 8% dos registros com fatalidade vs 92% sem.

### Features Utilizadas
| Feature | Descricao |
|---|---|
| ocorrencia_classificacao | Tipo da ocorrencia (Acidente, Incidente) |
| aeronave_nivel_dano | Nivel de dano da aeronave |
| aeronave_fase_voo | Fase do voo no momento da ocorrencia |
| aeronave_tipo_operacao | Tipo de operacao (privado, regular, etc.) |
| aeronave_segmento_aviacao | Segmento da aviacao |
| ocorrencia_uf | Estado da ocorrencia |
| mes | Mes da ocorrencia |

### Resultados

| Modelo | Precision | Recall | F1-Score |
|---|---|---|---|
| Random Forest | 0.64 | 0.64 | 0.64 |
| **Gradient Boosting** | 0.55 | **0.79** | 0.65 |

### Modelo Escolhido
**Gradient Boosting** — em seguranca aerea, **recall e a metrica mais critica**. E preferivel alertar um falso positivo do que deixar passar um acidente fatal real. O Gradient Boosting identificou 79% dos acidentes fatais corretamente.

### Feature Importance (Random Forest)
1. `ocorrencia_classificacao` — 35%
2. `aeronave_nivel_dano` — 22%
3. `aeronave_fase_voo` — 13%
4. `ocorrencia_uf` — 9%

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.10+**
- **Pandas** — manipulacao e limpeza de dados
- **NumPy** — operacoes numericas
- **Matplotlib / Seaborn** — visualizacoes
- **Scikit-learn** — Machine Learning

---

## 📁 Estrutura do Projeto

```
📦 acidentes-aereos
 ┣ 📄 accidents.csv          # Dataset original
 ┣ 📓 analise.ipynb          # Notebook com toda a analise
 ┗ 📄 README.md              # Este arquivo
```

---

## 🚀 Como Executar

```bash
# Clone o repositorio
git clone https://github.com/seu-usuario/acidentes-aereos

# Instale as dependencias
pip install pandas numpy matplotlib seaborn scikit-learn

# Abra o notebook
jupyter notebook analise.ipynb
```

---

## 📈 Proximos Passos

- [ ] Dashboard interativo com Streamlit
- [ ] Testar XGBoost e LightGBM
- [ ] Aplicar SMOTE para balanceamento mais sofisticado
- [ ] Deploy do modelo como API

---

## 👤 Autor

Desenvolvido como projeto de portfolio em Data Science.

---

## 📜 Licenca

Este projeto esta sob a licenca MIT.
