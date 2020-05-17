---
title: "Desafio de dados - Educação Pública SP"
date: 2020-05-02
tags: [EDA]
excerpt: "Análise exploratória dos dados de professores e dos alunos das Escolas Estaduais de SP"
---

# Introdução

Dois meses atrás o Estado de São Paulo promoveu um [desafio de dados abertos](https://www.educacao.sp.gov.br/noticia/avisos-de-pautas/educacao-lanca-desafio-de-dados-abertos/) e disponibilizou 12 conjuntos de dados referentes as suas escolas. As [tabelas](https://dados.educacao.sp.gov.br/search/field_topic/desafios-seduc-164) disponibilizados possuem dados que vão desde o grau de escolaridade dos professores da rede Estadual - mais de 200.000 profissionais - até a localização geográfica de cada escola.

Escolhendo os três datasets que mais me chamaram atenção: (i) informativo anual de diretores e vice-diretores, (ii)  ausência e (iii) grau de escolaridade de professores, resolvi realizar uma breve análise exploratória desses dados.

Analisando as variáveis da tabela de diretores resolvi descobrir por quantos anos um diretor permanece em uma esma escola e cheguei nos seguintes resultados:

| Tempo com<br>mesmo Diretor 	| Percentual<br>de Escolas 	|
|:--------------------------:	|--------------------------	|
|         3 ou menos         	| 8,3%                     	|
|              4             	| 19,5%                    	|
|              5             	| 28,8%                    	|
|              6             	| 43,3%                    	|

Ao encontrar esse resultado - menos de 50% dos diretores escolares conseguem implementar seu projeto pedagógico por mais de 5 anos, lembrei do fato das diretoras que tive em meu colégio (privado) passarem a impressão de serem todas milenares (estavam lá antes de mim e ali perduram até hoje) e também me recordei de um artigo do [Valor Econômicor](https://valor.globo.com/brasil/noticia/2017/04/03/rotatividade-no-emprego-chega-a-385-menor-nivel-em-10-anos.ghtml), que apresentava a queda do turnover no Brasil como algo positivo para as empresas. Optei então por aprimorar a análise e me guiar pela seguinte questão:

**Pergunta 1:** o conceito de [*turnover*](https://www.sebrae.com.br/sites/PortalSebrae/artigos/entenda-o-que-e-turnover-e-o-impacto-da-rotatividade-no-negocio,44e08fa0672f0510VgnVCM1000004c00210aRCRD), tão comum ao [ambiente empresarial](https://sambatech.com/blog/insights/prejuizos-rotatividade-de-funcionarios/), também poderia ser adaptado às realidades escolares?

Mas, antes de prosseguir com ela, visto que um dos conjuntos de dados continha o desempenho dos alunos da rede estadual no [SARESP](http://saresp.fde.sp.gov.br/2019/Default.aspx), primeiro segmentei as escolas em três grandes grupos, da seguinte maneira:

1. Escolas com média no SARESP acima da média estadual para todas as matérias (topo da pirâmide);
2. Escolas com média no SARESP acima da média estadual para algumas matérias (corpo da pirâmide);
3. Escolas com média no SARESP abaixo da média estadual para todas as matérias (base da pirâmide).

Após essa segmentação, agrupei os diretores e vice-diretores em uma mesmo conjunto - considerando-os como uma equipe diretiva da escola. Calculei então o turnover - função abaixo ([^1]) - para cada equipe diretiva entre 2014 e 2018.

[^1]: Função que detecta quando um ID, seja de diretor ou de vice, consta dentro do conjunto da equipe naquele ano e quando já não aparece mais

```r
calc_turnover <- function(equipe_ano_base, equipe_ano_calc) {
  a <- str_split(string = equipe_ano_base, "-")[[1]]
  b <- str_split(string = equipe_ano_calc, "-")[[1]]
  entrada <- length(b[!b %in% a])
  saida <- length(a[!a %in% b])
  turnover <- ((entrada+saida)/2)/length(a)
}
```

Após o cálculo do turnover da equipe diretiva de cada escola, cruzei esses dados com a segmentação escolar realizada anteriormente e tirei o turnover médio do corpo diretivo por segmento escolar, encontrando o seguinte resultado:

| Segmentação<br>Escolar 	| Turnover médio do<br>corpo diretivo 	|
|:----------------------:	|:-----------------------------------:	|
|    Base da Pirâmide    	|                28,2%                	|
|    Corpo da Pirâmide   	|                26,1%                	|
|    Topo da Pirâmide    	|                22,9%                	|

Com esses resultados em mãos penso que temos um ótimo indício de que uma maior rotatividade do corpo diretivo da escola pode estar relacionada com menores níveis de aprendizagem por parte dos alunos. Inclusive, pesquisando rapidamente na internet acabei encontrando uma pesquisadora brasileira que estuda o [impacto da rotatividade dos professores](https://www.teses.usp.br/teses/disponiveis/96/96131/tde-15092015-105243/publico/JessicaGMiranda_Original.pdf)) com o desempenho dos alunos na Prova Brasil.

Segui então para o próximo conjunto de dados: a tabela contendo as ausências do corpo docente. E a primeira coisa que fiz foi checar o tipo de falta predominante entre o total da faltas (ainda que os dados fossem referente apenas aos meses de Abril e Novembro de 2019). E o que encontrei foi:

|              Tipo de Falta             	| % em relação ao<br>Total de faltas 	|
|:--------------------------------------:	|:----------------------------------:	|
|             Licença prêmio             	|                37,4%               	|
|             Licença abonada            	|                22,3%               	|
| Licença por<br>interesses particulares 	|                19,3%               	|
|           Falta injustificada          	|                8,6%                	|
|            Licença gestante            	|                6,3%                	|
|              Outros tipos              	|                6,1%                	|

Chamou-me a atenção não por seu valor, mas pelo seu conteúdo, um tipo de falta: as injustificadas. Resolvi então verificar se elas teriam alguma correlação com a aprendizagem dos alunos, como havia feito com o turnover. Mais uma vez a maior parte do trabalho ficou na limpeza dos dados que foi feita através desse [script](https://github.com/ArthurCheib/desafio-seduc/blob/master/B_Analise-01.Rmd). Os resultados encontrados não foram muito animadores, mas revelam uma correlação negativa entre as faltas injustificadas e a aprendizagem dos alunos.

![Gráfico de Faltas](/assets/images/desafio-seduc/Graph_2_faltas_injustificadas.png)

Ao produzir esse gráfico minha intuição era: as faltas injustificadas devem ser predominantes em escolas onde o corpo diretivo demonstra algum grau de dificuldade em lidar com o corpo docente. Logo, a existência de tal postura também traria impactos para a aprendizagem escolar.

Por fim, tratando da tabela que contém a escolaridade dos professores da rede estadual, resolvi de maneira bem direta identificar se as três segmentações escolares que havia criado no início possuem um corpo docente com distintos graus de escolaridade (minha expectativa era a de que maiores graus de escolaridade poderiam ser encontradas em escolas cujos alunos possuíssem melhor desempenho na aprendizagem - mas não foi bem isso que encontrei):

![Gráfico de Escolaridade](/assets/images/desafio-seduc/Graph_3_escolaridade.png)
