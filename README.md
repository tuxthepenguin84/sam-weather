# sam-weather
Weather plugin for Nagios that lets you check temperature, humidity, wind, rain fall, dewpoint, heat index, windchill, pressure, solar radiation, and UV index. This also reports performance data to Nagios for graphing. The plugin uses data from Weather Underground. If you have any questions, issues, or suggestions please do not hesitate to email me (samueldockery@gmail.com).

Sam Weather Ver. 2.0 
Author: Sam Dockery 
Email: samueldockery@gmail.com 

What's New with 2.0: 
1. Warning & Critical levels 
2. Added Pressure, Solar Radiation, & UV Index to parameters 

To find your STATIONID, go to http://www.wunderground.com/wundermap/ and search for a station near your location. 
Click on the station and you will see an alphanumeric Station ID. 
Software requirements are LYNX, GREP, and CUT. These should be availble through your package manager (yum, apt-get, etc.) 
Should work with Nagios, NagiosXI, and any Unix/Linux system as long as the software requirements are met. 
Each weather parameter includes performance data (so long as the output isn't a string). 

Troubleshooting Tips: 
1. Make sure the plugin has the correct permissions on the file. chown nagios:nagios samweather or chown apache:apache samweather 
2. Make sure you have the correct stationid, put it in all caps to be safe. Example: KALAUBUR4 
3. Only use 1 weather parameter at a time. Might add the capability in the future for more parameters at a time. 
4. If the plugin returns no data, either the weather underground site is unavailable or you have an incorrect stationid. 
5. If you still have issues, verify you can open the stationid on the weather underground site. Replace your stationid with the one at the end of 
Example: http://api.wunderground.com/weatherstation/WXCurrentObXML.asp?ID=KALAUBUR4 
6. Verify you have LYNX, GREP, and CUT installed. 

Usage: 
./samweather stationid weatherparameter warn crit 

Example: 
./samweather KALAUBUR4 temp 80 90 

Output: 
Temperature: 79.5 F (26.4 C) | 'Temp F'=79.5 'Temp C'=26.4 

Weather Parameters are: 
temp - Temperature in F & C 
heatindex - Heat Index in F & C 
humidity - Relative Humidity 
wind - Wind direction, degrees, and MPH 
precip - Precipitation today in Inches & Cent. 
press - Pressure in MB & In 
dewpoint - Dewpoint in F & C 
windchill - Windchill in F & C 
solar - Solar Radiation in watts/m^2 
uv - UV Index 

Huge thanks to Daniele at www.kernel-panic.it for assiting in the development of this plugin. And a thanks to weyoon on the Nagios Exchange for the suggestion of adding Pressure stats to the plugin.
