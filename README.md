

# React Native Biometrics

`@ghitete/react-native-biometrics` is a React Native module that provides support for biometric authentication (Face ID and Fingerprint) on iOS devices. It allows developers to check the availability of biometric support and perform biometric authentication with optional password fallback.

## Features

- Check the availability of Face ID and Fingerprint.
- Perform biometric authentication with customizable options.
- Lightweight and easy to integrate.

---

## Installation

Install the library using npm or yarn:

```bash
npm install @ghitete/react-native-biometrics
```

or

```bash
yarn add @ghitete/react-native-biometrics
```

For iOS, link the native module:

```bash
npx pod-install
```

---

## Usage

### Import the module

```typescript
import {
  BiometricTypes,
  checkBiometricSupport,
  authenticate,
} from '@ghitete/react-native-biometrics';
```

---

### Check Biometric Support

Use the `checkBiometricSupport` function to verify if the device supports Face ID or Fingerprint.

```typescript
(async () => {
  try {
    const support = await checkBiometricSupport();
    console.log('Biometric Support:', support);
    // Output: { hasFaceId: boolean, hasFingerprint: boolean }
  } catch (error) {
    console.error('Error checking biometric support:', error);
  }
})();
```

---

### Perform Biometric Authentication

Use the `authenticate` function to prompt the user for biometric authentication.

```typescript
(async () => {
  try {
    const result = await authenticate({
      type: BiometricTypes.FACE_ID, // or BiometricTypes.FINGERPRINT
      allowPasswordFallback: true,  // Optional, defaults to false
    });
    console.log('Authentication result:', result);
  } catch (error) {
    console.error('Authentication failed:', error);
  }
})();
```

---

## API

### Enums

#### `BiometricTypes`
- `FACE_ID`: Use Face ID for authentication.
- `FINGERPRINT`: Use Fingerprint for authentication.

---

### Methods

#### `checkBiometricSupport(): Promise<BiometricSupportResult>`

Checks whether the device supports biometric authentication (Face ID or Fingerprint).

Returns:

```typescript
interface BiometricSupportResult {
  hasFaceId: boolean;
  hasFingerprint: boolean;
}
```

#### `authenticate(options: AuthenticationOptions): Promise<string>`

Prompts the user for biometric authentication.

```typescript
interface AuthenticationOptions {
  type: BiometricTypes;            // Biometric type to use
  allowPasswordFallback?: boolean; // Optional, defaults to false
}
```

Returns:
- `"SUCCESS"`: If authentication succeeds.
- Throws an error if authentication fails.

---

## iOS Integration

### Enable Face ID or Fingerprint

1. Open your Xcode project and enable Face ID or Fingerprint in your app's **Capabilities**.
2. Add a description to `Info.plist` to explain why the app requires Face ID.

```xml
<key>NSFaceIDUsageDescription</key>
<string>We need Face ID for secure authentication.</string>
```

---

## Development

To clone and contribute to this project, run the following commands:

```bash
git clone https://github.com/ghitete/react-native-biometrics.git
cd react-native-biometrics
npm install
```

---

## To Do

- [ ] Implement Android support.
- [ ] Write unit tests for both iOS and Android.

---

## License

MIT

---

## Notes

- This module currently supports **iOS only**. Android support will be added in future updates.
- Ensure biometric authentication is properly configured on the device before testing.

---

Feel free to customize further or let me know if there’s anything else you’d like to add!
