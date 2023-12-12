# Palmer penguins
#  R for Visualization



IN this project we gonna use different ideas and techniques to show clean,view ,Transform,orgaize and visualize Penguins data to get better understanding of basic concept of r visualization and insights finding through making plots by using ggplot.

> install.packages("tidyverse")

* package ‘tidyverse’ successfully unpacked and MD5 sums checked

	
> library(tidyverse)

install.packages(dplyr)
library(dplyr)
  * dplyr package is use to make the data clean


#
install.packages("palmerpenguins")
library(palmerpenguins)
install.packages("here")
library(here)
install.packages("janitor")
library(janitor)
install.packages("skimr")
library(skimr)
skim_without_charts(penguins)

* To see structure and get ideo of data frame 
head(penguins)
Str(penguins)
glimpse(penguins)
colrow(penguins) # to see column rowa 


## To sort the penguins data by bill_length_mm
penguins %>% arrange(bill_length_mm)



## putting value in a variable penguin_S
penguins_s<-penguins %>% arrange(bill_length_mm)
I![Screenshot (36)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/99393b9d-c187-4ad0-9516-1668ac49835e)


# mean of bill_length
penguins %>% group_by(island) %>% drop_na() %>% summarize(mean_bill_length_mm=mean(bill_length_mm))
# to find longest bill of island
penguins %>% group_by(island) %>% drop_na() %>% summarize(max_bill_length_mm=max(bill_length_mm))
#  grouping 2 column island, species 
penguins %>% group_by(island,species) %>% drop_na() %>% summarize(max_b1=max(bill_length_mm),mean_bL=mean(bill_length_mm))
# Filter only adelie species
penguins %>% filter(species=="Adelie")
![Screenshot (37)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/dc578cdb-601e-46af-9651-0076e6000c09)



# Visualization

install.packages("tidyverse")

library(ggplot2)

library(tidyverse)

View(penguins)

## creating the plot flipper length by body mass

ggplot(data = penguins)+ geom_point(mapping = aes(x=flipper_length_mm,y=body_mass_g))

![Rplot04](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/61bf0fc2-eb9e-4d16-aad3-41810ac3aeba)

## changing color to red
ggplot(data = penguins)+ geom_point(mapping = aes(x=flipper_length_mm,y=body_mass_g,color="red"))
![Rplot06](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/b5758f5d-87fe-49a6-9def-82878638a190)


# Showing Plot by adding  alpha
ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,alpha=species))
![Rplot05](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/df20f66a-987d-43d6-b15c-b7f73164e852)


## creating the plot bill length by bill depth

ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm))
![Rplot 1](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/3f3db191-704e-49b7-b459-9b1428fd842d)

## adding color to the plot

ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,color=species))

![Rplot 3](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/597d8f63-3cea-48e6-b505-c2e888352f6a)

## Adding shape to the plot
* Code---
ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,shape=species))

![Rplot01](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/090a7b58-1567-4abc-b197-b0201cf2ec27)

## Adding size to the plot
Code--
ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,size=species))

![Rplot02](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/a91f2190-1ddf-4349-8db1-2134c8ccd608)


# Adding shape size and color to the plot
Code--
ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,size=species,color=species,shape=species))

![Rplot03](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/2f891ea4-b36f-4a35-b234-dab30a5c399b)

# Adding facet_wrap to the code  to get different plot of species


ggplot(data = penguins)+ geom_point(mapping = aes(x=bill_length_mm,y=bill_depth_mm,size=species,color=species,shape=species))+
facet_wrap(~species)

![Rplot07](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/74341b8c-6f06-4378-84ba-e792b8e7c564)

## Showing plot through point chart by using facet_grid

ggplot(data=penguins)+geom_point(mapping=aes(x=bill_length_mm,fill=body_mass_g,color=species,size=species,shape=species))+facet_grid(island~species)

![Rplot09](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/078f3f62-f334-4fb7-a0c2-32da9c463439)



## Showing plot through bar chart by using facet_grid

ggplot(data=penguins)+geom_bar(mapping=aes(x=bill_length_mm,fill=body_mass_g,color=species,size=species,shape=species))+facet_grid(island~species)

![Rplot08](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/a1b9c7e1-e2ab-4b4f-bbdd-580bff8db7c9)

# Label fun and annonate

Adding title,subtitle,caption and label as gentoos are the largest by visualizing



ggplot(data = penguins)+geom_point(mapping = aes(x=flipper_length_mm,y=body_mass_g,shape=species,color=species,size=species))+ 
  labs(title = "Body_mass vs Flipper_length",subtitle = "Point plot", caption = "Data created by Dr. gormen ")+ 
  annotate("text",x=70,y=3500,label="gentoos are the largest",color="purple",fontface="bold",size=2.5,angle=90)+ facet_grid(island~species)
  ![Rplot15](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/59002201-394d-40ed-b38c-fc3ab19f11c1)


# Insights
 * Gentoo are largest on biscoe island.
 * Chinstrap  are largest on dream island.
 * Adelie are largest on torgersen island.




