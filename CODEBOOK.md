---
title: "The Codebook"
author: "kat_ruska"
---

#Data preparation
The 'tidy.txt' dataset is made based on the data collected from the accelerometers from the Samsung Galaxy S smartphone. The original dataset can be downloaded from [the original data](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip). 
The 'tidy.txt' is  result of the following transformations with the original data:

1. Merging training and test datasets, namely "X_train.txt", "X_test.txt", "Y_train.txt", "Y_test.txt", "subject_test.txt", "subject_train.txt".
2. Extracting only the mean and standard deviation for each measurement based on "features.txt" of the original dataset.
3. Recoding the activity variable, using desctiption in "activity_labels.txt" (walking, walking_upstairs, waking_downstairs, sitting, standing, laying). Renaming variables, using their desctiptive names.
4. Taking average of each variable by each activity and each subject(volunteer).

The 'run_analysis.R' contains the code to do the transformations. The README.md contains further explanations.

#Variables
The 'tidy.txt' contains the mean grouped by each activity of each subject/volunteer of the following variables:

"tBodyAcc-mean()-X"

"tBodyAcc-mean()-Y"

"tBodyAcc-mean()-Z"

"tBodyAcc-std()-X"

"tBodyAcc-std()-Y"

"tBodyAcc-std()-Z"

"tGravityAcc-mean()-X"

"tGravityAcc-mean()-Y"

"tGravityAcc-mean()-Z"

"tGravityAcc-std()-X"

"tGravityAcc-std()-Y"

"tGravityAcc-std()-Z"

"tBodyAccJerk-mean()-X"

"tBodyAccJerk-mean()-Y"

"tBodyAccJerk-mean()-Z"

"tBodyAccJerk-std()-X"

"tBodyAccJerk-std()-Y"

"tBodyAccJerk-std()-Z"

"tBodyGyro-mean()-X"

"tBodyGyro-mean()-Y"

"tBodyGyro-mean()-Z"

"tBodyGyro-std()-X"

"tBodyGyro-std()-Y"

"tBodyGyro-std()-Z"

"tBodyGyroJerk-mean()-X"

"tBodyGyroJerk-mean()-Y"

"tBodyGyroJerk-mean()-Z"

"tBodyGyroJerk-std()-X"

"tBodyGyroJerk-std()-Y"

"tBodyGyroJerk-std()-Z"

"tBodyAccMag-mean()"

"tBodyAccMag-std()"

"tGravityAccMag-mean()"

"tGravityAccMag-std()"

"tBodyAccJerkMag-mean()"

"tBodyAccJerkMag-std()"

"tBodyGyroMag-mean()"

"tBodyGyroMag-std()"

"tBodyGyroJerkMag-mean()"

"tBodyGyroJerkMag-std()"

"fBodyAcc-mean()-X"

"fBodyAcc-mean()-Y"

"fBodyAcc-mean()-Z"

"fBodyAcc-std()-X"

"fBodyAcc-std()-Y"

"fBodyAcc-std()-Z"

"fBodyAccJerk-mean()-X"

"fBodyAccJerk-mean()-Y"

"fBodyAccJerk-mean()-Z"

"fBodyAccJerk-std()-X"

"fBodyAccJerk-std()-Y"

"fBodyAccJerk-std()-Z"

"fBodyGyro-mean()-X"

"fBodyGyro-mean()-Y"

"fBodyGyro-mean()-Z"

"fBodyGyro-std()-X"

"fBodyGyro-std()-Y"

"fBodyGyro-std()-Z"

"fBodyAccMag-mean()"

"fBodyAccMag-std()"

"fBodyBodyAccJerkMag-mean()"

"fBodyBodyAccJerkMag-std()"

"fBodyBodyGyroMag-mean()"

"fBodyBodyGyroMag-std()"

"fBodyBodyGyroJerkMag-mean()"

"fBodyBodyGyroJerkMag-std()"

The original variables come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. The files "README.txt" and "features_info.txt" of the original data set contain more information about these variables.

#To obtain the 'tidy.txt' from the original data set:
To obrain the 'tidy.txt' download and unzip the orginal dataset to your working directory. Open and run 'run_analysis.R'.





