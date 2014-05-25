# Activity Recognition Code Book

This file describes the tidy dataset and the procedure used to generate it.

# Data
This file contains partial results from a series of experiments carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (`WALKING`, `WALKING_UPSTAIRS`, `WALKING_DOWNSTAIRS`, `SITTING`, `STANDING`, `LAYING`) wearing a smartphone (Samsung Galaxy S II) on the waist.

The original researchers published a primary dataset containing 561 features summarizing the sensor data. A subset of these summary features is presented here, aggregated to the mean by subject-activity.

The researchers' raw data (available in the "Inertial Signals" folder in the source data) is not used. In addition, variables measuring angular quantities are excluded since they cannot be aggregated meaningfully.

The data used in this analysis was originally collected by:

> Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

# Transformations
We applied several transformations to create the tidy dataset.

1. Re-combine matching test and training data files into unified files (e.g. X_test.txt + X_train.txt = X.txt)
2. Join the data matrix (`X`) with subject (`subject`) and activity (`y`) metadata
3. Attach appropriate variable names (from `features.txt`) to the merged dataset.
4. Keep only the columns that summarize the raw data via mean (`mean()`) or standard deviation (`std()`), or provide unit identification (`subject`, `activity`)
5. Replace activity id codes with descriptive activity names using the mapping from `activity_labels.txt`
6. Replace subject id codes with "subject [id]"
7. Reshape to a tidy dataset keyed by `subject` and `activity`, aggregating measures with `mean()`.

# Variables
The values for all non-id variables are the average value for that variable for that each `subject`-`activity` pair.

Most variables use the naming convention `domain`_`measure`_`aggregation`_`dimension` where:

 - `domain` (`freq` or `time`) indicates time or frequency domain
 - `measure` is the substantive quantity of interest
 - `aggregation` (`mean`, `meanFreq` or `std`) indicates whether the initial aggregation from the raw data was raw mean, frequency mean or standard deviation. (All variables were aggregated a second time, by mean, to create the tidy dataset)
 - `dimension` (`X`, `Y`, or `Z`) indicates which axis in 3-dimensional space was measured.

## Unit Variables
- `activity`, the activity performed by the subject to generate the data
- `subject`, the subject who performed the action

## Measure Variables
The tidy dataset contains many variables for each measure, accounting for different domains, aggregations and dimensions. Variables that refer to the same measure are grouped together.

### BodyAcc
The portion of acceleration attributable to the movement of the subject's body, as measured by the accelerometer. 

`time_BodyAcc_mean_X`, `time_BodyAcc_mean_Y`, `time_BodyAcc_mean_Z`, `time_BodyAcc_std_X`, `time_BodyAcc_std_Y`, `time_BodyAcc_std_Z`, `freq_BodyAcc_mean_X`, `freq_BodyAcc_mean_Y`, `freq_BodyAcc_mean_Z`, `freq_BodyAcc_std_X`, `freq_BodyAcc_std_Y`, `freq_BodyAcc_std_Z`, `freq_BodyAcc_mean_X`, `freq_BodyAcc_mean_Y`, `freq_BodyAcc_mean_Z`, `freq_BodyAcc_meanFreq_X`, `freq_BodyAcc_meanFreq_Y`, `freq_BodyAcc_meanFreq_Z`

### GravityAcc
The portion of acceleration attributable to gravity, as measured by the accelerometer. 

`time_GravityAcc_mean_X`, `time_GravityAcc_mean_Y`, `time_GravityAcc_mean_Z`, `time_GravityAcc_std_X`, `time_GravityAcc_std_Y`, `time_GravityAcc_std_Z`

