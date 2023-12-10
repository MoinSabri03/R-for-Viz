# R-for-Viz
#  R for Visualization

Palmers penguins and Diamond

IN this project we gonna use different ideas and techniques to show the effective and eye-catching visualization through which our audience understand it easily .


> install.packages("tidyverse")

* package ‘tidyverse’ successfully unpacked and MD5 sums checked

	
> library(tidyverse)

install.packages(dplyr)
library(dplyr)
  * dplyr package is use to make the data clean

# Code To filter and sort the toothgrowth data
> data("ToothGrowth")
> View((ToothGrowth))
>
> filtered_tg <-filter(ToothGrowth,dose==0.5)
> View(ToothGrowth)
      * filtering data where dose is 0.5


> arrange(filtered_tg,len)
      * sorting by len

O/p
    ![Screenshot (33)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/b8074a31-d0eb-4feb-b195-f53180c08292)

# to group by 
filtered_tgpipes<-ToothGrowth %>% 
  filter(dose==0.5) %>% 
  group_by(supp) %>% 
  summarize(mean_len=mean(len,na.rm = T),.groups = "drop")


![Screenshot (34)](https://github.com/MoinSabri03/R-for-Viz/assets/152681629/d337d4ff-fc6a-4664-bd01-36ac876c8259)


# MOdule 3
install.packages("palmerpenguins")
library(palmerpenguins)
install.packages("here")
library(here)
install.packages("janitor")
library(janitor)
install.packages("skimr")
library(skimr)
skim_without_charts(penguins)

head(penguins)

glimpse(penguins)

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


