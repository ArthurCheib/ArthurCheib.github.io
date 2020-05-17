---
title: "Inside one the most (badly) commented career in MG"
date: 2020-05-16
tags: [Data viz]
excerpt: "Data visualization produced with the public data available around the EPPGG career"
---


## Inside the EPPGG career

If a public career ought to be study by having as only criteria the total amount of gossip spread around it, the Public Policy and Government Management Specialist (EPPGG - in it's portuguese acronymous) would be, by far, the one with the greatest number of academic researchies committed to it.

The EPPGG is a career originated in the public sector of the Minas Gerais (MG) government. Whoever wish to join it, must first dedicated herself to four long years of formal education in a nobel institution in MG, called "Fundação João Pinheiro". So after receiving this years of training, they get into the realms of public sector by accessing one of the many posibles secretary of state, at their bottom level.

Once inside, they start doing what they were trained for: development of public policies and management, at any level, of the government structure.

At this far, just a few have tried to make some graphs using only the public data avaiable around this career, that is one of the reasons why I've dedicated this blog post to do so. And by doing it, Another reason it's trying to make the EPPGG career better known. All the data used in this brief research can be found [here](http://www.transparencia.mg.gov.br/).

### How big they are... and how much do they make?

The public data does not have many interesting variables but the ones that displays the position of each one of the EPPGG's in the responsability hierarchy ("Cargos de confiança"), and their monthly income.

The graph bellow maybe a good start for better knowing how large they are as a career and their increase over the last few years.

![Quantitativo de EPPGGs ano a ano no Estado](/assets/images/eppgg-career/03_histogram.png)

We can see that, as career, their size is quite small if compared to most of other careers. They barely have 700 people, which is nothing (0,35%) in a state that has more then 200.000 public servants.

We can also check that from 2017 to 2018 the number of EPPGGs inside the stats has decreased. And the reason is: in first place, 2017 was the first year wihtout appointment of EPPGGs ("nomeações") so nobody got in since the last nomination, that took place in the second semester of 2016. Second, the career has an anually dropout rate - some just abandon the career and others take a licenses to work outside of the government for a couple of years.

And what about their division among sex? Here we got it:

![Total de homens vs. mulheres ao longo do tempo](/assets/images/eppgg-career/04_stack_hist.png)

An important point here is that this data needed to be inputted, once it was not available publicly. And it was done so thourgh the usage of the package [GenderBR](https://github.com/meirelesff/genderBR), released by Fernando Meireles, profesor at the UFMG. The package basically has functions that "Predict gender from Brazilian first names", as described in its GitHub storage.

Despite having a little more men than women, the career is quite equal in the total amount, finishing the year of 2018 with just a 3,5% difference among sex.

Moving on to income distribution among the EPPGGs...

![Distribuição salarial da carreira em 2018](/assets/images/eppgg-career/01_boxplot.png)

When the subject is salary, the career is quite fortunate. In 2018 their median income (the exactly middle value) was near R$10.600,00, which is a far greater number then the ones for most of the public careers of MG. We can also see the big box inside the graph, which shows that 50% of the salaries are between 7.500 and 14.500 "reais".

Some comparison with others careers income would fit well in here, but that is something for later posts.


We can also visualize their salaries differences among sex, displayed by this graph:

![Diferença salarial por sexo](/assets/images/eppgg-career/06_piramide.png)

This graph give us a glimpse on how well distributed is the mean monthly income of an EPPGG (the numbers are not deflated). In all years displayed, except for 2018, women have a mean monthly salary just a bit higher then men. Another point to be observed is that, from 2017 to 2018, the average salary is decreased in a few "reais", and the reason for that is the new entries in the career. On December 2017, close to 40 new EPPGGs were appointed and received their very salary (R$4.500,00) in January-18, lowering the average salary of the whole career that year.

### Where do they work and they got "promotions" there?

After reviewing this salary graph, we went on to see: in which government branch where the most well payed EPPGG in 2018?

![Top 100 salários e local de trabalho](/assets/images/eppgg-career/02_donut.png)

What we see is that despite 1/3 of them being alocated in the "Secretaria de Planejamento e Gestão", which makes sense once that's what they can bestly do, they are, actually, fairly distributed among state departments. 53 of the best EPPGG's salaries, in 2018, came from 22 different departments.

One of the main reason for big salaries in government, apart from lots of year in the public service, is due to the occupation of trust positions ("cargos de confiança"). At Minas Gerais state, there are two types of this positions, called DAD and DAI. They mean a monthly bonus added in the total salary because of the occupation of higher posts in the public hierarchy, in which someone is expected to be able to deal with more responsabilities.

Considering this both options as the same, "occupying a trust position", this is what we get, when we look to the EPPGGs and try to see how large is the group, within the career, that occupy this level at the public sphere hierarchy.

![Percentual com e sem cargo](/assets/images/eppgg-career/05_hist_cargos.png)

This graph shows us a transition in which 82% of the career came from having "occupying a trust position", in 2013, to 58% at this same situation five years later.

*Note:* for producing this graph above we consider an EPPGG as "occupying a trust position" by the only rule of him having this position for more then 6 months within that year.

![Tempo para recebimento de um cargo](/assets/images/eppgg-career/07_geom_jitter.png)