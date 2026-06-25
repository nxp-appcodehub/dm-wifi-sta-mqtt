# WiFi_Cli_STA_MQTT

## Overview
The WiFi_Cli_STA_MQTT demo application demonstrates Wi-Fi station's connection to an access point while facilitating asynchronous data exchange between the local device and a remote broker via the MQTT protocol.

## Prepare the Demo
1.  Connect a micro USB cable between the PC host and the CMSIS DAP USB port on the board
2.  Open a serial terminal with the following settings:
    - 115200 baud rate
    - 8 data bits
    - No parity
    - One stop bit
    - No flow control
3.  Connect the Wi-Fi module. Refer to readme_modules.md and the [Supported boards](#supported-boards) section.
4.  Download the program to the target board.
5.  Either press the reset button on your board or launch the debugger in your IDE to begin running the demo.


## Running the demo
1.  Expected startup output:

        ========================================
        wifi cli demo
        ========================================
        Initialize WLAN Driver
        ========================================
        Starting AP Connect DEMO
        [i] Initializing Wi-Fi connection... 
        STA MAC Address: 9C:50:D1:45:0F:5D 
        FW DOWNLOAD CMPLETE
        [i] Successfully initialized Wi-Fi module
        wlan_add_network
        Status is 0
        Connecting as client to ssid: Simple with password 12345678
    
2. Ensure Wi-Fi Access Point (or mobile hotspot) is active with the shown wi-fi credentials:

3. The EVK board will automatically scan and connect to the AP using the credentials. Monitor the serial terminal to verify the Wi-Fi connection.

4. Confirm the following sequence appears in the console, indicating a successful connection:
 
    	[i] Connected to Wi-Fi
    	ssid: Simple
    	[!]passphrase: 12345678
    	Now join that network on your device and connect to this IP: 172.20.10.3
    	Resolving "broker.hivemq.com"...
    	Connecting to MQTT broker at 52.59.10.189 
    	mqtt_client_connect result - 0
        MQTT client "nxp_172171d7615548f0" connected.
    	Starting MQTT subscriptions...
    	Subscribing to the topic "lwip_topic/1" with QoS 0...
    	Subscribing to the topic "lwip_other/1" with QoS 1...
    	Subscribed to the topic "lwip_topic/1".
    	Going to publish to the topic "lwip_topic/100"...
    	Subscribed to the topic "lwip_other/1".
    	Published to the topic "lwip_topic/100".
    	Going to publish to the topic "lwip_topic/100"...
    	Published to the topic "lwip_topic/100".
    	Going to publish to the topic "lwip_topic/100"...

5. The board automatically subscribe for two specific topics: 1. The topic "lwip_topic/1" with QoS 0 and 2. The topic "lwip_other/1" with QoS 1.

6. Also board start to publish the messages on topic "lwip_topic/100" 

7. To verify the data exchange, use an MQTT client (like MQTT Explorer or HiveMQ) configured with:

Host: broker.hivemq.com

Port: 1883

Action 1 (Receive): Subscribe to "lwip_topic/100"  to see the board's messages.

Action 2 (Send): Publish a message to "lwip_topic/1" with QoS 0 and the topic "lwip_other/1" with QoS 1 and check the board's serial terminal to confirm receipt.


## Supported Boards
- [EVKB-IMXRT1050](../../_boards/evkbimxrt1050/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1060-EVKB](../../_boards/evkbmimxrt1060/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1170-EVKB](../../_boards/evkbmimxrt1170/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1060-EVKC](../../_boards/evkcmimxrt1060/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1040-EVK](../../_boards/evkmimxrt1040/wifi_examples/common/wifi_examples_readme.md)
- [EVK-MIMXRT1064](../../_boards/evkmimxrt1064/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1160-EVK](../../_boards/evkmimxrt1160/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT1180-EVK](../../_boards/evkmimxrt1180/wifi_examples/common/wifi_examples_readme.md)
- [EVK-MIMXRT595](../../_boards/evkmimxrt595/wifi_examples/common/wifi_examples_readme.md)
- [EVK-MIMXRT685](../../_boards/evkmimxrt685/wifi_examples/common/wifi_examples_readme.md)
- [FRDM-RW612](../../_boards/frdmrw612/wifi_examples/common/wifi_examples_readme.md)
- [MCX-N5XX-EVK](../../_boards/mcxn5xxevk/wifi_examples/common/wifi_examples_readme.md)
- [MCX-N9XX-EVK](../../_boards/mcxn9xxevk/wifi_examples/common/wifi_examples_readme.md)
- [FRDM-MCXN947](../../_boards/frdmmcxn947/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT685-AUD-EVK](../../_boards/mimxrt685audevk/wifi_examples/common/wifi_examples_readme.md)
- [MIMXRT700-EVK](../../_boards/mimxrt700evk/wifi_examples/common/wifi_examples_readme.md)
- [RD-RW612-BGA](../../_boards/rdrw612bga/wifi_examples/common/wifi_examples_readme.md)
