# OOCSI websocket client

This OOCSI client allows access to OOCSI from HTML, iOS web views and Android web views via the websocket protocol. 

# How to use

First, include the JavaScript source (either as the [source library](https://github.com/iddi/oocsi-websocket/blob/master/dist/oocsi-web.js) or as the [minified library](https://github.com/iddi/oocsi-websocket/blob/master/dist/oocsi-web.min.js)) into the HTML page.

Then connect to an OOCSI server (which needs to be running a websocket adapter):

```javascript
OOCSI.connect("wss://_SERVER_ADDRESS_/ws");
```
 

You can send data to a channel or individual client (here: "John"): 

```javascript
// JSON data object with two items, position and color
var data = {'position' : 90, 'color': 255};

// send data object to client "John"
OOCSI.send("John", data);
```

You can subscribe to a channel with a handler to handle messages:

```javascript
OOCSI.subscribe("testchannel", function(msg) {
	// handle message on “test channel"
	var position = msg.data.position;
	var color = msg.data.color;
});
```
