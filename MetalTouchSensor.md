# INTRODCUTION
## 1.METAL TOUCH SENSOR
**Introduction**

In this tutorial we will learn how to use metal touch sensor using Arduino. This sensor outputs a signal if the metal pike of the Sensor was touched. You can adjust the sensitivity of the sensor with the controller(using potenitiometer located on the sensor).

**Digital Out:** At the moment of contact detection, a signal will be outputted. 

**Analog Out:** Direct measuring value of the sensor unit.

![image](/metalsens.PNG)

The sensor has 3 main components on its circuit board. First, the sensor unit at the front of the module which measures the area physically and sends an analog signal to the second unit, the amplifier. The amplifier amplifies the signal, according to the resistant value of the potentiometer, and sends the signal to the analog output of the module.
The third component is a comparator which switches the digital out and the LED if the signal falls under a specific value.
You can control the sensitivity by adjusting the potentiometer.


**Please notice:** The signal will be inverted; that means that if you measure a high value, it is shown as a low voltage value at the analog output.

**Components**

1 * Arduino Uno board
1 * USB cable
1 * metal-touch sensorJumper wires(Female to Male)

**Experimental Procedures**

**Step 1:** Connect the circuit according to image shown below.

![image](/metaltouch.PNG)

~ DIGITAL SIGNAL TO PIN3.
~ +5V TO Vcc.
~ GND TO GND.
~ ANALOG SIGNAL TO PIN0.

**Step 2:** Write following code into your console. The Code is SELF-EXPLANATORY.
```
// Declaration and initialization of the input pin
int Analog_Eingang = A0; // X-axis-signal
int Digital_Eingang = 3; // Button
  
void setup ()
{
  pinMode (Analog_Eingang, INPUT);
  pinMode (Digital_Eingang, INPUT);
       
  Serial.begin (9600); // Serial output with 9600 bps
}
  
// The program reads the current value of the input pins
// and outputs it via serial out 
void loop ()
{
  float Analog;
  int Digital;
    
  // Current value will be read and converted to the voltage
  Analog = analogRead (Analog_Eingang) * (5.0 / 1023.0); 
  Digital = digitalRead (Digital_Eingang);
    
  // and outputted here
  Serial.print ("Analog voltage value:"); Serial.print (Analog, 4);  Serial.print ("V, ");
  Serial.print ("Extreme value:");
  
  if(Digital==1)
  {
      Serial.println (" reached");
  }
  else
  {
      Serial.println (" not reached yet");
  }
  Serial.println ("----------------------------------------------------------------");
  delay (200);
}
```
 
**Step 3:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 4:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/phupload.png)

**Step 5:** Open **Tools->SerialMonitor** to view your results.
