# Ant-clustering

# 1- Agrupando Itens
A formiga não empilha itens.
Os itens não são obstáculos para a formiga. Isto significa que elas podem transitar sobre as placas e itens.
A mesma quantidade de itens e de formigas vivas se mantém a mesma do início ao fim da aplicação.
Não existe uso de informação de limiar. A fórmula relacional para pegar e largar já dá bons resultados.<br/>

Etapas para construção do sistema:<br/>
a) Criar ambiente no formato de matriz
b) Distribuir itens (dados homogêneos) uniformemente na matriz
c) Criar estrutura dos agentes que atuarão no ambiente (formigas vivas): i. definir raio de visão. Usar raio 01 inicialmente; ii. estado ocupado/livre; iii. estrutura para o item a ser carregado
d) Definir rotina para deslocamento do agente. Usar deslocamento aleatório cima/embaixo/direita/esquerda
e) Criar regras para pegar e largar item

Sugestão para simulação: 50x50; 600 itens; raio 1; 15 formigas; 100.000 iterações. 

# 2- Agrupando Dados
Etapas para construção do sistema:
a) Adaptar a estrutura do ambiente para poder receber dados heterogêneos (ex: bidimensional)
b) Distribuir itens (dados heterogêneos) uniformemente na matriz
c) Adaptar a estrutura do agente (formiga viva) para receber dados heterogêneos
d) Criar regras para pegar e largar item com base em dissimilaridade (distância euclidiana) dos dados
e) Não usar rótulos para realizar o agrupamento. Usar os valores (x,y) de cada dado. Os rótulos são para fins de visualização na matriz
f) Ajustar parâmetros

Agrupamento de dados:
- 4 grupos (400 itens): sugestão de parâmetros: Quantidade de agentes: 100; Tamanho da matriz: 64 x 64; Quantidade de Iterações: 2000000; Raio de visão: 1. k1 = 0.3; k2 = 0.6; α = 11.8029; Raio de movimentação: 1 célula. 
- 4 grupos: k1 = 0.01, k2 = 0.015, α = 30 e raio de visão 1.
- 4 grupos:  α = 0.35, k1 = 0.5 e k2 = 0.025; 15 formigas vivas. Os dados foram normalizados; testar com cerca de 50.000.000 iterações.
- 15 grupos: α = 0.11, k1 = 0.9 e k2 = 0.05; 15 formigas vivas. Os dados foram normalizados; testar com cerca de 50.000.000 iterações.
