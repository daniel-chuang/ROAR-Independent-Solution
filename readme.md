# Second Place Solution in Summer 2022 ROAR S1/S2 Series

Written by Daniel Chuang, describing his experience and solution for his second place solution in Summer 2022 ROAR S1/S2 Series Competition. Iterating off of Aaron Xie's previous winning solution, he reprogrammed the car's controller to be more aggressive, and developed a suite of tools to optimize testing and waypoint tuning.

## Introduction

The Summer 2022 ROAR S1/S2 Series competition is an autonomous racing competition held by the University of California, Berkeley, by Allen Yang, the Executive Director for the FHL Vive Center for Enhanced Reality. Competitors use Python to automate a simulated Tesla Model 3 in the virtual Carla research environment, which was developed for the testing of self-driving car algorithms. The challenge is to autonomously control a car to drive around a simulation map of the Berkeley campus and the hills in its vicinity.

In this paper, I will discuss how I improved upon the previous solution developed by Aaron Xie, resulting in a lap time ~35 seconds faster than the previous record, for a ~6.7% faster speed. First, I developed a suite of tools to test the car efficiently, which is open-sourced for future competitors to use. Secondly, I reprogrammed the lateral controller to break at fewer sections, and manually tuned sections of the run that posed risk of collision. Finally, I made a new set of waypoints that followed more optimal racing lines, to minimize lost velocity during turns.

## Efficient Testing

## Reprogramming the Controller

## Tuning Racing Lines

## Conclusion
