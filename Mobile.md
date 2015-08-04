Go mobile subrepository adds support for mobile platforms (Android and iOS) and will provide tools to build mobile applications.

There are two strategies you can follow to include Go into your mobile stack:

- Writing all-Go native mobile applications.
- Writing SDK applications by generating bindings from a Go package and invoke them from Java (on Android) and Objective-C (on iOS).

This article will contain step-by-step guides to explain how to achieve
these strategies.

## Tooling

Go Mobile introduces a new tool, gomobile, to help you with the build
and the binding process. Go get gomobile and initialize it to install
the required toolchain.

On Mac OSX, you will need to have
[Xcode Command Line Tools](https://developer.apple.com/downloads/)
installed.

```
$ go get golang.org/x/mobile/cmd/gomobile
$ gomobile init # it might take a few minutes
```

(The following sections will help you how to use the gomobile tool.)

## Native applications

Native category includes applications entirely written in Go. Currently, the
[golang.org/x/mobile](https://godoc.org/golang.org/x/mobile)
contains only a small set of packages that focus on:

* App control and configuration
* OpenGL ES 2 bindings
* Asset management
* Event management
* Experimental packages include OpenAL bindings, audio, font, sprite and motion sensors

There are various example native applications under [golang.org/x/mobile/example](https://golang.org/x/mobile/example). We will build and deploy the basic example both to an Android and iOS device.

Grab the application.

```
$ go get -d golang.org/x/mobile/example/basic
```

### Building and deploying to Android

Run `gomobile build` to build an Android APK.

```
$ gomobile build -target=android golang.org/x/mobile/example/basic
```

Build command will build an APK named basic.apk.

If you have adb command installed on your machine, you can use `gomobile install` to build and push the APK to your mobile device.

```
$ gomobile install golang.org/x/mobile/example/basic
```

### Building and deploying to iOS
Run `gomobile build` to build the package as an iOS application.

Note: target=ios requires the host machine running Mac OS X.

```
$ gomobile build -target=ios golang.org/x/mobile/example/basic
```

The build command will build an application bundle, named basic.app. You can deploy application bundles to your iOS device by using the [ios-deploy](https://github.com/phonegap/ios-deploy) utility command line tool.

Use ios-deploy to push the application to your device.

```
$ ios-deploy -b basic.app
```

## SDK applications and generating bindings

In this category, we will show you how you can use a Go package in
your existing Android or iOS application.

The advantages to follow this strategy:

* You can reuse a Go package from a mobile app without making significant changes to your existing application.
* In cases where you want to share a partial common code base between your Android and iOS application, you can write the common functionality once in Go and glue them to the platform-specific code by invoking the Go package through bindings.

Current limitations are listed below.

* Only a subset of Go types are currently supported.
* Language bindings have a performance overhead.
* There are a few limitiations on how the exported APIs should look like due to the limitiations of the target language.

We will use the example package under [golang.org/x/mobile/example/bind/hello](https://golang.org/x/mobile/example/bind/hello) to generate bindings and invoke Greetings function from Java and Objective-C.

Grab the example by running the command below.

```
$ go get -d golang.org/x/mobile/example/bind
```

### Building and deploying to Android


If you are using Android Studio, you can use the Gradle plugin to automate this process.

1. Launch Android Studio.
2. File > Import Project... to import the reference project from $GOPATH/src/golang.org/x/mobile/example/bind/android.
3. Open hello/build.gradle to edit the absolute path to GOPATH and GO.
4. Build and deploy the application to the device.

If you are not using Android Studio, in order to work with bindings for Android, you need to have [Android SDK](https://developer.android.com/sdk/index.html#Other) installed and ANDROID_HOME environment variable set.

```
$ gomobile bind -target=android golang.org/x/mobile/example/bind/hello
```

The command above will generate an aar that is importable by your IDEs.

### Building an deploying to iOS

Note: You need a Mac OS X host machine and Xcode in order to continue.

```
$ cd $GOPATH/src/golang.org/x/mobile/example/bind
$ gomobile bind -target=ios golang.org/x/mobile/example/bind/hello
```

Gomobile bind will generate a framework bundle called `hello.framework`. Open the sample XCode project by running the command below.

```
$ open ios/bind.xcodeproj
```
Drag and drop the `hello.framework` bundle to the Xcode project. Your project layout should look like what's shown below.

![Xcode project layout with hello.framework](https://googledrive.com/host/0ByfSjdPVs9MZbkhjeUhMYzRTeEE/gowiki/gomobile-bind-ios.png)

Build and run it on the simulator or an actual device (Cmd+R). When the application launches, the label on the main view will be modified with the string returned from `GoHelloGreetings` which invokes the `Greetings` function from the hello package.
