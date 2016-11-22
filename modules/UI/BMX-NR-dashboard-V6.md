Return to the Node-RED flow editor, and locate the `Manage Palette` menu item:

![](/media/78057b55d74204fed32b0c6d4c859556.png)

Select `Manage Palette`, and form will open on the left side of the editor.
Select the `Install` tab, and enter `red-dashboard` in the search field:

![](/media/22d17f85c61f2f9634a285a42e6a8771.png)

Click the

![](/media/a683b6070886c4b9ad4e0104773a2d42.png)

button, wait for the nodes to be added to the editor, and then click

![](/media/7542fcffec22a68597f8ead40f55e93a.png)

.

Refresh your page, and the new dashboard nodes will appear at the bottom of the
list on the left:

![](/media/441103f6b15dbae61ec8016903511821.png)

As before, import the following flow definition into Node-RED,

![Sample dashboard visualisation for Node-Red](/media/text/example-nodered-dashboard-1.txt)

Connect the `temp` function node to the function node of the added flow.

![](/media/23907e937a7e6333a4b6a3372592d8bc.png)

Open the `chart` node and configure defaults settings for the dashboard group to
create the basic webpage that hosts the chart. Once set, click

![](/media/81b047c6bebb0a64beeef3ba38bc6d7a.png)

This will stream all the events through to the charting node, dynamically
updating the running averages, maximum and minimum values. The summary data is
then sent to the chart at the rate of 10 per minute.

On the right-hand side of the editor, look for the `dashboard` tab, select this
and then launch the new chart:

![Create dashboard](/media/NR-dashboard-create.png)
![View chart](/media/NR-dashboard-chart.png) 
