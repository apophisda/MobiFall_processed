you can download the mobiFall processed dataset by clicking [here](https://www.kaggle.com/datasets/arimaehiztaria/mobifall-processed/data)

# MobiFall Dataset Processing - README

## Issues with the Original MobiFall Dataset
The original MobiFall dataset contains sensor data from accelerometer, gyroscope, and orientation sensors. However, a major issue with the dataset is that the accelerometer data is not time-synchronized with the other sensors. This misalignment makes direct usage challenging for sequence-based models such as LSTMs. To address this, we applied linear interpolation to align the accelerometer data with timestamps from the gyroscope and orientation sensors, ensuring consistency across all three modalities.

More details about the original dataset can be found at: [MobiFall Dataset Website](https://bmi.hmu.gr/the-mobifall-and-mobiact-datasets-2/)

## Combined Dataset Structure
Each processed file contains synchronized data from the accelerometer, gyroscope, and orientation sensors, making it suitable for training machine learning models for activity recognition and fall detection.

### File Naming Convention
The combined files follow the naming format:
```
<ADL OR FALL_CODE>_<SUBJECT_ID>_<TRIAL_NO>.csv
```
- **ADL OR FALL_CODE**: Activity or fall event code (e.g., `STD`, `JOG`, `FOL`, `BSC`)
- **SUBJECT_ID**: Identifier for the subject
- **TRIAL_NO**: Trial number of the activity

### Data Format
Each file contains the following columns:
```
timestamp(ns), acc_x, acc_y, acc_z, gyro_x, gyro_y, gyro_z, ori_azimuth, ori_pitch, ori_roll
```
- **timestamp(ns)**: The synchronized timestamp in nanoseconds.
- **acc_x, acc_y, acc_z**: Accelerometer readings along the x, y, and z axes (m/s²).
- **gyro_x, gyro_y, gyro_z**: Gyroscope readings representing angular velocity (rad/s).
- **ori_azimuth, ori_pitch, ori_roll**: Orientation angles (degrees).

## Activities of Daily Living (ADL)
| ID  | Code | Activity     | Trials | Duration | Description                    |
|----|------|-------------|--------|----------|--------------------------------|
| 1  | STD  | Standing    | 1      | 5m       | Standing with subtle movements |
| 2  | WAL  | Walking     | 1      | 5m       | Normal walking                 |
| 3  | JOG  | Jogging     | 3      | 30s      | Jogging                        |
| 4  | JUM  | Jumping     | 3      | 30s      | Continuous jumping             |
| 5  | STU  | Stairs up   | 6      | 10s      | Stairs up (10 stairs)          |
| 6  | STN  | Stairs down | 6      | 10s      | Stairs down (10 stairs)        |
| 7  | SCH  | Sit chair   | 6      | 6s       | Sitting on a chair             |
| 8  | CSI  | Car-step in | 6      | 6s       | Step in a car                  |
| 9  | CSO  | Car-step out| 6      | 6s       | Step out a car                 |

## Falls
| ID  | Code | Activity           | Trials | Duration | Description                                             |
|----|------|--------------------|--------|----------|---------------------------------------------------------|
| 10 | FOL  | Forward-lying      | 3      | 10s      | Fall Forward from standing, use of hands to dampen fall |
| 11 | FKL  | Front-knees-lying  | 3      | 10s      | Fall forward from standing, first impact on knees       |
| 12 | BSC  | Back-sitting-chair | 3      | 10s      | Fall backward while trying to sit on a chair            |
| 13 | SDL  | Sideward-lying     | 3      | 10s      | Fall sidewards from standing, bending legs              |

## Sensors
| Code | Type          | Values                                      | Description                                                  |
|------|--------------|--------------------------------------------|--------------------------------------------------------------|
| acc  | Accelerometer | timestamp(ns), x, y, z (m/s²)            | Acceleration force along the x, y, z axes (including gravity). |
| gyro | Gyroscope     | timestamp(ns), x, y, z (rad/s)           | Rate of rotation around the x, y, z axes (Angular velocity).   |
| ori  | Orientation   | timestamp(ns), Azimuth, Pitch, Roll (°)  | Angle around the z, x, y axes.                                 |

This dataset provides synchronized motion data, making it suitable for machine learning applications such as activity classification and fall detection.

## Acknowledgment
The development of the MobiFall dataset was partially funded by the FP7 project “MyHealthAvatar – A Demonstration of 4D Digital Avatar Infrastructure for Access of Complete Patient Information”.

