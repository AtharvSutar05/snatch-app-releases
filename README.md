# 📦 Snatch App Releases

This repository hosts **official release builds** of the **Snatch Flutter app**, used for version distribution and in-app update checks.

The APKs published here are **signed release builds**, generated using Flutter’s build system, and are used by the Snatch backend to serve update information dynamically.

---

## 🚀 How it works

1. Each version of the app is published as a **GitHub Release**.  
   Example tag: `v1.0.0`

2. The corresponding release includes the compiled APK file:
```

app-release.apk

```

3. The public download URL from the release is provided to the Snatch backend, which exposes a JSON API endpoint at:
```

https://<your-render-app>.onrender.com/latest

````

4. The Flutter app calls that endpoint on startup to check for updates:
```json
{
  "version": "1.0.0",
  "buildNumber": 1,
  "mandatory": false,
  "url": "https://github.com/AtharvSutar05/snatch-app-releases/releases/download/v1.0.0/app-release.apk",
  "sha256": "<sha256_hash_here>",
  "changelog": "Initial release with meeting creation and real-time communication."
}
````

5. If a newer version is detected, the app downloads and installs the update automatically (after user confirmation).

---

## 🗂️ Version History

| Version    | Build | Date     | Description                                                                  |
| ---------- | ----- | -------- | ---------------------------------------------------------------------------- |
| **v1.0.0** | 1     | Nov 2025 | Initial release with meeting creation, joining, and real-time communication. |

---

## 📥 Download Latest Version

👉 [**Download Snatch v1.0.0 APK**](https://github.com/AtharvSutar05/snatch-app-releases/releases/download/v1.0.0/app-release.apk)

---

## 🧠 Notes for Developers

* New releases should follow the naming convention:

  * Tag: `vX.Y.Z`
  * File: `app-release.apk`
* After publishing a new release, update your backend’s `/latest` response to point to the new version URL.
* To verify file integrity, compute the SHA-256 hash:

  ```bash
  shasum -a 256 build/app/outputs/flutter-apk/app-release.apk
  ```

  or (Windows PowerShell):

  ```powershell
  Get-FileHash -Algorithm SHA256 build\app\outputs\flutter-apk\app-release.apk
  ```

---

## 🧩 Example Backend Response

```json
{
  "version": "1.1.0",
  "buildNumber": 2,
  "mandatory": false,
  "url": "https://github.com/AtharvSutar05/snatch-app-releases/releases/download/v1.1.0/app-release.apk",
  "sha256": "abc123...",
  "changelog": "• Improved performance\n• Fixed minor bugs"
}
```

---

## 🛠️ Tech Stack

* **Frontend:** Flutter
* **Backend:** Node.js (Express) deployed on Render
* **Hosting:** GitHub Releases for APK distribution

---

## 🧑‍💻 Maintainer

**Atharv Sutar**
Cross-Platform App Developer (Flutter + Node.js)

---

> ⚠️ Note: APKs published here are for testing and manual distribution purposes only.
> This repo is not affiliated with Google Play or any official store distribution.

```

