# Geolocation App

## 🚀 About the Project

The Geolocation App is a Flutter application designed for both web and mobile platforms, allowing users to record and visualize their trips on an interactive map. It leverages device GPS to capture the current location, performs reverse geocoding to retrieve the address, and displays it in a friendly interface.

Key Features:
- Location Capture: Automatically gets the current GPS coordinates.
- Interactive Map: Shows saved trips directly on a map using OpenStreetMap.
- Trip Registration: Users can register trips with descriptions and dates.
- Reverse Geocoding: Converts latitude and longitude into a readable address using OpenStreetMap Nominatim and Google Maps Geocoding API.
- Web and Mobile Version: Works seamlessly on both mobile devices and web browsers.
- Local Data Storage: Stores trip data locally during runtime without backend requirements.

This app is an excellent learning project for Flutter developers interested in geolocation, map integration, and API consumption.

---

## 🖼 Screenshots

### Mobile Version

https://github.com/user-attachments/assets/4792f877-0783-4767-9279-4abf2da9bd2b

### Web Version

https://github.com/user-attachments/assets/80c3fc3d-1cf2-45f4-9aee-e4a92137582e


### 🌐 Access the Web version at: https://flutter-geolocation-app.vercel.app/

---

## 🛠 Technologies Used

- Language: Dart
- Framework: Flutter
- Maps Integration: OpenStreetMap with `flutter_map`
- Geolocation: `geolocator` for GPS
- Reverse Geocoding: OpenStreetMap Nominatim API and Google Maps API
- State Management: `setState` (Flutter built-in)
- Routing: Named routes with `Navigator`
- UI Styling: Flutter Material Widgets
- Storage: Local memory (in-app storage)

---

## 📋 Requirements

- Flutter SDK (3.x or higher)
- Dart SDK
- IDE: VS Code, Android Studio, or IntelliJ
- Google Maps API Key (optional for advanced geocoding)
- Internet Connection (maps and API usage)

---

## 📥 Installing or Cloning the Repository

### Clone the repository

```
git clone https://github.com/your-username/GeolocationApp.git
```

```
cd GeolocationApp
```

```
flutter pub get
```

```
flutter run -d chrome
```

```
flutter run
```

---

## 📑 Project Structure
```
/lib
 ├── main.dart                # App entry point
 ├── SplashScreen.dart        # Splash screen
 ├── Home.dart                # Home page with trip list
 ├── Mapas.dart               # Map page with interactive OpenStreetMap
 ├── viagem_model.dart        # Trip model (data structure)
 └── geocoding_service.dart   # Reverse geocoding logic (OpenStreetMap and Google)

 /imagens                     # Assets for UI and README
 /web                         # Web-specific settings
 /android                     # Android platform folder
 /ios                         # iOS platform folder
```

---

## 🌍 API Integration Example

### OpenStreetMap (Nominatim) Reverse Geocoding
```
static Future<Map<String, dynamic>> getAddressFromCoordinates(LatLng coords) async {
  final response = await http.get(
    Uri.parse(
      'https://nominatim.openstreetmap.org/reverse?format=jsonv2&lat=${coords.latitude}&lon=${coords.longitude}',
    ),
    headers: {'User-Agent': 'YourAppName/1.0'}, // Required by Nominatim
  );
  if (response.statusCode == 200) {
    return json.decode(response.body);
  } else {
    throw Exception('Failed to fetch address');
  }
}
```

### Google Maps Geocoding Example

```
static Future<Map<String, dynamic>> getGoogleAddress(LatLng coords, String apiKey) async {
  final response = await http.get(
    Uri.parse(
      'https://maps.googleapis.com/maps/api/geocode/json?latlng=${coords.latitude},${coords.longitude}&key=$apiKey',
    ),
  );
  if (response.statusCode == 200) {
    return json.decode(response.body);
  } else {
    throw Exception('Failed to fetch address from Google');
  }
}
```

---

## 📚 App Tabs/Pages
- Splash Screen: Startup screen with app branding.
- Home: Lists saved trips, showing the name, date, and basic info.
- Map: Displays all registered trips on an interactive OpenStreetMap.
- Trip Details: Shows detailed info including latitude, longitude, and resolved address (via API).

---

## 🎯 Learning Objectives
- Understand how to integrate maps in Flutter using the flutter_map package.
- Learn how to capture the user’s current location using the geolocator package.
- Perform reverse geocoding with OpenStreetMap Nominatim and Google Maps API.
- Apply state management using simple setState mechanisms.
- Develop fully responsive applications for both Web and Mobile using a single codebase.
- Improve UI/UX design for geolocation apps, focusing on responsiveness and clean layouts.
