# SENSORS 
## 1. INFRARED TRANSMITTER
**Introduction**

This tutorial will guide on using KY-005 infrared transmitter(IR) module using Arduino(Basics only). This sensor is generally used to transmit IR signals to other devices such as TVs and AV equipment.

![image](/IRtrans.PNG)

The KY-005 infrared transmitter module is designed to transmit coded infrared signals at a frequency of 38kHz and a wavelength of 940nm. This is outside the spectrum detectable by humans.

**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * KY-005 infrared transmitter
- Jumper wires(Female to Male)

**Experimental Procedures**

**Step 1:** Connect circuit equipments according to the following schematic shown:

![image](/IRschem.PNG)

**Step 2:** Download [IRremote](https://www.arduinolibraries.info/libraries/i-rremote) header file using given links.

Extract the download .rar file into *C:\Program Files (x86)\Arduino\libraries* such that a new folder for files is created.

**Step 3:** Copy the following code into your console.

```
#include <IRremote.h>
#include <IRremoteInt.h>
   
IRsend irsend;
   
void setup()
{
}
   
// main program loop
void loop() {
  irsend.sendRC5(0xA90, 12); 
  delay(1000); 
}
```

We recommend you to learn more about these header files, so that you can understand the code and later fiddle with sensor and code to send your own encoded data.

[IRremote header file and its function](https://github.com/z3t0/Arduino-IRremote)

The header file you just downloaded has a number of example codes that you can access using **File->Examples->IRremote**. 

![image](/IRexample.png)

*Try IRrecord and you may see the difference. You shall need IR receiver to recieve its signal.*

**Step 4:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 5:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/phupload.JPG)

**Step 6:** Your IR remote is sending signal.
