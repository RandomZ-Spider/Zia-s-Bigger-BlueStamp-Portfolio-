# A.I. Powered Claw Car
<!--Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!-->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Zia S. | Archbishop Mitty Highschool | Computer Engineering | Incoming Sophmore |

<figure>
  <img src="Zia.jpg"  width="50%" height="50%">
  <figcaption>Picture of Me (2024)</figcaption>
</figure>
  
<!--# Final Milestone (A.I. Powered Claw Car)

<iframe width="901" height="507" src="https://www.youtube.com/embed/uxMxAbv3sPU" title="Zia S. Milestone 3" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="901" height="507" src="https://www.youtube.com/embed/zHDSXegHkWQ" title="Hexapod Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<img src="Zia-Project.png" width = "600" height = "800">

<img src="Picture-Hexapod-V3.jpg" width = "600" height = "553.7513">


<!--For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE-->

<!--<h1>Summary</h1>
<h2>Project</h2>
My project is an A.I. Powered Claw Car, a robot that travels using 2 wheels controlled by servos and has a claw attached on top. Using a raspberry camera module and an object identification A.I. program, it is capable of identifying various objects based a training data set and pick them up with the claw. <br>

<h2>Components</h2>
<ul>
  <li>Ultrasonic Sensors</li>
  <li>0.96'' OLED Display</li>
  <li>Jumper Cables</li>
  <li>Small Breadboard</li>
</ul>

<h2>How Components Work Together</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The ultrasonic sensors measure distance by sending out a 40,000 hertz sound wave and receives the pulse coming from the echo of the wave. The microcontroller (the controller board) uses a program to calculate the distance by taking the time it took for the sound wave to come back using the equation distance is equal to time divided by 2 (taking into account the wave going back and forth) times the speed of sound (340 m/s). The OLED display uses 8192 bits which turn on or off, and using the Adafruit library, the OLED can be programmed to display text and images by turning off and on certain bits. The system uses the first ultrasonic sensor to get the distance in cm, and then the OLED takes the distance as an integer value and constantly displays the current distance. The Hexapod also uses the distance value to determine when to dance. The first ultrasonic sensor and OLED display are both attached to a cardboard piece each to make it easier to mount to the Hexapod, and the pins poke through to allow connection to the controller board from behind. The other two ultrasonic sensors are attached to mounts which I modeled and 3D printed on both sides of the Hexapod. 

<h2>What I Accomplished</h2> <!-- What I did in previous milestones and what I did for third milestone. -->
<!--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; In the previous milestones, I assembled and calibrated the Hexapod, programmed a dance, and built a battery stand. For the third milestone, I added three ultrasonic sensors and an OLED display to the Hexapod. I also programmed the Hexapod to display the measured distance on the OLED. I also programmed it to walk around randomly and dance whenever the ultrasonic sensor detects a distance of 5 cm or less. Using the other two sensors, the Hexapod is also able to traverse through hallways, meaning that whenever it reaches a wall, the Hexapod will dance, check for a gap on each side, and turn towards the gap if found; otherwise, the Hexapod would turn 180 degrees and continue walking. Currently, the dance for the Hexapod is just a boogie, but originally it was longer and more varied. I had to change it because it would not be able to go through hallways due to the change in position.  

<h2>Challenges & Triumps</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Some challenges that I had during the project were assembling the Hexapod, building the battery stand, and wire management. I had a lot of trouble attaching the legs to the Hexapod's servo stands; the legs each needed the correct orientation to function properly. It was very tough to fix them on the servo stands correctly; some servos did not fit in the correct direction, and I had to force them into position. It took three days, but I fully assembled the Hexapod and completed the final calibration step to fix any deviations in the legs. The most frustrating part of building the battery holder was measuring the holes correctly. It took me three tries to drill the holes to match the Hexapod's standoffs and fit smoothly. Wire management was time-confusing as the breadboard, which held the ground and power wires, was attached to a cardboard platform at the bottom of the Hexapod. I had to set up the wires from the breadboard so that they were facing the right way for easier connection, but some were too long. As a result, I had to bunch up the wires inside the Hexapod so that the legs did not pull them out which was very frustrating. The same was true for the Trig and Echo pin wires (ultrasonic sensor) and the SDA and SCL pin wires (OLED display). Mounting each device to the Hexapod was challenging as the wires resisted change. It was harder for the two side mounts as I had to cut off the sides of the battery holder to fit the jumper cables for each side ultrasonic sensor; even then, it was still a challenge to screw each mount on. However, I triumphed over these challenges and produced a Hexapod that can measure distance and display it on an OLED display and dance. 

<h2>What I Learned</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I learned many essential topics during the project, such as the basics of Arduino and using breadboards, coding with the Arduino IDE to control different devices such as an ultrasonic sensor, LEDs, and piezo buzzers, how servo motors work, checking for circuit shorts, and using a drill and saw.

<h2>Next Step</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; After learning everything I have learned at BlueStamp Engineering, I really hope to learn more advanced concepts in robotics and electrical engineering. <br><br> 

<h2>Hexapod_Ultrasonic2_OLED.ino</h2>

