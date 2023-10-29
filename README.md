# Node-Red-Telegram-Bot-with-Temperature-Logger-Part-2

![alt text](https://hackster.imgix.net/uploads/attachments/1638852/image_dJ7o6kMSos.png?auto=compress%2Cformat&w=740&h=555&fit=max)

Telegram is a popular messaging app that offers end-to-end encryption, cloud-based storage, and a variety of features for communication. One of these features is the ability to create and interact with bots, which are automated programs that can perform tasks or provide information. In this blog post, I will show you how to use Telegram bots to control your home automation system with Node-RED, a visual programming tool that allows you to connect and orchestrate devices, services, and APIs.
To follow this tutorial, you will need:

A Telegram account and a smartphone with the Telegram app installed.
A Node-RED instance running on a device that can access your home automation system. You can use a Raspberry Pi, a computer, or a cloud service. For more information on how to install and run Node-RED, see here.
The node-red-contrib-telegrambot node provides Telegram bot nodes for Node-RED. You can install it from the Node-RED palette manager or by running the following command in your Node-RED directory:

npm install node-red-contrib-telegrambot

A Telegram bot token is a unique identifier for your bot. You can create a bot and get its token by talking to the @BotFather bot on Telegram. For more details.
A chat ID is a unique identifier for the chat between you and your bot. You can get your chat ID by sending a message to your bot.

![alt text](https://hackster.imgix.net/uploads/attachments/1638841/image_xNmD9U9oBW.png?auto=compress%2Cformat&w=740&h=555&fit=max)

The basic idea is to use Node-RED to create a flow that receives messages from your Telegram bot, parses them to extract commands or queries, and then sends commands or responses back to your bot. The node-red-contrib-telegrambot node provides two main nodes for this purpose: the receiver node and the sender node.

The receiver node listens for messages from your bot and outputs a message object with the following properties:

msg.payload.chatId: The chat ID of the sender.
msg.payload.type: The type of the message, such as “message”, “photo”, “location”, etc.
msg.payload.content: The content of the message, such as a text string, a file ID, or an object with additional data.
The sender node takes a message object as input and sends it to your bot. The message object should have the following properties:

msg.payload.chatId: The chat ID of the recipient.
msg.payload.type: The type of the message, such as “message”, “photo”, “location”, etc.
msg.payload.content: The content of the message, such as a text string, a file ID, or an object with additional data.
You can use other nodes in between the receiver and sender nodes to process the messages and perform actions on your home automation system. For example, you can use a switch node to route messages based on their type or content, a function node to write custom logic in JavaScript, or an HTTP request node to call external APIs.

![alt text](https://hackster.imgix.net/uploads/attachments/1638844/image_7lLAKwyqYU.png?auto=compress%2Cformat&w=740&h=555&fit=max)

In the last article, we have seen how to trigger the sensor readings from Node-Red to Telegram, now let's see how to trigger and get the sensor data from Telegram Bot.

First, we need to use the telegram receiver node.

And configure the node with your bot credentials. Then add a debug block.

Next, just try to send some messages to your bot and look at the response in the debug console.

Now, you can see your texts are coming under payload.content. So, we are going to filter the content then based on the content we are going to trigger the actions.

Here are my complete blocks.

In this, I have tried to filter the contents as Green, Red, Blue, Off, and Env. Based on the contents we are going to trigger the neo pixels with certain colors.

Finally, just deploy the flow, open the telegram bot, and test out the connections.

In this blog post, I showed you how to use Telegram bots to control your home automation system with Node-RED. You can use this method to create your own custom interface for your smart home devices and services. You can also extend the functionality of your bot by adding more nodes and logic to your flow. For example, you can use the command node to create custom commands with parameters, the callback query node to handle inline buttons, or the answer inline query node to provide suggestions. You can also use other nodes from the node-red-contrib-telegrambot package or other Node-RED packages to integrate with more Telegram features or other platforms.

I hope you enjoyed this tutorial and learned something new. If you have any questions or feedback, please leave a comment below. Happy coding!

![alt text](https://hackster.imgix.net/uploads/attachments/1518136/8_tJuwoRM3dI.JPG?auto=compress%2Cformat&w=740&h=555&fit=max)

You must check out [PCBWAY](https://www.pcbway.com/) for ordering PCBs online for cheap!

You get 10 good-quality PCBs manufactured and shipped to your doorstep for cheap. You will also get a discount on shipping on your first order. Upload your Gerber files onto PCBWAY to get them manufactured with good quality and quick turnaround time. [PCBWay](https://www.pcbway.com/) now could provide a complete product solution, from design to enclosure production. Check out their online Gerber viewer function. With reward points, you can get free stuff from their gift shop.Also, check out this useful blog on PCBWay Plugin for KiCad from [here](https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html). Using this plugin, you can directly order PCBs in just one click after completing your design in KiCad.
