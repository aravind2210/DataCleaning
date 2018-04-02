# DataCleaning



Coursera - Getting and Cleaning Data 
==================================================================

This data set was drawn from the Human Activity Recognition Using Smartphones Data Set, which was created as follows: The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

I have combined the test data and training data into one data set and extracted several measures from it.

The signals were used to estimate variables of the feature vector for each pattern:
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ tGravityAcc-XYZ tBodyAccJerk-XYZ tBodyGyro-XYZ tBodyGyroJerk-XYZ tBodyAccMag tGravityAccMag tBodyAccJerkMag tBodyGyroMag tBodyGyroJerkMag fBodyAcc-XYZ fBodyAccJerk-XYZ fBodyGyro-XYZ fBodyAccMag fBodyAccJerkMag fBodyGyroMag fBodyGyroJerkMag

My data set has extracted several variables from the above data set, namely, mean(): Mean value and std(): Standard deviation for each of the directions and signals. I have aggregated the data by subject (the 30 volunteers) and activity (walking, Walking upstairs, etc.) and summarized the data by giving the mean and standard devition for each of the directions and signals.

=======================================================================
