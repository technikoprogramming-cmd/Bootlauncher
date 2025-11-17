# Build Your APK on GitHub (Completely Free & Automatic)

This guide shows you how to use **GitHub Actions** to automatically build your NCS Launcher APK without needing Android Studio or any local setup.

## Step-by-Step Guide

### Step 1: Create a GitHub Account (if you don't have one)

1. Go to https://github.com
2. Click "Sign up"
3. Enter your email, create password, username
4. Verify your email
5. Done!

---

### Step 2: Create a New Repository

1. Go to https://github.com/new
2. Fill in:
   - **Repository name**: `ncs-launcher` (or any name)
   - **Description**: `NCS Custom Launcher for Android`
   - **Public** or **Private** (your choice)
3. Click "Create repository"

---

### Step 3: Upload Your Project Files

#### Option A: Upload via GitHub Web Interface (Easiest)

1. In your new repository, click "Add file" → "Upload files"
2. Download the `ncs-launcher.tar.gz` file from earlier
3. Extract it on your computer
4. Drag and drop the `android-launcher` folder contents into GitHub
5. Include all files EXCEPT the `.gradle` and `build` folders
6. Click "Commit changes"

#### Option B: Use Git Command Line (If you know Git)

```bash
git clone https://github.com/YOUR_USERNAME/ncs-launcher.git
cd ncs-launcher
# Copy android-launcher files here
git add .
git commit -m "Initial commit: NCS Launcher"
git push origin main
```

---

### Step 4: GitHub Actions Will Automatically Build!

1. Go to your repository
2. Click the **"Actions"** tab
3. You should see **"Build Android APK"** workflow
4. It will automatically start building (watch the progress)
5. Wait 5-10 minutes for the build to complete

---

### Step 5: Download Your APK

1. Go to **Actions** tab
2. Click the latest **"Build Android APK"** workflow run
3. Scroll down to **"Artifacts"**
4. Click **"app-debug"** to download
5. Extract the ZIP file
6. You'll have `app-debug.apk` ✅

---

### Step 6: Install on Your S23

1. Download the APK to your phone
2. Open file manager
3. Tap the APK file
4. Tap "Install"
5. Allow installation from unknown sources if prompted
6. Done!

---

### Step 7: Set as Default Launcher

1. Press Home button
2. Select "NCS"
3. Check "Always"

---

## That's It! 🎉

Now every time you:
- Push code to GitHub
- Make changes to the project
- Update files

GitHub will **automatically rebuild your APK** for you!

---

## How to Make Changes

### Change App Name

1. Go to your GitHub repository
2. Navigate to `app/src/main/res/values/strings.xml`
3. Click the edit button (pencil icon)
4. Change `<string name="app_name">NCS</string>` to your name
5. Click "Commit changes"
6. GitHub automatically rebuilds! ✅

### Change Shortcuts

1. Navigate to `app/src/main/java/com/ncs/launcher/MainActivity.kt`
2. Find the `setupHomeScreen()` function
3. Edit the shortcuts list
4. Commit changes
5. GitHub rebuilds automatically

### Any Other Changes

Just edit files in GitHub web interface → Commit → GitHub rebuilds automatically!

---

## Troubleshooting

### Build Failed?

1. Go to **Actions** tab
2. Click the failed workflow
3. Scroll down to see the error
4. Common issues:
   - **Gradle sync failed**: Usually temporary, try again
   - **Memory error**: GitHub will retry automatically
   - **SDK not found**: The workflow handles this automatically

### Can't Find APK Download?

1. Make sure the workflow completed (green checkmark)
2. Look for "Artifacts" section
3. If not there, the build may have failed - check the logs

### Need to Rebuild?

1. Go to **Actions**
2. Click the workflow
3. Click "Re-run all jobs"

---

## Advanced: Automatic Release APK

Want a signed release APK? This requires a keystore file. Contact me if you need this setup.

---

## Free Tier Limits

GitHub Actions gives you:
- ✅ **2,000 free build minutes per month** (plenty!)
- ✅ **Unlimited repositories**
- ✅ **Unlimited builds**

You won't hit these limits unless you build 100+ times per day.

---

## Summary

| Step | Time | What You Do |
|------|------|-----------|
| 1 | 2 min | Create GitHub account |
| 2 | 1 min | Create repository |
| 3 | 5 min | Upload project files |
| 4 | 10 min | Wait for GitHub to build |
| 5 | 1 min | Download APK |
| 6 | 2 min | Install on phone |
| 7 | 1 min | Set as default launcher |
| **TOTAL** | **~22 minutes** | **Your launcher is ready!** |

---

## Questions?

- GitHub Help: https://docs.github.com
- GitHub Actions: https://docs.github.com/en/actions
- Android Build: https://developer.android.com/build
