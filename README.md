# react-native-screen-brightness

Access and update the system brightness on a device.

## React Native compatibility
|         React Native version          |         Compatible `react-native-screen-brightness` version   |
| :------------------: | :------------------: |
| v0.60+ | v2.x |
| v0.27 - v0.59 | v1.x |

## Install

Install with [yarn](https://yarnpkg.com) or [npm](https://www.npmjs.com).

```shell
yarn add react-native-screen-brightness
```

```shell
npm i --save react-native-screen-brightness
```

## Install IOS (auto linking)
Open shell/command
Browse to yourproject/iod directory 
run 'pod install'

## Example

```js
import ScreenBrightness from 'react-native-screen-brightness';

ScreenBrightness.setBrightness(0.5); // between 0 and 1

ScreenBrightness.getBrightness().then(brightness => {
  console.log('brightness', brightness);
});
```
## Setting up permissions android
Asking for permissions is neede to succesfully run on Android devices. 

First update your Manifest:
Change your manifest to:
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.kiter" **xmlns:tools="http://schemas.android.com/tools"**>

And add:

<uses-permission android:name="android.permission.WRITE_SETTINGS" tools:ignore="ProtectedPermissions"/>

Then in your JS implementation also check if permission is granted:  
```js
import ScreenBrightness from 'react-native-screen-brightness';

let hasPerm = await ScreenBrightness.hasPermission();

if(!hasPerm){
  alert('System settings permission is needed to manage the brightness of your device');
   ScreenBrightness.requestPermission();
   return;
}
```
