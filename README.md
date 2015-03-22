---
title: "README.md"
author: "kat_ruska"
---

#The repo contains:
1. The original dataset 'HARData.zip' downloaded from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip.
2. The 'run_analysis.R' file, containing the code, tranforming the original data and creating 'tidy.txt' file.
3. The 'codebook.md', describing the variables.
4. The 'README.md', describing how the script in the 'run_analysis.R' works.

#How the script works:

Read and merge "X_train.txt", "X_test.txt", "Y_train.txt", "Y_test.txt", "subject_test.txt", "subject_train.txt" of the original dataset into the data frame names 'XYS'.

```{r}
x.train <- read.table("./train/X_train.txt")
y.train <- read.table("./train/y_train.txt")
s.train <- read.table("./train/subject_train.txt")
x.test <- read.table("./test/X_test.txt")
y.test <- read.table("./test/y_test.txt")
s.test <- read.table("./test/subject_test.txt")
Y <- rbind(y.train, y.test)
S <- rbind(s.train, s.test)
X <- rbind(x.train, x.test)
XYS <- cbind(S, Y, X)
colnames(XYS)[1:2] <- c("subject", "activity")
```

Extracting only the mean and standard deviation for each measurement based on "features.txt" of the original dataset. The 'myDAT' is an output dataframe, containing the variable along with subjects and activities.

```{r}
feat <- read.table("./features.txt")
m.std.codes <- subset(feat, grepl("mean\\(\\)|std\\(\\)", 
                                  feat[, 2], ignore.case = T, perl = T), 
                      select = 1:2)
Vcodes <- sapply(m.std.codes[,1], function(x) paste("V", x, sep = ""))
DAT <- XYS[, Vcodes]
colnames(DAT) <- m.std.codes[,2]
myDAT <- cbind(XYS[1:2], DAT)
```

``` {r, echo = False}
head(myDAT[, 1:10])
```
Recoding activities: add descriptive activity names instead of numbers based on 'activity_labels.txt' of the original dataset.

```{r}
activ.lab <- read.table("./activity_labels.txt")
activ.lab[,2] <- as.character(activ.lab[, 2])
for (i in 1:length(myDAT$activity)) myDAT$activity[i] <- activ.lab[myDAT$activity[i], 2]
```

Creating and saving a new tidy data set with the means of each variables grouped by subject and activity.

```{r}
myDATn <- aggregate(. ~ activity + subject, data = myDAT, mean)
myDATn <- myDATn[, c(2, 1, 3:ncol(myDATn))]
write.table(myDATn, file = "tidy.txt", sep = " ", row.name = F)
```