# Getting and Cleaning Data course project

This code book is attributable to the `tidy_data.txt` file of this repository, which is a text file, containing space-separated values.

The first row contains the names of the variables.
The following rows contain the values of the variables. 

## Variables <a name="variables"></a>

Each row contains 81 variables:
- subject ID
- activity ID
- 79 averaged signal measurements.

### IDs <a name="ids"></a>

- `subject`

	Subject ID, integer (from 1 to 30).

- `activity`

	Activity ID, string: 
	- `WALKING`: subject walking
	- `WALKING_UPSTAIRS`: subject walking upstairs
	- `WALKING_DOWNSTAIRS`: subject walking downstairs
	- `SITTING`: subject sitting
	- `STANDING`: subject standing
	- `LAYING`: subject laying

### Averages of measurements <a name="averages-of-measurements"></a>

Measurements are floating-point values, normalised, constrained within [-1,1].

- Average time-domain body acceleration in the X, Y and Z directions
- Standard deviation of the time-domain body acceleration in the X, Y and Z directions
- Average time-domain gravity acceleration in the X, Y and Z directions
- Standard deviation of the time-domain gravity acceleration in the X, Y and Z directions
- Average time-domain body acceleration jerk in the X, Y and Z directions
- Standard deviation of the time-domain body acceleration jerk in the X, Y and Z directions
- Average time-domain body angular velocity in the X, Y and Z directions
- Standard deviation of the time-domain body angular velocity in the X, Y and Z directions
- Average time-domain body angular velocity jerk in the X, Y and Z directions
- Standard deviation of the time-domain body angular velocity jerk in the X, Y and Z directions
- Average and standard deviation of the time-domain magnitude of body acceleration
- Average and standard deviation of the time-domain magnitude of gravity acceleration
- Average and standard deviation of the time-domain magnitude of body acceleration jerk
- Average and standard deviation of the time-domain magnitude of body angular velocity
- Average and standard deviation of the time-domain magnitude of body angular velocity jerk
- Average frequency-domain body acceleration in the X, Y and Z directions
- Standard deviation of the frequency-domain body acceleration in the X, Y and Z directions
- Weighted average of the frequency components of the frequency-domain body acceleration in the X, Y and Z directions
- Average frequency-domain body acceleration jerk in the X, Y and Z directions
- Standard deviation of the frequency-domain body acceleration jerk in the X, Y and Z directions
- Weighted average of the frequency components of the frequency-domain body acceleration jerk in the X, Y and Z directions
- Average frequency-domain body angular velocity in the X, Y and Z directions
- Standard deviation of the frequency-domain body angular velocity in the X, Y and Z directions
- Weighted average of the frequency components of the frequency-domain body angular velocity in the X, Y and Z directions
- Average, standard deviation, and weighted average of the frequency components of the frequency-domain magnitude of body acceleration
- Average, standard deviation, and weighted average of the frequency components of the frequency-domain magnitude of body acceleration jerk
- Average, standard deviation, and weighted average of the frequency components of the frequency-domain magnitude of body angular velocity
- Average, standard deviation, and weighted average of the frequency components of the frequency-domain magnitude of body angular velocity jerk


## Performed transformations <a name="performed-transformations"></a>

The following transformations were performed to the source data:

1. The training and test sets were merged to create one data set (using 'data.table', 'rbind', 'cbind').
2. The measurements of the mean and standard deviation were extracted for each measurement, omiting the others (using 'grepl').
3. The activity IDs were replaced with descriptive activity names (using 'factor').
4. The variable names were replaced with descriptive variable names (using 'gsub').
5. From the data set in step 4, the final data set was created with the average of each variable for each activity and each subject (using 'group_by', 'summarise_each').

Sourcing the data and the transformations were applyed by the `run_analysis.R` R script.