# First Place Solution in Summer 2022 ROAR S1/S2 Series

Written by Daniel Chuang, describing his team's experience and solution for their first place solution in the Summer 2022 ROAR S1/S2 Series Competition with teammates Lucy Wang and Chris Wang. Iterating off of Aaron Xie's previous winning solution, he reprogrammed the car's controller to be more aggressive, and developed a suite of tools to optimize testing and waypoint tuning.

## Introduction

The Summer 2022 ROAR S1/S2 Series competition is an autonomous racing competition held by the University of California, Berkeley. Competitors use Python to automate a simulated Tesla Model 3 in the virtual Carla research environment, which was developed for the testing of self-driving car algorithms. The objective is to autonomously control a car to drive around a simulated environment of the Berkeley campus and its vicinity as fast as possible.

In this paper, I will discuss how we improved upon the previous solution developed by Aaron Xie, resulting in a lap time ~35 seconds faster than the previous record, for a ~6.7% faster speed. First, we reprogrammed the lateral controller to break at fewer sections, and manually tuned portions of the run that posed risk of collision. Secondly, we made a new set of waypoints that followed more optimal racing lines, to minimize lost velocity during turns. Finally, we developed a suite of tools to test the car efficiently, which is open-sourced for future competitors to use.

## Reprogramming the Controller

Our car is controlled by

## Tuning Racing Lines

## Efficient Testing

### Minimap

One of the immediate challenges that we encountered in this competition was the difficulty of testing changes. The lap is extremely long, yet competitors can only monitor the immediate field of view of the car. Given the miniscule proportion that the field of view is compared to the entire race course, and the high speed that the car is traveling at, this lack of information leads to inefficient testing of algorithms, slowing down development time. Moreover, this lack of information also means that only the current state of the car can be monitored.

In response to this issue, we created a program that generates a live map of the race course that displays the car's current position, as well its past positions. By doing so, we were able to constantly run the algorithm, keeping track of locations at which the car would crash without needing a team member to constantly monitor it. Every time the car crashed, the program would save an image of the map, so we were able to see exactly what happened during the collision. Additionally, we were able to execute better racing lines when planning and creating the waypoints for the car. This is because we factored in not only the current turn but also the turns that came after it, which was a significant improvement upon the previous solution. However, the most useful feature of this map was 

In order to create the map, we downloaded the occupancy map of the race course [https://roar.berkeley.edu/berkeley-major-map/] and imported it as a 2-dimensional Numpy array. Then, we created 12 checkpoints, dividing the map into smaller sections. Using this data, we programmed a function that takes the coordinates of the car using the Carla API, and records it onto a birds-eye view of the map during a run by modifying the Numpy array and displaying it with OpenCV, with different colors scaling off of speed and magnitude of acceleration.

### Checkpoint by Checkpoint Timing

Another challenge with measuring the efficiency of an algorithm was the immense length of the race course. Since our goal is to achieve maximum speed, we used a measurement of how long it took for our algorithm's iterations to complete a complete lap in order to further improve it, keeping changes that shortened our lap time, and undoing changes that extended it.

  A full lap takes hundreds of seconds to complete, so between every change of the algorithm our team would have to wait for minutes before recieving feedback as to whether or not to keep that change. Additionally, new changes can cause the car to crash, which prevents us from recieving any feedback at all. 
Additionally, once we did recieve feedback 

## Conclusion
