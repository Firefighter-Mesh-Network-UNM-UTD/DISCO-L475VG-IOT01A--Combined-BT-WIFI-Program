How to connect your Discovery board to WIFI, send data to it, and have it send data back

1. Create a GitHub account: https://github.com/

2. Create an Mbed account: https://os.mbed.com/docs/mbed-os/v6.15/quick-start/build-with-the-online-compiler.html

3. Add this board to your compiler: https://os.mbed.com/platforms/ST-Discovery-L475E-IOT01A/ 

4. Download Tera Term as your console emulator: https://tera-term.en.softonic.com/download

5. Connect the Discovery board to your computer. Open Tera Term. Start a new serial connection (the program should automatically select the port which your device is connected to). Open the "Setup" tab and choose "Serial port...". Make sure "Speed" is '115200', "Data" is '8 bit', and "Parity" is 'none'. Click "New Settings" to save your changes.

6. Download "TCP/UDP Test Tool" application on your phone: https://play.google.com/store/apps/details?id=jp.gr.java_conf.tcp_udp_testtool and "nRF Connect for Mobile": https://play.google.com/store/apps/details?id=no.nordicsemi.android.mcp

7. Start a "TCP Server" in the application and enter '8002' for your "Local Port" value.

8. Download this program's contents as a .zip file, then upload it to your compiler.

9. Your board should be selected in the compiler already; but if it isn't, click in the top right corner of the compiler to select a board. You should see the "Combined-Program" code in your "my programs" list; click on it. Open the file named "mbed-app.json". In that file, enter your WIFI SSID (network name) and your WIFI password in the proper fields (only replace the word "SSID" and "PASSWORD" in the "value" areas; leave any other characters).

10. Connect your phone to the same WIFI network you want to connect the device to. Get your phone's IP address (this should have four parts to it; each part separated by a period). In the "mbed-app.json" file, replace each "server-ip-x" value with the values as they appear in your phone's IP address (there are four "server-ip-x" areas and four parts to your phone's IP address).

11. Once you have entered all of that data, save the file, then click "compile" to have the code downloaded as a binary file. Drop the binary file into your Discovery board's drive. The board will automatically run the program. In Tera Term, you should see the server connection being made successfully.

12. Open the nRF Connect application on your phone. Open the "scanner" tab, then click "SCAN".

13. Find the device named "BT/WIFI Test" and click "CONNECT" to connect to it.

14. The BT/WIFI Test service has the UUID "0xA000" and includes the writable characteristic which has the UUID "0xA001". These two items may be labled as "unknown service" and "unknown characteristic", respectively. Click on the characteristic to reveal two arrows. Click on the "upward-facing arrow" with represents the "write" function. Change the data type to be an 8-bit (Byte) size. Enter any number between 0 and 255 (FF in hexidecimal), then click "SEND". This should send the chosen data to the board and the console should display the entered data value in hexidecimal format.

This was as far as we were able to get in this test program for our development boards. We established a bluetooth connection, a WIFI connection, and we sent data from an external bluetooth-enabled device to our development board over a bluetooth connection. The next step, which we were unable to achieve, is to send the received data over a WIFI connection to an external WIFI-enabled device.

15.
