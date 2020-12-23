---
date: "2016-11-05T19:41:01+05:30"
draft: false
image: img/portfolio/business-card-26.jpg
showonlyimage: false
title: [菜狗学R] 数据清理的方法和建立网站的方法，你学会（废）了吗？
weight: 1
---



```{r}
### 这个是md文件，写不了代码啊！！！！


cz <- read.csv("cz.xlsx")

cz$ym <- paste(cz$year, cz$month, sep = "_")
  
cz2 <- data.frame(year = rep(2006:2019, each = 12),
                  month = rep(1:12, 14))
cz2$ym <- paste(cz2$year, cz2$month, sep = "_")


cz3 <- merge(cz, cz2, by = "ym", all = TRUE)
cz3 <- cz3[, !(colnames(cz3) %in% c("ym", "year.y", "month.y"))] #!表示“非”
cz4 <- cz3[order(cz3$year.x, cz3$month.x), ]

write.csv(cz4,"cz4.csv")

```