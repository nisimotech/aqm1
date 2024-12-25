# Air Quality Monitor One

This is the ESPhome configuration for the Nisimo Tech Air Quality Monitor One device.

Internally, the device is an ESP8266 microcontroller with 4GB of flash memory, a BME680 sensor module and an SSD1306 OLED display module. The display and the sensor are both connected to the ESP8266 using the I2C bus.

## Sensor Values

| Entity                | Description                              |
| :-------------------- | :--------------------------------------- |
| IAQ Accuracy          | Current IAQ accuracy classification      |
| Numeric IAQ Accuracy  | Numeric IAQ accuracy                     |
| IAQ Classification    | Indoor Air Quality Interpretation        |
| IAQ                   | Numeric Indoor Air Quality Value         |
| Breath VOC Equivalent | |
| Gas Resistance        | Raw resistance from the VOC gas detector |
| Humidity              | Humidity percentage                      |
| Temperature           | Current air temperature in Celcius       |
| Temperature °F        | Current air temperature in Fahrenheit    |
| Pressure              | Air pressure in hPA                      |

## Configuration Options

| Entity                | Description                              |
| :-------------------- | :--------------------------------------- |
| Display Mode          | Summary screen or rotating screens       |
| Temperature Unit      | Temperature unit for on-screen display   |

## Indoor Air Quality

### IAQ Interpretation

| IAQ Range | Classification | Meaning |
| :-------: | :------------: | :------ |
| 0 - 50    | GREAT          | Excellent; pure air |
| 51 - 100  | GOOD           | Good air quality; no irritation |
| 101 - 150 | LIGHT          | Lightly polluted air |
| 151 - 200 | MODERATE       | Moderately polluted air; irritation possible |
| 201 - 250 | HEAVY          | Heavily polluted air; limit exposure |
| 251 - 350 | SEVERE         | Severely polluted air; health issues possible |
| > 351     | EXTREME        | Extremely polluted air; health issues likely |

### IAQ Accuracy

| Numeric | Classification | Description |
| :-----: | :------------: | :---------- |
| 0       | Stabilizing    | After initial power on sensor needs to stabilize |
| 1       | Uncertain      | Result uncertain (see below) |
| 2       | Calibrating    | Running calibration on the sensor |
| 3       | Calibrated     | Calibrated; results accurate |

Note: If the accuracy shows `Uncertain` and remains stuck in that state it may be necessary to expose the sensor to some poor quality air (eg hold it near an open bottle of isopropyl alcohol, or similar VOC) to kick it into calibration.

## GPIO Assignments

| GPIO Pin | Assignment |
| :------: | :--------- |
| 12       | I2C Data   |
| 14       | I2C Clock  |