```c++
#include <FNHR.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128 // OLED display width, in pixels
#define SCREEN_HEIGHT 64 // OLED display height, in pixels

// Declaration for an SSD1306 display connected to I2C (SDA, SCL pins)
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

FNHR robot;

// Sensor 1
const int trigPin1 = 2;
const int echoPin1 = 3;

// Sensor 2
// Have to put in A0 and A1 manually

// Sensor 3
const int trigPin3 = 14;
const int echoPin3 = 15;

long duration;
int distanceCm1;
int distanceCm2;
int distanceCm3;
int danceCm = 8;
bool Walk = true;

void setup() 
{
  // Sensor 1
  pinMode(trigPin1, OUTPUT);
  pinMode(echoPin1, INPUT);

  // Sensor 2
  pinMode(A1, OUTPUT);
  pinMode(A0, INPUT);

  // Sensor 3
  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);

  // OLED setup
  Serial.begin(115200);

  if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { // Address 0x3D for 128x64
    Serial.println(F("SSD1306 allocation failed"));
    for(;;);
  }
  delay(2000);
  robot.Start();
  int distanceCm1 = 100;
}
void loop()
{
  // Ultrasonic sensor 1 measuring
  digitalWrite(trigPin1, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin1, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin1, LOW);
  duration = pulseIn(echoPin1, HIGH);
  distanceCm1 = duration * 0.034 / 2;
  Serial.println(distanceCm1);

  // Ultrasonic sensor 2 measuring
  digitalWrite(A1, LOW);
  delayMicroseconds(2);
  digitalWrite(A1, HIGH);
  delayMicroseconds(10);
  digitalWrite(A1, LOW);
  duration = pulseIn(A0, HIGH);
  distanceCm2 = duration * 0.034 / 2;
  Serial.println(distanceCm2);

  // Ultrasonic sensor 3 measuring
  digitalWrite(trigPin3, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin3, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin3, LOW);
  duration = pulseIn(echoPin3, HIGH);
  distanceCm3 = duration * 0.034 / 2;
  Serial.println(distanceCm3);

  // Robot walking around randomly and checking sides
  if (distanceCm1 > danceCm && Walk == true)
  {
    robot.CrawlForward();
  }
  else
  {
    Walk = false;
    MiniDance();
    robot.ChangeBodyHeight(50);
    delay(100);
    
    if (distanceCm2 > danceCm)
    {
      for (int i = 0; i < 16; i++)
     {
       robot.TurnRight();
     }
     Walk = true;
    }
    else if (distanceCm3 > danceCm)
    {
      for (int i = 0; i < 16; i++)
     {
       robot.TurnLeft();
     }
     Walk = true;
    }
    else
    {
      for (int i = 0; i < 32; i++)
     {
       robot.TurnRight();
     }
     Walk = true;
    }
  }
  
  // Distance is less than 10
  if (distanceCm1 < 10)
  {
    display.clearDisplay();
    display.setTextSize(9);
    display.setTextColor(WHITE);
    display.setCursor(40, 0);
    display.print(distanceCm1);
    display.display(); 
  }

  // Distance more or equal to 10 and less than 100
  if (distanceCm1 >= 10 && distanceCm1 < 100)
  {
    display.clearDisplay();
    display.setTextSize(9);
    display.setTextColor(WHITE);
    display.setCursor(15, 0);
    display.print(distanceCm1);
    display.display(); 
  }

  // Distance more or equal to 100 and less or equal to than 400
  if (distanceCm1 >= 100 && distanceCm1 <= 400)
  {
    display.clearDisplay();
    display.setTextSize(7);
    display.setTextColor(WHITE);
    display.setCursor(1, 10);
    display.print(distanceCm1);
    display.display(); 
  }

  // Distance more than 400
  if (distanceCm1 > 400)
  {
    display.clearDisplay();
    display.setTextSize(4);
    display.setTextColor(WHITE);
    display.setCursor(30, 0);
    display.println("Too");
    display.setCursor(30,30);
    display.println("Far");
    display.display(); 
  }
  
}

void MiniDance()
{
  robot.SetActionSpeed(50);

  delay(500);

  //Max height is 50

  // Dance Move 1
  for (int i = 0; i < 3; i++)
  {
    robot.SetActionSpeed(200);
    robot.ChangeBodyHeight(50);
    robot.ChangeBodyHeight(30);
  }
}

```

<!--**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**-->

# Second Milestone (A.I. Powered Claw Car)

<iframe width="560" height="315" src="https://www.youtube.com/embed/mGiasDcI_J0" title="Zia S. Second Milestone" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<figure>
  <img src="Claw_Picc.jpg" width="534.9527" height="500">
</figure>

<h1>Summary</h1>
<h2>Project</h2>
My project is an A.I. Powered Claw Car, a robot that travels using 2 wheels controlled by servos and has a claw attached on top. Using a raspberry camera module and an object identification A.I. program, it is capable of identifying various objects based a training data set and pick them up with the claw. <br>

