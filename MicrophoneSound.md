# SENSORS
## 1. MICROPHONE SOUND SENSOR
**Introduction**

In this guide we will learn how to use the microphone sound sensor with the Arduino. The microphone sound sensor, as the name says, detects sound. It gives a measurement of how loud a sound is. There is a wide variety of these sensors. The figure below you can see the most
common ones used with the Arduino.

![image](/microphone.PNG)

At the left you can see the KY-038 and at the right the LM393 microphone sound
sensors. Both sensor modules have a built-in potentiometer to adjust the sensitivity
of the digital output pins.

**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * LM393 microphone sound sensor
- 1 * DuPont wires (Male to Female) / Jumper Wires
- 1 * 220Ω Resistor
-1 * LED

**Experimental Procedures**

**Step 1:**  Connect circuit as shown in the following photo:

![image](/microschem.PNG)

For connection, +5V goes to Vcc, GND to GND, OUT to any digital pin on Arduino.

**Step 2:** CODE on your console. Copy and Paste following code on your console while making sure you understand it as well.

```

int ledPin=13; // Arduino has a built-in LED connected to pin 13
int sensorPin=7; // For this tutorial, OUT pin is connected to pin 7
boolean val =0;  // can also use integer data type and use conditions to set up a threshold for LED.
                 // Can also use int val to vary intensity of LED according to intensity of sound received (try this).
void setup(){
pinMode(ledPin, OUTPUT);
pinMode(sensorPin, INPUT);
Serial.begin (9600);
}

void loop(){
val =digitalRead(sensorPin); // Also writing on Serial Monitor to verify
Serial.println (val); // when the sensor detects a signal above the threshold value, LED flashes
if (val==HIGH) {
digitalWrite(ledPin, HIGH);
}
else {
digitalWrite(ledPin, LOW);
}
}

```

**Step 3:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 4:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**. LED must now start blinking according to sound received by sensor.

![image](/microdemon.PNG)

**Step 5:** Open the **Tools->Serial Monitor** to see value of val variable.


