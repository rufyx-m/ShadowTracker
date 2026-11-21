+# Shadow Tracker - Complete Project Report

## 1. Project Folder Structure
```text
D:/shadowtracker/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/sh/shadowtracker/
│   │       │   ├── MainActivity.kt
│   │       │   ├── services/
│   │       │   │   ├── AntiTheftService.kt
│   │       │   │   └── ShutdownReceiver.kt
│   │       │   └── utils/
│   │       │       ├── CameraHelper.kt
│   │       │       ├── EmailHelper.kt
│   │       │       ├── FirebaseHelper.kt
│   │       │       └── LocationHelper.kt
│   │       ├── res/
│   │       │   ├── drawable/app_logo.png
│   │       │   └── ... (layouts, values, etc.)
│   │       └── AndroidManifest.xml
│   ├── google-services.json
│   └── build.gradle.kts
├── build.gradle.kts (Project Level)
└── DOCUMENTATION.md
```

## 2. Detailed File Descriptions

| File Name | Location | Purpose / Content |
| :--- | :--- | :--- |
| **AndroidManifest.xml** | `app/src/main/` | Core configuration. Contains all permissions (Camera, Location, Internet, Background Location) and registers the Service and High-Priority Receiver. |
| **MainActivity.kt** | `com/sh/shadowtracker/` | User Interface. Handles Recovery Email setup (Primary & Secondary), Permission requests (including Background Location dialog), and Manual Test button. |
| **AntiTheftService.kt** | `services/` | The engine of the app. A Foreground Service that runs during shutdown. It coordinates Location fetching, Photo capturing, Email sending, and Firebase uploading. |
| **ShutdownReceiver.kt** | `services/` | A High-Priority Broadcast Receiver that detects when the phone is turning off and immediately kicks off the AntiTheftService. |
| **CameraHelper.kt** | `utils/` | CameraX implementation. Silently clicks a photo from the front camera and saves it both to the private cache (for email) and the public Gallery (ShadowTracker folder). |
| **LocationHelper.kt** | `utils/` | GPS logic. Uses FusedLocationProvider to get high-accuracy coordinates and generates a standard Google Maps URL. |
| **EmailHelper.kt** | `utils/` | SMTP Mail logic. Uses JavaMail API to send an email with the photo attachment and location link to multiple recipients using a Gmail App Password. |
| **FirebaseHelper.kt** | `utils/` | Cloud Storage & Database logic. Uploads the captured photo to Firebase Storage and saves a text record (links, emails, timestamp) in Firestore. |
| **build.gradle.kts** | `app/` | Dependency manager. Includes CameraX, Google Play Services, Firebase BoM, Firestore, Storage, and JavaMail libraries. |
| **google-services.json**| `app/` | Firebase configuration file that connects your Android app to your specific Firebase project console. |

## 3. Technology Stack
- **Language:** Kotlin
- **UI Framework:** Jetpack Compose (Material 3)
- **Database:** Firebase Firestore
- **Storage:** Firebase Cloud Storage
- **Communication:** SMTP via JavaMail
- **Hardware APIs:** CameraX & Google Fused Location

---
**Report Generated on:** May 01, 2026
**Project Name:** Shadow Tracker
**Developer:** Maaruf / Shadow Tracker Team
