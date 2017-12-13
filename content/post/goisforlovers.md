---
title: "Time Series "
date: 2014-04-02
tags: [ "visualization"]
draft: false
---

This Time Series will display Babe Ruth's homerun total trends over the years.

```{r}

library(Lahman)
library(sqldf)
library(devtools)
library(ggplot2)

# extracting the data------------------------ 
  
query<-"SELECT yearID,HR 
FROM Teams 
Where teamID='NYA'" 
  
result<-sqldf(query) 
  
#visualize the data------------------- 
  
ggplot()+ 
  geom_line(data=result,aes(x=yearID,y=HR))+ 
  xlab('year')+ 
  ylab('homeruns') 
  
```