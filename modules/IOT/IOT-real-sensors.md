
Current options available include:

-	Texas Instruments SensorTag
	http://www.ti.com/ww/en/wireless_connectivity/sensortag2015/appsAndPartners.html#main
	
	![](/media/93774f020b17d40f4abb647dc81b5e8c.png)
	
	This device requires a bluetooth (BLE) device to act as a gateway, as it has no built-in internet connectivity.
	
	Texas Instruments provides suitable apps in both the 
	[Apple App Store](https://itunes.apple.com/gb/app/ti-sensortag/id552918064?mt=8) and 
	[Google Play store for Android](https://play.google.com/store/apps/details?id=com.ti.ble.sensortag&hl=en_GB)

-	ARM mbed IOT Starter Kit
	https://developer.mbed.org/platforms/IBMEthernetKit
	
	![](/media/ed797e7eb4b1673cea96a84c07334d56.png)
	
	This device has built-in ethernet support for connecting to the internet - you will need an ethernet cable,
	and suitably-configured network port to be able to use this kit.
  
-	Other kits and guides on how to connect them to the Quickstart service are
	available at the Recipes page:
	https://developer.ibm.com/recipes

If ethernet access to the internet is available, we will use the ARM kit as an example.

Following the "Quickstart" guide supplied in the kit, connect the device to the 
internet, and identify its Device Id from the onboard display.

In the Node-RED editor screen, add another `IBM IOT App in` node, update the 
config to connect to the new Device Id, and link into the existing flow:

![](/media/65f108b661c7567007308b122bd32d9e.png)

Because this device generates a temperature value and tags it with the same 
field name (`temp`) as the IOTSensor simulator, its data can be integrated
 directly to the current application.

Update the dashboard webpage to use the new sensor Device Id, and your application
 will now display the data feed from the actual device.
