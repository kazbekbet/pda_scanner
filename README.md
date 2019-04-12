# PDA Scanner
  
[![License][license-image]][license-url] 

A Flutter plugin 🛠 to scanning. Ready for Android 🚀

## Installation

Add this to your package's pubspec.yaml file:

```
dependencies:
 pda_scanner: ^0.1.0
```

## Usage example
```dart
static const scannerPlugin = const EventChannel('com.shinow.pda_scanner/plugin');
StreamSubscription _subscription;
var _code;

@override
void initState() {
super.initState();
/// 开启监听
if (_subscription == null) {
  _subscription = scannerPlugin
      .receiveBroadcastStream()
      .listen(_onEvent, onError: _onError);
}
}

@override
void dispose() {
    super.dispose();
    /// 取消监听
    if (_subscription != null) {
      _subscription.cancel();
  }
}

void _onEvent(Object event) {
    setState(() {
      _code = event;
      print("ChannelPage: $event");
    });
}

void _onError(Object error) {
    setState(() {
      _code = "扫描异常";
      print(error);
    });
}
```

## Contribute

We would ❤️ to see your contribution!

## License

Distributed under the MIT license. See ``LICENSE`` for more information.

## About

Created by Shusheng.

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-url]: LICENSE
