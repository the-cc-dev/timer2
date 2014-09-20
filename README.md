# timer2

timer2 is an evented timer.

## Installation

    $ npm install timer2

## Quick start

First you need to add a reference to timer2 to your application.

```javascript
var Timer = require('timer2');
```

Then you are able to create new timers by calling the `Timer` constructor with the desired timeout in milliseconds.

```javascript
var timer = new Timer(100);
```

The timer then periodically emits `tick` events. You can subscribe to these events using the usual `EventEmitter` functions, such as `on` and `once`.

```javascript
timer.on('tick', function () {
  // ...
});
```

Please remember that you need to unsubscribe from the `tick` event if you do not need the timer any longer. For that you can use the usual `EventEmitter` functions, such as `removeListener` and `removeAllListeners`.

### Creating immediate timers

By default, timers do not start immediately, but wait for the specified number of milliseconds before emitting the first `tick` event. If you need a timer that starts immediately, provide an `options` object to the constructor and set its `immediate` property to `true`.

```javascript
var timer = new Timer(100, {
  immediate: true
});
```

### Creating wobbling timers

Normally, the timer ticks at a constant rate. If you want to make ticking a little unreliable, you can specify a variation for the `timeout`. This means, e.g. if you specify a timeout of 2000 ms and a variation of 500 ms, you will get ticks between every 1500 ms and 2500 ms.

To enable wobbling, provide a `variation` property within the `options` object and set its value to the desired number of milliseconds.

```javascript
var timer = new Timer(2000, {
  variation: 500
});
```

### Stopping and restarting timers

You can stop a running timer at an arbitrary point in time. For that you need to call its `stop` function.

```javascript
timer.stop();
```

To restart a stopped timer call its `start` function accordingly.

```javascript
timer.start();
```

## Running the build

This module can be built using [Grunt](http://gruntjs.com/). Besides running the tests, this also analyses the code. To run Grunt, go to the folder where you have installed timer2 and run `grunt`. You need to have [grunt-cli](https://github.com/gruntjs/grunt-cli) installed.

    $ grunt

## License

The MIT License (MIT)
Copyright (c) 2013-2014 the native web.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
