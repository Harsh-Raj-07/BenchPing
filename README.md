
# BenchPing
BenchPing is an offline Android messaging app for people nearby. One person hosts a chat, the other joins, and both confirm a pairing code. They can then exchange text messages directly over Bluetooth or Wi-Fi without mobile data or an internet connection. Each phone saves its own chat history.

## Bluetooth prototype

BenchPing currently supports one-to-one chats over Bluetooth Classic on Android 6.0 and up. Wi-Fi transport is planned.

1. Install the debug app on two Android phones and pair the phones in Android Bluetooth settings.
2. Open BenchPing on both phones. On Android 12 and newer, allow **Nearby devices** when prompted.
3. Tap **Host a chat** on one phone. Tap **Join a chat** on the other and select the host.
4. Compare the six-digit code on both screens. Tap **Codes match** on both phones when the codes agree.
5. Send a message in either direction. After disconnecting, **Chat history** opens saved conversations on each phone, even with Bluetooth off. It shows the most recent 100 messages per peer.

## Build

Install a JDK (17 or newer) and Android SDK Platform 35. Use Android Studio or run these commands from the repository root with `ANDROID_HOME` pointing to the Android SDK.

```sh
./gradlew :app:assembleDebug :app:lintDebug
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

To check offline messaging on hardware, leave Bluetooth on and turn off Wi-Fi and mobile data on both phones. Verify that sending stays unavailable until both people confirm, exchange messages in both directions, then reopen each app and check the saved history.