<h2>Components</h2>
<ul>
  <li>Acrylic Plates</li>
  <li>Arduino Nano</li>
  <li>Arduino Shield</li>
  <li>Servo Package</li>
  <li>Joysticks</li>
  <li>USB Cable</li>
  <li>Jumper Cables</li>
  <li>Battery Case</li>
  <li>AA Batteries</li>
  <li>Turntable</li>
</ul>

<h2>How Components Work Together</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The acrylic parts of the claw act as the base and main body that house the servos, Arduino Nano, and Arduino shield. The base of the claw has a servo that rotates a ball-bearing wheel, rotatating the entire claw. Two other servos control the arm of the claw, making it capable of moving up or down. The final servo controls the actual claw; it is attached to one claw half with a gear at the end that is in contact with the gear of the other claw half so when the servo rotates, the entire claw grabs or releases. The servos are controlled by two joysticks that are connected to the Arduino Nano; one controls the rotation and position of the claw arm and the other control the claw itself. 

<h2>Progress</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For the second milestone, I had to cut the ground and voltage wires of the battery port of the claw and solder them to a new battery case as lithium batteries are not allowed in Bluestamp projects. Before beginning assembly, I used the Arduino program, Servo_90_ADJ.ino, provided by the pdf claw tutorial to adjust the servos to all be 90°, using a USB to connect the Arduino Nano to my computer. I then assembled the stand for the Arduino Nano and shield using standoffs and did the same for the ball-bearing base of the claw arm. Next, I added the servo for the base of the claw arm and attached a rectangular piece to it that would allow the servo to rotate the entire base. I then screwed together the claw arm with two servos, making sure that they were straight. Finally, I screwed in the servo for the claw and attached the claw half to it and lined up the other half with the first. I then assembled a simple controller using one of the acrylic plates and screwing in two joysticks. I then did the necessary wiring for the claw to properly work and be controllled by the claw. I uploaded the Arduino program, Arm.ino, provided by the tutorial to the Arduino Nano, allowing me to control the claw with the joysticks. 

<h2>Challenges Faced</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;One of the major problems I faced with the claw assembly was screwing in small screws into tiny nuts in tight spaces. It was quite difficult for me and wasted a lot of time. Eventually, I figured out a way to make it easier by always turning the claw over to a side in which the nut would be lying down to facilitate the screwing process. Another problem I faced was accidently attached the rectangular piece the wrong way on the base servo. This was an issue because one, the traction of the servo and the ball-bearing base was weak, leading to little rotation, and two, removing the servo arm from the rectangular piece is difficult. The servo arm is attached to the retangular piece using self-tapping screws which are difficult to remove once they are screwed in. It also did not help that the screwdriver I was using broke away from the handle, making it ineffective. I wasted more time trying to remove the self-tapping screws but managed to get them out using a plier that had a good grip on them. <br>

<h2>Next Step</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;My third milestone will be mounting the claw onto the car and programming them to be controlled by the same controller by making communication between the Arduino Uno of the car and Arduino Nano of the claw possible. I must learn how to make communication between two Arduino board possible and how to make a custom controller for the robot. <br> <br>

<h2>Servo_90_ADJ.ino</h2>

```c++
//
/*
 * This code applies to cokoino mechanical arm
 * Through this link you can download the source code:
 * https://github.com/Cokoino/CKK0006
 * Company web site:
 * http://cokoino.com/

#include<Servo.h>
Servo myservo1;  // Create a servo class
Servo myservo2;  // Create a servo class
Servo myservo3;  // Create a servo class
Servo myservo4;  // Create a servo class

void setup() {  
myservo1.attach(4);  //Set the servo control pin as D4
myservo2.attach(5);  //Set the servo control pin as D5
myservo3.attach(6);  //Set the servo control pin as D6
myservo4.attach(7);  //Set the servo control pin as D7
delay(100);          //delay 100ms 
}
/////////////////////////////////////////////////////////
void loop() {
 myservo1.write(90);  //The servo is 90 degrees
 myservo2.write(90);  //The servo is 90 degrees
 myservo3.write(90);  //The servo is 90 degrees
 myservo4.write(90);  //The servo is 90 degrees
 delay(1000);
 }
```

<h2>Schematic</h2>

<figure>
  <img src="M2_Schematic.jpg" alt="Provided by Cokoino" width="600" height="374">
  <figcaption>Provided by Cokoino.</figcaption>
</figure>

<h2>Arm.ino</h2>

