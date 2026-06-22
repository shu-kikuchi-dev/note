# How to Get the Graph in MATLAB

In MATLAB, you can get a graph in several ways. This note will tell some significant ways of them.



### Method 1. Get from Command Window

In this classical way, you can get a beautifully plotted graph with some commands executing.



##### In Simulink Field:

At first, you have to send the data that you want to plot from Simulink to MATLAB workspace. You can achieve this through "to Workspace" block.

So, find out the block and place it to your Simulink field, and connect the arbitrary signal to it. And double click the block, you have to specify the name of signal.

If the signal is named like "v", you can set the name like "v\_data" for example. Additionally, you better change the saving form "Time series" to "Array". "Array" is easy to treat for beginners.

After you checked the name of the block has changed through the procedure, now you can execute the simulation.

When the simulation has done, you can move to the command window.



##### In Command Window:

In command window, you have to execute below commands one by one.



> {arbitrary signal name} = out.{arbitrary signal name you set in the Simulink};

> t = out.tout;



Do not worry about "tout". "tout" is made by MATLAB automatically. So you do not have to specify this signal data in Simulink.

And, in this time, we will use the below whole example for instance. This example is attempting to get the Friction Force and Velocity in the workspace and extract

the certain execution time.



> v = out.v\\\_data;

> F = out.F\\\_data;

> t = out.tout;

> idx = find(t > 0.8);

> plot(v(idx), F(idx));

> grid on;

> xlabel('Velocity /(m/s)');

> ylabel('Friction Force /N');



Now you got the plotted graph with a new window. So you can save that with arbitrary name.

And do not forget to execute below command. If you do not do that, you cannot execute the same command to save another figure again.



> close all

###### 

### Method 2. Get at Simulink Directly

This method is easy way to get a graph.

###### 

### Option: Plot Several Curves in One Graph

This will introduce how to plot several curves in one graph to compare the condition. Most of the procedure is similar to Method 1, but we have to add some operation before plot a curve.



##### In Command Window:

At first, you have to operate at command window to let the system to remain previous plotted graph.



> close all	# clean your last time graph at first

> figure		# just show up the empty figure

> grid on

> hold on	# this will work to let the system to remain previous one



##### In Simulink Field:

In Simulink, execute the simulation and do not forget about add "to Workspace" block to send data to the workspace. The procedure to achieve it is explained in Method 1.

When you achieved simulation for the first condition, you can go back to command window and do some operations.



##### In Command Window:

In command window, you have to do the same thing as Method 1. This will plot the graph you simulated.



And now, you will go back to Simulink field and try another condition. Then, move on to the command window to plot them with hold previous curve.

When you tried all of conditions, you can save it with legends and other settings(e.g. axis labeling).

