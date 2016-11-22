
An SMS text message may be more convenient, accessible and immediately visible
for phone users that do not use their phone for emails.

Twilio offers a Bluemix microservice which can be used to send text messages.
*(Twilio also supports incoming text messages and can be configured to forward
those messages to an application URL, which can be implemented in a Bluemix
application).*

To get started, you will need a Twilio trial account (no charge). Open a new
browser (yes another one) and connect to <http://www.twilio.com>. This is a
multi-step process, but only needs to be done once to set up and configure the
account.

![](media/0e957eec318b925a67e38811c9041d0f.png)

Click on `GET STARTED`.

![](media/53d60753c13191a7d27d1f99dd965736.png)

Enter your contact details, and a password - Twilio enforces a *strong*
password.

You will then be prompted for a mobile phone number to verify your details --
make sure to select the correct country code prefix using the flag drop-down.

![](media/280e85237ee9697b771e9d7630d16a48.png)

Once you have entered a contact number and pressed `Get Started`, you will
receive a text message with 6-digit activation code - get ready to enter that in
the next verification form.

![](media/88f4a6971c5eb841ccec984955999ee9.png)

Once the verification code has been Submitted, you'll be taken to the account
administration panel.

For Twilio to send/receive text messages for you, it assigns you one of its
phone numbers -- click on `Get your Twilio number` to have this set for your
account

![](media/cdf373f2442506dbbe589f3db7c73333.png)

![](media/df02bed6bfefa217945d63dd1fe50339.png)

![](media/323b120080c8d6b77662ae795f1bb52c.png)

When you return to the administration panel, click on `Show API Credentials`.

![](media/e5d793fdb3515e041b9c9ebf5ac6b1b7.png)

You now have the 3 pieces of information needed to configure the Twilio service
in Node-RED -- the "SID", the token, and your number.

One final step needed for non-USA numbers; you will need to enable SMS services
for the countries you want to send to. This is set within the Geographic
Permissions section under Account management.

![](media/23e8d5e8254b9743dbaac46122b67ba7.png)

![](media/465bd29b84beb71657f3b0ade178c984.png)

![](media/812e0a5b28fb4e4a0682528ce1bc9156.png)

Here, we have filtered the list of countries for messaging to show `kingdom` and
checked the box beside the United Kingdom -- this will allow your Twilio node in
Node-RED to send to UK phone numbers.

Now, return to the Node-RED flow editor window, and add a Twilio node to the
flow:

![](media/1a32a85ca8ca63bd08dcd9ffc494f35b.png)

Double-click on the Twilio node to start the configuration:

![](media/d21f78da7fc25abcca3669cd0f17ce08.png)

And then click on the pencil icon to provide the Twilio details:

![](media/c5a1a095903dbbd75b96a1b2e5f5a0de.png)

Click `Add` and you'll be ready to send SMS messages!

![](media/bd18a6416f4e577df27ff8249ed53270.png)

You need to provide a phone number to which the SMS message will be sent -- use
the number you provide to Twilio for your account verification.

(Putting that number into the Name property of the Twilio node makes it easy to
see what's going on in the flow editor).

To prevent inadvertently sending a burst of SMS messages, we'll add a "rate
limiter".

Locate the `delay` node under Functions on the left side of the flow editor

![](media/8cc77f83755fa4b3fe07a90e59ac1331.png)

Click and drag this on the flow page near the Twilio node.

![](media/c5d600e8b3f81005f28183a925910dc1.png)

Double-click the Delay node and configure:

![](media/9b7705a3c4187d1d3f3afa38d03ee4a1.png)

![](media/5ce85a3dbb10da67f0808b9f3b2890b4.png)

Make sure to check the `drop intermediate messages`.

Now, by clicking (and holding) on the output from the `danger` node, drag a
connection to the input of the `limit 1 msg/m` node, and release.

![](media/97029161db06dbc2aa672df526c3a57f.png)

Link the `Limit` node output to the `Twilio` node input, and the flow is complete.

![](media/dfa2e0fb750e3073ae4cf425f976be8a.png)

As before, use the

![Deploy](media/NR-deploy-button.png)

button at the top of the flow editor to update the running application.

Now, when the temperature exceeds the danger level, an SMS message will be sent
to your designated phone number.
