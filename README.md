# Elevator-Group-Control-System

This project implements an elevator group control system. An elevator group control algorithm based on the principle of minimizing the total waiting and travelling time of a passenger is developed, with outer control panels with inputs of passengers' destination floors are assumed to be used to provide necessary information for optimization. A platform for visualizing elevator group control system is developed in accordance. As long as the same variables recording the elevator states and request queues defined in the beginning of the initialization code part are used, any other algorithm can be used to replace the current algorithm implemented here.

## Details

The elevator group control algorithm is developed to minimize the sum of the waiting time for the elevator to come and the travelling time from the current floor to the destination floor for a passenger with the constraint that the elevator shall not change its current travelling direction to take the passenger. The constraint is added to avoid specific passengers waiting for too long in extreme cases. To implement this algorithm and visualize it, the program is developed as follows:

A series of variables are used for recording the operation state of the elevators, with their possible values defined as constants in the first part of the initialization code part. A list called callqueue is used to store all unprocessed request, and three lists queue1, queue2, queue3 store the task lists waited to be fulfilled in a proper order for three elevators respectively.

The sampleGenerator function generates passenger requests at a given time.

The elevatorAssign function calculates the time cost for each elevator to go to the requesting floor and take the passenger to his/her destination floor by mapping the timeCost function for three elevators, and assign the elevator with lowest time cost to take the request. The time cost is a summation of the time the elevator takes to directly travel from its current position to the floor where the request is from and then to the passenger's destination floor, and the time the elevator takes to stop at intermediate stops. The calculation is made possible as the outer control panel provides the system with information on the destination floor of each passenger. If the constraint cannot be fulfilled by any of the three elevator to take the request, the request remain unprocessed until the constraint is fulfilled.

The elevatorSystem function operates the elevator system according to the states of the elevators and their task queues.

The modelling part is an extension of a demonstration project of elevator systems by William Drevno with all the manual inputs provided by the elevatorSystem function automatically.

The system works as time flows, simulating the real-life case. The time variable is set to be 0 initially and increments by 1 whenever the tick-tock signal changes its value. The tick-tock signal is used to reach an appropriate animation speed for demonstration, as when the range of a variable becomes really large, the animation speed will be  set to be really large, and here my program needs to simulate the system for a long enough time.

However, in my project, the capacity of the elevator is assumed to be infinity. Therefore, possible future improvements are: adding a sensor monitoring the crowds in the elevator and if it is full, reject any request along the way; counting the number of requests to decide the number of elevators needed to be assigned to fulfill the needs. Also, as a final notice, for the sake of simplicity, the acceleration and acceleration process of the elevators are ignored.
