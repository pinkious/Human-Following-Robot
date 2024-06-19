The programming that goes into the robot’s movement is comprised of two functions, one for music and the other for movement. The code used is a similar version to a Connor Nishijima’s Miduino player and Gourav Tak’s Human Following Robot code as a combination. For the music, a speaker emits six tones to produce polyphonic music. This is generated by taking advantage of hardware timers in the Arduino Uno. Normally, the Uno can only process up to three simultaneous commands to play a tone at once, absorbing all three hardware timers and leaving no availability for other actions; by “polling”, however, or using only one hardware timer that interrupts at 20 Khz, or once every 50 microseconds, the illusion of multiple tones at once can be achieved. The interrupt routine determines which, if any, of the currently playing notes need to be toggled. The pins that each of the six inputs use are the analog pins, A0 through A6. These wires were bound together to all reach the speaker because this design does not include a breadboard. In the initial part of the code, an array of 94 values for frequencies is present. Then follows the array used to play the music. This was automatically generated by a program called Miditones by Len Shustek using MIDI files of the music of choice. These generated arrays are made up of set values that determine the frequency, duration, and voice type of each note. If the value is 0xF0, then it will stop the music. This is put at the end of the array to stop playing the music once it finishes. To create percussion, white noise can be emulated by creating a series of frequencies that play in quick succession. These percussion values are stored at frequencies above the 94 specified before. When the frequency in a note is above 16744hz, or C10, the following notes are a sequence of percussion instruments, such as bass drum 1 and 2, closed hi-hat, open hi-hat, and snare 1 and 2. These have to be manually added as they were not originally included in Miditones. Overall, the goal is to always have three songs play on loop. This part of the code takes up a large percentage of the flash memory. As for the robot’s movement code, it is designed to follow a human target using three ultrasonic sensors. The schematic for pin placement is included in the image below. Assuming the ultrasonic sensors emit a frequency at the speed of sound, 343 m/s, the time it takes to receive is divided by 58 to find the distance in centimeters. These values are displayed in the Serial monitor while the code is running. The motors respond to these inputs by moving in the direction of the sensor that records the closest input within a certain range. If there is no recorded input within the maximum distance, 40 centimeters, then the robot will stop. If there is an object within the minimum distance, 5 centimeters, the robot will move backward.  Since the design does not include a breadboard, the three wires for each sensor designated for ground and 5V need to be bound together to receive the one input. On an additional note, to create lights for the star rod that the robot will be holding, the team plans to connect the anode to the pin that generates music; the light will turn on when a note is playing on one of the six tone generators corresponding to six LEDs. Below is the Circuit Diagram for the project.

![image](https://github.com/pinkious/Human-Following-Robot/assets/119024361/1ac1841e-f000-4b24-bf26-d1f823567a9b)

The final result of the project is included below.

![20240619_024229](https://github.com/pinkious/Human-Following-Robot/assets/119024361/661efee0-3acb-431e-a67a-5d7970fa0572)
