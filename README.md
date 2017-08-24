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
#setwd("I:/Unreviewed Excel Training Data/ Matt'sExcelTraining Data")
library(XLConnect)

data1 = readWorksheetFromFile("Boys + Girls Club Camp Training 2016.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data1) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data1)
data1$site = rep(1,length(data1$`Pre-Competent`))
head(data1)

data2 = readWorksheetFromFile("Indiana School Health Conference.xlsx", sheet = 1, startCol = 6, endCol = 15)
colnames(data2) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data2)
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
data13 = as.data.frame(data13[-c(1),])

data14 = readWorksheetFromFile("Merriville Training 7272016.xlsx", sheet = 1, startCol = 8, endCol = 17)
colnames(data14) = c("Pre-Competent",	"Pre-Confident",	"Pre-Comfort",	 "Post-Competent",	"Post-Confident",	"Post-Comfort",	"Learned",	"Effective",	"Came Away With",	"Recommend")
head(data14)
data14 = data14[-c(1),]
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
dataPreComp = as.factor(data$`Pre-Competent`)
levels(dataPreComp)
data = as.data.frame(data)

dataPreCon = as.factor(data$`Pre-Confident`)
levels(dataPreCon)
data = as.data.frame(data)

data = as.data.frame(data)
dataPreComfort = as.factor(data$`Pre-Comfort`)
levels(dataPreComfort)
data = as.data.frame(data)


data = as.data.frame(data)
dataPostComp = as.factor(data$`Post-Competent`)
head(dataPostComp)
levels(dataPostComp)
data = as.data.frame(data)
data$`Post-Competent`

data = as.data.frame(data)
data$`Post-Confident`
dataPostCon = as.factor(data$`Post-Confident`)
head(dataPostCon)
levels(dataPostCon)
data = as.data.frame(data)

# Here need to recode based upon this.  You are grabbing the wrong values somewhere.
data = as.data.frame(data)
data$`Post-Comfort`
dataPostConf = as.factor(data$`Post-Comfort`)
head(dataPostConf)
levels(dataPostConf)
data = as.data.frame(data)


data = as.data.frame(data)
data$Learned
dataLearned = as.factor(data$Learned)
head(dataLearned)
levels(dataLearned)
data = as.data.frame(data)

data = as.data.frame(data)
data$Effective
dataEffective = as.factor(data$Effective)
head(dataEffective)
levels(dataEffective)
data = as.data.frame(data)

data = as.data.frame(data)
data$`Came Away With`
dataCAW = as.factor(data$`Came Away With`)
head(dataCAW)
levels(dataCAW)
data = as.data.frame(data)

data = as.data.frame(data)
data$Recommend
dataRec = as.factor(data$Recommend)
head(dataRec)
levels(dataRec)
data = as.data.frame(data)

data = apply(data,2, function(x){ifelse(x == "[Crossed out 7] 9 ", 9, ifelse(x == "2 <-> 3", 2.5, ifelse(x == "7 & 10", 8.5, ifelse(x == "7&8", 7.5, ifelse(x == "8-9", 8.5, ifelse(x == "No Pre", NA, ifelse(x == "7_8" , 7.5, ifelse(x == "NR", NA, ifelse(x == "6-7", 6.5, ifelse(x == "7_9", 8, ifelse(x == "8_10", 9, ifelse(x == "9 10", 9.5, ifelse(x =="4-5", 4.5, ifelse(x == "7-9", 8, ifelse(x == "N/A", NA, ifelse(x =="\"N/A\"", NA, ifelse(x == "3 I can't create it.", 3, ifelse(x == "6_7", 6.5, ifelse(x == "8&9", 8.5, ifelse(x == "No Pre", NA, ifelse(x == "[Crossed out 9] 7", 7, ifelse(x == "3_4", 3.5, ifelse(x == "5 6", 5.5, ifelse(x == "7-8", 8.5, ifelse(x == "9-10", 9.5, ifelse(x == "Not sure", NA, ifelse(x == "9 (10 crossed out) ", 9, ifelse(x == "N/A", NA,ifelse(x == "9 10 ", 9.5, ifelse(x == "[Crossed out 7] 9", 9, ifelse(x == "6 7 ", 6.5, ifelse(x == "9&10", 9.5, ifelse(x == "[Crossed out 9] 10", 10, ifelse(x =="5 Resources helpful", 5, ifelse(x == "7 (Crossed out \"4\")", 7, ifelse(x == "8_9", 8.5, ifelse(x == "9_10", 9.5, ifelse(x == "99", NA, ifelse(x == "[Scribbled out 5]", NA, ifelse(x == "4_5" , 4.5, ifelse(x == "8-8", 8,ifelse(x == "10 (\"Crossed out \"7\")", 10,ifelse(x == "10 (Crossed out 9)", 10, ifelse(x == "5 6 ", 5.5, ifelse(x == "6 I mean, for myself.", 6, ifelse(x == "7 (5 crossed out)", 7, ifelse(x == "9_11", 10.5, ifelse(x == "\"Better\"", NA, x ))))))))))))))))))))))))))))))))))))))))))))))))})
data = as.data.frame(data)

