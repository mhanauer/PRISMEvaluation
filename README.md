---
title: "Missing Data Project"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Here we are reading in each data file naming them data1:total.  See what happens when there is missing data.

Pre-Competent,	Pre-Confident,	Pre-Comfort,	 Post-Competent,	Post-Confident,	Post-Comfort,	Learned,	Effective,	Came Away With,	Recommend

Get differences bewteen pre and post of competent, confident, and then transform learned, effective came away with, and recommend to scales combine all positive and get percentage of people who agreed with these statements. 

Also include the number of sites they supported and the different types of professional they supported

Could do a separate analysis on pre and post tests for MCCSC PrePost Tests data set.

Pride board training or Allied media data set had a different set of outcomes variables.
```{r}
setwd("~/Box Sync/Unreviewed Excel Training Data/ Matt'sExcelTraining Data")
library(XLConnect)

data1 = readWorksheetFromFile("Boys + Girls Club Camp Training 2016.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data1) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data1)
data1$site = rep(1,length(data1$`Pre-Competent`))
head(data1)

data2 = readWorksheetFromFile("Indiana School Health Conference.xlsx", sheet = 1, startCol = 6, endCol = 15)
colnames(data2) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data1)
data2$site = rep(2,length(data2$`Pre-Competent`))

data3 = readWorksheetFromFile("ISCA Fall 2015.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data3) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data3)
data3$site = rep(3,length(data3$`Pre-Competent`))

data4 = readWorksheetFromFile("IU Pre School Training 12716.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data4) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data4)
data4$site = rep(4,length(data4$`Pre-Competent`))

data5 = readWorksheetFromFile("IU Pre School Training 12716.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data5) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data5)
data5$site = rep(5,length(data5$`Pre-Competent`))

data6 = readWorksheetFromFile("IUSSW Alumni Conference.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data6) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data6)
data6$site = rep(6,length(data6$`Pre-Competent`))


data7 = readWorksheetFromFile("Ivy Tech 2017 Training.xlsx", sheet = 1, startCol = 6, endCol = 15)
colnames(data7) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data7)
data7$site = rep(7,length(data7$`Pre-Competent`))

data8 = readWorksheetFromFile("IYI Conference.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data8) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data8)
data8$site = rep(8,length(data8$`Pre-Competent`))

data9 = readWorksheetFromFile("MCCSC LGBTQA+ Competency Training_assessment data.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data9) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data9)
data9$site = rep(9,length(data9$`Pre-Competent`))

data10 = readWorksheetFromFile("MCCSC LGBTQA+ Competency Training_assessment data.xlsx", sheet = 2, startCol = 8, endCol = 17)
colnames(data10) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data10)
data10$site = rep(10,length(data10$`Pre-Competent`))


data11 = readWorksheetFromFile("MCCSC LGBTQA+ Competency Training_assessment data.xlsx", sheet = 3, startCol = 9, endCol = 18)
colnames(data11) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data11)
data11$site = rep(11,length(data11$`Pre-Competent`))

data12 = readWorksheetFromFile("Meadows Hospital Lunch & Learn.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data12) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data12)
data12$site = rep(12,length(data12$`Pre-Competent`))

data13 = readWorksheetFromFile("Merriville Training 7272016.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data13) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data13)
data13$site = rep(13,length(data13$`Pre-Competent`))

data14 = readWorksheetFromFile("Merriville Training 7272016.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data14) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data14)
data14$site = rep(14,length(data14$`Pre-Competent`))

data15 = readWorksheetFromFile("Terre Haute 7272016.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data15) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data15)
data15$site = rep(15,length(data15$`Pre-Competent`))


data16 = readWorksheetFromFile("IUSSW Alumni Conference.xlsx", sheet = 2, startCol = 7, endCol = 16)
colnames(data16) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data16)
data16$site = rep(16,length(data16$`Pre-Competent`))

data17 = readWorksheetFromFile("Youth Services Association Administraiont 9012016.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data17) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data17)
data17$site = rep(17,length(data17$`Pre-Competent`))

data18 = readWorksheetFromFile("Youth Services Association Session 2.xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data18) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data18)
data18$site = rep(18,length(data18$`Pre-Competent`))

data19 = readWorksheetFromFile("Youth Services Bureau 7-29-16 (Created by Piper; Edited by Brie).xlsx", sheet = 1, startCol = 7, endCol = 16)
colnames(data19) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data19)
data19$site = rep(19,length(data19$`Pre-Competent`))

data = rbind(data1, data2, data3, data4, data5, data6, data7, data8, data9, data10, data11, data12, data13, data14, data15, data16, data17, data18, data19)
data = as.data.frame(data)
data = apply(data, 2, function(x){ifelse(x == "Blank", NA, x)})
data = as.data.frame(na.omit(data))
dim(data)
data
```
Now figure out the levels for each and make sense of each 
```{r}

```

