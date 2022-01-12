# **Example 1: Sending ASCII-characters using a serial connection**

Make sure the following nodes are activated in Node-Red (the modbus-nodes must be deactivated):

![Example 1 Node-Red](graphics/nodered-example-1.png)

You can enable/disable nodes as follows: Double-Click on the node -> Change Enabled / Disabled -> Click Done -> Press Deploy to apply the changes

Open the Virtual Machine on your PC connected to the IOT2050. If not already done, open a terminal and install picocom (in this manual version 3.1 is used) with the following command:

    sudo apt-get install picocom

With the following command you can then check if the installation was successful:

    which picocom

The terminal should show the output on the image:

![Picocom success](graphics/check-picocom.png)

Remove the USB to serial converter from your PC and plug it in again. Make sure that the USB device now connects to the virtual machine. The following message appears in VMWare Workstation 16 Player:

![device detected](graphics/device-detected.png)

Start picocom with the following command:

    sudo picocom /dev/ttyUSB0 -c -b 115200

## **Sending from Virtual Machine to IOT2050**

Once picocom is ready, characters can be entered and then transmitted. The split input timeout is set to 2000ms by default. The output can then be viewed in Node-Red under "debug messages".

![sending serial from VM to IOT2050](graphics/sending-serial-vm-to-iot2050.png)

## **Sending from IOT2050 to Virtual Machine**

Make sure that picocom is enabled so that a signal can be received. Then, in node-red, the output can be triggered by clicking on the inject-node. The text "Example-123" is configured in the inject-node by default.

![sending serial from IOT2050 to VM](graphics/sending-serial-iot2050-to-vm.png)

You can exit the picocom-command by pressing CTRL+A and CTRL+Q.

## **Other documents**

- [**Application-Overview**](../README.md)
- [**Prepare the IOT2050**](README-Prepare-the-IOT2050.md)
- [**Example 2: Sending array-packages using modbus-protocol**](README-Example-2.md)