data = apply(data,2, function(x){ifelse(x == "[Scribbled out 5 and underlined 8]", 8, ifelse(x == "10 (Crossed out \"7\")", 10, ifelse(x == "2 \"Willing but a lot to learn", 2, ifelse(x == "5 to 7", 6, ifelse(x == "6 (3 crossed out)", 6, ifelse(x == "7 Still need practice!!", 7 , ifelse(x == "9 10 sometimes I mess up.", 9.5, ifelse(x== "As long as I know what they are.", 9, ifelse(x == "9_12", 10.5, ifelse(x == "S", NA, ifelse(x == "Same response as on the PRE-ASSESSMENT.", NA, ifelse(x == "A + Strongly Agree", 7, ifelse(x== "Strongly Agree", 7, ifelse(x == "Strongly Disagree", 1, ifelse(x == "Disagree", 3, ifelse(x == "Neutral", 4, ifelse(x == "Agree", 6, ifelse(x == "Strongly Agree", 7, ifelse(x == "Circled Strongly Agree and Agree", 6, ifelse(x == "Neural", 4, ifelse(x== "Stringly Agree", 7,ifelse(x == "Strongly Agree [Crossed out \"Strongly Disagree\"]", 7, ifelse(x == "Agree *Strongly Agree*", 6, ifelse(x == "D_N", NA, ifelse(x == "N + Agree", 4, ifelse(x == "Neutral ", 3, ifelse(x == "Nuetral", 3,ifelse(x == "Strongly agree", 5, ifelse(x == "Strongly Agree ", 7,ifelse(x == "N_A", NA, ifelse(x == "Agree ", 6, ifelse(x== "Agree Strongly Agree", 7, ifelse(x == "Stongly Agree", 7, ifelse(x == "[circled \"LGBTQ+ youth\"]", NA, ifelse(x == "Agree Don't directly work w/youth in my job.", 6, ifelse(x == "I learned a lot from the research data statements. That was eye popping to me. I plan to share those findings to my students.", NA, ifelse(x == "Strongly Agree (Police Dept. Sherifs Dept.)", 7, ifelse(x =="Strongly Agree!", 7, ifelse(x == " Strongly Agree", 7, x)))))))))))))))))))))))))))))))))))))))})
data = as.data.frame(data)
data = apply(data,2, function(x){ifelse(x == "\"Unsure\"", NA, ifelse(x == "?", NA, ifelse(x == "[Crossed out 8] 10", 10, ifelse(x == "[Crossed out 8] 5 I usually use their name, so I don't make a mistake and offend someone.", 5, ifelse(x == "10 -Had transgender student in class and referred to the student's preferred gender pronouns", 10, ifelse(x == "10 I see no reason why you could object to this as long as you know the preference.", 10, ifelse(x == "2_3", 2.5, ifelse(x ==  "4 My fear is of offending the person by doing something wrong." , 4, ifelse(x=="5_7", 6,ifelse(x == "6 to 10 [wrote \"competent\"]", 8, ifelse(x== "6&7", 6.5, ifelse(x == "8 I'm comfortable using them I'm just horrible @ remembering!!!" , 8, ifelse(x =="N/A 9", 9, ifelse(x == "Using the pronouns to refer to that someone: 9 using the pronouns to refer to myself, or for myself: would depend on what the pronouns were.", NA, ifelse(x == "5_6", 5.5, ifelse(x =="6 I mean, for myself…", 6, ifelse(x == "77", 7, ifelse(x== "6 I mean, for myself…", 6, ifelse(x == "10 [wrote \"& confident\"]", 10, ifelse(x == "9 As long as I know what they are.", 9, ifelse(x =="WOULD NEED TO PRACTICE THIS ONE seemed to go over fast - future maybe give examples more", NA, x)))))))))))))))))))))})
dat = as.data.frame(data)
dim(dat)
```
Now set up t-tests if there is a difference bewteen post and pre.  Use Wilcoxon Signed-Ranks Test: http://www.uv.es/visualstats/vista-frames/help/lecturenotes/lecture09/lec9part4.html

Here I am getting the statistically significant tests and the percentage increase in medians.

Also grabing the number of particpants here 954
```{r}
library(MASS)
write.csv(dat, "dat.csv", row.names = FALSE)
dat = as.data.frame(read.csv("dat.csv", header = TRUE))
## Grabbing number of particpants before deleting data
dim(dat)
dat = as.data.frame(na.omit(dat))
wilcox.test(dat$Pre.Competent, dat$Post.Competent, paired=TRUE)
wilcox.test(dat$Pre.Confident, dat$Post.Confident, paired=TRUE)
wilcox.test(dat$Pre.Comfort, dat$Post.Comfort, paired=TRUE)
datMean = as.data.frame(t((apply(dat, 2, mean)))); datMean

datMean$CompInc = (datMean$Post.Competent-datMean$Pre.Competent)/datMean$Pre.Competent

datMean$ConfiInc =(datMean$Post.Confident-datMean$Pre.Confident)/datMean$Pre.Confident

datMean$ComiInc =(datMean$Post.Comfort-datMean$Pre.Comfort)/datMean$Pre.Comfort
datMean = round(datMean,2); datMean
```
Now we need to figure out 
