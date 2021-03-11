
# React Native Cybersource Device Fingerprint

## Installation

Using npm:

```shell
npm install --save react-native-cybersource-device-fingerprint
```

or using yarn:

```shell
yarn add react-native-cybersource-device-fingerprint
```


### Manual installation


#### Settings

NOTE: This version of lib was developed to be used in NR 0.60+

1. Open or create the file `react-native.config.js`
2. Add the library dependency in module.exports the following code
    ```javascript
    'react-native-cybersource-device-fingerprint': {
        platforms: {
          android: {
            packageInstance: 'new RNCybersourceDeviceFingerprintPackage(this.getApplication())',
          },
        },
      },
    ```
    example of what the file should look like:
    ```javascript
    module.exports = {
      assets: ['./src/assets/fonts/'],
      dependencies: {
        'react-native-cybersource-device-fingerprint': {
          platforms: {
            android: {
              packageInstance: 'new RNCybersourceDeviceFingerprintPackage(this.getApplication())',
            },
          },
        },
      },
    }
    ```
3. Build your project again (`yarn ios`) or (`yarn android`)<

## Usage
```javascript
import RNCybersourceDeviceFingerprint from 'react-native-cybersource-device-fingerprint'

// INITIALIZING THE SDK AND SESSION AT CYBERSOURCE
// ❗️ NOTE: WE ADVISE THAT THIS INITIALIZATION OCCURS IN A PROCESS BEFORE SENDING FINGERPRINT TO YOUR API
RNCybersourceDeviceFingerprint.configure(ORG_ID, FP_SERVER).then( () => {
	console.log('✅ The Cybersource session has started')
})
.catch(err => {
	console.log('⛔️ An error occurred while trying to sign in with Cybersource ', err)
})

// getSession accepts custom attributes for session, check the Cybersource SDK documentation
RNCybersourceDeviceFingerprint.getSessionID([]).then( (obj) => {
	console.log(`The FingerprintID is ${obj.sessionId}`)
})
.catch(err => {
	console.log('⛔️ CYBERSOURCE ERROR: ', err)
})

```
  
