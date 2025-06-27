# Detecção de Fraude em Cartão de Crédito

## 📄 Sobre o Projeto

Este projeto tem como objetivo principal a detecção de fraudes em transações de cartão de crédito. No cenário digital atual, onde trilhões de transações ocorrem diariamente, a identificação de atividades fraudulentas é um desafio crescente, dada a evolução constante das táticas dos criminosos cibernéticos. 

## 💾 Fonte de Dados

Os dados utilizados simulam transações de cartão de crédito e contêm variáveis que descrevem a natureza de cada operação, permitindo a construção de um modelo para identificar transações fraudulentas.

## 📚 Explicação das Variáveis

  * `distancefromhome`: Distância de casa onde a transação ocorreu.
  * `distancefromlast_transaction`: Distância da última transação.
  * `ratiotomedianpurchaseprice`: Razão entre o preço de compra da transação e o preço mediano de compra.
  * `repeat_retailer`: Indica se a transação ocorreu no mesmo varejista (1 = sim, 0 = não).
  * `used_chip`: Indica se a transação foi realizada via chip do cartão (1 = sim, 0 = não).
  * `usedpinnumber`: Indica se a transação utilizou o número PIN (1 = sim, 0 = não).
  * `online_order`: Indica se a transação foi um pedido online (1 = sim, 0 = não).
  * `fraude`: Variável alvo, indica se a transação é fraudulenta (1 = sim, 0 = não).

## 📊 Análise Exploratória de Dados (EDA) e Pré-processamento

O conjunto de dados contém **1.000.000 de registros** e **8 colunas**, sem valores nulos, o que facilita o pré-processamento. A variável `fraud` (fraude) é a variável alvo, sendo aproximadamente **91.00%** das transações não fraudulentas e aproximadamente **9.00%** fraudulentas, o que representa um desbalanceamento significativo na base de dados.

### Insights sobre transações fraudulentas

  * **`repeat_retailer`**: A maioria das transações fraudulentas (aproximadamente 88%) ocorreu em varejistas repetidos.
  * **`used_chip`**: Cerca de 74% das fraudes não envolveram o uso de chip, enquanto 26% sim.
  * **`used_pin_number`**: A grande maioria das fraudes (quase 100%) não utilizou o número PIN.
  * **`online_order`**: Aproximadamente 95% das fraudes foram transações online.

### Tratamento de Variáveis Numéricas

As colunas `distance_from_home`, `distance_from_last_transaction` e `ratio_to_median_purchase_price` apresentavam distribuições com *outliers* e alta dispersão, o que dificultava a visualização e a interpretação. Para mitigar esse problema e normalizar a escala, foi aplicada uma **transformação logarítmica (log10)** a essas variáveis nas transações fraudulentas. A análise da matriz de correlação revelou que `online_order`, `distance_from_home` e `ratio_to_median_purchase_price` são as variáveis mais correlacionadas com a ocorrência de fraude.

## 🤖 Modelagem e Escalonamento de Dados

O conjunto de dados foi dividido em 80% para treinamento e 20% para teste, utilizando estratificação para manter a proporção de classes da variável alvo (`fraud`) em ambos os conjuntos.

Para otimizar o desempenho do modelo, foi realizado o escalonamento dos dados. As técnicas de **MinMaxScaler** (normalização, ajustando valores entre 0 e 1) e **StandardScaler** (padronização, zerando a média e ajustando o desvio padrão para 1) foram consideradas. A análise das plotagens antes e depois das transformações permitiu verificar se houve mudanças significativas na distribuição dos dados. A escolha do escalonamento foi baseada na preservação do padrão visual dos dados, o que é crucial para não descaracterizar a informação original.

## 🧪 Escolha e Otimização do Modelo

O modelo escolhido para a detecção de fraudes foi o **KNeighborsClassifier (KNN)**, que classifica transações com base na similaridade com outras já conhecidas, identificando padrões de comportamento suspeito.

Para encontrar o melhor valor de `k` (número de vizinhos) para o KNN, foi realizada uma análise iterativa. O erro do modelo foi calculado para valores de `k` de 1 a 10. O gráfico de erro resultante indicou que **k = 7** e **k = 9** minimizou o erro, sendo, portanto, os valores ideais para o modelo.

## ✨ Resultados

O modelo **KNeighborsClassifier** configurado com `n_neighbors=7` alcançou uma **acurácia de 97.16%** nos dados de teste após o escalonamento. É importante notar que, **sem o escalonamento, a acurácia do modelo foi significativamente menor (aproximadamente 75.13%)**, o que ressalta a importância da etapa de pré-processamento para a performance do modelo.
