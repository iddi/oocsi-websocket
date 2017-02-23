#OOCSI Websocket client#

OOCSI client for Websocket protocol; allows access to OOCSI from HTML, iOS webview, Android webview, etc.

#How to use#

First, include the JavaScript source (either as the [full library](oocsi-websocket/dist/oocsi-web.js) or as the [minified library](oocsi-websocket/dist/oocsi-web.js)) into the HTML page.

Then connect to an OOCSI server running a websockets adapter:

	OOCSI.connect("ws://_SERVER_ADDRESS_/");

You can send data to a channel or individual client (here: "John"): 

	// JSON data object with two items, position and color
	var data = {'position' : 90, 'color': 255};
    
	// send data object to client "John"
	OOCSI.send("John", data);

You can subscribe to a channel with a handler to handle messages:

	OOCSI.subscribe(“testchannel", function(msg) {
	// handle message on “test channel"
	var position = msg.data.position;
	var color = msg.data.color;
	});

