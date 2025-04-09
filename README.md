# Logitech  MX Master 3S - Input Switcher
Switch inputs with hidapitester (Windows &amp; Linux) and Solaar (Linux)

> inspired by the repository **[input-switcher](https://github.com/marcelhoffs/input-switcher/tree/master)**


## 1 - Introduction

The scripts provided in this repository allow me to toggle the mouse with a command. This repository contains scripts for Windows and Linux. You can use this repository to create your own specific setup.

## 2 - Windows

The **windows** folder contains the following files:

- hidapitester.exe
- switch1.bat
- switch3.bat

### 2.1 - Windows key binding

On Windows, use the PowerToys keyboard manager to define a shortcut that runs the bash script.

![Windows](/images/windows.png)

## 3 - Linux

The **linux** folder contains the following files:

- config.yaml
- rules.yaml
- hidapitester
- switch1.sh
- switch2.sh

> config.yaml and rules.yaml are used by the solaar.

### 3.1 - Linux key binding

In Linux it depends on the desktop environment you use. In Debian you can do it via: **Settings > Keyboard > View and Customize Shortcuts > Custom Shortcuts**

![Debian](/images/debian.png)

### Extra tip on linux

* Install solaar to set dpi, check battery, switch hosts and use gestures.
* In my rules.yaml there are two gestures to change host.

## 4 - Modify the scripts

### Disclaimer

The scripts in the repository were written to use the bluetooth connection, if you want to use the dongle you must have the correct **RCVR_VID** and **MSE_PID**.

### Example


```bash
hidapitester --vidpid ${RCVR_VID}:${MSE_PID} -q --open --length 20 --send-output 0x11,0x00,${MSE_ID},0x1e,${DST_CH},0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00
```

> Use hidapitester --list-detail to obtain both the vendorID and productID


#### My variables

| Variable    |       Value      |    Description            |
| ----------- |------------------|---------------------------|
|  RCVR_VID   |    046D          | Referring to vendorId     |
|  MSE_ID     |    0x0A          | Referring to mx master 3s |
|  DST_CH     | 0x00, 0x01, 0x03 | Destination channel       |
