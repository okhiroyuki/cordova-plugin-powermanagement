# PowerManagement

The PowerManagement plugin offers access to the devices power-management functionality.
It should be used for applications which keep running for a long time without any user interaction.

For details on power functionality see:

* Android: [PowerManager](http://developer.android.com/reference/android/os/PowerManager.html)

## Supported Platforms

* Android

## Installation

```sh
cordova plugin add @red-mobile/cordova-plugin-powermanagement
```

### uninstall

```sh
cordova plugin remove cordova-plugin-powermanagement
npm uninstall @red-mobile/cordova-plugin-powermanagement
```

## Usage

### window.powerManagement.acquire(successCallback, failureCallback)

Acquire a wakelock by calling this.

```js
	window.powerManagement.acquire(function() {
		console.log('Wakelock acquired');
	}, function() {
		console.log('Failed to acquire wakelock');
	});
```

### window.powerManagement.dim(successCallback, failureCallback)

This acquires a partial wakelock, allowing the screen to be dimmed.

```js
	window.powerManagement.dim(function() {
		console.log('Wakelock acquired');
	}, function() {
		console.log('Failed to acquire wakelock');
	});
```

This function is nort supported on windows platform and will invoke the successCallback.

### window.powerManagement.release(successCallback, failureCallback)

Release the wakelock. It's important to do this when you're finished with the wakelock, to avoid unnecessary battery drain.

```js
	window.powerManagement.release(function() {
		console.log('Wakelock released');
	}, function() {
		console.log('Failed to release wakelock');
	});
```

### window.powerManagement.setReleaseOnPause(enabled, successCallback, failureCallback)

By default, the plugin will automatically release a wakelock when your app is paused (e.g. when the screen is turned off, or the user switches to another app). It will reacquire the wakelock upon app resume. If you would prefer to disable this behaviour, you can use this function.

```js
	window.powerManagement.setReleaseOnPause(false, function() {
		console.log('Set successfully');
	}, function() {
		console.log('Failed to set');
	});
```

Note that in all the above examples, all callbacks are optional.
