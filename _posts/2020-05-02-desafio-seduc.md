---
title: "Desafio de dados - Educação Pública SP"
date: 2020-05-02
tags: [EDA]
excerpt: "Análise exploratória dos dados de professores e dos alunos das Escolas Estaduais de SP"
---

# Introdução

Há dois meses atrás o Estado de São Paulo promoveu um [desafio de dados abertos](https://www.educacao.sp.gov.br/noticia/avisos-de-pautas/educacao-lanca-desafio-de-dados-abertos/) e, para tanto, disponibilizou 12 conjuntos de dados referentes as escolas estaduais. Esses [datasets](https://dados.educacao.sp.gov.br/search/field_topic/desafios-seduc-164) possuem variáveis que contém desde o grau de escolaridade dos professores da rede Estadual - mais de 200.000 profissionais - até a carga horária que estes possuem, por escola de SP.

Quando tive contato com este desafio pensei em algumas perguntas que considerava como interessantes e que, talvez, pudessem ser respondidas. Dentre essas, selecionei três que mais me atraíam:

**Pergunta 1:** uma vez que dentre os dados disponibilizados estavam os anos de direção e vice-direção ocupados por cada profissional - de quando até quando tal pessoa foi diretor(a) - resolvi analisar: o conceito de [*turnover*](https://www.sebrae.com.br/sites/PortalSebrae/artigos/entenda-o-que-e-turnover-e-o-impacto-da-rotatividade-no-negocio,44e08fa0672f0510VgnVCM1000004c00210aRCRD), tão comum ao [ambiente empresarial](https://sambatech.com/blog/insights/prejuizos-rotatividade-de-funcionarios/), também poderia ser adaptado às realidades escolares?

Numa rápida pesquisa acabei encontrando o [artigo de uma pesquisadora brasileira](https://www.teses.usp.br/teses/disponiveis/96/96131/tde-15092015-105243/publico/JessicaGMiranda_Original.pdf) que analisa, com uma metodologia rigorosa, os impactos do turnover de diretores na aprendizagem - especificamente no desempenho dos alunos na Prova Brasil.

**Pergunta 2:** observando os dados de ausência de professores em 2019 (infelizmente somente para os meses de Abril e Novembro), optei por verificar se um tipo de falta em específico - faltas injustificadas - teria alguma correlação com a aprendizagem dos alunos - aqui entendida como o desempenho deles no [SARESP](http://saresp.fde.sp.gov.br/2019/Default.aspx).

**Pergunta 3:** escolas no topo da pirâmide, em termos de aprendizagem, possuem professores com o mesmo grau de escolaridade dos professores das escolas que se encontram na base da pirâmide? (essa segmentação escolar por pirâmide é melhor explicada abaixo).

Segmentação escolar: dividi a escola de acordo com os critérios listados abaixo:

1. Escolas com média no SARESP acima da média estadual para todas as matérias;
2. Escolas com média no SARESP acima da média estadual para algumas matérias;
3. Escolas com média no SARESP abaixo da média estadual para todas as matérias

# Análise exploratória de dados

**Análise da Pergunta 01: turnover das equipes diretivas e aprendizagem**

    Definições prévias necessárias a compreensão da pergunta:

* Equipe diretiva = diretores + vice-diretores
* Turnover (rotatividade) = ((total de pessoas que entraram na equipe + total de pessoas que saíram da equipe) / 2) / total de pessoas na equipe no ano de cálculo (foto abaixo).

    A parte mais envolvente no tratamento dos dados foi pensar em como obter o conjunto que forma a equipe diretiva - combinação de dois datasets - para então conseguir detectar quando um ID, seja de diretor ou de vice, consta dentro do conjunto da equipe naquele ano e quando já não aparece mais.

Para tanto, criei a seguinte função:

```r
calc_turnover <- function(equipe_ano_base, equipe_ano_calc) {
  
  a <- str_split(string = equipe_ano_base, "-")[[1]]
  b <- str_split(string = equipe_ano_calc, "-")[[1]]
  entrada <- length(b[!b %in% a])
  saida <- length(a[!a %in% b])
  
  turnover <- ((entrada+saida)/2)/length(a)
  
}
```


Resultado encontrado:
![Gráfico de Turnover](/assets/images/desafio-seduc/Graph_1_turnover.png)

**Análise da Pergunta 02: faltas injustificadas de professores e aprendizagem**

Resultado encontrado:
![Gráfico de Faltas](/assets/images/desafio-seduc/Graph_2_faltas_injustificadas .png)

**Análise da Pergunta 03: como se distribui o grau de escolaridade dos professores entre os segmentos escolares?**

Resultado encontrado:
![Gráfico de Escolaridade](/assets/images/desafio-seduc/Graph_3_escolaridade.png)