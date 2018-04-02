Human Activity Recognition Using Smartphones Dataset Version 1.0
================================================================

Jorge L. Reyes-Ortiz(1,2), Davide Anguita(1), Alessandro Ghio(1), Luca
Oneto(1) and Xavier Parra(2) 1 - Smartlab - Non-Linear Complex Systems
Laboratory DITEN - Università degli Studi di Genova, Genoa (I-16145),
Italy. 2 - CETpD - Technical Research Centre for Dependency Care and
Autonomous Living Universitat Politècnica de Catalunya (BarcelonaTech).
Vilanova i la Geltrú (08800), Spain activityrecognition '@' smartlab.ws

=============================================================================================

### Dataset Description

The experiments have been carried out with a group of 30 volunteers
within an age bracket of 19-48 years. Each person performed six
activities (WALKING, WALKING\_UPSTAIRS, WALKING\_DOWNSTAIRS, SITTING,
STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the
waist. Using its embedded accelerometer and gyroscope, we captured
3-axial linear acceleration and 3-axial angular velocity at a constant
rate of 50Hz. The experiments have been video-recorded to label the data
manually. The obtained dataset has been randomly partitioned into two
sets, where 70% of the volunteers was selected for generating the
training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by
applying noise filters and then sampled in fixed-width sliding windows
of 2.56 sec and 50% overlap (128 readings/window). The sensor
acceleration signal, which has gravitational and body motion components,
was separated using a Butterworth low-pass filter into body acceleration
and gravity. The gravitational force is assumed to have only low
frequency components, therefore a filter with 0.3 Hz cutoff frequency
was used. From each window, a vector of features was obtained by
calculating variables from the time and frequency domain. See
'features\_info.txt' for more details.

For each record it is provided:

-   Triaxial acceleration from the accelerometer (total acceleration)
    and the estimated body acceleration.
-   Triaxial Angular velocity from the gyroscope.
-   A 561-feature vector with time and frequency domain variables.
-   Its activity label.
-   An identifier of the subject who carried out the experiment.

The dataset includes the following files:

-   'README.txt'

-   'features\_info.txt': Shows information about the variables used on
    the feature vector.

-   'features.txt': List of all features.

-   'activity\_labels.txt': Links the class labels with their
    activity name.

-   'train/X\_train.txt': Training set.

-   'train/y\_train.txt': Training labels.

-   'test/X\_test.txt': Test set.

-   'test/y\_test.txt': Test labels.

The following files are available for the train and test data. Their
descriptions are equivalent.

-   'train/subject\_train.txt': Each row identifies the subject who
    performed the activity for each window sample. Its range is from 1
    to 30.

-   'train/Inertial Signals/total\_acc\_x\_train.txt': The acceleration
    signal from the smartphone accelerometer X axis in standard gravity
    units 'g'. Every row shows a 128 element vector. The same
    description applies for the 'total\_acc\_x\_train.txt' and
    'total\_acc\_z\_train.txt' files for the Y and Z axis.

-   'train/Inertial Signals/body\_acc\_x\_train.txt': The body
    acceleration signal obtained by subtracting the gravity from the
    total acceleration.

-   'train/Inertial Signals/body\_gyro\_x\_train.txt': The angular
    velocity vector measured by the gyroscope for each window sample.
    The units are radians/second.

### Feature Selection

The features selected for this database come from the accelerometer and
gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain
signals (prefix 't' to denote time) were captured at a constant rate of
50 Hz. Then they were filtered using a median filter and a 3rd order low
pass Butterworth filter with a corner frequency of 20 Hz to remove
noise. Similarly, the acceleration signal was then separated into body
and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ)
using another low pass Butterworth filter with a corner frequency of 0.3
Hz.

Subsequently, the body linear acceleration and angular velocity were
derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and
tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional
signals were calculated using the Euclidean norm (tBodyAccMag,
tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these
signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ,
fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to
indicate frequency domain signals).

These signals were used to estimate variables of the feature vector for
each pattern: '-XYZ' is used to denote 3-axial signals in the X, Y and Z
directions.

