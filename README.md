   
# ESP-Touch v2 and PushingBox API Example

## Description

This project is a simple example of the integration between [ESP-Touch v2 application](https://github.com/EspressifApp/EsptouchForAndroid/releases/tag/v2.0.0/esptouch-v2.0.0.apk) and the [PushingBox API](https://www.pushingbox.com/api.php).

## Configure the project

```
idf.py menuconfig
```

Set following parameters under Application Configuration:

* Set `GPIO reset pin` with the desire pin number that will be used to change the system to the Resting Parameters Behavior.

## Build and Flash

Build the project and flash it to the board, then run monitor tool to view serial output:

```
idf.py -p PORT flash monitor
```

(To exit the serial monitor, type ``Ctrl-]``.)

## Expected Behavior

### With `GPIO reset pin` set to LOW:

On the first execution of the program, it will be necessary to configure the Wifi credentials and the deviceID (required to use the PushingBox API) using the ESP-Touch v2 Application. 

After this initial configuration the program will immediately send a PushingBox notification to the provided deviceID scenario.

The following execution will try to use the save parameters and automatically connects to the Wifi and sends the notification. 

If it fails to connect to the Wifi or it fails to retrieve the saved parameters it will revert to the initial behavior.

### With `GPIO reset pin` set to HIGH:

If the `GPIO reset pin` is set to HIGH, the program will enter in "Resting Parameters Behavior", all the saved paramters will be deleted, and the program reverts to the initial behavior.