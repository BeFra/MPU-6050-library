# MPU-6050-library

This library provides methods for the communication with an MPU-6050 Six-Axis (Gyro + Accelerometer) 
MEMS MotionTracking Sensor.

With the *#define ACCELEROMETER_RANGE* and *#define GYROSCOPE_RANGE* the range of the Gyro and Accelerometer measurement could be defined.
    
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


The methods _"void get_acc_raw(int16_t* data)"_ and *"void get_gyro_raw(int16_t* data"* write the raw data of the Accelerometer or Gyro to the 3 * 16 Bit array data. For each axis there are two registers which were only 8 Bit wide so each entry in the array must be 16 Bit wide.
The methods *"void get_acc(float* data)"* and *"void get_gyro(float* data)"* write the convertet data of the Accelerometer or Gyro to the 3 * 16 Bit array data.

*"int16_t get_temperature_raw()"* return the raw value of the temperature sensor. The method *"float get_temperature()"* return the converted temperauture value.
