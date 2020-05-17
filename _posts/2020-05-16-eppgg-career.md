---
title: "Inside one of the most "popular" career in MG"
date: 2020-05-16
tags: [Data viz]
excerpt: "Data visualization produced with the public data available around the EPPGG career"
---


## Inside the EPPGG career

If a public career ought to be study by having as only criteria the total amount of gossip spread around it, the Public Policy and Government Management Specialist (EPPGG, in it's portuguese acronymous) would be the one with the higher number of academic researchies committed to it.

The [EPPGG](http://www.sindesp.org/#carreira) career is one of the many in Minas Gerais (MG) government. Whoever wish to join it, must first dedicate herself to four long years of formal education in a nobel institution, called "Fundação João Pinheiro".

After receiving this years of training, they get into the realms of public sector by accessing the bottom level of different posibles government branches. Once inside, they start doing what they were trained for: development of public policies and management, at any level, of the government structure.

Despite being both highly criticized and praised, just a few have tried to analyze the public data avaiable around this career and that is one of the reasons why I've dedicated this blog post to do so.

Another reason for doing so it's trying to make the EPPGG career better known. All the data used in this brief post can be found [here](http://www.transparencia.mg.gov.br/).

*Note: my e-mail is at the top of this website and available to everybody that has suggestions and critics.*

### How big they are... and how much do they make?

The public data does not have too many interesting variables, but the ones that displays which trust position ("Cargos de confiança") each EPPGG occupy and his monthly income.

The graph below may be a good start for better knowing how large they were as a career, back in 2018, and also the evolution of the total number of members within it.

![Quantitativo de EPPGGs ano a ano no Estado](/assets/images/eppgg-career/03_histogram.png)

We can see that, as career, their size is quite small if compared to most of others. They barely reach 700 people - which is nothing - in a state that has more then 200.000 public servants.

We can also notice something a awkward from 2017 to 2018: the number of EPPGGs inside the stats has decreased. I can think of two main reasons for that.

In first place, 2017 was the first year within that series wihtout appointment ("nomeações") of EPPGGs. Second, the career has an anually dropout rate.

Since the variables available does not contain nothing that allows us to distinguish someone that had just abandoned the career from someone that took a license, both are being considering in here.

And what about their division among sex? Here we got it:

![Total de homens vs. mulheres ao longo do tempo](/assets/images/eppgg-career/04_stack_hist.png)

An important point here is that this variable needed to be imputed, since it's not a public data. It was done so through the package [GenderBR](https://github.com/meirelesff/genderBR), released by Fernando Meireles, profesor at the UFMG. The package basically has functions that "predict gender from Brazilian first names".

Despite having a little more men than women, the career is quite equal in the total amount, finishing the year of 2018 with a difference among sex of just 3,5%.

Moving on to the average of monthly salary distribution among the EPPGGs...

![Distribuição salarial da carreira em 2018](/assets/images/eppgg-career/01_boxplot.png)

When the subject is salary, the career is quite fortunate. In 2018 their median income (the exactly middle value) was near R$10.600,00, which is a far greater number then the ones for most of the public careers of MG.

We can also see a big box inside the graph, which shows that 50% of the salaries are between 7.500 and 14.500 "reais".

*Note: Some comparison with others careers income would fit well in here, but that is something for later posts.*

We can also visualize their salaries differences among sex:

![Diferença salarial por sexo](/assets/images/eppgg-career/06_piramide.png)

It give us a glimpse on how well distributed is the mean monthly income of an EPPGG (the numbers are not deflated). In all years displayed, except for 2018, women have a mean monthly salary just a bit higher then men.

Another point to be observed is that, from 2017 to 2018, the average salary is decreased in a few "reais", because of the new entries in the career. On December 2017, close to 40 new EPPGGs were appointed and received their very first salary (R$4.500,00) in January-18, lowering the average of the whole career that year.

### Where do they work and they got "promotions" there?

After reviewing this salary graph, we move to the next question: in which government branch are the most well payed EPPGG in 2018?

![Top 100 salários e local de trabalho](/assets/images/eppgg-career/02_donut.png)

What we see is that despite 1/3 of them being alocated in the "Secretaria de Planejamento e Gestão" (SEPLAG), they are, actually, fairly distributed among state departments. After all, fifty three (53) of the best EPPGGs salaries, in 2018, can be found in 22 different departments.

Now lets check the occupation of trust positions by the EPPGG, since, after lots of year in the public service and graduate degrees titles, that is one one of the main reason for big salaries in government.

At Minas Gerais state, there are two types of this positions: DAD and DAI. They mean a monthly bonus added in the total salary because of the occupation of higher posts in the public hierarchy, in which someone is expected to be able to deal with more responsabilities.

Considering this two types as just one variable that equals to "occupying a trust position", when we look to the EPPGGs and try to see how large is the group, within the career, that occupy this level at the public sphere hierarchy, this is what we get:

![Percentual com e sem cargo](/assets/images/eppgg-career/05_hist_cargos.png)

This graph shows us a transition in which 82% of the career came from having "occupying a trust position", in 2013, to just 58% at this same situation five years later.

*Note: for producing this graph above we consider an EPPGG as "occupying a trust position" by the only rule of him having this position for more then 6 months within that year.*

Because we can eye-note this decrease in the occupation of trust position by the career as a whole, we decided to check on how does the new entries were affected by it. This is the result:

![Tempo para recebimento de um cargo](/assets/images/eppgg-career/07_geom_jitter.png)