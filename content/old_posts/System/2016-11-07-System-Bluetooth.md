---
title: "Bluetooth Stack (BlueZ)"
header:
  image: images/main_network1.jpg
  teaser: images/network.jpg
  caption: "Photo credit: [**pixabay**](https://pixabay.com)"
tag:
  - Bluetooth
  - BT
  - Bluetooth-Stack
categories:
  - System
---

{% include toc %}

# Mode

- **Bluetooth BR/EDR (Basic Rate / Enhanced Data Rate)**: In short, it supports small coverage and dedicates continuous connections.  

- **Bluetooth LE (Low Energy)**: Supports longer coverage than Bluetooth BR/EDR and it is idel for sending data for short amount of time such as **IoT (Internet of Things) Environment**. Moreover,     

- **Dual-Mode**: Supports both of two modes.

![Bluetooth Mode](/images/bluetooth/bluetooth1.png)


Various version of Bluetooth Stack with available protocols

![Various Version of Bluetooth Stack](/images/bluetooth/various_bt_stack.jpg)


## BlueZ

It is an official Linux Bluetooth stack. It provides support for core Bluetooth layers and protocols. This consists of followings:

- HCI Core
- HCI UART, USB and Virtual HCI device drivers
- L2CAP module
- Configuration and testing utilities

Required pakcages:

- Bluez-Firmware
- Bluez
- Bluez-dev



![BlueZ Overview](/images/bluetooth/BlueZ.png)

<br>

USB:

	CONFIG_USB_HID
	CONFIG_USB_SUPPORT
	CONFIG_USB_ARCH_HAS_HCD
	CONFIG_USB_ARCH_HAS_OHCI
	CONFIG_USB_ARCH_HAS_EHCI
	CONFIG_USB
	CONFIG_USB_DEBUG  (for debugging purposes)
	CONFIG_USB_DEVICE_CLASS
	CONFIG_USB_EHCI_HCD
	CONFIG_USB_OHCI_HCD
	CONFIG_USB_OHCI_LITTLE_ENDIAN
	CONFIG_USB_SERIAL (for STLC2500 device)
	CONFIG_USB_SERIAL_PL2303 (for STLC2500 device)

BT:

	CONFIG_BT
 	CONFIG_BT_L2CAP
 	CONFIG_BT_SCO
 	CONFIG_BT_RFCOMM
 	CONFIG_BT_RFCOMM_TTY
 	CONFIG_BT_BNEP
 	CONFIG_BT_BNEP_MC_FILTER
 	CONFIG_BT_BNEP_PROTO_FILTER
 	CONFIG_BT_HIDP
 	CONFIG_BT_HCIUSB
 	CONFIG_BT_HCIUSB_SCO
 	CONFIG_BT_HCIUART
 	CONFIG_BT_HCIUART_H4
 	CONFIG_BT_HCIUART_BCSP

![Bluetooth Driver](/images/bluetooth/bt_driver.jpg)

- **bluetooth.ko**: contains core infrastructure of BlueZ. It exports sockets of the Bluetooth family  AF_BLUETOOTH. All BlueZ modules utilise its services.

- **hci_uart.ko & hci_usb.ko**: Correspond to BlueZ Bluetooth HCI implementation (Those HCI packets are transported over UART or USB).

- **l2cap.ko**: Relates to L2CAP layer of Bluetooth, which is responsible for segmentation, reassembly and protocol multiplexing.

- **bnep.ko**: By this, TCP/IP applications can run over Bluetooth. This emulates an Ethernet port over the L2CAP layer. The kernel thread named kbnepd is responsible for BNEP connections.

- **rfcomm.ko**: Responsible for running serial port applications like the terminal. This emulates serial ports over the L2CAP layer. The kernel thread named krfcommd is responsible for RFCOMM connections.

- **hidp.ko**: implements the HID (human interface device) layer. The user mode daemon hidd allows BlueZ to handle input devices like Bluetooth mice.

- **sco.ko**: implements the synchronous connection oriented (SCO) layer to handle audio. SCO connections do not specify a channel to connect to a remote host; only the host address is specified.

## Bluetooth Host

Part of the stack and from the stack, the **features** of the following are:

**L2CAP(Logical Link Control and Adaptation Protocol)**:

- The capability to multiplex data between different higher layer protocols; hence, various protocols like RFCOM, SDP, etc, can operate over it
- Segmentation and reassembly
- Quality of service
- It supports a group abstraction, enabling implementation for mapping a group on to a piconet

<br>

**RFCOMM (Radio Frequency Communication)**

- A serial port emulation protocol situated over the L2CAP layer. It emulates RS-232 control and data signals over the Bluetooth baseband.

- Roughly the same service and reliability guarantees as TCP. Unlike to TCP, which provides 65,535 ports, RFCOMM allows only 30.

**SDP (Service Discovery Protocol)**

- Required by all Bluetooth applications, Devices are discovered by this, and each service is identified by a universally unique identifier (UUID).

## Bluetooth Profile

- **GAP (generic access profile)**: requirements for detecting and establishing a connection to a Bluetooth device. It is a core profile that is available by default.
- **GOEP (generic object exchange profile)**: This defines the requirement of OBEX, a communication protocol used to exchange binary objects between devices while using minimal resources and usage models.
- **HSP (headset profile)**: This defines the procedure that supports the interoperability between **a headset and a mobile device** that the headset controls through AT commands, and depends upon the serial port profile.
- **SPP (serial port profile)**: This defines the requirements for virtual serial port connections over the RFCOMM

## Reference
[1] Bluetooth in *wikipedia* [http://en.wikipedia.org/wiki/Bluetooth](http://en.wikipedia.org/wiki/Bluetooth)<br>
[2] Bluetooth stack in *wikipedia* [http://en.wikipedia.org/wiki/List_of_Bluetooth_protocols](http://en.wikipedia.org/wiki/List_of_Bluetooth_protocols)<br>
[3] The basic of Bluetooth [http://opensourceforu.com/2015/06/linux-without-wires-the-basics-of-bluetooth/](http://opensourceforu.com/2015/06/linux-without-wires-the-basics-of-bluetooth/)
[4] Bluetooth profiles [http://www.eetimes.com/document.asp?doc_id=1275960](http://www.eetimes.com/document.asp?doc_id=1275960)
[5] How to Run BlueZ [http://www.stlinux.com/kernel/bluetooth/how-to-run-BlueZ](http://www.stlinux.com/kernel/bluetooth/how-to-run-BlueZ)<br>
[6] Bluetooth Programming [http://people.csail.mit.edu/albert/bluez-intro/c404.html#bzi-choosing](http://people.csail.mit.edu/albert/bluez-intro/c404.html#bzi-choosing)<br>
[7] Simple Explanation of bluetooth protocol [http://www.drdobbs.com/mobile/using-bluetooth/232500828?pgno=1](http://www.drdobbs.com/mobile/using-bluetooth/232500828?pgno=1)<br>



## Bluetooth Issue
jessie bluetooth bluez.error.notavailable

https://fixmynix.com/bluetooth-in-linux-with-bluez-and-hcitool/
