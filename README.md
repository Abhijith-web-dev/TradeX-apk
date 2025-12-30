# TradeX 📈

**Master the Market. Zero Risk.**

![Version](https://img.shields.io/badge/version-1.0.0--beta-blue?style=flat-square)
![Flutter](https://img.shields.io/badge/Made%20with-Flutter-02569B?style=flat-square&logo=flutter)
![Firebase](https://img.shields.io/badge/Backend-Firebase-FFCA28?style=flat-square&logo=firebase)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

**TradeX** is a professional-grade **Paper Trading Application** built for the Indian Stock Market (NSE/BSE). It allows students and beginners to practice trading with **₹10,00,000 virtual capital** using real-time market data, without the risk of losing actual money.

---

## 🚀 Key Features

* **💰 Virtual Portfolio:** Start with ₹1 Lakhs virtual cash. Buy, Sell, and track positions instantly.
* **⚡ Real-Time Data Engine:**
    * **"Heartbeat" Scheduler:** Auto-fetches prices every 60 seconds.
    * **Stealth Mode:** Custom Session Manager to bypass Yahoo Finance 401 errors.
    * **Simulated Ticks:** Local interpolation for smooth price changes between API calls.
* **📊 Advanced Analytics:**
    * Interactive Sparkline charts (Green/Red trend indication).
    * Intraday P&L tracking.
    * Visual "Demand Meter" for market sentiment.
* **📰 Live Market News:** Integrated RSS feed from **The Economic Times** with auto-image extraction.
* **🔄 Auto-Update System:** Self-hosted OTA updates via GitHub Releases (No Play Store required).
* **🔔 Smart Notifications:** Daily market close alerts (3:20 PM IST) to remind users to square off.

---

## 🛠️ Tech Stack

* **Frontend:** Flutter (Dart)
* **Backend:** Firebase Auth, Cloud Firestore
* **State Management:** Provider
* **API Sources:**
    * Yahoo Finance (Stealth Scraper)
    * Economic Times (RSS XML)
* **Key Packages:**
    * `http` & `html`: Web scraping & API requests.
    * `fl_chart`: Financial graphing.
    * `r_upgrade`: In-app updates.
    * `flutter_local_notifications`: Scheduled alerts.
    * `shared_preferences`: Local settings persistence.

---

## 🏗️ System Architecture

TradeX uses a **Hybrid Data Architecture** to ensure speed and reliability without hitting API rate limits:

1.  **The "Handshake" Layer:**
    * On startup, `YahooSessionManager` pings Yahoo servers to acquire a valid `Cookie` and `Crumb` (API Key).
    * These credentials are used for all subsequent requests to prevent "401 Unauthorized" errors.

2.  **The "Heartbeat" Scheduler:**
    * A centralized timer fetches data every **60 seconds** (the "Pulse").
    * It uses **Batch Processing** (fetching stocks 3 at a time) to prevent UI lag.
    * Between fetches, a local **Simulator** applies tiny random micro-ticks to prices so the app feels "alive" (1.2s latency feel).

3.  **Zero-Latency Navigation:**
    * Price data is passed directly from the *Watchlist* to the *Order Screen* via constructors. This ensures the "Buy" page opens instantly with **0ms delay**.

---

## ⚙️ Installation & Setup

### Prerequisites
* Flutter SDK (3.0+)
* Dart SDK
* A Firebase Project (Free Tier)

### Steps

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/Abhijith-web-dev/TradeX-apk.git](https://github.com/Abhijith-web-dev/TradeX-apk.git)
    cd TradeX
    ```

2.  **Firebase Configuration**
    * Create a project in the [Firebase Console](https://console.firebase.google.com/).
    * Add an Android App (package name: `com.sparklab.tradex`).
    * Download `google-services.json` and place it in `android/app/`.
    * Enable **Authentication** (Email/Password) and **Firestore Database**.

3.  **Install Dependencies**
    ```bash
    flutter pub get
    ```

4.  **Run the App**
    ```bash
    flutter run
    ```

---

## 📲 Auto-Update Mechanism

TradeX does not rely on the Google Play Store. It uses a **Self-Hosted GitHub Release System**:

1.  The app checks a raw `version.json` file hosted on this repo on startup.
2.  **JSON Format:**
    ```json
    {
      "version": "1.0.1",
      "apkUrl": "[https://github.com/Abhijith-web-dev/TradeX-apk/blob/main/app-release.apk](https://github.com/Abhijith-web-dev/TradeX-apk/blob/main/app-release.apk)",
      "changelog": "Fixed P&L calculation bug."
    }
    ```
3.  If a new version is detected, the user sees a dialog to **Download & Install** instantly.

**To Push an Update:**
1.  Build APK: `flutter build apk --release`
2.  Create a GitHub Release (e.g., `v1.0.2`).
3.  Upload the APK.
4.  Update `version.json` in the repo root.

---

## 🤝 Contributing

Contributions are welcome!
1.  Fork the project.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👨‍💻 Developer Info

**Developed by Abhijith S**
* **Studio:** SparkLab Info
* **Website:** [https://sparklabinfo.netlify.app/](https://sparklabinfo.netlify.app/)
* **Contact:** sparklabinfo1@gmail.com

> *"Building tools to democratize financial literacy."*