tBodyAcc-XYZ tGravityAcc-XYZ tBodyAccJerk-XYZ tBodyGyro-XYZ
tBodyGyroJerk-XYZ tBodyAccMag tGravityAccMag tBodyAccJerkMag
tBodyGyroMag tBodyGyroJerkMag fBodyAcc-XYZ fBodyAccJerk-XYZ
fBodyGyro-XYZ fBodyAccMag fBodyAccJerkMag fBodyGyroMag fBodyGyroJerkMag

The set of variables that were estimated from these signals are:

mean(): Mean value std(): Standard deviation mad(): Median absolute
deviation max(): Largest value in array min(): Smallest value in array
sma(): Signal magnitude area energy(): Energy measure. Sum of the
squares divided by the number of values. iqr(): Interquartile range
entropy(): Signal entropy arCoeff(): Autorregresion coefficients with
Burg order equal to 4 correlation(): correlation coefficient between two
signals maxInds(): index of the frequency component with largest
magnitude meanFreq(): Weighted average of the frequency components to
obtain a mean frequency skewness(): skewness of the frequency domain
signal kurtosis(): kurtosis of the frequency domain signal
bandsEnergy(): Energy of a frequency interval within the 64 bins of the
FFT of each window. angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window
sample. These are used on the angle() variable:

gravityMean tBodyAccMean tBodyAccJerkMean tBodyGyroMean
tBodyGyroJerkMean

The complete list of variables of each feature vector is available in
'features.txt'

### Notes:

Features are normalized and bounded within \[-1,1\]. Each feature vector
is a row on the text file. The units used for the accelerations (total
and body) are 'g's (gravity of earth -&gt; 9.80665 m/seg2). The
gyroscope units are rad/seg. A video of the experiment including an
example of the 6 recorded activities with one of the participants can be
seen in the following link: <http://www.youtube.com/watch?v=XOEN9W05_4A>
For more information about this dataset please contact:
activityrecognition '@' smartlab.ws

1. Loading and pre-processing the dataset
-----------------------------------------

    ## Packages required
    library(reshape2)
    library(data.table)

    ## 
    ## Attaching package: 'data.table'

    ## The following objects are masked from 'package:reshape2':
    ## 
    ##     dcast, melt

    ## Download file from UCI and unzip the file
    download.file("http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip", "sp.zip")
    zipF<-file.choose() # lets you choose a file and save its file path in R (at least for windows)
    outDir<-"smartphones" # Define the folder where the zip file should be unzipped to 
    unzip(zipF,exdir=outDir)

### Loading the feature table

    feature <- read.table(".//smartphones//UCI HAR Dataset//features.txt")[,2]
    length(feature)

    ## [1] 561

### Extracting feature containg mean and std column names

    extract_feature <- grepl("mean|std", feature) 

### Loading activity dataset consisting of activity labels.

    activity <- read.table(".//smartphones//UCI HAR Dataset//activity_labels.txt")[,2]
    head(activity)

    ## [1] WALKING            WALKING_UPSTAIRS   WALKING_DOWNSTAIRS
    ## [4] SITTING            STANDING           LAYING            
    ## 6 Levels: LAYING SITTING STANDING WALKING ... WALKING_UPSTAIRS

### Loading the testing dataset

    x_test <- read.table(".//smartphones//UCI HAR Dataset//test//X_test.txt")
    dim(x_test)

    ## [1] 2947  561

    y_test <- read.table(".//smartphones//UCI HAR Dataset//test//Y_test.txt")
    subject_test <- read.table(".//smartphones//UCI HAR Dataset//test//subject_test.txt")
    head(subject_test)

    ##   V1
    ## 1  2
    ## 2  2
    ## 3  2
    ## 4  2
    ## 5  2
    ## 6  2

    names(x_test) = feature

The x\_test consists of 561 attributes. The analysis depends on mean and
std columns. So, updating x\_test, so that it contains only the mean and
std columns.

    x_test <- x_test[,extract_feature]

    ## Naming labels for test set

    y_test[,2] = activity[y_test[,1]]
    names(y_test) <- c("ID", "Label")
    names(y_test)

    ## [1] "ID"    "Label"

    names(subject_test) <- "Subject"