### BodyAccJerk
The portion of [jerk](https://en.wikipedia.org/wiki/Jerk_\(physics\)) attributable to the movement of the subject's body, as measured by the accelerometer.

`time_BodyAccJerk_mean_X`, `time_BodyAccJerk_mean_Y`, `time_BodyAccJerk_mean_Z`, `time_BodyAccJerk_std_X`, `time_BodyAccJerk_std_Y`, `time_BodyAccJerk_std_Z`, `freq_BodyAccJerk_mean_X`, `freq_BodyAccJerk_mean_Y`, `freq_BodyAccJerk_mean_Z`, `freq_BodyAccJerk_std_X`, `freq_BodyAccJerk_std_Y`, `freq_BodyAccJerk_std_Z`, `freq_BodyAccJerk_mean_X`, `freq_BodyAccJerk_mean_Y`, `freq_BodyAccJerk_mean_Z`, `freq_BodyAccJerk_meanFreq_X`, `freq_BodyAccJerk_meanFreq_Y`, `freq_BodyAccJerk_meanFreq_Z`

### BodyGyro
The portion of acceleration attributable to the movement of the subject's body, as measured by the gyroscope. 

`time_BodyGyro_mean_X`, `time_BodyGyro_mean_Y`, `time_BodyGyro_mean_Z`, `time_BodyGyro_std_X`, `time_BodyGyro_std_Y`, `time_BodyGyro_std_Z`, `freq_BodyGyro_mean_X`, `freq_BodyGyro_mean_Y`, `freq_BodyGyro_mean_Z`, `freq_BodyGyro_std_X`, `freq_BodyGyro_std_Y`, `freq_BodyGyro_std_Z`, `freq_BodyGyro_mean_X`, `freq_BodyGyro_mean_Y`, `freq_BodyGyro_mean_Z`, `freq_BodyGyro_meanFreq_X`, `freq_BodyGyro_meanFreq_Y`, `freq_BodyGyro_meanFreq_Z

### BodyGyroJerk
The portion of [jerk](https://en.wikipedia.org/wiki/Jerk_\(physics\)) attributable to the movement of the subject's body, as measured by the gyroscope.

`time_BodyGyroJerk_mean_X`, `time_BodyGyroJerk_mean_Y`, `time_BodyGyroJerk_mean_Z`, `time_BodyGyroJerk_std_X`, `time_BodyGyroJerk_std_Y`, `time_BodyGyroJerk_std_Z`

### BodyAccMag
The portion of acceleration magnitude (i.e. the sum of acceleration across all three dimensions) attributable to the movement of the subject's body, as measured by the accelerometer. 

`time_BodyAccMag_mean`, `time_BodyAccMag_std`, `freq_BodyAccMag_mean`, `freq_BodyAccMag_std`, `freq_BodyAccMag_meanFreq`

### GravityAccMag
The portion of acceleration magnitude (i.e. the sum of acceleration across all three dimensions) attributable to gravity, as measured by the accelerometer. 

`time_GravityAccMag_mean`, `time_GravityAccMag_std`

### BodyAccJerkMag
The portion of [jerk](https://en.wikipedia.org/wiki/Jerk_\(physics\)) magnitude (i.e. the sum of jerk across all three dimensions) attributable to the movement of the subject's body, as measured by the accelerometer. 

`time_BodyAccJerkMag_mean`, `time_BodyAccJerkMag_std`, `freq_BodyAccJerkMag_mean`, `freq_BodyAccJerkMag_std`, `freq_BodyAccJerkMag_meanFreq`

### BodyGyroMag
The portion of [jerk](https://en.wikipedia.org/wiki/Jerk_\(physics\)) magnitude (i.e. the sum of jerk across all three dimensions) attributable to the movement of the subject's body, as measured by the gyroscope. 

`time_BodyGyroMag_mean`, `time_BodyGyroMag_std`, `freq_BodyGyroMag_mean`, `freq_BodyGyroMag_std`, `freq_BodyGyroMag_meanFreq`

### BodyGyroJerkMag
The portion of acceleration magnitude (i.e. the sum of acceleration across all three dimensions) attributable to the movement of the subject's body, as measured by the gyroscope.

`time_BodyGyroJerkMag_mean`, `time_BodyGyroJerkMag_std`, `freq_BodyGyroJerkMag_mean`, `freq_BodyGyroJerkMag_std`, `freq_BodyGyroJerkMag_meanFreq`



























