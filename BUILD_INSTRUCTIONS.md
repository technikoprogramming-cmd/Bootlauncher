# NCS Launcher - Build Instructions

## Quick Start

This is a complete Android Studio project for the **NCS Launcher** - a custom Android home screen launcher with swipe-based app drawer navigation.

### Prerequisites

1. **Android Studio** (latest version) - Download from https://developer.android.com/studio
2. **Android SDK** (API 34) - Installed via Android Studio
3. **Java 11+** - Usually comes with Android Studio

### Step 1: Open the Project

1. Open Android Studio
2. Click **File** → **Open**
3. Navigate to and select the `android-launcher` folder
4. Click **Open**
5. Wait for Gradle to sync (this may take 5-10 minutes on first build)

### Step 2: Configure SDK (if needed)

If you see SDK errors:

1. Go to **File** → **Settings** (or **Android Studio** → **Preferences** on macOS)
2. Navigate to **Appearance & Behavior** → **System Settings** → **Android SDK**
3. Install:
   - **SDK Platforms**: Android 14 (API 34)
   - **SDK Tools**: Android SDK Build-Tools 34.0.0

### Step 3: Build the APK

#### Option A: Debug APK (for testing)

1. Click **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
2. Wait for the build to complete
3. You'll see a notification with the APK location
4. APK location: `app/build/outputs/apk/debug/app-debug.apk`

#### Option B: Release APK (for distribution)

1. Click **Build** → **Generate Signed Bundle / APK**
2. Follow the wizard:
   - Create a new keystore (or use existing)
   - Fill in key details
   - Select "APK" and "Release"
3. The signed APK will be in `app/build/outputs/apk/release/app-release.apk`

### Step 4: Install on Device/Emulator

#### Using Emulator:

1. Click **Tools** → **Device Manager**
2. Create or select a virtual device
3. Click the play button to start the emulator
4. Click **Run** → **Run 'app'** in Android Studio
5. Select the emulator and click **OK**

#### Using Physical Device:

1. Enable **Developer Mode**:
   - Go to **Settings** → **About Phone**
   - Tap **Build Number** 7 times
   - Go back and open **Developer Options**
   - Enable **USB Debugging**

2. Connect via USB cable
3. Click **Run** → **Run 'app'** in Android Studio
4. Select your device and click **OK**

### Step 5: Set as Default Launcher

1. Press the Home button on your device
2. A dialog will appear asking which launcher to use
3. Select "NCS" and check "Always"
4. Or go to **Settings** → **Apps** → **Default Apps** → **Home** and select "NCS"

## Project Structure

```
android-launcher/
├── app/
│   ├── src/main/
│   │   ├── java/com/ncs/launcher/
│   │   │   ├── MainActivity.kt
│   │   │   ├── ShortcutAdapter.kt
│   │   │   └── AppDrawerAdapter.kt
│   │   ├── res/
│   │   │   ├── layout/
│   │   │   │   ├── activity_main.xml
│   │   │   │   ├── item_shortcut.xml
│   │   │   │   └── item_app.xml
│   │   │   └── values/
│   │   │       ├── strings.xml
│   │   │       └── themes.xml
│   │   └── AndroidManifest.xml
│   └── build.gradle.kts
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

## Features

- **Home Screen** with large digital clock
- **Date and Time Display**
- **Weather Widget** (placeholder)
- **Quick App Shortcuts** (4 customizable shortcuts)
- **App Drawer** with all installed applications
- **Swipe Gestures**:
  - Swipe LEFT to open app drawer
  - Swipe RIGHT to close app drawer
- **Dark Theme** with modern design
- **Smooth Animations**

## Customization

### Change App Name

Edit `app/src/main/res/values/strings.xml`:
```xml
<string name="app_name">Your App Name</string>
```

### Change Shortcuts

Edit `MainActivity.kt` in the `setupHomeScreen()` method:
```kotlin
val shortcuts = listOf(
    AppShortcut("Phone", android.R.drawable.ic_dialog_dialer),
    AppShortcut("Messages", android.R.drawable.ic_dialog_email),
    AppShortcut("Camera", android.R.drawable.ic_menu_camera),
    AppShortcut("Settings", android.R.drawable.ic_menu_preferences)
)
```

### Change Colors

Edit `app/src/main/res/values/themes.xml` to modify the color scheme.

## Troubleshooting

### Build fails with "SDK not found"
- Ensure Android SDK is installed via Android Studio SDK Manager
- Check that `local.properties` has the correct SDK path

### App crashes on launch
- Check Logcat in Android Studio for error messages
- Ensure all permissions are granted in `AndroidManifest.xml`
- Verify the app has `QUERY_ALL_PACKAGES` permission

### Swipe gesture not working
- Test on a physical device (emulator gestures can be unreliable)
- Adjust gesture sensitivity in the code if needed

### App drawer not showing
- Ensure other apps are installed on the device
- Check that the app has `QUERY_ALL_PACKAGES` permission

## Support

For issues, refer to:
- [Android Developer Documentation](https://developer.android.com/docs)
- [Android Studio Help](https://developer.android.com/studio/intro)
- [Gradle Build System](https://developer.android.com/build)

## License

This project is provided as-is for educational and personal use.
