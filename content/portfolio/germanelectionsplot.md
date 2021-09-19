---
date: "2016-11-05T18:25:22+05:30"
draft: false
image: img/germanElections_plot_home.jpg
showonlyimage: false
title: German Election Polls
weight: 2
---

![German Election Poll Graph][1]

```r
#Select only necessary columns of the dataset
german_election_polls_cleaned <- german_election_polls %>%
  select(end_date, union, spd, af_d, fdp, linke, grune)

#Assigning colors to each political party, extracted from original plot using adobe color 
col_union <- 'black'
col_spd <- '#BF0404'
col_af_d <- '#8C1F7A'
col_fdp <- '#F2AE2E'
col_linke <- '#0A5789'
col_grune <- '#45BF41'

#Plotting the election outcomes
german_elections_plot <- german_election_polls_cleaned %>%
  ggplot +
  geom_point(aes(x=end_date, y=union, colour='black')) + #Union Party points assigned the color black
  geom_smooth(aes(x=end_date, y=union), colour='black', span=0.09, se=F) + #Union Party curve with span = 0.09 assigned the color black
  geom_point(aes(x=end_date, y=spd), colour=col_spd, alpha=0.5) + #SPD Party points assigned the color red
  geom_smooth(aes(x=end_date, y=spd), colour=col_spd, span=0.09, se=F) + #SPD Party curve with span = 0.09 assigned the color red
  geom_point(aes(x=end_date, y=af_d), colour=col_af_d, alpha=0.5) + #AfD Party points assigned the color purple
  geom_smooth(aes(x=end_date, y=af_d), colour=col_af_d, span=0.09, se=F) +  #AfD Party curve with span = 0.09 assigned the color purple
  geom_point(aes(x=end_date, y=fdp), colour=col_fdp, alpha=0.5) + #FDP Party points assigned the color yellow
  geom_smooth(aes(x=end_date, y=fdp), colour=col_fdp, span=0.09, se=F) + #FDP Party curve with span = 0.09 assigned the color yellow
  geom_point(aes(x=end_date, y=linke), colour=col_linke, alpha=0.5) + #Linke Party points assigned the color blue
  geom_smooth(aes(x=end_date, y=linke), colour=col_linke, span=0.09, se=F) + #Linke Party curve with span = 0.09 assigned the color blue
  geom_point(aes(x=end_date, y=grune), colour=col_grune, alpha=0.5) + #Grune Party points assigned the color green
  geom_smooth(aes(x=end_date, y=grune), colour=col_grune, span=0.09, se=F) + #Grune Party curve with span = 0.09 assigned the color green
  scale_y_continuous(breaks=seq(0, 40, 10), labels=c('0%', '10%', '20%', '30%', '40%')) + #Adjusting the scale
  geom_hline(yintercept=5, linetype='dashed', color='gray') + 
  scale_color_manual(name='',
                     labels = c('Union', 'SPD', 'AfD', 'FDP', 'Linke', 'Grüne'),
                     values = c('col_union'=col_union,'col_spd'=col_spd,'col_af_d'=col_af_d,'col_fdp'=col_fdp,'col_linke'=col_linke,'col_grune'=col_grune)) + #Creating a legend 
    labs(x='', y='') +
  theme_minimal() + #change theme to be more similar to the original
  theme(legend.background = element_rect(fill=NA, size=.3, linetype="solid")) + #add box around legend to be more similar to the original
  NULL

ggsave(file='germanElections_plot_home.jpg', plot=german_elections_plot, path = '~/Desktop/LBS/Term1/my-website/my-website/static/img', width=18, height=18)

ggsave(file='germanElections_plot.jpg', plot=german_elections_plot, path = '~/Desktop/LBS/Term1/my-website/my-website/static/img', width=18, height=8)
``` 

> A relevant comment

You can even add some 

* Bullet
* Points

[1]: /img/germanElections_plot.jpg
