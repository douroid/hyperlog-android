# Android Logging Library

##Overview
A utility logger library for Android on top of standard Android `Log` class. This is a simple library that will allow Android apps or library to store log into database so that developer can pull the logs from the database as `File` or push to their server.

##Download
Download the latest version or grab via Gradle.

The library is available on `mavenCentral()` and `jcenter()`. In your module's `build.gradle`, add the following code snippet and run the gradle-sync.


```
dependencies {
    ...
    compile 'io.hypertrack:smart-scheduler:0.0.8'
    ...
}
```

##Initialize
* Inside `onCreate` of Application class or Launcher Activity. 
```
SmartLog.initialize(this);
SmartLog.setLogLevel(Log.VERBOSE);
```

##Usage
```
SmartLog.d(TAG,"Test");
```
 
##Get Logs in a File
```
File file = SmartLog.getDeviceLogsInFile(this);
```

##Push Logs to Server
SmartLog will push logs to server in compressed form using GZIP compression.
```
SmartLog.setURL("API URL");
SmartLog.pushLogs(this, new SmartLogCallback() {
            @Override
            public void onSuccess(@NonNull String response) {

            }

            @Override
            public void onError(@NonNull VolleyError errorResponse) {

            }
});
```

##Additional Methods
* Different types of log.
```
SmartLog.d(TAG,"debug");
SmartLog.i(TAG,"information");
SmartLog.e(TAG,"error");
SmartLog.v(TAG,"verbose");
SmartLog.w(TAG,"warning");
SmartLog.a(TAG,"assert");
SmartLog.exception(TAG,"exception",throwable);
```

* To check whether any device logs are available.
```
SmartLog.hasPendingDeviceLogs();
```

* Get the count of stored device logs.
```
SmartLog.logCount();
```

* Pass additional headers along with API call while pushing logs to server.
```
HashMap<String, String> additionalHeaders = new HashMap<>();
additionalHeaders.put("Authorization","Token");
SmartLog.pushLogs(this, additionalHeaders, smartLogCallback);
```



## Contribute
Please use the [issues tracker](https://github.com/hypertrack/smart-logging-android/issues) to raise bug reports and feature requests. We'd love to see your pull requests, so send them in!

## About HyperTrack
Developers use [HyperTrack](https://www.hypertrack.com) to build location features, not infrastructure. We reduce the complexity of building and operating location features to a few APIs that just work.
Check it out. [Sign up](https://dashboard.hypertrack.com/signup/) and start building! Join our [Slack community](http://slack.hypertrack.io) for instant responses. You can also email us at help@hypertrack.io

## License

```
MIT License

Copyright (c) 2016 HyperTrack

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```