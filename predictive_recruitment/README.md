# Recrutamento Preditivo com Machine Learning
# Recrutamento Preditivo


## 📄 Sobre o Projeto

Este projeto de Ciência de Dados tem como objetivo otimizar o processo de seleção e recrutamento de novos talentos. Utilizando técnicas de **People Analytics**, a iniciativa visa aprimorar a identificação de candidatos ideais, aumentando a eficácia do recrutamento.

## 🎯 Problema de Negócio

A empresa **HighTech** busca identificar os indicadores mais relevantes para o recrutamento de profissionais qualificados, visando uma contratação mais assertiva e eficiente.

## 💡 Desafio

Como cientista de dados, o desafio foi criar um modelo preditivo de recrutamento capaz de prever quais variáveis são as mais eficazes para identificar um profissional bem qualificado.

## 📊 Base de Dados

O conjunto de dados utilizado para este projeto contém diversas características dos candidatos. A variável **target** (alvo) do modelo é a coluna `status`, que indica se o profissional foi ou não contratado.

### Colunas e Descrição

  * `sl_no`: Número de série (identificador único de cada registro).
  * `gender`: Gênero da pessoa (M = Masculino, F = Feminino).
  * `ssc_p`: Percentual obtido no ensino médio (nível SSC – Secondary School Certificate).
  * `ssc_b`: Tipo de escola no ensino médio (Central ou Others).
  * `hsc_p`: Percentual obtido no ensino médio superior (nível HSC – Higher Secondary Certificate).
  * `hsc_b`: Tipo de escola no ensino médio superior.
  * `hsc_s`: Área de estudo no ensino médio superior (Commerce, Science, Arts).
  * `degree_p`: Percentual obtido na graduação.
  * `degree_t`: Tipo de curso de graduação (Sci\&Tech, Comm\&Mgmt).
  * `workex`: Experiência de trabalho prévia (Yes = Sim, No = Não).
  * `etest_p`: Nota em um teste de empregabilidade.
  * `specialisation`: Especialização no MBA (Mkt\&HR = Marketing e RH, Mkt\&Fin = Marketing e Finanças).
  * `mba_p`: Percentual obtido no MBA.
  * `status`: Situação de colocação profissional (Yes = foi contratado, No = não foi).
  * `salary`: Salário.

## 🔍 Análise de Dados e Pré-processamento

  * **Tratamento de Valores Nulos**: A coluna `salary` apresentava 67 valores nulos, que foram preenchidos com `0`. Isso se deve ao fato de que esses registros correspondem a candidatos não contratados, para os quais não há informação salarial.
  * **Análise de Variáveis Numéricas**: Histogramas e boxplots foram utilizados para `hsc_p`, `degree_p`, `etest_p`, `mba_p` e `salary` a fim de entender suas distribuições e identificar *outliers*.
  * **Influência do MBA e Experiência de Trabalho**: Observou-se uma relação entre a pontuação no MBA (`mba_p`) e a experiência de trabalho (`workex`) com a decisão de contratação. Profissionais com boas pontuações de MBA e experiência prévia demonstraram maior probabilidade de serem contratados.
  * **Remuneração por Gênero e Especialização**: Análises revelaram que os salários mais altos e a média salarial foram predominantemente oferecidos a candidatos do sexo masculino, com variações dependendo da especialização (Marketing e RH vs. Marketing e Finanças).

## 🤖 Modelagem

Para a previsão do status de contratação, foram explorados os algoritmos LinearSVC (Linear Support Vector Classification) e KNeighborsClassifier. Para o KNeighborsClassifier, foi realizada uma análise para determinar o melhor valor de k (número de vizinhos mais próximos), otimizando a performance do modelo.



## ✨ Resultados

O modelo KNeighborsClassifier demonstrou um desempenho superior ao LinearSVC, alcançando uma acurácia de aproximadamente 88%. Já o LinearSVC obteve uma acurácia de aproximadamente 86%.
