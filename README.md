# ESP32 Water Level Monitoring with and LineNotify
<h2>Description</h2>
This is an Arduino program that reads values from a HC-SR04 ultrasonic sensor and sends them to the Line messaging app. The program is intended to be run on an ESP32 board. The program also has an autoconnect WiFi feature, so it can connect to a WiFi network automatically without the need for manual setup.<br>
<b>2019</b>
<h2>Prerequisites</h2>

- ESP32 board<br>
- HC-SR04 ultrasonic sensor<br>
- WiFi network with internet access<br>
- Line developer account<br>
- Line Notify API token<br>
<h2>Installation and Usage</h2>
1. Install the required libraries: ESP8266WiFi, WiFiClientSecureAxTLS, DNSServer, ESP8266WebServer, WiFiManager, and TimeLib.<br>
2. Connect the HC-SR04 sensor to the ESP32 board.<br>
3. Replace the <b>'LINE_TOKEN'</b> value with your Line Notify API token.<br>
4. Compile and upload the code to the ESP32 board.<br>
5. Open the Serial Monitor to see the program output.<br>
6. The program will automatically connect to a WiFi network if available.<br>
7. Once connected to the network, the program will get the time from an NTP server.<br>
8. The program will then continuously read the distance from the HC-SR04 sensor and send a notification to your Line account every 15 minutes at :15, :30, :45, and :00 of every hour.<br>
9. To stop the program, press the reset button on the ESP32 board.<br>
<h2>Code Explanation</h2>

- <b>'echoPin'</b> and <b>'trigPin'</b> are the pins used for the HC-SR04 sensor.<br>
- <b>'timezone'</b> is the timezone used to set the correct time.<br>
- <b>'dst'</b> is used to set the daylight saving time.<br>
- <b>'count'</b>, <b>'savehour'</b>, and <b>'savemin'</b> are used to keep track of the time.<br>
- <b>'ckh'</b> and <b>'ckm'</b> are used to check the current hour and minute.<br>
- <b>'A'</b> is a flag that is used to check if a notification has already been sent.<br>
- <b>'message1'</b>, <b>'message2'</b>, <b>'message3'</b>, and <b>'message4'</b> are variables used to construct the message sent to Line.<br>
- <b>'humid'</b> and <b>'temp'</b> are variables used to read the humidity and temperature from the BME280 sensor.<br>
- <b>'setup()'</b> initializes the program by setting the pin modes, starting the serial communication, and connecting to a WiFi network using the <b>'WiFiManager'</b> library.<br>
- <b>'loop()'</b> is the main program loop that continuously reads the time and distance from the HC-SR04 sensor. If the current time matches the scheduled time, the program sends a notification to Line.<br>
- <b>'Line_Notify()'</b> is a function that sends a notification to Line using the Line Notify API.<br>
<h2>Limitations</h2>

- The program is currently hard-coded to send notifications every 15 minutes. This can be changed by modifying the <b>'ckm'</b> variable.<br>
- The program uses the HC-SR04 sensor to measure distance, which has limitations in terms of accuracy and range.<br>
- The program may encounter issues with time synchronization if the NTP server is not reachable.<br>
<h2>License</h2>
This code is licensed under the MIT License. See the LICENSE file for details.
