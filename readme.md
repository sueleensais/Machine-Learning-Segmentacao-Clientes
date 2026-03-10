# Clusterização Estratégica para Personalização de Campanhas de Marketing

## Descrição do Projeto
Este projeto tem como objetivo a segmentação estratégica de uma base de clientes utilizando técnicas de aprendizado de máquina não supervisionado. Através do algoritmo K-Means, os clientes são agrupados com base em perfis sociodemográficos e de consumo (idade, renda anual e pontuação de gastos). 

A solução integra o processamento estatístico em Python com a visualização analítica no Power BI, permitindo que gestores de marketing identifiquem clusters específicos para a personalização de campanhas e otimização de alocação de recursos.

## Pipeline do Projeto
1. Coleta e Extração 
2. Análise Exploratória e Estatística Descritiva 
3. Pré-Processamento e Padronização de Atributos 
4. Implementação e Treinamento do Modelo de Clusterização 
5. Exportação e Integração de Dados 
6. Visualização Analítica e Dashboards 

## Objetivos Técnicos
* **Análise Multivariada:** Avaliação da distribuição e consistência das variáveis de idade, renda e comportamento de gastos.
* **Padronização Estatística:** Aplicação de StandardScaler para garantir que variáveis em escalas distintas contribuam de forma equilibrada para o modelo.
* **Clusterização:** Implementação do algoritmo K-Means para identificação de padrões ocultos e agrupamento de perfis similares.
* **Business Intelligence:** Desenvolvimento de dashboards para monitoramento das médias de cada cluster e distribuição volumétrica de clientes.

## Tecnologias e Ferramentas
* **Python:** Linguagem base para o processamento de dados.
* **Pandas:** Manipulação e estruturação de datasets.
* **Scikit-Learn:** Implementação de algoritmos de Machine Learning e pré-processamento.
* **Power BI Desktop:** Construção da camada de visualização e suporte à decisão.

## Desenvolvimento da Solução

### 1. Coleta e Extração

```python
# Versão da Linguagem Python

from platform import python_version
print('Versão da Linguagem Python Usada Neste Jupyter Notebook:', python_version())
```
```python
# Importa os pacotes
import pandas as pd
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
```
```python
# Carrega os dados
df_dsa = pd.read_csv('dados/dados_clientes.csv')
```
```python
# Verifica o tipo do objeto
type(df_dsa)
```

```python
# Visualiza as 10 primeiras linhas
df_dsa.head(10)
```

### 2. Análise Exploratória e Estatística Descritiva

```python
# Resumo estatístico das variáveis para verificar consistência e distribuição dos dados
df_dsa[['idade', 'renda_anual', 'pontuacao_gastos']].describe()
```

### 3. Pré-Processamento e Padronização de Atributos 

```python
# Cria o padronizador dos dados
padronizador = StandardScaler()
```

```python
# Aplica o padronizador somente nas variáveis de interesse
dados_padronizados = padronizador.fit_transform(df_dsa[['idade', 'renda_anual', 'pontuacao_gastos']])
```

```python
# Visualiza os dados
print(dados_padronizados)
```

### 4. Implementação e Treinamento do Modelo de Clusterização

```python
# Definição do número de clusters (k).
k = 3
```
```python
# Cria o modelo K-means
kmeans = KMeans(n_clusters = k)
```
```python
# Treina o modelo com os dados padronizados
kmeans.fit(dados_padronizados)
```
```python
# Atribui os rótulos dos clusters aos clientes
df_dsa['cluster'] = kmeans.labels_
```
```python
# Exibe o resultado (10 primeiras linhas)
df_dsa.head(10)
```
### 5. Exportação e Integração de Dados
```python
# Salva o resultado em disco
df_dsa.to_csv('dados/segmentos.csv', index = False)
```
### 6. Visualização Analítica e Dashboards 

O resultado da segmentação processado em Python foi integrado ao Power BI Desktop para a construção de dashboards estratégicos, contemplando:

* Análise de médias demográficas por segmento.
* Comparativo de rentabilidade (renda) versus comportamento (gastos).
* Volumetria e representatividade de cada cluster na base total.

![Dashboard Power BI](dashboard.png)

---
*Projeto desenvolvido como parte do programa de formação em Business Intelligence da Data Science Academy.*