```c++
/*
 * This code applies to cokoino mechanical arm
 * Through this link you can download the source code:
 * https://github.com/Cokoino/CKK0006
 * Company web site:
 * http://cokoino.com/
 *                                     ________
 *                         ----|servo4| 
 *                        |            --------
 *                    |servo3|   
 *                        |
 *                        |
 *                    |servo2|
 *                        |
 *                        |
 *                  ___________
 *                  |  servo1 |
 *         ____________________
 *         ____________________
 * Fanctions:
 * arm.servo1.read();   //read the servo of angle
 * arm.servo2.read();
 * arm.servo3.read();
 * arm.servo4.read();
 * 
 * arm.servo1.write(angle);   //servo run
 * arm.servo2.write(angle);
 * arm.servo3.write(angle);
 * arm.servo4.write(angle);
 * 
 * arm.left(speed);    //perform the action 
 * arm.right(speed);
 * arm.up(speed);
 * arm.down(speed);
 * arm.open(speed);
 * arm.close(speed);
 * 
 * arm.captureAction();    //capture the current action,return pointer array
 * arm.do_action(int *p,int speed);  //P is a pointer to the array
 * 
 * arm.JoyStickL.read_x(); //Returns joystick numerical
 * arm.JoyStickL.read_y();
 * arm.JoyStickR.read_x();
 * arm.JoyStickR.read_y();
 */
#include "src/CokoinoArm.h"
#define buzzerPin 9

CokoinoArm arm;
int xL,yL,xR,yR;

const int act_max=10;    //Default 10 action,4 the Angle of servo
int act[act_max][4];    //Only can change the number of action
int num=0,num_do=0;
///////////////////////////////////////////////////////////////
void turnUD(void){
  if(xL!=512){
    if(0<=xL && xL<=100){arm.up(10);return;}
    if(900<xL && xL<=1024){arm.down(10);return;} 
    if(100<xL && xL<=200){arm.up(20);return;}
    if(800<xL && xL<=900){arm.down(20);return;}
    if(200<xL && xL<=300){arm.up(25);return;}
    if(700<xL && xL<=800){arm.down(25);return;}
    if(300<xL && xL<=400){arm.up(30);return;}
    if(600<xL && xL<=700){arm.down(30);return;}
    if(400<xL && xL<=480){arm.up(35);return;}
    if(540<xL && xL<=600){arm.down(35);return;} 
    }
}
///////////////////////////////////////////////////////////////
void turnLR(void){
  if(yL!=512){
    if(0<=yL && yL<=100){arm.right(0);return;}
    if(900<yL && yL<=1024){arm.left(0);return;}  
    if(100<yL && yL<=200){arm.right(5);return;}
    if(800<yL && yL<=900){arm.left(5);return;}
    if(200<yL && yL<=300){arm.right(10);return;}
    if(700<yL && yL<=800){arm.left(10);return;}
    if(300<yL && yL<=400){arm.right(15);return;}
    if(600<yL && yL<=700){arm.left(15);return;}
    if(400<yL && yL<=480){arm.right(20);return;}
    if(540<yL && yL<=600){arm.left(20);return;}
  }
}
///////////////////////////////////////////////////////////////
void turnCO(void){
  if(xR!=512){
    if(0<=xR && xR<=100){arm.close(0);return;}
    if(900<xR && xR<=1024){arm.open(0);return;} 
    if(100<xR && xR<=200){arm.close(5);return;}
    if(800<xR && xR<=900){arm.open(5);return;}
    if(200<xR && xR<=300){arm.close(10);return;}
    if(700<xR && xR<=800){arm.open(10);return;}
    if(300<xR && xR<=400){arm.close(15);return;}
    if(600<xR && xR<=700){arm.open(15);return;}
    if(400<xR && xR<=480){arm.close(20);return;}
    if(540<xR && xR<=600){arm.open(20);return;} 
    }
}
///////////////////////////////////////////////////////////////
void date_processing(int *x,int *y){
  if(abs(512-*x)>abs(512-*y))
    {*y = 512;}
  else
    {*x = 512;}
}
///////////////////////////////////////////////////////////////
void buzzer(int H,int L){
  while(yR<420){
    digitalWrite(buzzerPin,HIGH);
    delayMicroseconds(H);
    digitalWrite(buzzerPin,LOW);
    delayMicroseconds(L);
    yR = arm.JoyStickR.read_y();
    }
  while(yR>600){
    digitalWrite(buzzerPin,HIGH);
    delayMicroseconds(H);
    digitalWrite(buzzerPin,LOW);
    delayMicroseconds(L);
    yR = arm.JoyStickR.read_y();
    }
}
///////////////////////////////////////////////////////////////
void C_action(void){
  if(yR>800){
    int *p;
    p=arm.captureAction();
    for(char i=0;i<4;i++){
    act[num][i]=*p;
    p=p+1;     
    }
    num++;
    num_do=num;
    if(num>=act_max){
      num=0;
      buzzer(600,400);
      }
    while(yR>600){yR = arm.JoyStickR.read_y();}
    //Serial.println(act[0][0]);
  }
}
///////////////////////////////////////////////////////////////
void Do_action(void){
  if(yR<220){
    buzzer(200,300);
    for(int i=0;i<num_do;i++){
      arm.do_action(act[i],15);
      }
    num=0;
    while(yR<420){yR = arm.JoyStickR.read_y();}
    for(int i=0;i<2000;i++){
      digitalWrite(buzzerPin,HIGH);
      delayMicroseconds(200);
      digitalWrite(buzzerPin,LOW);
      delayMicroseconds(300);        
    }
  }
}
///////////////////////////////////////////////////////////////
void setup() {
  //Serial.begin(9600);
  //arm of servo motor connection pins
  arm.ServoAttach(4,5,6,7);
  //arm of joy stick connection pins : xL,yL,xR,yR
  arm.JoyStickAttach(A0,A1,A2,A3);
  pinMode(buzzerPin,OUTPUT);
}
///////////////////////////////////////////////////////////////
void loop() {
  xL = arm.JoyStickL.read_x();
  yL = arm.JoyStickL.read_y();
  xR = arm.JoyStickR.read_x();
  yR = arm.JoyStickR.read_y();
  date_processing(&xL,&yL);
  date_processing(&xR,&yR);
  turnUD();
  turnLR();
  turnCO();
  C_action();
  Do_action();
}
```

