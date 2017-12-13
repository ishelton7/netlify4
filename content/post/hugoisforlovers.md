---
title: "Histograms"
date: 2014-04-02
tags: ["visualization]
draft: false
---

Histograms use only one column of data which is shown below when we look for player weights from the Master table.

```{r}

library(Lahman)
library(sqldf)
library(ggplot2)

query<-"SELECT weight FROM Master"

result<-sqldf(query)

#visualizing the data

ggplot()+
  geom_histogram(data=result,aes(x=weight),color="green",fill="black",bins=50)+
  ggtitle("Baseball Player Body-Weight Distribution")

```