# Gesture Controlled Car With Accelerometer
This project is to be able to control a robot by making gestures with our hands. The main part of this project is to be able to make a robot and have that robot sense what he have on our hand and the robot is able to move around based on hand movements.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Arnesh K | Irvington High School | Software Engineering | Incoming Senior



![Headstone Image](https://user-images.githubusercontent.com/82551067/176963922-bd0d1fae-6cec-4a3d-b53b-b8d81b48ec56.jpg)


# Demo Night

Here is the Demo Night for my project, which is the Gesture Controlled Car with Accelerometer!

<iframe width="560" height="315" src="https://www.youtube.com/embed/kvBYvs6ONag" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Robot DC Motors and Gestures with Accelerometer

My final milestone was setting up the DC motors and determining the gestures for the robot. I soldered the male to male jumper wires to the DC motors and attached the other end of the male to male jumper wires to the OUT of the H bridge for the DC motors. I connected digital pins 6, 7, 8, and 9 to IN1, IN2, IN3, and IN4 of the H bridge respectively. I also had to connect the red wire of the battery switch to +12V of the H bridge, ground pin of the Arduino UNO and black wire of the battery switch to the ground of the H bridge, and 5V of the Arduino UNO to the +5V of the H bridge. The main problem I faced was that the metal part of the black wire of the battery switch was small so I had to strip the wire then solder the metal part and then it was easier to fasten to the ground of the H bridge. In my Arduino IDE, I made a test program to see if the DC motors were working and after seeing that the DC motors worked, I had to figure out the gestures depending on the position of the accelerometer. Using the set of xyz coordinates given from the position of the accelerometer in the Arduino IDE, I was able to determine the gestures according to how I held my accelerometer, through which I then wrote to the Arduino MICRO. The next and final step was transmitting the data from the bluetooth module (which is connected to the Arduino MICRO and the accelerometer) to the other bluetooth module (which is connected to the Arduino UNO, the H bridge, and the robot). Depending on the position of the accelerometer, I had to read the bluetooth data accordingly. After reading the data, I was finally able to get the wheels spinning in the direction I wanted to based on the position of the accelerometer.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dNV2loiNRy4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Bluetooth Module Pairing

My first milestone was pairing two bluetooth modules together and being able to allow one bluetooth module to gather and receive data from the other bluetooth module through serial communication. I connected my Arduino UNO to the breadboard using jumper wires to connect to the bluetooth module and used resistors to divide current, where I connected RXD and TXD to digital pins 2 and 3 respectively. I also had my Arduino MICRO on the breadboard and used the same connections I made with the Arduino UNO, except I directly connected to TX and RX pins, instead of digital pins 2 and 3. The main problem I came across with was that I was able to make my AT commands work with the Arduino UNO but the AT commands would not work with my Arduino Micro. I had to talk with my instructor and we were able to solve the problem by receiving a new pair of bluetooth modules that were able to work through AT commands with both the Arduino UNO and Arduino MICRO. After connecting both the bluetooth modules, I was able to run the Serial Monitor on one COM port and allow one bluetooth module to gather and receive data from the Serial Monitor on the other COM port.

<iframe width="560" height="315" src="https://www.youtube.com/embed/7DE207wJoCg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Bill of Materials

|:--:|:--:|:--:|:--:|:--:|:--:|
| **Part** | **Quantity** | **Description** | **Reference Designator** | **Cost** | **Website** |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Robot Kit | 1 | Chassis, Battery Pack, DC Motors, Wheels, etc. | M1, M2 | 18.99 | [amazon](https://www.amazon.com/perseids-Chassis-Encoder-Wheels-Battery/dp/B07DNYQ3PX)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Bluetooth Module | 2 | Serial Communication | HC-05 | 19.98 | [amazon](https://www.amazon.com/HiLetgo-Wireless-Bluetooth-Transceiver-Arduino/dp/B071YJG8DR)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Accelerometer | 1 | Measure Linear Acceleration Along Axis | ADXL345 | 13.59 | [amazon](https://www.amazon.com/Wishiot-ADXL345-Accelerometer-Inclination-Raspberry/dp/B09T6VJWNY/ref=sr_1_2_sspa?keywords=adxl345&qid=1656710211&sr=8-2-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFZUVlSVVZaVU1VOVgmZW5jcnlwdGVkSWQ9QTA0NjkxNTRLRzJVTjNOU1VHVzcmZW5jcnlwdGVkQWRJZD1BMDEwNTE1NzFPVFAxQzVINjdWMEgmd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Arduino Uno | 1 | Microcontroller Board | R3 | 23.00 | [arduino](https://store.arduino.cc/products/arduino-uno-rev3)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Arduino Micro | 1 | Microcontroller Board | R3 | 20.70 | [arduino](https://store.arduino.cc/products/arduino-micro)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Jumper Wires | 1 | Connection Wires | N/A | 6.98 | [amazon](https://www.amazon.com/Elegoo-EL-CP-004-Multicolored-Breadboard-arduino/dp/B01EV70C78)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Dual H Bridge | 1 | Control Direction of DC Motors | L298N | 6.99 | [amazon](https://www.amazon.com/Qunqi-Controller-Module-Stepper-Arduino/dp/B014KMHSW6/ref=asc_df_B014KMHSW6/?tag=hyprod-20&linkCode=df0&hvadid=167139094796&hvpos=&hvnetw=g&hvrand=13469222211329594770&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9032008&hvtargid=pla-306436938191&psc=1)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Breadboard | 1 | Build Circuits Without Soldering | N/A | 11.98 | [amazon](https://www.amazon.com/dp/B07DL13RZH/ref=redir_mobile_desktop?_encoding=UTF8&aaxitk=b163d500edcc33b8ecdb35867663512a&content-id=amzn1.sym.53aae2ac-0129-49a5-9c09-6530a9e11786%3Aamzn1.sym.53aae2ac-0129-49a5-9c09-6530a9e11786&hsa_cr_id=4991273630901&pd_rd_plhdr=t&pd_rd_r=e6730cd8-8e3e-463d-932b-2c49d394f510&pd_rd_w=jX1If&pd_rd_wg=pAAek&qid=1656710515&ref_=sbx_be_s_sparkle_mcd_asin_0_img&sr=1-1-a094db1c-5033-42c6-82a2-587d01f975e8)
|:--:|:--:|:--:|:--:|:--:|:--:|
| Resistors | 1 | Control Flow of Electrical Current | N/A | 10.99 | [amazon](https://www.amazon.com/BOJACK-Values-Resistor-Resistors-Assortment/dp/B08FD1XVL6/ref=sr_1_2_sspa?crid=27KYFJ2PLSL8G&keywords=resistor&qid=1656710541&s=industrial&sprefix=resist%2Cindustrial%2C143&sr=1-2-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUE1UTlIUDRJRElBSlomZW5jcnlwdGVkSWQ9QTA0ODQ1ODUyVzBGOEhZN1hJSVNPJmVuY3J5cHRlZEFkSWQ9QTAyMjA5NTdGT1c4RjFYSTkxNTUmd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl)

# Tools Required

|:--:|:--:|:--:|
| **Tool** | **Cost** | **Website** |
|:--:|:--:|:--:|
| Soldering Iron | 15.99 | [amazon](https://www.amazon.com/Soldering-Kit-Temperature-Desoldering-Electronics/dp/B07GTGGLXN/ref=asc_df_B07GTGGLXN/?tag=hyprod-20&linkCode=df0&hvadid=241999416883&hvpos=&hvnetw=g&hvrand=137463208067721732&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9031525&hvtargid=pla-590653449503&psc=1)
| Screwdriver Kit | 6.99 | [amazon](https://www.amazon.com/Small-Screwdriver-Set-Mini-Magnetic/dp/B08RYXKJW9)



# Schematics

![Schematics](https://user-images.githubusercontent.com/82551067/176963218-7c0eecbe-7689-48f5-b6ea-48579ae6fb1c.jpg)
