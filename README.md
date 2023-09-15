# Bearing sensor data feature extraction and fault detection.
Bearings are vital components of rotating machines that are prone to unexpected faults. The main objective is to detect the faults occuring in the IMS bearings that are installed on a shaft - a rotating machinery fault diagnosis to reduce the operational costs and downtime.
## About Dataset
### Dataset Description
--------------------
`Four bearings` were installed on a shaft. The rotation speed was kept constant at 2000 RPM by an AC motor coupled to the shaft via rub belts. 
A radial load of 6000 lbs is applied onto the shaft and bearing by a spring mechanism. All bearings are force lubricated.
Rexnord ZA-2115 double row bearings were installed on the shaft. PCB 353B33 High Sensitivity Quartz ICP accelerometers were installed
on the bearing housing (two accelerometers for each bearing [x- and y-axes] for data set 1, one accelerometer for each bearing for data sets 2 and 3).
### Dataset Structure
----------------------
Three (3) data sets are included in the data packet. Each data set describes a test-to-failure experiment. 
Each data set consists of individual files that are `1-second vibration signal` snapshots recorded at specific intervals.
Each file consists of `20,480 points` with the sampling rate set at 20 kHz. The file name indicates when the data was collected. 
Each record (row) in the data file is a data point.
## Set 1
- *Recording Duration*: October 22, 2003 12:06:24 to November 25, 2003 23:39:56
- *No. of Files*: `2,156`
- *No. of Channels*: 8
- *Channel Arrangement*: Bearing 1 – Ch 1&2; Bearing 2 – Ch 3&4; Bearing 3 – Ch 5&6; Bearing 4 – Ch 7&8.
- *File Recording Interval*: Every 10 minutes (except the first 43 files were taken every 5 minutes)
- *File Format*: ASCII
- Description: At the end of the test-to-failure experiment, `inner race defect` occurred in `bearing 3` and` roller element defect` in `bearing 4`.
## Set 2
- _Recording Duration_: February 12, 2004 10:32:39 to February 19, 2004 06:22:39
- _No. of Files_: `984`
- _No. of Channels_: 4
- _Channel Arrangement_: Bearing 1 – Ch 1; Bearing2 – Ch 2; Bearing3 – Ch3; Bearing 4 – Ch 4.
- _File Recording Interval_: Every 10 minutes
- _File Format_: ASCII
- Description: At the end of the test-to-failure experiment, `outer race failure` occurred in `bearing 3.`
## Set 3
- _Recording Duration_: March 4, 2004 09:27:46 to April 4, 2004 19:01:57
- _No. of Files_: `4,448`
- _No. of Channels_: 4
- _Channel Arrangement_: Bearing1 – Ch 1; Bearing2 – Ch 2; Bearing3 – Ch3; Bearing4 – Ch4;
- _File Recording Interval_: Every 10 minutes
- _File Format_: ASCII
- Description: At the end of the test-to-failure experiment, `outer race failure` occurred in `bearing 3.`
### Raw data
-----------------------
1. The file name indicates when the data was collected. 
2. Each row in the data is a data point. 
3. Each file consist of 20,480 points. Sample data points are shown below,

| -0.049 |-0.071 | -0.132 | -0.010 |
| ------------- |:-------------:| -----:| -----:|
| -0.042 | -0.073 | -0.007 | -0.105 |
| -0.051 | 0.020 | -0.002 | 0.100 |

### Feature Engineering
----------------------------------
The following nine features are engineered for each datasetin the data packet,

1. Minimum
2. Maximum
3. Mean
4. Standard Deviation
5. RMS
6. Skewness
7. Kurtosis
8. Crest Factor
9. Form Factor

These features are engineered for each bearing of the three data set and stored seperately as csv files as follows,
- Time_feature_matrix_bearing_1_Test_ 1.csv
- Time_feature_matrix_bearing_1_Test_ 2.csv
- Time_feature_matrix_bearing_1_Test_ 3.csv
- Time_feature_matrix_bearing_2_Test_ 1.csv
- Time_feature_matrix_bearing_2_Test_ 2.csv
- Time_feature_matrix_bearing_2_Test_ 3.csv
- Time_feature_matrix_bearing_3_Test_ 1.csv
- Time_feature_matrix_bearing_3_Test_ 2.csv
- Time_feature_matrix_bearing_3_Test_ 3.csv
- Time_feature_matrix_bearing_4_Test_ 1.csv
- Time_feature_matrix_bearing_4_Test_ 2.csv
- Time_feature_matrix_bearing_4_Test_ 3.csv
### Data Preprocessing
-----------------------------
Initially the date time were in the format 2003.10.22.12.06.13. Using pandas the date and time are formatted as 2003-10-22 12:06:13('%Y.%m.%d.%H.%M' format). The data in set 1 have 8 columns 2 channels for each bearing. Features are engineered for each channels and they are combined to form four columns each column coressponds to each bearing. So, we have 4 colums of data in every dataset. After preprocessing the data is as follows,
|	  | Max |	Min |	Mean |	Std	| RMS |	Skewness |	Kurtosis |	Crestfactor |	Formfactor |
|:----------|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
| 2003-10-22 12:06:13 | 0.5445	|-0.6419999999999999	|-0.09423961130914595|	0.07588751560955571|	0.12105623624716813|	0.0951497966020166|	2.067108229313727|	4.539860602168228|	-1.2844332552893867|
	

### Visualization
-----------------
All the preprocessed data stored in seperate csv files are read and visualized using matplotlib.










