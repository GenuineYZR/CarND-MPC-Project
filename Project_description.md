# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---

## The MPC model

* The model was established basically following the quiz in the lecture and contains the car states, actuators and other elements like the update functions. The states have the position of the car in x, y coordinates(car space), the psi which stands for the steering angle against the x coordinate, the car velocity(m/s), the cross-track error and the error of psi. The actuators contains the throttle and the acceleration. 
Those above are just the same as in the quiz while the update function is a little different. This is because the trajectory in the project is a curve instead of a straight line as in the quiz. The main difference in the update function can be found from line 110 to 114 in the MPC.cpp file. I think the cte and epsi of the next timestamp can no longer be simply updated by the current cte and epsi because the reference trajectory from which the cte and epsi are calculated keeps changing. My own point of view is that the new cte and epsi can be reached by using the predicted psi, predicted y position and the new reference trajectory.

* The first N and dt I chose were 25 and 0.2 but it turned out to be too complicated for the car to find a good solution. As a result I change the N to 8 and the dt to 0.15 which was seemingly better. I suppose it also has something to do with the cpu of the laptop. Maybe someone else with a robust laptop could gain a better results? : )

* As with the latency, to be honest, for me it didn't make any difference to the performance. However, apart from the latency, the time consumed by the optimizor to calculate and find a good result may also need to be considered? For a more complicated algorithm it can be much more time consuming for the car to react.
    ```
