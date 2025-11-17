# Android Custom Launcher

A modern, feature-rich Android custom launcher application with a beautiful dark theme, clock display, weather widget, and swipe-based app drawer navigation.

## Features

- **Home Screen** with large clock display and date
- **Weather Widget** showing current temperature and conditions
- **Quick App Shortcuts** (4 customizable shortcuts at the bottom)
- **App Drawer** with all installed applications
- **Swipe Navigation** - Swipe left to open app drawer, swipe right to close
- **Dark Theme** with modern, minimalist design
- **Smooth Animations** for drawer transitions
- **Launcher Integration** - Can be set as default home screen

## Screenshots

The launcher displays:
- Large digital clock (HH:MM:SS format)
- Current date and day of week
- Weather information
- 4 quick-access app shortcuts
- Full app drawer accessible via swipe gesture

## Requirements

- Android Studio (latest version)
- Android SDK 26 or higher
- Gradle 8.0+
- Java 11 or higher

## Setup Instructions

### 1. Open the Project in Android Studio

1. Download and install [Android Studio](https://developer.android.com/studio)
2. Open Android Studio
3. Click **File** → **Open** and select the `android-launcher` directory
4. Wait for Gradle to sync (this may take a few minutes)

### 2. Configure Android SDK

1. In Android Studio, go to **File** → **Settings** (or **Android Studio** → **Preferences** on macOS)
2. Navigate to **Appearance & Behavior** → **System Settings** → **Android SDK**
3. Install the following:
   - **SDK Platforms**: Android 14 (API 34)
   - **SDK Tools**: Android SDK Build-Tools 34.0.0

### 3. Update local.properties

Edit the `local.properties` file and set the correct path to your Android SDK:

```properties
sdk.dir=/path/to/your/android/sdk
```

On macOS, this is typically:
```properties
sdk.dir=/Users/YourUsername/Library/Android/sdk
```

On Windows, this might be:
```properties
sdk.dir=C:\\Users\\YourUsername\\AppData\\Local\\Android\\sdk
```

On Linux, this might be:
```properties
sdk.dir=/home/YourUsername/Android/Sdk
```

### 4. Build the Project

1. In Android Studio, click **Build** → **Make Project**
2. Wait for the build to complete

### 5. Run on Emulator or Device

#### Option A: Using Android Emulator

1. Click **Tools** → **Device Manager**
2. Create a new virtual device (if you don't have one)
3. Select your device and click the play button to start the emulator
4. Once the emulator is running, click **Run** → **Run 'app'** in Android Studio
5. Select the emulator and click **OK**

#### Option B: Using Physical Device

1. Enable **Developer Mode** on your Android device:
   - Go to **Settings** → **About Phone**
   - Tap **Build Number** 7 times
   - Go back to **Settings** → **Developer Options**
   - Enable **USB Debugging**

2. Connect your device to your computer via USB
3. In Android Studio, click **Run** → **Run 'app'**
4. Select your device and click **OK**

### 6. Build APK

To create a release APK:

1. Click **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
2. Wait for the build to complete
3. The APK will be located at: `app/build/outputs/apk/debug/app-debug.apk`

For a signed release APK:

1. Click **Build** → **Generate Signed Bundle / APK**
2. Follow the wizard to create a keystore and sign the APK
3. The signed APK will be in `app/build/outputs/apk/release/`

### 7. Set as Default Launcher

Once the app is installed:

1. Press the home button on your device
2. A dialog will appear asking which launcher to use
3. Select "Custom Launcher" and check "Always"
4. Alternatively, go to **Settings** → **Apps** → **Default Apps** → **Home** and select "Custom Launcher"

## Project Structure

```
android-launcher/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/example/launcher/
│   │       │   ├── MainActivity.kt          # Main launcher activity
│   │       │   ├── ShortcutAdapter.kt       # Adapter for shortcuts grid
│   │       │   └── AppDrawerAdapter.kt      # Adapter for app drawer
│   │       ├── res/
│   │       │   ├── layout/
│   │       │   │   ├── activity_main.xml    # Main layout
│   │       │   │   ├── item_shortcut.xml    # Shortcut item layout
│   │       │   │   └── item_app.xml         # App drawer item layout
│   │       │   └── values/
│   │       │       ├── strings.xml          # String resources
│   │       │       └── themes.xml           # Theme definitions
│   │       └── AndroidManifest.xml          # App manifest
│   ├── build.gradle.kts                     # App-level build configuration
│   └── proguard-rules.pro                   # ProGuard rules for release
├── build.gradle.kts                         # Project-level build configuration
├── settings.gradle.kts                      # Gradle settings
├── gradle.properties                        # Gradle properties
└── README.md                                # This file
```

## Customization

### Change Shortcuts

Edit the `setupHomeScreen()` method in `MainActivity.kt` to add or modify shortcuts:

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

### Modify Layout

Edit `app/src/main/res/layout/activity_main.xml` to change the UI layout and spacing.

## Troubleshooting

### Build Fails with "SDK not found"
- Ensure `local.properties` has the correct SDK path
- Run `Tools` → `SDK Manager` in Android Studio to install required SDK versions

### App Crashes on Launch
- Check the Logcat in Android Studio for error messages
- Ensure all permissions are granted in `AndroidManifest.xml`
- Verify that the app has permission to query installed packages

### Swipe Gesture Not Working
- Ensure the device's gesture sensitivity is set appropriately
- Test on a physical device if emulator gestures are not responsive

### App Drawer Not Showing
- Verify that the app has `QUERY_ALL_PACKAGES` permission
- Check that other apps are installed on the device

## License

This project is provided as-is for educational and personal use.

## Support

For issues or questions, refer to the [Android Developer Documentation](https://developer.android.com/docs).
