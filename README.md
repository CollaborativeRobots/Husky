# # Husky

## [Getting](http://wiki.ros.org/husky_bringup/Tutorials/Install%20Husky%20Software%20%28Advanced%29) [Started](http://www.clearpathrobotics.com/assets/guides/husky/InstallHuskySoftware.html)

### Installing
1) Download the appropriate [Kinetic Husky ISO](http://packages.clearpathrobotics.com/stable/images/latest/kinetic-husky/) image for your platform (32 bit - i386, 64 bit - amd64).

2) Setup an install USB

3) Connect your robot PC to wired internet access, a keyboard, and a monitor. Make sure that the PC is connected to shore power, or the Husky battery is either fully charged.

**Warning**
> The next step wipe your robot’s hard drive, so make sure you have that image backed up on another system!

4) Boot your robot PC from the USB drive, and let installer work it’s magic.
5) The setup process will be automated, and may take a long time depending on the speed of your internet connection.
6) Once the setup process is complete, the PC will turn off. Please unplug the USB drive and turn the PC back on.
7) On first boot, the username will be administrator and the password will be clearpath.
8) Please follow the configuration instructions on the screen. If the computer reboots, wait for the PC to boot to the login screen, and re-enter the login credentials.
9) Once the computer configuration is complete, you may use passwd utility to change administrator account password.
10) To setup a factory-standard Husky robot, ensure all your peripherals are plugged in, and run the following command:
```
$ rosrun husky_bringup install
```
The install script will configure a husky-core upstart service, that will bring up the base Husky launchfiles on boot. The script will also detect any standard peripherals (IMU, GPS, etc.) you have installed, and add them the service.

## SPECIAL STEPS
At this point in our initial install we followed the instructions in [this](http://wiki.ros.org/husky_bringup/Tutorials/Install%20Husky%20Software%20%28Advanced%29) link at the advice of team fire fighting. It is unclear whether this was strictly necessary, but this is how we got it working.

## Testing base configuration

1) To test your configuration, start the background service with the following command:
```
$ sudo service husky-core start
```
    
2) The COMM light on your Husky should go from red to green. You can check that the service has started correctly by checking the logs:
```
$ sudo tail /var/log/upstart/husky-core.log -n 30
```
3) Your husky should now be accepting commands from your joystick. The service will automatically start each time you boot your Husky's PC. 


## [Diagnostics](http://www.clearpathrobotics.com/assets/guides/husky/InterfacingWithHusky.html)

To get diagnostic information on the husky, install rqt by running the [following](http://wiki.ros.org/rqt/UserGuide/Install/Groovy):

1) Standard packages (rqt's core library + common plugins) can be installed by: 
```
$ sudo apt-get install ros-%YOUR_ROS_DISTRO%-rqt ros-%YOUR_ROS_DISTRO%-rqt-common-plugins`
```
2) Additionally, you can also install rqt_robot_plugins that provide features to be used when interacting with robots:

```
$ sudo apt-get install ros-%YOUR_ROS_DISTRO%-rqt-robot-plugins
$ sudo apt-get install ros-%YOUR_ROS_DISTRO%-rqt-pr2-dashboard (only when you need PR2 dashboard feature) 
```

3) If you only want to install a specific rqt plugin (rqt_moveit for instance):
```
$ sudo apt-get install ros-%YOUR_ROS_DISTRO%-rqt-moveit
```

Once rqt is installed you can activate rqt by running:
```
$ rosrun rqt_runtime_monitor rqt_runtime_monitor
```
