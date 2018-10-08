# P11: Path Planning

The project includes the following files

* CMakeLists.txt
* src folder
* notes.txt (this file)

## Description

The project was addressed the following way:

* Review the [QA session](https://youtu.be/7sI3VHFPP0w) to get started.
* Review code from the quizzes and classes.
* Review the [Forum](https://discussions.udacity.com/c/nd013-path-planning) messages and Slack #s-t3-p-path-planning channel.
* Get basic Path planning working and start tweaking. It involves
  * considering obstacles
  * decide when to change lanes

## Considerations

The QA session was very important to get started. I could not have done path planning without watching the walk through video.

Once the basics is assembled using the QA session I started working on a "cost module" to make lane changing and safety decisions.

As suggested I used the Spline library to generate a smooth trajectory.

From the sensor fusion, check vehicles within range (is_within_range method) and create the following variables to be used later with the Finite State Machine:

* cars_ahead: check if there is a car ahead too close.
* car_left_lane: flag to check close cars on the left lane.
* car_right_lane: flag to check close cars on the right lane.

Using a hand made Finite State Machine there is a lane control mechanism using the previous variables. The states considered are:

* Free state
* Car Ahead
* Cars to the left
* Cars to the right

 Taking into account the car position and previous variables, I decide lane switching if needed and velocity changes. I did not use cost functions.

Then. the same code from the QA follows:

* Create a list of widely spaced (x,y) waypoints, evenly spaced at 30m.
* Interpolate these waypoints with a spline and fill it in with more points that control speed.
* Use Frenet coordinates and shift car reference angle to 0 degree.
* Calculate reference speed using calculate_speed method.
* Load next_x_vals and next_y_vals variables.

## Resources

* [http://robots.stanford.edu/papers/junior08.pdf](Junior: The Stanford Entry in the Urban Challenge)

## Test

Follow these steps for validation:

1. Compile the project as detailed `cmake .. && make` under the build directory.
2. Run `./path_planning`
3. Run the simulator; select the track and start.