# First Milestone (A.I. Powered Claw Car)

<iframe width="560" height="315" src="https://www.youtube.com/embed/jHtg-IWIxA0" title="Zia S. First Milestone" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<img src="Car_Pic.jpg"  width="500" height="474">

<h1>Summary</h1>

<h2>Project</h2>
My project is an A.I. Powered Claw Car, a robot that travels using 2 wheels controlled by servos and has a claw attached on top. Using a raspberry camera module and an object identification A.I. program, it is capable of identifying various objects based a training data set and pick them up with the claw. <br>

<h2>Components</h2>
<ul>
  <li>Acrylic Plate</li>
  <li>Arduino Uno</li>
  <li>Mini Breadboard</li>
  <li>TT Wheel</li>
  <li>1" Wheel</li>
  <li>TT Motor</li>
  <li>WLAN Module</li>
  <li>USB Cable</li>
  <li>Jumper Cables</li>
  <li>9V Battery</li>
  <li>IR Reciever</li>
  <li>IR Controller</li>
  <li>Velcro</li>
</ul> <br>

<h2>How Components Work Together</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The acrylic plate acts as the base of the car; everything including the servos, Arduino Uno, mini breadboard, L9110 module, universal wheel, and 9V Battery is attached to it. Whenever a button is pressed on the IR controller, the IR reciever recieves the signal and sends it to the Arduino Uno. The Uno then processes the signal and depending on the button pressed, sends a signal to the L9110 module with the specific activation truth table. This activates the motors and moves the car. 

<h2>Progress</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For the first milestone, I assembled the whole car and downloaded the necessary software, such as the Arduino library IRRemote and the Processing IDE, to control the car using the IR remote. 
<h2>Challenges Faced</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; I had a few troubles attaching the motors to the acrylic plate as the window for attachment was very tight and took me a bit to attach. I also wasted much time looking for specific standoffs that were missing from my kit that were needed for the universal wheel and ended up having to use slightly longer standoffs. 

<h2>Next Step</h2>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The next step is completing my second milestone: assembling the claw and programming it.<br><br>

<h2>Car_Remote_Control.ino</h2>

<h2>Schematic</h2>

<figure>
  <img src="M1_Schematic.jpg" alt="Provided by SunFounder" width="600" height="400">
  <figcaption>Provided by Cokoino.</figcaption>
</figure>
  
```c++
#include <IRremote.h>

const int IR_RECEIVE_PIN = 12;  // Define the pin number for the IR Sensor

const int A_1B = 5;
const int A_1A = 6;
const int B_1B = 9;
const int B_1A = 10;


int speed = 150;

void setup() {
  Serial.begin(9600);

  //motor
  pinMode(A_1B, OUTPUT);
  pinMode(A_1A, OUTPUT);
  pinMode(B_1B, OUTPUT);
  pinMode(B_1A, OUTPUT);

  //IR remote
  IrReceiver.begin(IR_RECEIVE_PIN, ENABLE_LED_FEEDBACK);  // Start the IR receiver // Start the receiver
  Serial.println("REMOTE CONTROL START");

}

void loop() {

  if (IrReceiver.decode()) {
    //    Serial.println(results.value,HEX);
    String key = decodeKeyValue(IrReceiver.decodedIRData.command);
    if (key != "ERROR") {
      Serial.println(key);

      if (key == "+") {
        speed += 50;
      } else if (key == "-") {
        speed -= 50;
      } else if (key == "2") {
        moveForward(speed);
        delay(1000);
      } else if (key == "1") {
        moveLeft(speed);
      } else if (key == "3") {
        moveRight(speed);
      } else if (key == "4") {
        turnLeft(speed);
      } else if (key == "6") {
        turnRight(speed);
      } else if (key == "7") {
        backLeft(speed);
      } else if (key == "9") {
        backRight(speed);
      } else if (key == "8") {
        moveBackward(speed);
        delay(1000);
      }

      if (speed >= 255) {
        speed = 255;
      }
      if (speed <= 0) {
        speed = 0;
      }
      delay(500);
      stopMove();
    }

    IrReceiver.resume();  // Enable receiving of the next value
  }
}

void moveForward(int speed) {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, speed);
  analogWrite(B_1B, speed);
  analogWrite(B_1A, 0);
}

void moveBackward(int speed) {
  analogWrite(A_1B, speed);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, speed);
}

void turnRight(int speed) {
  analogWrite(A_1B, speed);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, speed);
  analogWrite(B_1A, 0);
}

void turnLeft(int speed) {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, speed);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, speed);
}

void moveLeft(int speed) {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, speed);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, 0);
}

void moveRight(int speed) {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, speed);
  analogWrite(B_1A, 0);
}

void backLeft(int speed) {
  analogWrite(A_1B, speed);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, 0);
}

void backRight(int speed) {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, speed);
}

void stopMove() {
  analogWrite(A_1B, 0);
  analogWrite(A_1A, 0);
  analogWrite(B_1B, 0);
  analogWrite(B_1A, 0);
}


String decodeKeyValue(long result)
{
  switch(result){
    case 0x16:
      return "0";
    case 0xC:
      return "1"; 
    case 0x18:
      return "2"; 
    case 0x5E:
      return "3"; 
    case 0x8:
      return "4"; 
    case 0x1C:
      return "5"; 
    case 0x5A:
      return "6"; 
    case 0x42:
      return "7"; 
    case 0x52:
      return "8"; 
    case 0x4A:
      return "9"; 
    case 0x9:
      return "+"; 
    case 0x15:
      return "-"; 
    case 0x7:
      return "EQ"; 
    case 0xD:
      return "U/SD";
    case 0x19:
      return "CYCLE";         
    case 0x44:
      return "PLAY/PAUSE";   
    case 0x43:
      return "FORWARD";   
    case 0x40:
      return "BACKWARD";   
    case 0x45:
      return "POWER";   
    case 0x47:
      return "MUTE";   
    case 0x46:
      return "MODE";       
    case 0x0:
      return "ERROR";   
    default :
      return "ERROR";
    }
}
}

```

