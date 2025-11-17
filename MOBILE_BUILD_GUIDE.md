# Build NCS Launcher on Your Samsung S23

Since you only have a mobile device, here are the best ways to compile the APK:

## Option 1: Gradle on Android (EASIEST - Recommended)

### What You Need:
- **Termux** (free terminal emulator) - Download from F-Droid or Google Play
- **Java** (installed via Termux)
- **Gradle** (installed via Termux)
- The project files

### Steps:

1. **Install Termux**
   - Download from F-Droid (https://f-droid.org/en/packages/com.termux/) - More reliable
   - Or Google Play Store
   - Open Termux

2. **Install Java and Gradle in Termux**
   ```bash
   pkg update
   pkg upgrade
   pkg install -y openjdk-17
   pkg install -y gradle
   ```
   (This takes 5-10 minutes)

3. **Extract the Project**
   - Download the ncs-launcher.tar.gz file to your phone
   - In Termux:
   ```bash
   cd ~/storage/downloads
   tar -xzf ncs-launcher.tar.gz
   cd android-launcher
   ```

4. **Build the APK**
   ```bash
   gradle assembleDebug
   ```
   (This takes 10-20 minutes on first build)

5. **Find Your APK**
   ```bash
   ls -la app/build/outputs/apk/debug/
   ```
   - The file `app-debug.apk` is your launcher!
   - Copy it to your Downloads folder

6. **Install the APK**
   - Open your file manager
   - Navigate to Downloads
   - Tap `app-debug.apk`
   - Tap "Install"
   - Allow installation from unknown sources if prompted

---

## Option 2: Using AIDE (Android IDE)

### What You Need:
- **AIDE** app (free version available) - Download from Google Play
- The project files

### Steps:

1. **Install AIDE**
   - Download from Google Play Store
   - Open AIDE

2. **Create New Project**
   - Choose "Import Project"
   - Select the extracted `android-launcher` folder

3. **Build**
   - Click the Build button (hammer icon)
   - Wait for compilation (15-30 minutes)

4. **Run/Install**
   - AIDE will automatically install the APK
   - Or find it in AIDE's output folder

---

## Option 3: Using Replit or GitHub Codespaces (Cloud)

If you have internet but want to avoid installing on your phone:

1. **Go to Replit.com**
2. **Create new project** → Select "Java"
3. **Upload the project files**
4. **Run build commands in terminal**
5. **Download the APK** from the output folder

---

## Recommended: Option 1 (Termux)

**Pros:**
- ✅ Free
- ✅ Works offline (after initial setup)
- ✅ Full control
- ✅ Fastest on S23

**Cons:**
- Takes 30-40 minutes first time (Java + Gradle install)
- Requires ~2GB free space

---

## Troubleshooting

### "Command not found: gradle"
```bash
pkg install -y gradle
```

### "Out of memory" error
- Close other apps
- Increase Termux memory (Settings → Termux → Memory)

### "Permission denied" when installing APK
- Settings → Apps → Special app access → Install unknown apps
- Enable for your file manager

### Build takes too long
- This is normal on first build
- Subsequent builds are faster
- Keep your phone plugged in

---

## After Building

Once you have the APK installed:

1. **Set as Default Launcher**
   - Press Home button
   - Select "NCS" 
   - Check "Always"

2. **Customize**
   - Edit `MainActivity.kt` to change shortcuts
   - Rebuild for changes to take effect

---

## Quick Termux Commands Reference

```bash
# Update packages
pkg update && pkg upgrade

# Install Java
pkg install -y openjdk-17

# Install Gradle
pkg install -y gradle

# Navigate to project
cd ~/storage/downloads/android-launcher

# Build APK
gradle assembleDebug

# Find APK
find . -name "*.apk"

# Copy APK to downloads
cp app/build/outputs/apk/debug/app-debug.apk ~/storage/downloads/
```

---

## Need Help?

- **Termux Issues**: https://github.com/termux/termux-app
- **Gradle Issues**: https://gradle.org/help
- **Android Build**: https://developer.android.com/build