### Combining all the test tables to a single data frame.

    test <- cbind(as.data.table(subject_test), y_test, x_test)
    names(test)

    ##  [1] "Subject"                         "ID"                             
    ##  [3] "Label"                           "tBodyAcc-mean()-X"              
    ##  [5] "tBodyAcc-mean()-Y"               "tBodyAcc-mean()-Z"              
    ##  [7] "tBodyAcc-std()-X"                "tBodyAcc-std()-Y"               
    ##  [9] "tBodyAcc-std()-Z"                "tGravityAcc-mean()-X"           
    ## [11] "tGravityAcc-mean()-Y"            "tGravityAcc-mean()-Z"           
    ## [13] "tGravityAcc-std()-X"             "tGravityAcc-std()-Y"            
    ## [15] "tGravityAcc-std()-Z"             "tBodyAccJerk-mean()-X"          
    ## [17] "tBodyAccJerk-mean()-Y"           "tBodyAccJerk-mean()-Z"          
    ## [19] "tBodyAccJerk-std()-X"            "tBodyAccJerk-std()-Y"           
    ## [21] "tBodyAccJerk-std()-Z"            "tBodyGyro-mean()-X"             
    ## [23] "tBodyGyro-mean()-Y"              "tBodyGyro-mean()-Z"             
    ## [25] "tBodyGyro-std()-X"               "tBodyGyro-std()-Y"              
    ## [27] "tBodyGyro-std()-Z"               "tBodyGyroJerk-mean()-X"         
    ## [29] "tBodyGyroJerk-mean()-Y"          "tBodyGyroJerk-mean()-Z"         
    ## [31] "tBodyGyroJerk-std()-X"           "tBodyGyroJerk-std()-Y"          
    ## [33] "tBodyGyroJerk-std()-Z"           "tBodyAccMag-mean()"             
    ## [35] "tBodyAccMag-std()"               "tGravityAccMag-mean()"          
    ## [37] "tGravityAccMag-std()"            "tBodyAccJerkMag-mean()"         
    ## [39] "tBodyAccJerkMag-std()"           "tBodyGyroMag-mean()"            
    ## [41] "tBodyGyroMag-std()"              "tBodyGyroJerkMag-mean()"        
    ## [43] "tBodyGyroJerkMag-std()"          "fBodyAcc-mean()-X"              
    ## [45] "fBodyAcc-mean()-Y"               "fBodyAcc-mean()-Z"              
    ## [47] "fBodyAcc-std()-X"                "fBodyAcc-std()-Y"               
    ## [49] "fBodyAcc-std()-Z"                "fBodyAcc-meanFreq()-X"          
    ## [51] "fBodyAcc-meanFreq()-Y"           "fBodyAcc-meanFreq()-Z"          
    ## [53] "fBodyAccJerk-mean()-X"           "fBodyAccJerk-mean()-Y"          
    ## [55] "fBodyAccJerk-mean()-Z"           "fBodyAccJerk-std()-X"           
    ## [57] "fBodyAccJerk-std()-Y"            "fBodyAccJerk-std()-Z"           
    ## [59] "fBodyAccJerk-meanFreq()-X"       "fBodyAccJerk-meanFreq()-Y"      
    ## [61] "fBodyAccJerk-meanFreq()-Z"       "fBodyGyro-mean()-X"             
    ## [63] "fBodyGyro-mean()-Y"              "fBodyGyro-mean()-Z"             
    ## [65] "fBodyGyro-std()-X"               "fBodyGyro-std()-Y"              
    ## [67] "fBodyGyro-std()-Z"               "fBodyGyro-meanFreq()-X"         
    ## [69] "fBodyGyro-meanFreq()-Y"          "fBodyGyro-meanFreq()-Z"         
    ## [71] "fBodyAccMag-mean()"              "fBodyAccMag-std()"              
    ## [73] "fBodyAccMag-meanFreq()"          "fBodyBodyAccJerkMag-mean()"     
    ## [75] "fBodyBodyAccJerkMag-std()"       "fBodyBodyAccJerkMag-meanFreq()" 
    ## [77] "fBodyBodyGyroMag-mean()"         "fBodyBodyGyroMag-std()"         
    ## [79] "fBodyBodyGyroMag-meanFreq()"     "fBodyBodyGyroJerkMag-mean()"    
    ## [81] "fBodyBodyGyroJerkMag-std()"      "fBodyBodyGyroJerkMag-meanFreq()"

