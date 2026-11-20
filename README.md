# VOW – mobile app project (Android + iOS)

This folder wraps the VOW web app (`www/index.html`) into real Android and iOS apps using Capacitor.

## 1. Install (on your computer)
- Install Node.js (https://nodejs.org, LTS version)
- For Android: Android Studio
- For iOS: a Mac with Xcode (no Mac? use a cloud build service such as Codemagic or Ionic Appflow)

## 2. Build the apps
```bash
npm install
npx cap add android
npx cap add ios        # Mac only
npx cap sync
npm run android        # opens Android Studio -> press Run
npm run ios            # opens Xcode -> press Run
```
Before publishing, change `appId` in `capacitor.config.json` to your own unique ID (example: `com.yourname.vow`). It cannot be changed after release.

## 3. Icon and splash screen
Put a 1024x1024 `icon.png` and a 2732x2732 `splash.png` in a folder named `assets`, then run:
```bash
npm install -D @capacitor/assets
npx capacitor-assets generate
```

## 4. Publish
| Store | Account | Cost |
|---|---|---|
| Google Play | Play Console | $25 one time |
| Apple App Store | Apple Developer Program | $99 per year |

- Android: in Android Studio use Build > Generate Signed Bundle (AAB), upload it in Play Console.
- iOS: in Xcode use Product > Archive > Distribute, then finish in App Store Connect.

## 5. What the stores will REQUIRE for a dating app
Apple and Google review dating apps strictly. Without these, the app will be rejected:
1. **Real backend.** Accounts and photos must be stored on a server (for example Supabase), not only in the phone. Apple rejects apps that are just a website in a box.
2. **Account deletion inside the app** (required by both stores).
3. **Report and block** buttons on every profile, plus a way to remove abusive users (required for user-generated content).
4. **18+ only:** set the age rating to 18+ and verify age at sign-up.
5. **Privacy policy and terms** published at a public web address, with a clear explanation of how photos, orientation and location are used.
6. **Safety tools:** photo verification and moderation are strongly recommended.
7. **Native features** help the review (camera for photos, push notifications for new matches).

## Next steps we should build
1. Supabase backend (login, database, photo storage)
2. Real profiles in the swipe cards, real matches, and chat
3. Report / block / delete account
4. Push notifications
