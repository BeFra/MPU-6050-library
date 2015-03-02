# MPU-6050-library

This library provides methods for the communication with an MPU-6050 Six-Axis (Gyro + Accelerometer) 
MEMS MotionTracking Sensor.

With the __#define ACCELEROMETER_RANGE__ and __#define GYROSCOPE_RANGE__ the range of the gyro and accelerometer measurement could be defined.
    
For #define ACCELEROMETER_RANGE:

|define|Full Scale Range|LSB Sensitivity|
|---|---|---|
|ACCELEROMETER_RANGE_2G|-/+2g|16384 LSB/g|
|ACCELEROMETER_RANGE_4G|-/+4g|8192 LSB/g|
|ACCELEROMETER_RANGE_8G|-/+8g|4096 LSB/g|
|ACCELEROMETER_RANGE_16G|-/+16g|2048 LSB/g|



For #define GYROSCOPE_RANGE:

|define|Full Scale Range|LSB Sensitivity|
|---|---|---|
|GYROSCOPE_RANGE_250|-/+250°/s|131 LSB/°/s|
|GYROSCOPE_RANGE_500|-/+500°/s|65.5 LSB/°/s|
|GYROSCOPE_RANGE_1000|-/+1000°/s|32.8 LSB/°/s|
|GYROSCOPE_RANGE_2000|-/+2000°/s|16.4 LSB/°/s|


The methods __"void get_acc_raw(int16_t* data)"__ and __"void get_gyro_raw(int16_t* data")__ write the raw data of the accelerometer or gyro to the 3 * 16 Bit array data. For each axis there are two registers which were only 8 Bit wide so each entry in the array must be 16 Bit wide.
The methods __"void get_acc(float* data)"__ and __"void get_gyro(float* data)"__ write the convertet data of the Accelerometer or Gyro to the 3 * 16 Bit array data.

__"int16_t get_temperature_raw()"__ return the raw value of the temperature sensor. The method __"float get_temperature()"__ return the converted temperauture value.

To calibrate the Sensor there are two methods for Gyro and Accelerometer __void calibrate_gyroscope()__ and __void calibrate_accelerometer()__  they read x times the raw values and build the average of the values.

The method __get_angles()__ returns the angles of all three Axis x, y, z The gyro and accelerometer values are fused with the complementary filter.

To calcuclate the angles roll, pitch and yaw with the accelerometer data simple trigonometry were used.
roll:  alpha = arctan( Ax / sqrt( (Ay)^2 + (Az)^2)),
pitch: beta = arctan( Ay / sqrt( (Ax)^2 + (Az)^2)) and finally
yaw:   theta = arctan( sqrt( (Ax)^2 + (Ay)^2) / Az ).

To calculate the angles roll, pitch and yaw with the gyro data we need the time between two requests of the gyro data, because the gyro sensor measures the rotational motion
roll = Ax * dt * last_gyro_x_angle,
ptich = Ay * dt * last_gyro_y_angle,
yaw = Az * dt * last_gyro_z_angle

with dt = t_now - last_request_time.


Links:

[MPU-6000 and MPU-6050 Register Map and Descriptions Revision 4.0] (http://www.invensense.com/mems/gyro/documents/RM-MPU-6000A.pdf)

[MPU-6000 and MPU-6050 Product Specification Revision 3.4]
(http://www.invensense.com/mems/gyro/documents/PS-MPU-6000A-00v3.4.pdf)
