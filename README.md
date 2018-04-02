# DataCleaning



Coursera - Getting and Cleaning Data 
==================================================================

The analysis works as follows:

After we have downloaded and unpacked the .zip-file in our working directory, the script extracts the relevant .txt files (note: we do not need all the .txt files included in the zip).

The script then merges the test and train sets into total sets and adds descriptive column names, using the 'features.txt' file.

Then, the script extracts only the measurements on the mean and standard deviation for each measurement and merges the separate tables together, creating the tidy_data_1 table. Finally, the script adds descriptive activity names to name the activities in the dataset.

Our script then creates the second table, called tidy_data_2, including the average of each variable for each activity and each subject. This dataset is called tidy_data_2.
