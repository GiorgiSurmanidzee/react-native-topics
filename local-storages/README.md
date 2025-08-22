## Methods of Storing Local Data in React Native Expo

### AsyncStorage

AsyncStorage is a simple, unencrypted, asynchronous key-value storage system.
Works in both Expo and React Native CLI.

### Use Cases:

- Storing user preferences and settings
- Caching small pieces of data
- Saving non-sensitive information

install:
``` 
npm install @react-native-async-storage/async-storage
```

### SecureStore

SecureStore provides a secure way to store sensitive data, such as authentication tokens and user credentials. It leverages the device's secure storage mechanisms like iOS Keychain and Android Keystore, ensuring high security.

SecureStore → best in Expo; if not using Expo, prefer  ``` react-native-keychain ```.

### Use Cases:

- Storing authentication tokens
- Saving user credentials
- Keeping sensitive configuration settings

install:
``` 
expo install expo-secure-store
```