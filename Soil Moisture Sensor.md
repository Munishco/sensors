#SENSORS
##1. SOIL MOISTURE SENSOR

**Introduction**

The soil moisture sensor or the hygrometer is usually used to detect the humidity of
the soil. So, it is perfect to build an automatic watering system or to monitor the soil
moisture of your plants.
The sensor is set up by two pieces: the electronic board (at the right), and the probe
with two pads, that detects the water content (at the left).

![image](/soilmoisture.PNG)

The sensor has a built-in potentiometer for sensitivity adjustment of the digital
output (D0), a power LED and a digital output LED, as you can see in the following
figure.

![image](/soilsens.PNG)

**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * Soil Moisture Sensor
- 2 * LEDs
- 2 * 220Ω Resistor
- DuPont wires(Female to Male)

**Output from the Sensor**

The voltage that the sensor outputs changes accordingly to the water content in the
soil. When the soil is:

~ Wet: the output voltage decreases
~ Dry: the output voltage increases

The output can be a digital signal (D0) LOW or HIGH, depending on the water
content. If the soil humidity exceeds a certain predefined threshold value, the
modules outputs LOW, otherwise it outputs HIGH. The threshold value for the
digital signal can be adjusted using the potentiometer. The output can also be an
analog signal and so you’ll get a value between 0 and 1023.

**Experimental Procedures**

**Step 1:** Connect the circuit using following schematic diagram.

![image](/smschem.PNG)

**Step 2:** Write following code on your console. The code is more of self-explanatory.
```
int rainPin = A0;
int greenLED = 6;
int redLED = 7;
// you can adjust the threshold value
int thresholdValue = 800;
void setup(){
  pinMode(rainPin, INPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(redLED, OUTPUT);
  digitalWrite(greenLED, LOW);
  digitalWrite(redLED, LOW);
  Serial.begin(9600);
}
void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(rainPin);
  Serial.print(sensorValue);
  if(sensorValue < thresholdValue){
    Serial.println(" - Doesn't need watering");
    digitalWrite(redLED, LOW);
    digitalWrite(greenLED, HIGH);
  }
  else {
    Serial.println(" - Time to water your plant");
    digitalWrite(redLED, HIGH);
    digitalWrite(greenLED, LOW);
  }
  delay(500);
}
```
**Step 3:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 4:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/phupload.png)

**Step 5:** Open **Tools->SerialMonitor** to see the output for your sensor.
