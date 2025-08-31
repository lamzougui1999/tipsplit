# TipSplit — Flutter (iOS & Android)

A simple, privacy‑respecting **tip & bill split calculator** with localized tipping norms and respectful ads.

> **Ads policy:** One small Banner at the bottom of the screen + **one Interstitial on first open only**. No pop-ups, no forced videos.

---

## 👷 Build Instructions (Flutter)

1) Install Flutter (3.22+), Dart SDK, and platform toolchains (Xcode for iOS, Android SDK).
2) In this folder, run:
```
flutter pub get
flutter create .   # generates missing platform folders (android/ios) if absent
```
3) Add your **AdMob App IDs**:
   - **Android**: open `android/app/src/main/AndroidManifest.xml`, add
     ```xml
     <manifest>
       <application>
         <meta-data
           android:name="com.google.android.gms.ads.APPLICATION_ID"
           android:value="ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY"/>
       </application>
     </manifest>
     ```
   - **iOS**: open `ios/Runner/Info.plist`, add
     ```xml
     <key>GADApplicationIdentifier</key>
     <string>ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY</string>
     ```
   Replace with your real App IDs. Unit IDs used in code are **Google test IDs**; replace before release.
4) Run:
```
flutter run -d ios     # or
flutter run -d android
```
5) (Optional) Create release builds:
```
flutter build ios --release
flutter build apk --release
```

---

## 🧠 Features

- Bill input, **Tip %** slider, **Split** slider (1–20).
- Real‑time results: **Tip**, **Total**, **Split Tip**, **Split Total**.
- **Round Total**: buttons to round up/down to nearest integer.
- **Localized tipping norms** by country (from device locale, with offline JSON fallback).
- **Arabic & English** UI; automatic RTL/LTR.
- **Respectful ads**: bottom banner + first‑open interstitial only.

### Data & Privacy
- No sign‑in, no analytics, no personal data storage.
- Only AdMob SDK is used for ads.

---

## 📁 Code Structure

```
lib/
  main.dart                  # App bootstrap + localization setup + Ads init
  home_page.dart             # Main screen UI and tip logic
  l10n/app_localizations.dart# Simple EN/AR localization
  ads/ad_helper.dart         # Ad unit helpers (test IDs by default)
assets/data/tipping_norms.json # Offline norms by country code
backend/                     # Optional tiny backend (see below)
pubspec.yaml
```

---

## ☁️ Optional Backend (Node.js)

Although the app works **fully offline**, you may host/update tipping norms remotely.

### Run locally
```
cd backend
npm install
npm run start
# serves http://localhost:8080/tipping-norms
```

### Configure the app to use your endpoint
- In `home_page.dart` you can fetch from your hosted JSON instead of assets, if desired.

---

## 📣 Store Listing Tips (EN)
- Keywords: tip calculator, split bill, gratuity, restaurant, check splitter.
- Value props: instant results, localized guidance, privacy, respectful ads.

## 📣 نصائح صفحة المتجر (AR)
- كلمات مفتاحية: حاسبة البقشيش، تقسيم الفاتورة، مطاعم، بقشيش، إكراميات.
- نقاط القوة: نتيجة فورية، إرشادات حسب الدولة، خصوصية، إعلانات غير مزعجة.

---

## 📝 License
This project is provided as-is for your personal/commercial use. Replace ad IDs and branding before publishing.
