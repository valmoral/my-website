---
title: "Radiation Statistics Experiment"
draft: no
date: '2016-11-05T19:56:17+05:30'
showonlyimage: yes
image: img/portfolio/radiation.jpg
weight: 10
---

For the final project of Statistics 101B: Design of Experiment, I was asked to collaborate with a group to create and execute a statistical experiment on mock subjects. After extensive research, my group and I decided to analyze whether radiation has an effect on cognitive memory. The subjects we used were "Islanders," a virtual population that supports learning and teaching in experimental design. Although they were not real people, any experiments done on the subject were in real time so timing had to be considered. 

For our experiment, created a two-way randomized block design, utilizing amount of radiation, in Greys (Gy), and age as our two factors. To avoid any variance created by gender, we utilized gender as our block. Through a G*Power test, we found that in order to have a power of .8, we needed to have a sample size of at least 138. In order to create a balanced design, we sampled 144 subjects, divided into 3 age groups, further divided into a control group (0 Gy), group 1 (1 Gy), and group 2 (3 Gy). Through an analysis of variance (ANOVA) done in R, we found that as radiation increases, memory decreases. We did not find any interaction effects between age and amount of radiation. However, due to deviance from normality and confounding variables, we were unable to conclude if there is a direct causation. 