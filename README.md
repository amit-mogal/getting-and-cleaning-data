Getting and Cleaning Data
This is a repository for any and all code written for the Getting and Cleaning Data Coursera course through Johns Hopkins University.

Course Project
(find all project-related materials in the UCI HAR Dataset directory, however, copies of the important files have been put into this main directory to fulfill the submission requirement)

Unzip the source (https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) into a folder on your local drive, say C:\Users\yourname\Documents\R\

Put run_analysis.R into C:\Users\yourname\Documents\R\UCI HAR Dataset\

In RStudio: setwd("C:\\Users\\yourname\\Documents\\R\\UCI HAR Dataset\\"), followed by: source("run_analysis.R")

Use data <- read.table("data_set_with_the_averages.txt") to read the data. It is 180x68 because there are 30 subjects and 6 activities, thus "for each activity and each subject" means 30 * 6 = 180 rows. Note that the provided R script has no assumptions on numbers of records, only on locations of files.




run_analysis.R file contains all the logic to get and clean data in order to perform analysis. Execute the script to obtain tidy data set, which will be similar to the dataset stored in tidy_dataset.csv file.

There are 4 functions in run_analysis.R file
1- merge_train_test_dataset
The function returns dataset which contains observations from both train and test dataset. It first loads the training data from X_train.txt file stored in UCI HAR Dataset/train directory into a data table and binds with it subject variable as well as activity variable related to the training data, which is stored in file subject_train.txt and activity_labels.txt respectively. It then performs same steps for test data as well which is stored in directory UCI HAR Dataset/test and then merges the train and test dataset.

2- activities_transforming_into_descriptive_activities
The function apply transformation to activity variable by transforming activity values into descriptive form. The following transformation/mapping was applied:
1 was mapped to WALKING
2 was mapped to WALKING_UPSTAIRS
3 was mapped to WALKING_DOWNSTAIRS
4 was mapped to SITTING
5 was mapped to STANDING
6 was mapped to LAYING

3- extract_measurements_mean_std
The function is resposible for extracting only the measurements on the mean and standard deviation for each measurement from the dataframe returned by above function.

4- average_activity_subject
The function takes in the dataframe returned by above function and then calculates the average of each variable for each activity and each subject and returns the summary in a dataframe.
