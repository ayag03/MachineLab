# 🎠Carousel Progress #3-Aya, Evelyn, Ehtisham
Continuing from the last progress of our Carousel, we started connecting the power supplies, wires and Arduino
with the help of the Slipring to our structure.
## Supplying power through the Slipring while the carousel is rotating 
- First, we built the structure with the help of the metal square tube by bolting them
to the two circle wood base and tops of the carousel. Nelson was super helpful during this process by helping us to
cut the second wood circle as well as giving us the metal tube. 
![structure](https://github.com/ayag03/MachineLab/blob/main/images/carousel_structure.jpg)
- Secondly, with the help of Professor Shiloh, we figured out how to connect and get power supplies from the bottom
of the carousel to the top, where we will connect Arduino, neopixels, and servo motors.

![diagram](https://github.com/ayag03/MachineLab/blob/main/images/diagram.png)
In order to do that, we connected the slipring to the bottom part of the Lazy Suzan, sorted out and organized the 12 wires, and soldered them together into 3 groups - 6 for the ground, 5 for the 5V Neopixels and servos as they take a lot of current, and 1 for the 9V arduino as it takes less current. We also used heat shrink tubing after soldering the wires to avoid any risks of open wire space and any loose connections that could happen during the movement.

![soldering](https://github.com/ayag03/MachineLab/blob/main/images/solder.png)
- Next, before mounting the whole structure, we first checked all the wire connections by giving power to the Arduino and everything worked well!
  



https://github.com/ayag03/MachineLab/assets/91026712/65c1fb1b-47cf-4f24-bf85-1ad86d6b84a0




- Finally, we mounted the metal square tube, placed the wires inside, connected them correspondingly to Arduino, powered the DC motor that rotates the carousel, and verified that all the connections work well while rotating. Yay, success of the day!


https://github.com/ayag03/MachineLab/assets/91026712/76c96f73-8435-471b-8ffe-3d875560e2c2


## Connecting Servo motors for the horse up and down movement
As the next step, we started working on the horse movement with the servo motor. Spoiler: we had lots of trials and errors!
Our cute horse model ^^

![horse](https://github.com/ayag03/MachineLab/blob/main/images/cute_horse.png)


- Trial #1: copper wire and 90-degree rotation

https://github.com/ayag03/MachineLab/assets/91026712/39f54309-1dd1-4873-88dd-0222aa38e698

- Trial #2:copper wire and 180-degree rotation

https://github.com/ayag03/MachineLab/assets/91026712/5842a199-9368-48e2-b662-275d1ed3166c

As you can see, the movement was going horizontal and nothing close to what we envisioned in the classic carousel. That is why, we tried changing the handle of the servo. 

- Trial #3. New handle and the movement is 👍

https://github.com/ayag03/MachineLab/assets/91026712/1d517107-17db-4a09-89ed-35c6605a26c0

- Trial #4. We tried combining the up-down movement with the rotation and played around with the speed.


https://github.com/ayag03/MachineLab/assets/91026712/363b1d23-f4d2-4643-8738-b2c354391f4c

- Bonus trial: it seemed like the horse was moving too slowly, and therefore the up and down movement was not obvious and clear, so we tried changing the degree change in servo, but our horse went crazy instead😭

https://github.com/ayag03/MachineLab/assets/91026712/079c44e8-ae5a-4af4-b5b3-aaaa7c3df018

- Trial #5. We tried changing the soft wire to something more rigid, hoping that the movement would be more clear. So we attached the horse to the servo using a straw. 


https://github.com/ayag03/MachineLab/assets/91026712/0d51ae3e-e60a-444e-af4b-fc50cbbd6125




https://github.com/ayag03/MachineLab/assets/91026712/b66a842d-473f-47ea-ae87-93ac299e73c3







- Trial #6. We were still not satisfied with the movement, as the horse was moving around a lot, so we tried attaching a thread to the servo, and hanging two horses from opposite sides so that the thread would be pulling up and down the horses respectively. 



https://github.com/ayag03/MachineLab/assets/91026712/4dc6418a-ebb3-46a7-a2c6-6ebcd027bf39







- Trial #7. The thread still seemed not rigid enough, so we tried replicating the same pulling system with the wire. However, the wire again moved the horses horizontally, and we remembered why we abandoned it from the first try😅🫣


https://github.com/ayag03/MachineLab/assets/91026712/5c0d6202-0d0f-4ffa-b45b-88168cadc3a6




### Final trial for now: 
We came back to the thread and tried rotating the carousel. While this structure is the best one out of numerous trials we did, we are still not satisfied and want to work more on the horse movement. 



https://github.com/ayag03/MachineLab/assets/91026712/4a52cf55-076d-489b-a11c-5e40241f50c3



## Next steps
As we mentioned above, we are not quite content with the horse movement yet, so our next step would be refining that. Our guess for the next trial is to try drilling a hole in the circle, so maybe the tube(straw) would have less space to move around and have more motion control. 
Also, another rough visualization of the potential structure for the movement.



https://github.com/ayag03/MachineLab/assets/91026712/8fdaf74e-721c-41a9-90d2-1f8c4b6e17aa

### Summary
1. Fix the horse movement
2. Test with more horse prototypes
3. Add neopixels
4. Build a prototype dome to hide all the hardware on top, and do a final test.
5. Start working on the actual model: building a stage, hiding the metal tube, generally decorating the carousel, add colors and magic!



## Code
### DC Motor for rotation
// Motor A connections
int enA = 9;
int in1 = 8;
int in2 = 7;
// Motor B connections


void setup() {
	// Set all the motor control pins to outputs
	pinMode(enA, OUTPUT);
	//pinMode(enB, OUTPUT);
	pinMode(in1, OUTPUT);
	pinMode(in2, OUTPUT);

	
	// Turn off motors - Initial state
	digitalWrite(in1, LOW);
	digitalWrite(in2, LOW);
	//digitalWrite(in3, LOW);
	//digitalWrite(in4, LOW);
}

void loop() {
	directionControl();
	delay(1000);
	//speedControl();
	delay(1000);
}

// This function lets you control spinning direction of motors
void directionControl() {
	// Set motors to maximum speed
	// For PWM maximum possible values are 0 to 255
	//analogWrite(enA, 255);
	//analogWrite(enB, 255);

	// Turn on motor A & B
	digitalWrite(in1, HIGH);
	digitalWrite(in2, LOW);
	//digitalWrite(in3, HIGH);
	//digitalWrite(in4, LOW);
	delay(2000);
  analogWrite(enA, 70);


}


### Servo Motor for up and down movement

#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 0; pos <= 180; pos += 2) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15 ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 2) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15 ms for the servo to reach the position
  }
}



