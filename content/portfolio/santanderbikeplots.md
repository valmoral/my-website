---
date: "2016-11-05T19:57:40+05:30"
draft: false
image: img/bike_plot1_home.jpg
showonlyimage: false
title: Santander Bike Rentals (1)
weight: 5
---

![Add Photos][1]

```r
# Clean the data 
bike_exp <- bike %>%
  filter(year > 2015) %>% #Filter all the data that after 2015
  group_by(month) %>%
  summarise(expected_rentals=mean(bikes_hired)) # Calculate the expected rentals

# Replicate the first graph of actual and expected rentals for each month across years
plot <- bike %>%
  filter(year > 2015) %>%
  group_by(year, month) %>%
  summarise(actual_rentals=mean(bikes_hired)) %>% # Calculate the actual mean rentals for each month
  inner_join(bike_exp, by='month') %>% # Combine the data with original dataset
  mutate(
    up=if_else(actual_rentals > expected_rentals, actual_rentals - expected_rentals, 0),
    down=if_else(actual_rentals < expected_rentals, expected_rentals - actual_rentals, 0)) %>% # Create the up and down variable for plotting the shaded area using geom_ribbon
  ggplot(aes(x=month)) +
  geom_line(aes(y=actual_rentals, group=1), size=0.1, colour='black') +
  geom_line(aes(y=expected_rentals, group=1), size=0.7, colour='blue') + # Create lines for actual and expected rentals data for each month across years
  geom_ribbon(aes(ymin=expected_rentals, ymax=expected_rentals+up, group=1), fill='#7DCD85', alpha=0.4) +
  geom_ribbon(aes(ymin=expected_rentals, ymax=expected_rentals-down, group=1), fill='#CB454A', alpha=0.4) + # Create shaded areas and fill with different colors for up and down side
  facet_wrap(~year) + # Facet the graphs by year
  theme_bw() + # Theme
  labs(title="Monthly changes in TfL bike rentals", subtitle="Change from monthly average shown in blue and calculated between 2016-2019", x="", y="Bike rentals") +
  NULL

ggsave(file='bike_plot1_home.jpg', plot=plot, path = '~/Desktop/LBS/Term1/my-website/my-website/static/img', width=18, height=18) 

ggsave(file='bike_plot1.jpg', plot=plot, path = '~/Desktop/LBS/Term1/my-website/my-website/static/img', width=18, height=8) 
```

> A relevant comment

You can even add some 

* Bullet
* Points

#[1]: /img/germanElections_plot.jpg 
