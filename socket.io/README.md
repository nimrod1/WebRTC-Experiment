#### WebRTC One-to-One video sharing using Socket.io / [Demo](https://webrtc-experiment.appspot.com/socket.io/)

This `WebRTC Experiment` is using [socket.io over node.js](https://github.com/muaz-khan/WebRTC-Experiment/tree/master/socketio-over-nodejs) for signalig.

----

#### Use your own socket.io implementation!

If you want to install/use your own `socket.io` implementation; [visit this link](https://github.com/muaz-khan/WebRTC-Experiment/tree/master/socketio-over-nodejs).

```javascript
connection.openSignalingChannel = function(config) {
   var URL = 'http://domain.com:8888/';
   var channel = config.channel || this.channel || 'default-channel';
   var sender = Math.round(Math.random() * 60535) + 5000;
   
   io.connect(URL).emit('new-channel', {
      channel: channel,
      sender : sender
   });
   
   var socket = io.connect(URL + channel);
   socket.channel = channel;
   
   socket.on('connect', function () {
      if (config.callback) config.callback(socket);
   });
   
   socket.send = function (message) {
        socket.emit('message', {
            sender: sender,
            data  : message
        });
    };
   
   socket.on('message', config.onmessage);
};
```

----

#### Browser Support

This [One-to-one WebRTC video chat using socket.io](https://webrtc-experiment.appspot.com/socket.io/) experiment works fine on following web-browsers:

| Browser        | Support           |
| ------------- |:-------------:|
| Firefox | [Stable](http://www.mozilla.org/en-US/firefox/new/) / [Aurora](http://www.mozilla.org/en-US/firefox/aurora/) / [Nightly](http://nightly.mozilla.org/) |
| Google Chrome | [Stable](https://www.google.com/intl/en_uk/chrome/browser/) / [Canary](https://www.google.com/intl/en/chrome/browser/canary.html) / [Beta](https://www.google.com/intl/en/chrome/browser/beta.html) / [Dev](https://www.google.com/intl/en/chrome/browser/index.html?extra=devchannel#eula) |
| Internet Explorer / IE | [Chrome Frame](http://www.google.com/chromeframe) |
| Android | Chrome Beta |

----

#### License

[WebRTC one-to-one video sharing using socket.io](https://webrtc-experiment.appspot.com/socket.io/) is released under [MIT licence](https://webrtc-experiment.appspot.com/licence/) . Copyright (c) 2013 [Muaz Khan](https://plus.google.com/100325991024054712503).
