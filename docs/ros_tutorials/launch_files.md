Hopefully by this point you've realized that starting every node individually is not always the best option.  Doing so not only takes time, but it also results in a plethora of command terminals.  'roslaunch' is a tool in ROS that allows you to start multiple nodes (which are defined in a launch file) with only one command.

## Prerequisites
In order to complete this tutorial we need a package in which to place our launch file in.  Go ahead and complete these two tutorials from the official ROS tutorials.

* [Creating Packages](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

* [Building Packages](http://wiki.ros.org/ROS/Tutorials/BuildingPackages)

==== Using roslaunch ====
`roslaunch` starts nodes as defined in a launch file.

Usage:

 roslaunch [package] [filename.launch]

First go to the `beginner_tutorials` package we [http://wiki.ros.org/ROS/Tutorials/CreatingPackage created] and [http://wiki.ros.org/ROS/Tutorials/BuildingPackages built] earlier:

 roscd beginner_tutorials

If `roscd` says something similar to "roscd: No such package/stack 'beginner_tutorials" this simply means that ROS can't find your package. Check your .rosrc file in your home directory (which runs every time you open a new terminal) for the command:
 source ~/your_workspace/devel/setup.bash

Then let's make a launch directory:

 roscd beginner_tutorials
 mkdir launch
 cd launch

NOTE: The directory to store launch files don't necessarily have to be named as `launch`. In fact you don't even need to store them in a directory. `roslaunch` command automatically looks into the passed package and detects available launch files. However, it is good practice to do so.

==== The Launch File ====
Now let's create a launch file called turtlemimic.launch and paste the following:

<pre class="prettyprint linenums">
<launch>

  <group ns="turtlesim1">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>

  <group ns="turtlesim2">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>

  <node pkg="turtlesim" name="mimic" type="mimic">
    <remap from="input" to="turtlesim1/turtle1"/>
    <remap from="output" to="turtlesim2/turtle1"/>
  </node>

</launch>
</pre>

==== The Launch File Explained ====
Now, let's break the launch xml down.
 <pre class="prettyprint linenums">
     <launch>
</pre>

Here we start the launch file with the launch tag, so that the file is identified as a launch file.
<pre class="prettyprint linenums:3">
  <group ns="turtlesim1">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>

  <group ns="turtlesim2">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>
</pre>

Here we start two groups with a namespace tag of turtlesim1 and turtlesim2 with a turtlesim node with a name of sim. This allows us to start two simulators without having name conflicts.

<pre class="prettyprint linenums:11">
<node pkg="turtlesim" name="mimic" type="mimic">
    <remap from="input" to="turtlesim1/turtle1"/>
    <remap from="output" to="turtlesim2/turtle1"/>
  </node>
</pre>  
Here we start the mimic node with the topics input and output renamed to turtlesim1 and turtlesim2. This renaming will cause turtlesim2 to mimic turtlesim1.

<pre class="prettyprint linenums:16">
</launch>
</pre>

This closes the xml tag for the launch file.


==== Additional Renaming Methods ====
In addition to using "group ns" as described above, there are two other methods for renaming nodes
<pre class="prettyprint linenums:11">
<remap from="/sim" to="george"/>
<node pkg="turtlesim" name="sim" type="turtlesim_node"/>
</pre>
<pre class="prettyprint linenums:11">
<node pkg="turtlesim" name="sim" type="turtlesim_node" ns="george"/>
</pre>

==== roslaunching ====
Now let's `roslaunch` the launch file:

 roslaunch beginner_tutorials turtlemimic.launch

Two turtlesims will start and in a '''new terminal''' send the `rostopic` command:

  rostopic pub /turtlesim1/turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'

You will see the two turtlesims start moving even though the publish command is only being sent to turtlesim1.

[[File:mimic.png]]

'''NOTE:''' Don't worry too much about understanding the 'rostopic pub' command, we will return to it later. Basically, this usage of the command continuously publishes commands to turtlesim which tells the turtle to travel in a circle.

We can also use [http://wiki.ros.org/rqt_graph rqt_graph] to better understand what our launch file did. Run [http://wiki.ros.org/rqt rqt]'s main window and select [http://wiki.ros.org/rqt_graph rqt_graph]:

 rqt

Or simply:

 rqt_graph

[[File:mimiclaunch.jpg]]


In one command from the command line we were able to start 4 nodes! This is obviously a much cleaner and more efficient approach to starting multiple nodes than starting them individually.


'''Previous:''' [[The ROS Filesystem]] / '''Next:''' [[Assignment 2: Creating Your Own Launch File]]

'''Return to ROS Tutorials Main Page:''' [[ROS Tutorials]]