<!--# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 


# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|-->

# Starter Project (Retro Arcade Console)

<iframe width="560" height="315" src="https://www.youtube.com/embed/hHAm_oHuuT8" title="Zia C. Starter Project" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<figure>
  <img src="Starter_Project2.jpg" width="50%" height="50%">
</figure>

My Starter Project is the Retro Arcade Console which uses multiple buttons, a digitron display, 2 dot matrixes, and a buzzer to create a full-on gaming experience with 5 retro games including Tetris and Snake.  

Materials:
* 1 Buzzer
* 1 220uF 16V Capacitor
* 1 Micro USB
* 1 Power Cable
* 1 Self-switch
* 1 Self-switch cap
* 1 Digitron display
* IC Chip
* 2 LED dot matrix modules
* 6 Buttons
* 6 Button caps
* 1 PCB
* 8 M3x5mm Screws
* 2 M3x8mm Screws
* 4 Copper columns
* 4 Hexagonal columns
* 1 Battery Case
* 6 Acrylic shells
* 1 Solder & Soldering Iron
* 1 Screwdriver

Procedure: 
1. First, I soldered all of the main parts to the PCB; I soldered the 6 buttons, then the micro USB, then the capacitor, then the self-lock switch, then the digitron display, and finally the dot matrix modules.
2. Second, I soldered the ground and voltage wires of the battery case to the PCB, attached the case to an acrylic shell using screws, and attached the button caps to all of the buttons.
3. Finally, I assembled the acyrlic cage using mutiples screws and columns to space out the console. 

