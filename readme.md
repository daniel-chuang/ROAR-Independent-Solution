# Second Place Solution in Summer 2022 ROAR S1/S2 Series

Written by Daniel Chuang, describing his experience and solution for his second place solution in Summer 2022 ROAR S1/S2 Series Competition. Iterating off of Aaron Xie's previous winning solution, he reprogrammed the car's controller to be more aggressive, and developed a suite of tools to optimize testing and waypoint tuning.

## Introduction

The Summer 2022 ROAR S1/S2 Series competition is an autonomous racing competition held by the University of California, Berkeley, by Allen Yang, the Executive Director for the FHL Vive Center for Enhanced Reality. Competitors use Python to automate a simulated Tesla Model 3 in the virtual Carla research environment, which was developed for the testing of self-driving car algorithms. The challenge is to autonomously control a car to drive around a simulation map of the Berkeley campus and the hills in its vicinity.

In this paper, I will discuss how I improved upon the previous solution developed by Aaron Xie, resulting in a lap time ~35 seconds faster than the previous record, for a ~6.7% faster speed. First, I reprogrammed the lateral controller to break at fewer sections, and manually tuned portions of the run  that posed risk of collision. Secondly, I made a new set of waypoints that followed more optimal racing lines, to minimize lost velocity during turns. Finally, I developed a suite of tools to test the car efficiently, which is open-sourced for future competitors to use. 

## Reprogramming the Controller

## Tuning Racing Lines

## Efficient Testing

### Minimap

One of the immediate challenges I encountered in this competition was the difficulty of testing changes. The lap is extremely long, yet competitors can only monitor the field of view of the car. Given the miniscule proportion that the field of view is compared to the entire race course, and the high speed that the car is traveling at, this information is very flawed for meaningful testing. In response to this issue, I created a map of the race course that displays the car's live position, as well as its previous route.

First, I downloaded the occupancy map of the race course [https://roar.berkeley.edu/berkeley-major-map/] and imported it as a 2-dimensional Numpy array. Then, I created 12 checkpoints, dividing the map into smaller sections. Using this data, I programmed a function that takes the coordinates of the car, and records it onto a birds-eye view of the map during a run, with different colors scaling off of speed and magnitude of acceleration. This allowed for me to test my code and monitor the results with far more ease, and understand the entirety of a run with just one image. Additionally, it allowed for me to record positions at which the car would crash, which I would accordingly tune with new waypoints or lateral controller restrictions, as explained in the previous sections.

## Conclusion
