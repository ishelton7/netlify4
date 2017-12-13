---
title: "Bar Plots"
date: 2014-09-28
tags: ["visualization"]
draft: false
---

Within this post we will be looking at visualization using Bar Plots.

```{r}

llibrary(Lahman)
library(sqldf)
library(devtools)
library(ggplot2)

# extracting the data---------------------------- 
  
query<-"SELECT name,HR 
FROM Teams 
Where yearID=1980 
ORDER BY HR" 
  
result<-sqldf(query) 
  
result$name<-factor(result$name,levels=result$name) 
  
# visualizing the data----------------------------- 
  
ggplot()+ 
  geom_bar(data=result,aes(x=name,y=HR),stat='identity',color='blue',fill='white')+ 
  coord_flip()+ 
  ylab("homeruns")+ 
  xlab("team")+ 
  ggtitle("1980 Team Homerun Distribution")
  
```