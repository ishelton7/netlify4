---
title: "Scatterplot"
date: 2014-03-10
tags: ["visualization"]
draft: false
---

```{r}

library(Lahman)
library(sqldf)
library(devtools)
library(ggplot2)

#extracting data

query<-"SELECT playerID,sum(HR) AS career_HR,
sum(SO) AS career_SO FROM Batting 
GROUP BY playerID HAVING sum(HR)>=400"

result<-sqldf(query)

#visualizing data

ggplot()+
  geom_point(data=result,aes(x=career_SO,y=career_HR), size=1,color="Blue")+
  ggtitle("Career Strikeouts v. Homeruns for Great Hitters")+
  xlab("Career Strikeouts")+
  ylab("Career Homeruns")
  
```
