# 🗺️ Android Map API Test (MapApi)

A simple **Android (Java)** sample app that demonstrates how to integrate **Google Maps** 🧭, request **device location** 📍, and (optionally) draw **routes/polylines** 🛣️ using the **Google Directions API**.

---

## ✨ Features

- 🗺️ **Google Maps** integration using `SupportMapFragment`
- 📍 **Current location** access with **FusedLocationProviderClient**
- 🎛️ Map UI controls enabled (zoom controls + compass)
- 🎨 Optional **custom map style** via `res/raw/map_style.json`
- 🧩 Includes networking libraries (**Retrofit + OkHttp**) for API calls
- 🧵 Route drawing support using **Google Maps Utils** (`PolyUtil`)

---

## 🧰 Tech Stack

- ☕ Java (Android)
- 🧱 AndroidX + Material Components
- 🗺️ Google Play Services Maps + Location
- 🔌 Retrofit + OkHttp + Gson
- 🧭 Google Maps Services (Directions API client)
- 🔐 Maps Platform **Secrets Gradle Plugin**

---

## ✅ Requirements

### 🖥️ Development
- 🧑‍💻 **Android Studio** (latest stable recommended)
- 📦 **Android Gradle Plugin**: `8.13.2`
- ☕ **JDK 11** (project is configured for Java 11)
- 🤖 Android SDK:
  - `minSdk` **27**
  - `targetSdk` **36**
  - `compileSdk` **36** (as configured)

### 🔑 Google / Maps
You’ll need a Google Cloud project with billing enabled and the following APIs:

- ✅ **Maps SDK for Android**
- ✅ **Directions API** (if you use routing / directions)

---

## 📂 Project Structure (high-level)

- `app/src/main/java/lk/acx/mapapi/MapsActivity.java` 🧠  
  Main activity that initializes the map, requests location permissions, and handles map rendering.

- `app/src/main/java/lk/acx/mapapi/service/DirectionApi.java` 🌐  
  Retrofit interface for calling the Directions REST endpoint.

- `app/src/main/res/layout/activity_maps.xml` 🧩  
  Contains the `SupportMapFragment` and a `mapId`.

- `app/src/main/res/raw/map_style.json` 🎨  
  Optional JSON map styling file (already included).

---

## ⚙️ How It Works (Flow)

1. 🚀 App launches `MapsActivity`
2. 🧩 `SupportMapFragment` loads the map and triggers `onMapReady()`
3. 🧭 Map UI options are enabled (zoom controls, compass)
4. 🔐 App requests **location permission** (if not granted)
5. 📍 Once permission is granted, app can fetch and update the user’s location
6. 🧷 App moves the camera to a predefined `LatLng` (your “home” location)
7. 🛣️ (Optional) App can call Directions API and decode polylines to draw a route

---

## ▶️ Setup & Run

### 1) 📥 Clone the repository
```bash
git clone https://github.com/Achintha-999/android-map-api-test.git
```

### 2) 📂 Open in Android Studio
- Open Android Studio → **Open** → select the project folder.

### 3) 🔑 Add your API keys (IMPORTANT)

This project uses the **Secrets Gradle Plugin**:
```gradle
id 'com.google.android.libraries.mapsplatform.secrets-gradle-plugin'
```

#### ✅ Recommended way (safe): `local.properties`
1. Open (or create) the file:
   - `local.properties` (in the project root)

2. Add your key(s):
```properties
MAPS_API_KEY=YOUR_GOOGLE_MAPS_API_KEY_HERE
DIRECTIONS_API_KEY=YOUR_GOOGLE_DIRECTIONS_API_KEY_HERE
```

> 🔒 **Do not commit** real keys to GitHub. Keep them local.

#### 🔁 Where the keys are used
You’ll typically reference these keys in one of these places:
- `AndroidManifest.xml` (for Maps SDK key via `<meta-data>`)
- or via generated `BuildConfig` fields depending on your secrets plugin configuration

If your project currently doesn’t include the manifest `<meta-data>` yet, add this:

```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="${MAPS_API_KEY}" />
```

---

## 🧭 Replace the Demo Location (LatLng)

In:
- `app/src/main/java/lk/acx/mapapi/MapsActivity.java`

You will see:
```java
LatLng home = new LatLng(<YOUR_LatLng_HERE>);
```

✅ Replace it with real coordinates, for example:
```java
LatLng home = new LatLng(6.9271, 79.8612); // Colombo, Sri Lanka
```

---

## 🗺️ About `mapId` in Layout

In:
- `app/src/main/res/layout/activity_maps.xml`

You have:
```xml
app:mapId="cc584b0041aa16f6a052eae9"
```

✅ This is a **Cloud-based Map ID** (Maps styling / configuration).  
If you have your own Map ID, replace it with yours. If you don’t use Map IDs, you can remove that attribute.

---

## 🧪 Testing

- ✅ Instrumented tests exist under:
  - `app/src/androidTest/...`

Run:
- Android Studio → **Run > Run 'All Tests'** (or per test class)

---

## 🛡️ Security Notes (Keys & Billing)

- 🔐 Never hardcode API keys inside Java files.
- 🧾 Enable **billing** for Google Maps Platform.
- 🧱 Restrict keys in Google Cloud Console:
  - ✅ Android app restriction (package name + SHA-1)
  - ✅ API restrictions (Maps SDK, Directions API, etc.)

---

## 🧩 Dependencies (Highlights)

- 🗺️ `play-services-maps`
- 📍 `play-services-location`
- 🌐 `retrofit`, `okhttp`, `converter-gson`
- 🧭 `com.google.maps:google-maps-services`
- 🧵 `android-maps-utils`

---

## 🤝 Contributing

- 🍴 Fork the repo
- 🌿 Create a feature branch
- ✅ Open a PR

---

## 📄 License

📌 Add a license if you plan to distribute this project publicly (MIT/Apache-2.0 recommended).

---
badges, troubleshooting, etc.).