<table>
  <thead>
    <tr>
      <th style="text-align: center"><strong>Part</strong></th>
      <th style="text-align: center"><strong>Note</strong></th>
      <th style="text-align: center"><strong>Price(USD)</strong></th>
      <th style="text-align: center"><strong>Link</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center">DIY Soldering RGB Practice Kit</td>
      <td style="text-align: center">The Starter Project. Practice for soldering</td>
      <td style="text-align: center">$7.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Soldering-Practice-Learning-Electronics-Training/dp/B0BKM3D927"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Raspberry Pi 400</td>
      <td style="text-align: center">Powers the Smart Mirror.</td>
      <td style="text-align: center">$70.00</td>
      <td style="text-align: center"><a href="https://www.digikey.com/en/products/detail/raspberry-pi/SC0373/13282408"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Wireless Mouse</td>
      <td style="text-align: center">Configures Raspberry Pi for the mirror display.</td>
      <td style="text-align: center">$7.79</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Wireless-TECKNET-Receiver-Portable-Adjustable/dp/B095HBY3RF?th=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Ultrasonic Distance Sensor</td>
      <td style="text-align: center">Tracks and calculates a person’s distance from a mirror to turn on or off the mirror.</td>
      <td style="text-align: center">$4.50</td>
      <td style="text-align: center"><a href="https://www.sparkfun.com/products/15569"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Power Strip</td>
      <td style="text-align: center">Powers Smart Mirror components.</td>
      <td style="text-align: center">$16.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/gp/product/B092J8LPWR?ie=UTF8&amp;psc=1&amp;linkCode=sl1&amp;tag=qtkwa-20&amp;linkId=2711afc9129fc98b2bd0b14730062c9a&amp;language=en_US&amp;ref_=as_li_ss_tl"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">WS2812B Individual Addressable LED Strip</td>
      <td style="text-align: center">Goes around the monitor behind the mirror.</td>
      <td style="text-align: center">$32.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/BTF-LIGHTING-Flexible-Individually-Addressable-Non-waterproof/dp/B01CDTEJBG?th=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">TV/Monitor Wall Mount</td>
      <td style="text-align: center">Mounts the mirror and monitor to a wall.</td>
      <td style="text-align: center">$24.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/dp/B00ZKFRKIU/ref=sspa_dk_detail_0?psc=1&amp;pd_rd_i=B00ZKFRKIU&amp;pd_rd_w=NpFq1&amp;content-id=amzn1.sym.d81b167d-1f9e-48b6-87d8-8aa5e473ea8c&amp;pf_rd_p=d81b167d-1f9e-48b6-87d8-8aa5e473ea8c&amp;pf_rd_r=ZFB3M2YBGTBNGR7KZRPM&amp;pd_rd_wg=Lls5P&amp;pd_rd_r=a5ab98a2-3174-4a0e-b8e7-f68a6ebf6cfc&amp;s=office-products&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWxfdGhlbWF0aWM&amp;spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExRzczMExYQ1dITFI0JmVuY3J5cHRlZElkPUEwODgyMDAxMk5PWERRVEpDUTYwWSZlbmNyeXB0ZWRBZElkPUEwNDU0MzI0MUVEWDFMNEtTTkIyVCZ3aWRnZXROYW1lPXNwX2RldGFpbF90aGVtYXRpYyZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU="> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">18in x 24in Semi-Transparent Mirror</td>
      <td style="text-align: center">Transparent mirror that is semi-transparent to see the monitor and LEDs.</td>
      <td style="text-align: center">$42.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/SupremeTech-Acrylic-See-Through-Resistant-Transparent/dp/B07XTRCTQL/ref=sr_1_5?keywords=18+x+24+transparent+mirror&amp;qid=1689800283&amp;sr=8-5"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">18in x 24in x 1/4in Plywood</td>
      <td style="text-align: center">Only x1 Plywood needed. Cut a rectangle into the plywood to fit the monitor in.</td>
      <td style="text-align: center">$71.39 for 4</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Premium-Plywood-Perfect-Projects-Woodpeckers/dp/B07NWYN5K2/ref=sr_1_6?crid=1WK154IDSAJRR&amp;keywords=18%2Bx%2B24%2Bplywood&amp;qid=1689800390&amp;sprefix=18%2Bx%2B24%2Bplyw%2Caps%2C348&amp;sr=8-6&amp;ufe=app_do%3Aamzn1.fos.18ed3cb5-28d5-4975-8bc7-93deae8f9840&amp;th=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">2 oz. Black Acrylic Paint</td>
      <td style="text-align: center">Paint plywood and anything behind the mirror black.</td>
      <td style="text-align: center">$0.97</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Apple-Barrel-21985E-Surface-Acrylic/dp/B07BG4NH83/ref=sr_1_7?crid=1T4IH7UW641XX&amp;keywords=black+acrylic+paint&amp;qid=1689800559&amp;sprefix=black+acrylic+pain%2Caps%2C151&amp;sr=8-7"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Black Electrical Tape</td>
      <td style="text-align: center">Covers any imperfections behind the mirror that the black paint cannot cover. In addition, good for temporarily binding components to the back of the plywood.</td>
      <td style="text-align: center">$12.60</td>
      <td style="text-align: center"><a href="https://www.amazon.com/AmazonCommercial-Electrical-4-inch-60-feet-6-Pack/dp/B07YDRY8ZS/ref=sr_1_1_ffob_sspa?crid=1I6NMKH4MUOHR&amp;keywords=black+electrical+tape&amp;qid=1689800720&amp;sprefix=black+electrical+tape%2Caps%2C145&amp;sr=8-1-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&amp;psc=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Mini PCB Prototype Breadboard</td>
      <td style="text-align: center">For the circuitry of the ultrasonic sensor, which requires a voltage divider circuit.</td>
      <td style="text-align: center">$9.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/ElectroCookie-Solderable-Breadboard-Electronics-Gold-Plated/dp/B081MSKJJX/ref=sr_1_3?crid=1LVR7D95R3GD3&amp;keywords=1%2F4+perf+board&amp;qid=1689800932&amp;sprefix=1%2F4+perf+board%2Caps%2C134&amp;sr=8-3"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Nylon Webbing</td>
      <td style="text-align: center">Holds the monitor to the mirror.</td>
      <td style="text-align: center">$11.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Buckle-Strap-Inch-Adjustable-Tri-Glide/dp/B08LD8CJ8D/ref=sr_1_1_sspa?crid=3B44Y1K6F1IMV&amp;keywords=nylon+webbing&amp;qid=1689801174&amp;sprefix=nylon+webbing%2Caps%2C158&amp;sr=8-1-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&amp;psc=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Assorted Jumper Wires</td>
      <td style="text-align: center">For the wiring to the Raspberry Pi or the Ultrasonic Sensor.</td>
      <td style="text-align: center">$7.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/EDGELEC-Breadboard-Optional-Assorted-Multicolored/dp/B07GD2BWPY/ref=sr_1_4?crid=25R300F7Y1R6Z&amp;keywords=jumper+wires&amp;qid=1689801332&amp;sprefix=jumper+wires%2Caps%2C156&amp;sr=8-4"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Solid Core Hookup Wire</td>
      <td style="text-align: center">For wiring the LEDs or lengthening the wire connections of the Ultrasonic Sensor to the Raspberry Pi. Soldering wires together may be necessary.</td>
      <td style="text-align: center">$16.94</td>
      <td style="text-align: center"><a href="https://www.amazon.com/EDGELEC-Breadboard-Optional-Assorted-Multicolored/dp/B07GD2BWPY/ref=sr_1_4?crid=25R300F7Y1R6Z&amp;keywords=jumper+wires&amp;qid=1689801332&amp;sprefix=jumper+wires%2Caps%2C156&amp;sr=8-4"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">5V Power Supply</td>
      <td style="text-align: center">For powering the LED strip. It is necessary for the LEDs since the Raspberry Pi’s 5V power cannot reliably power numerous individual LEDs.</td>
      <td style="text-align: center"><a href="https://www.amazon.com/BTF-LIGHTING-Plastic-Adapter-Transformer-WS2812B/dp/B01D8FM71S/ref=sr_1_1_sspa?crid=3QLXK7OHS1LHA&amp;keywords=5v+power+supply&amp;qid=1689802491&amp;sprefix=5v+%2Caps%2C204&amp;sr=8-1-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&amp;psc=1"> Link </a></td>
      <td style="text-align: center"> </td>
    </tr>
    <tr>
      <td style="text-align: center">18 inch by 24 inch Black Frame</td>
      <td style="text-align: center">Frame for the mirror.</td>
      <td style="text-align: center">$26.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/Americanflat-18x24-Poster-Frame-Black/dp/B071LPY3RH/ref=sr_1_1_sspa?crid=29KKX26ZAFZT9&amp;keywords=18+by+24+frame&amp;qid=1689802692&amp;sprefix=18+by+24+fram%2Caps%2C150&amp;sr=8-1-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&amp;psc=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Grommet Tool Kit + 500pc Silver Grommets</td>
      <td style="text-align: center">Grommets for screwing the nylon webbing onto the plywood. Washers may be necessary for securing the monitor with the nylon webbing for the wood screws.</td>
      <td style="text-align: center">$38.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/BIZOEPRO-Handheld-Grommets-Punching-Machine/dp/B07WS5C378/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.b7ddaaf5-d42c-4edb-8609-c401608d4edc%3Aamzn1.sym.b7ddaaf5-d42c-4edb-8609-c401608d4edc&amp;crid=13Y8IKQUMNP9E&amp;cv_ct_cx=grommet+tool+kit&amp;keywords=grommet+tool+kit&amp;pd_rd_i=B07WS5C378&amp;pd_rd_r=6ddf07b9-ee90-4e30-9954-81333ccab440&amp;pd_rd_w=79ey8&amp;pd_rd_wg=RAYYd&amp;pf_rd_p=b7ddaaf5-d42c-4edb-8609-c401608d4edc&amp;pf_rd_r=3ET1QZY2VEDZZEM21NKF&amp;qid=1689802822&amp;sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&amp;sprefix=gromme%2Caps%2C165&amp;sr=1-1-14c6653e-7b09-4215-b407-298aef9958b8-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&amp;psc=1"> Link </a></td>
    </tr>
    <tr>
      <td style="text-align: center">Variety of Wood Screws</td>
      <td style="text-align: center">Longer wood screws will be necessary for drilling the plywood to the frame. Shorter wood screws with washers would be ideal to secure the grommets with the nylon webbing to the back of the plywood to secure the monitor to the mirror. Be cautious of securing the nylon webbing to the plywood as to not damage the mirror.</td>
      <td style="text-align: center">$22.99</td>
      <td style="text-align: center"><a href="https://www.amazon.com/BIZOEPRO-Handheld-Grommets-Punching-Machine/dp/B07WS5C378/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.b7ddaaf5-d42c-4edb-8609-c401608d4edc%3Aamzn1.sym.b7ddaaf5-d42c-4edb-8609-c401608d4edc&amp;crid=13Y8IKQUMNP9E&amp;cv_ct_cx=grommet+tool+kit&amp;keywords=grommet+tool+kit&amp;pd_rd_i=B07WS5C378&amp;pd_rd_r=6ddf07b9-ee90-4e30-9954-81333ccab440&amp;pd_rd_w=79ey8&amp;pd_rd_wg=RAYYd&amp;pf_rd_p=b7ddaaf5-d42c-4edb-8609-c401608d4edc&amp;pf_rd_r=3ET1QZY2VEDZZEM21NKF&amp;qid=1689802822&amp;sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&amp;sprefix=gromme%2Caps%2C165&amp;sr=1-1-14c6653e-7b09-4215-b407-298aef9958b8-spons&amp;sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&amp;psc=1"> Link </a></td>
    </tr>
  </tbody>
</table>


<!--# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.-->
