# sim_manager
Automatic PIN code input on a WAGO PFC 4G controller 

## Description

This script can be used on a WAGO PFC 4G controller (750-8217/xxx-xxx) when the end-user uses SIM card where the PIN code is always the same.
This will automate the PIN input, in order to avoid to do it in the WBM.

This script uses the USR LED to display the result.

The operation is as follows:

- The script is called when the controller starts. (orange USR LED)
- It waits for the modem to be initialized
- When the modem is initialized, it “grabs” the PIN code
- It checks the result, if it is OK, the LED turns solid green, otherwise (incorrect PIN code or other problem), the LED turns solid red.


## Installation
In the script sim_manager you must adapt the PIN code to the level of PIN="0000"
It must then be transferred via SFTP to the controller, in the /etc/init.d/ directory (via the root user)
```
chmod +x /etc/init.d/sim_manager
```
You must then enter the following command so that it is called at startup
```
ln -s /etc/init.d/sim_manager S99_sim_manager
```
