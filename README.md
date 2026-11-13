# EASIEST: get the APK without Android Studio
1. Create a free account at github.com, then a New repository (private is fine).
2. Upload ALL files from this folder (drag the unzipped contents onto the repo page; keep the .github folder).
3. Open the Actions tab -> "Build Jarvis APK" -> wait ~5 minutes for the green tick.
4. Click the run -> Artifacts -> Jarvis-APK, download, unzip to get app-debug.apk.
5. Send it to your phone, tap it, allow "Install unknown apps", install.
In the app: paste both keys -> Save keys -> Enroll voice -> Start Jarvis -> Allow phone control.

# Jarvis for Android

1. Get a free AccessKey at https://console.picovoice.ai. You paste it into the app itself (no code editing).
2. Open this folder in Android Studio, let Gradle sync, run on your phone (Android 8+).
3. In the app: Enroll my voice -> Start Jarvis -> Allow phone control (turn on "Jarvis Phone Control").
4. Android Settings -> Battery -> set Jarvis to "Unrestricted" so it keeps listening.

Say "Jarvis" then: "open WhatsApp", "tap Send", "scroll down", "go back", "go home",
"what's the weather", "remind me to call Mum tomorrow at 9am", "remind me to pay rent on Friday at 5pm", "what are my reminders", "clear reminders".

Gmail setup (one time, free; needs Google Play services on the phone)
1. console.cloud.google.com -> new project -> enable "Gmail API".
2. OAuth consent screen: External, add your own Gmail as a Test user.
3. Credentials -> Create OAuth client ID -> type "Android", package name com.example.jarvis, and the SHA-1 of your
   signing key. For a debug build run: ./gradlew signingReport  (or keytool -list -v -keystore ~/.android/debug.keystore
   -alias androiddebugkey -storepass android). Nothing needs pasting into the code.
4. In the app tap "Connect Gmail (read-only)" and approve. Then say "Jarvis, check my email".
Unverified-app warnings are normal for your own test project. New-mail notifications arrive every ~10 minutes.

Notes
- Picovoice's built-in wake word is "Jarvis" (not "Hey Jarvis"); a custom "Hey Jarvis" can be trained in their console.
- Library versions in app/build.gradle.kts may need updating to the latest on Maven Central; Picovoice APIs
  (Porcupine, Eagle, EagleProfiler) occasionally change, so adjust calls if the compiler complains.
- Speaker threshold is 0.5 in JarvisService (raise for stricter, lower if it rejects you).
- AI chat: paste your Claude API key (console.anthropic.com) into the app and tap Save. Costs apply per use.
- Not included: reading WhatsApp/Facebook/email and social media tips (see the web version).