### Reading training set data

    x_train <- read.table(".//smartphones//UCI HAR Dataset//train//X_train.txt")
    y_train <- read.table(".//smartphones//UCI HAR Dataset//train//Y_train.txt")
    subject_train <- read.table(".//smartphones//UCI HAR Dataset//train//subject_train.txt")

    ## Naming x_train columns
    names(x_train) <- feature

    ## Updating x_train so that it only contains meand and std col names
    x_train <- x_train[,extract_feature]

    ## Naming labels for training set
    y_train[,2] <- activity[y_train[,1]]
    names(y_train) <- c("ID", "Label")
    names(subject_train) <- "Subject"

### Merging all the train tables into a single table

    train <- cbind(as.data.frame(subject_train), y_train,x_train)
    dim(train)

    ## [1] 7352   82

### Merging test and train data

    tidy_data <- rbind(test,train)
    dim(tidy_data)

    ## [1] 10299    82

    variables = names(tidy_data[,-c("Subject","ID","Label")])
    melt_data = melt(tidy_data, id = c("Subject","ID","Label"), measure.vars = variables)
    head(tidy_data,2)

    ##    Subject ID    Label tBodyAcc-mean()-X tBodyAcc-mean()-Y
    ## 1:       2  5 STANDING         0.2571778       -0.02328523
    ## 2:       2  5 STANDING         0.2860267       -0.01316336
    ##    tBodyAcc-mean()-Z tBodyAcc-std()-X tBodyAcc-std()-Y tBodyAcc-std()-Z
    ## 1:       -0.01465376       -0.9384040       -0.9200908       -0.6676833
    ## 2:       -0.11908252       -0.9754147       -0.9674579       -0.9449582
    ##    tGravityAcc-mean()-X tGravityAcc-mean()-Y tGravityAcc-mean()-Z
    ## 1:            0.9364893           -0.2827192            0.1152882
    ## 2:            0.9274036           -0.2892151            0.1525683
    ##    tGravityAcc-std()-X tGravityAcc-std()-Y tGravityAcc-std()-Z
    ## 1:          -0.9254273          -0.9370141          -0.5642884
    ## 2:          -0.9890571          -0.9838872          -0.9647811
    ##    tBodyAccJerk-mean()-X tBodyAccJerk-mean()-Y tBodyAccJerk-mean()-Z
    ## 1:            0.07204601            0.04575440          -0.106042660
    ## 2:            0.07018069           -0.01787602          -0.001720629
    ##    tBodyAccJerk-std()-X tBodyAccJerk-std()-Y tBodyAccJerk-std()-Z
    ## 1:           -0.9066828           -0.9380164           -0.9359358
    ## 2:           -0.9492040           -0.9726989           -0.9777267
    ##    tBodyGyro-mean()-X tBodyGyro-mean()-Y tBodyGyro-mean()-Z
    ## 1:        0.119976160        -0.09179234          0.1896285
    ## 2:       -0.001552463        -0.18729119          0.1807052
    ##    tBodyGyro-std()-X tBodyGyro-std()-Y tBodyGyro-std()-Z
    ## 1:        -0.8830891        -0.8161636        -0.9408812
    ## 2:        -0.9255665        -0.9295992        -0.9675810
    ##    tBodyGyroJerk-mean()-X tBodyGyroJerk-mean()-Y tBodyGyroJerk-mean()-Z
    ## 1:             -0.2048962            -0.17448771            -0.09338934
    ## 2:             -0.1386685            -0.02580207            -0.07141841
    ##    tBodyGyroJerk-std()-X tBodyGyroJerk-std()-Y tBodyGyroJerk-std()-Z
    ## 1:            -0.9012242            -0.9108601            -0.9392504
    ## 2:            -0.9623042            -0.9562894            -0.9813408
    ##    tBodyAccMag-mean() tBodyAccMag-std() tGravityAccMag-mean()
    ## 1:         -0.8669294        -0.7051911            -0.8669294
    ## 2:         -0.9689614        -0.9539024            -0.9689614
    ##    tGravityAccMag-std() tBodyAccJerkMag-mean() tBodyAccJerkMag-std()
    ## 1:           -0.7051911             -0.9297665            -0.8959942
    ## 2:           -0.9539024             -0.9737168            -0.9410078
    ##    tBodyGyroMag-mean() tBodyGyroMag-std() tBodyGyroJerkMag-mean()
    ## 1:          -0.7955439         -0.7620732              -0.9251949
    ## 2:          -0.8984331         -0.9108583              -0.9733934
    ##    tBodyGyroJerkMag-std() fBodyAcc-mean()-X fBodyAcc-mean()-Y
    ## 1:             -0.8943436        -0.9185097        -0.9182132
    ## 2:             -0.9440900        -0.9609030        -0.9644333
    ##    fBodyAcc-mean()-Z fBodyAcc-std()-X fBodyAcc-std()-Y fBodyAcc-std()-Z
    ## 1:        -0.7890915       -0.9482903       -0.9251369       -0.6363167
    ## 2:        -0.9566748       -0.9843500       -0.9701748       -0.9418619
    ##    fBodyAcc-meanFreq()-X fBodyAcc-meanFreq()-Y fBodyAcc-meanFreq()-Z
    ## 1:            0.01111695             0.1212507            -0.5229487
    ## 2:            0.35206637             0.1745468            -0.3206734
    ##    fBodyAccJerk-mean()-X fBodyAccJerk-mean()-Y fBodyAccJerk-mean()-Z
    ## 1:            -0.8996332            -0.9374850            -0.9235514
    ## 2:            -0.9435190            -0.9691623            -0.9734489
    ##    fBodyAccJerk-std()-X fBodyAccJerk-std()-Y fBodyAccJerk-std()-Z
    ## 1:           -0.9244291           -0.9432104           -0.9478915
    ## 2:           -0.9616312           -0.9800263           -0.9807873
    ##    fBodyAccJerk-meanFreq()-X fBodyAccJerk-meanFreq()-Y
    ## 1:                 0.4510054                 0.1371670
    ## 2:                 0.4728516                 0.1671977
    ##    fBodyAccJerk-meanFreq()-Z fBodyGyro-mean()-X fBodyGyro-mean()-Y
    ## 1:                -0.1802991         -0.8235579         -0.8079160
    ## 2:                -0.2431146         -0.9225130         -0.9264957
    ##    fBodyGyro-mean()-Z fBodyGyro-std()-X fBodyGyro-std()-Y
    ## 1:         -0.9179126        -0.9032627        -0.8226770
    ## 2:         -0.9682295        -0.9270506        -0.9320107
    ##    fBodyGyro-std()-Z fBodyGyro-meanFreq()-X fBodyGyro-meanFreq()-Y
    ## 1:        -0.9561651             0.18403457            -0.05932286
    ## 2:        -0.9701434             0.01810862            -0.22726634
    ##    fBodyGyro-meanFreq()-Z fBodyAccMag-mean() fBodyAccMag-std()
    ## 1:              0.4381072         -0.7909464        -0.7110740
    ## 2:             -0.1516984         -0.9541266        -0.9597458
    ##    fBodyAccMag-meanFreq() fBodyBodyAccJerkMag-mean()
    ## 1:             -0.4834525                 -0.8950612
    ## 2:              0.2034652                 -0.9454372
    ##    fBodyBodyAccJerkMag-std() fBodyBodyAccJerkMag-meanFreq()
    ## 1:                -0.8963596                    -0.03535579
    ## 2:                -0.9341520                    -0.49121253
    ##    fBodyBodyGyroMag-mean() fBodyBodyGyroMag-std()
    ## 1:              -0.7706100             -0.7971128
    ## 2:              -0.9244608             -0.9167741
    ##    fBodyBodyGyroMag-meanFreq() fBodyBodyGyroJerkMag-mean()
    ## 1:                 -0.04739130                  -0.8901655
    ## 2:                 -0.03147392                  -0.9519774
    ##    fBodyBodyGyroJerkMag-std() fBodyBodyGyroJerkMag-meanFreq()
    ## 1:                 -0.9073076                      0.07164545
    ## 2:                 -0.9382124                     -0.40118872

    dim(melt_data)

    ## [1] 813621      5

