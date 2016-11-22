We can now add email to the flow in order to send events for critical `danger`
level temperature alerts for attention and actions required.

**\*\*NOTE\*\*** - *although the following example uses the Gmail service, this
is no longer supported without making changes to the security settings on the
gmail account; if using the email node, avoid the use of gmail.com* **\*\* NOTE
\*\***

1.  In the Node-RED flow editor, scroll down thru the node selections on the
	left panel to the category for Social, select the `e-mail output` (as shown
	below, icon on the right of the node) and drag and drop it onto the flow to
	the right of the `danger` temperature decision node.

1.  Create a connector from the output of the `danger` temperature decision node
	to the input of the email node.

	![](media/7eb742442a7f7e3a6b30bdd8b5d1f9df.png)

1.  Double-click the new output node and enter configuration settings for your
	e-mail account you'd like to use to send the email from the flow -- any email
	service provider can be used, so just enter the destination recipient email
	address, email server, (optional) port, userid, and password for the email
	account to be used to send the notification:

	![](media/5a1409f92c1ca23c95a46ff0136e9d5c.png)

	Content of the e-mail will be set from the msg.payload property, with a
	subject line of msg.topic:

1.	Click **OK**, then click **Deploy** to redeploy the flow

Use the sensor device simulator to generate sensor events for temperature
reading above the danger level of 40 degrees -- alerts should now be sent to the
configured e-mail address.
