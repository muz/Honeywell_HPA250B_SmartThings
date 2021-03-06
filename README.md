Integration of Honeywell HPA250B into smartthings using Raspberry Pi and BluePi

<h2>Hardware needed:</h2>
<p>
<li> Honeywell HPA250B (Bluetooth enabled)</li>
<li> Raspberry Pi 3 rev 2 </li>
</p>
<p></p>
<p></p>
<h2>Raspberry configuration:</h2>
<p>
<li>Bluez (http://www.elinux.org/RPi_Bluetooth_LE)</li>
<li>BluePy (https://github.com/IanHarvey/bluepy)</li>
<li>requests (http://raspberrypi-aa.github.io/session4/requests.html)</li>
<li>netifaces (python -m pip install netifaces)  
<li>Assign static IP address. Port 12345 will be used between Raspberry and SmartThings Hub.</li>
</p>

<li>Put in /home/pi the python script ssdp_server.py (this file uses wlan0 as interface. You can change the code to use eth0 or other)</li>
<li>Create a folder "lib" in /home/pi</li>
<li>Put in /home/pi/lib the 2 files ssdp.py and upnp_http_server.py.</li>
<li>This is mandatory the 2 files are in a lib folder and the lib folder at the same location as ssdp_server.py </li>

<p>Command line for py script on Raspberry Pi: <b>sudo python hpa250b_agent.py [mac address] [port] [inet] [hci port #] &</b>
</p>
<p> Example: sudo python hpa250b_agent.py fe:ed:fa:ce:da:ad 12345 wlan0 1 &
</p>
<li>SSDP UPnP Server: <b>python ssdp_server_hpa250b.py &</b></li>
<h2>Configuration SmartThings:</h2>
<p>Install the Honeywell HPA250B UPnP Service Manager from the app Smartapps -> myApps after you published it for yourself</p>
<p>Search for the Raspberry, select it, save. The Device will be created automatically.</p>
<p></p>
<h2> Pollster</h2>
<p>Configure Pollster to frequently poll the HPA250B notifications in case you plan to use the device panel. I will work later on pushing the notification to SmartThings Handler. For now, the changes done on the device are either refreshed when a command is sent from the SmartThings app or when pollster polls the refresh. I use 1 minute pollster refresh on my side for now".

Hope you like it!
[![Support via PayPal](https://cdn.rawgit.com/twolfson/paypal-github-button/1.0.0/dist/button.svg)](https://www.paypal.me/philippeportesppo)

<h2> General architecture </h2>
<img src=https://github.com/philippeportesppo/Honeywell_HPA250B_SmartThings/blob/master/HPA250B.png>