Finding average of all values using dcast
-----------------------------------------

    tidy_data2 <- dcast(melt_data, Subject + Label ~ variable,mean)
    head(tidy_data2, 2)

    ##    Subject   Label tBodyAcc-mean()-X tBodyAcc-mean()-Y tBodyAcc-mean()-Z
    ## 1:       1  LAYING         0.2215982      -0.040513953        -0.1132036
    ## 2:       1 SITTING         0.2612376      -0.001308288        -0.1045442
    ##    tBodyAcc-std()-X tBodyAcc-std()-Y tBodyAcc-std()-Z tGravityAcc-mean()-X
    ## 1:       -0.9280565       -0.8368274       -0.8260614           -0.2488818
    ## 2:       -0.9772290       -0.9226186       -0.9395863            0.8315099
    ##    tGravityAcc-mean()-Y tGravityAcc-mean()-Z tGravityAcc-std()-X
    ## 1:            0.7055498            0.4458177          -0.8968300
    ## 2:            0.2044116            0.3320437          -0.9684571
    ##    tGravityAcc-std()-Y tGravityAcc-std()-Z tBodyAccJerk-mean()-X
    ## 1:          -0.9077200          -0.8523663            0.08108653
    ## 2:          -0.9355171          -0.9490409            0.07748252
    ##    tBodyAccJerk-mean()-Y tBodyAccJerk-mean()-Z tBodyAccJerk-std()-X
    ## 1:          0.0038382040           0.010834236           -0.9584821
    ## 2:         -0.0006191028          -0.003367792           -0.9864307
    ##    tBodyAccJerk-std()-Y tBodyAccJerk-std()-Z tBodyGyro-mean()-X
    ## 1:           -0.9241493           -0.9548551        -0.01655309
    ## 2:           -0.9813720           -0.9879108        -0.04535006
    ##    tBodyGyro-mean()-Y tBodyGyro-mean()-Z tBodyGyro-std()-X
    ## 1:        -0.06448612         0.14868944        -0.8735439
    ## 2:        -0.09192415         0.06293138        -0.9772113
    ##    tBodyGyro-std()-Y tBodyGyro-std()-Z tBodyGyroJerk-mean()-X
    ## 1:        -0.9510904        -0.9082847            -0.10727095
    ## 2:        -0.9664739        -0.9414259            -0.09367938
    ##    tBodyGyroJerk-mean()-Y tBodyGyroJerk-mean()-Z tBodyGyroJerk-std()-X
    ## 1:            -0.04151729            -0.07405012            -0.9186085
    ## 2:            -0.04021181            -0.04670263            -0.9917316
    ##    tBodyGyroJerk-std()-Y tBodyGyroJerk-std()-Z tBodyAccMag-mean()
    ## 1:            -0.9679072            -0.9577902         -0.8419292
    ## 2:            -0.9895181            -0.9879358         -0.9485368
    ##    tBodyAccMag-std() tGravityAccMag-mean() tGravityAccMag-std()
    ## 1:        -0.7951449            -0.8419292           -0.7951449
    ## 2:        -0.9270784            -0.9485368           -0.9270784
    ##    tBodyAccJerkMag-mean() tBodyAccJerkMag-std() tBodyGyroMag-mean()
    ## 1:             -0.9543963            -0.9282456          -0.8747595
    ## 2:             -0.9873642            -0.9841200          -0.9308925
    ##    tBodyGyroMag-std() tBodyGyroJerkMag-mean() tBodyGyroJerkMag-std()
    ## 1:         -0.8190102              -0.9634610             -0.9358410
    ## 2:         -0.9345318              -0.9919763             -0.9883087
    ##    fBodyAcc-mean()-X fBodyAcc-mean()-Y fBodyAcc-mean()-Z fBodyAcc-std()-X
    ## 1:        -0.9390991        -0.8670652        -0.8826669       -0.9244374
    ## 2:        -0.9796412        -0.9440846        -0.9591849       -0.9764123
    ##    fBodyAcc-std()-Y fBodyAcc-std()-Z fBodyAcc-meanFreq()-X
    ## 1:       -0.8336256       -0.8128916            -0.1587927
    ## 2:       -0.9172750       -0.9344696            -0.0495136
    ##    fBodyAcc-meanFreq()-Y fBodyAcc-meanFreq()-Z fBodyAccJerk-mean()-X
    ## 1:            0.09753484            0.08943766            -0.9570739
    ## 2:            0.07594608            0.23882987            -0.9865970
    ##    fBodyAccJerk-mean()-Y fBodyAccJerk-mean()-Z fBodyAccJerk-std()-X
    ## 1:            -0.9224626            -0.9480609           -0.9641607
    ## 2:            -0.9815795            -0.9860531           -0.9874930
    ##    fBodyAccJerk-std()-Y fBodyAccJerk-std()-Z fBodyAccJerk-meanFreq()-X
    ## 1:           -0.9322179           -0.9605870                 0.1324191
    ## 2:           -0.9825139           -0.9883392                 0.2566108
    ##    fBodyAccJerk-meanFreq()-Y fBodyAccJerk-meanFreq()-Z fBodyGyro-mean()-X
    ## 1:                0.02451362                0.02438795         -0.8502492
    ## 2:                0.04754378                0.09239200         -0.9761615
    ##    fBodyGyro-mean()-Y fBodyGyro-mean()-Z fBodyGyro-std()-X
    ## 1:         -0.9521915         -0.9093027        -0.8822965
    ## 2:         -0.9758386         -0.9513155        -0.9779042
    ##    fBodyGyro-std()-Y fBodyGyro-std()-Z fBodyGyro-meanFreq()-X
    ## 1:         -0.951232        -0.9165825           -0.003546796
    ## 2:         -0.962345        -0.9439178            0.189153021
    ##    fBodyGyro-meanFreq()-Y fBodyGyro-meanFreq()-Z fBodyAccMag-mean()
    ## 1:            -0.09152913             0.01045813         -0.8617676
    ## 2:             0.06312707            -0.02978392         -0.9477829
    ##    fBodyAccMag-std() fBodyAccMag-meanFreq() fBodyBodyAccJerkMag-mean()
    ## 1:        -0.7983009             0.08640856                 -0.9333004
    ## 2:        -0.9284448             0.23665501                 -0.9852621
    ##    fBodyBodyAccJerkMag-std() fBodyBodyAccJerkMag-meanFreq()
    ## 1:                -0.9218040                      0.2663912
    ## 2:                -0.9816062                      0.3518522
    ##    fBodyBodyGyroMag-mean() fBodyBodyGyroMag-std()
    ## 1:              -0.8621902             -0.8243194
    ## 2:              -0.9584356             -0.9321984
    ##    fBodyBodyGyroMag-meanFreq() fBodyBodyGyroJerkMag-mean()
    ## 1:               -0.1397750127                  -0.9423669
    ## 2:               -0.0002621867                  -0.9897975
    ##    fBodyBodyGyroJerkMag-std() fBodyBodyGyroJerkMag-meanFreq()
    ## 1:                 -0.9326607                       0.1764859
    ## 2:                 -0.9870496                       0.1847759

    dim(tidy_data2)

    ## [1] 180  81

The dataset is tidy and cleaned which can be used for the analysis.
