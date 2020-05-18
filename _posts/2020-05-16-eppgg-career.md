---
title: "Inside one of the most commented career in MG"
date: 2020-05-16
tags: [Data Viz]
excerpt: "Data visualization produced with the public data available around the EPPGG career"
---

## Inside the EPPGG career

The [EPPGG](http://www.sindesp.org/#carreira) career is one of the many in Minas Gerais (MG) government. Whoever wish to join it, must first dedicate herself to four years of formal education in a nobel institution, called "Fundação João Pinheiro".

After being trained, they get into the realms of public sector by having the possibility of accessing different government branches. Once inside, they start doing what they were educated for: development of public policies and management, at any level, of the government structure.

Despite its members being both highly criticized and praised, there are not many analyses of the public data available around the career and that is one of the reasons why I've dedicated this post to do so.

One my reasons is also to better know the EPPGG career and also make it better known. All the data used in this brief post can be found [here](http://www.transparencia.mg.gov.br/).

*Note: my e-mail is at the top of this website and available to everybody that has suggestions and critics.*

## How big they are... and how much do they make?

The public data does not have too many interesting variables, but the ones that displays which trust position ("Cargos de confiança") each EPPGG occupy and his monthly income.

The graph below may be a good start for better knowing how large they were as a career, back in 2018, and also the evolution of the total number of members within it.

![Quantitativo de EPPGGs ano a ano no Estado](/assets/images/eppgg-career/03_histogram.png)

We can see that, as a career, their size is quite small if compared to most of others. They barely reach 700 people - which is nothing - in a state that has more then 200.000 public servants.

We can also notice something awkward from 2017 to 2018: the number of EPPGGs has decreased. I can think of two main reasons for that.

In first place, the year of 2017 was the first within the series wihtout appointment ("nomeações") of EPPGGs. And second, the career has an anually dropout rate.

Since among the availables variables there is no data that allows us to distinguish someone that had just abandoned the career from someone that took a license, both are being considered.

And what about their division among sex? Here we got it:

![Total de homens vs. mulheres ao longo do tempo](/assets/images/eppgg-career/04_stack_hist.png)

An important point here is that this variable needed to be imputed, since it's not a public data. It was done so through the package [GenderBR](https://github.com/meirelesff/genderBR), released by Fernando Meireles(UFMG). It's function basically "predicts gender from Brazilian first names".

Despite having a little more men than women, the career is quite equal in the total amount, finishing the year of 2018 with a difference among sex of just 3,5%.

Moving on to the average of monthly salary among the EPPGGs...

*Important note: the "Portal da Transparência" website contains the salary of each member as a total amount of their ground salary ("vencimento básico") added by their gratifications and bonus. So the income that you will see below is not the ground salary, but the total amount.*

![Distribuição salarial da carreira em 2018](/assets/images/eppgg-career/01_boxplot.png)

When the subject is salary, the career is quite fortunate. In 2018 their median income (the exactly middle value) was near R$10.600,00, which is a far greater number then the ones for most of the public careers of MG.

We can also see a big box inside the graph, which shows that 50% of the salaries are between 7.500 and 14.500 "reais".

*Note: a comparison with others careers income would fit well here, but that is something for later posts.*

We can also visualize their salaries differences among sex:

![Diferença salarial por sexo](/assets/images/eppgg-career/06_piramide.png)

It give us a glimpse on how well distributed is the mean monthly income of an EPPGG (the numbers are not deflated). In all years displayed, except for 2018, women have a mean monthly salary just a bit higher then men.

Another point to be observed is that, from 2017 to 2018, the average salary is decreased in a few "reais", because of the new entries in the career. On December 2017, close to 40 new EPPGGs were appointed and received their very first salary (close to R$4.500,00) in Jan-18, lowering the average of the whole career that year.

## Where do they work and they got "promotions" there?

After reviewing this salary graph, we move on to the next question: in which government branch are the most well payed EPPGG in 2018?

![Top 100 salários e local de trabalho](/assets/images/eppgg-career/02_donut.png)

What we see is that despite 1/3 of them being alocated in the "Secretaria de Planejamento e Gestão" (SEPLAG), they are, actually, fairly distributed among state departments. After all, fifty three (53) of the best EPPGGs salaries, in 2018, can be found in 22 different departments.

Now lets check the occupation of trust positions by the EPPGG, since that is one of the main reason for big salaries in government, after time within the public service and graduate degrees titles.

Minas Gerais state has two types trust positions: DAD and DAI. They mean a monthly bonus added in the total salary, once the occupation of higher posts come with more responsabilities, for which people get payed.

Considering this two types as just one variable that equals to "occupying a trust position", when we look to the EPPGGs and try to see how large is the group, within the career, that occupy this level at the public sphere hierarchy, this is what we get:

![Percentual com e sem cargo](/assets/images/eppgg-career/05_hist_cargos.png)

This graph shows us a transition in which 82% of the career came from having "occupying a trust position", in 2013, to just 58% at this same situation five years later.

*Note: for producing this graph above we consider an EPPGG as "occupying a trust position" by the only rule of him holding this position for more then 6 months within that year.*

Because we can eye-note this decrease in the occupation of trust position by the career as a whole, we decided to check on how does the new entries were affected by it. This is the result:

![Tempo para recebimento de um cargo](/assets/images/eppgg-career/07_geom_jitter.png)

What we get is that the career freshmen after 2016 does not had many opportunities to occupy trust position. Actually, something new happened, in comparison with the freshmen before 2016: in their first year onworking, the ones that got in after 2016 have not received any trust position. This seems very contrary to whay used to happen, when you look at the same data for new entries of before 2016.
