# Firebase Authentication with MMKV Storage

Proyek React Native Expo dengan Firebase Authentication dan MMKV untuk penyimpanan credentials yang aman dan performa tinggi.

## Tech Stack

- **React Native** - Framework untuk mobile app
- **Expo** (~54.0.23) - Platform untuk development
- **Firebase** (^12.6.0) - Authentication
- **MMKV** (^4.0.0) - Fast & secure key-value storage
- **Expo Router** (~6.0.14) - File-based routing

## Prerequisites

Sebelum memulai, pastikan Anda telah menginstall:

- [Node.js](https://nodejs.org/) (versi 18 atau lebih tinggi)
- [Xcode](https://developer.apple.com/xcode/) (untuk iOS development)
- [Xcode Command Line Tools](https://developer.apple.com/download/more/)
- [CocoaPods](https://cocoapods.org/) - untuk iOS dependencies

## Setup Project

### 1. Install Dependencies

```bash
npm install
```

### 2. Setup Firebase

Pastikan file `GoogleService-Info.plist` sudah ada di root project untuk konfigurasi Firebase iOS.

## Menjalankan di iOS Simulator

### Metode 1: Development Build (Recommended)

Metode ini melakukan native build dan memberi Anda kontrol penuh terhadap native modules.

**Langkah 1: Prebuild untuk iOS**

```bash
npx expo prebuild --platform ios
```

Command ini akan:
- Membuat folder `ios/` dengan native code
- Menginstall CocoaPods dependencies
- Mengkonfigurasi native modules

**Langkah 2: Jalankan di Simulator**

```bash
npm run ios
```

Atau dengan Expo CLI:

```bash
npx expo run:ios
```

Aplikasi akan otomatis dibuild dan terbuka di iOS Simulator.

**Tips:**
- Build pertama kali membutuhkan waktu lebih lama (5-10 menit)
- Pastikan minimal 1 iOS Simulator sudah terinstall di Xcode
- Untuk memilih device spesifik: `npx expo run:ios --device`

### Metode 2: Expo Go (Untuk Quick Testing)

Metode ini lebih cepat tapi tidak mendukung semua native modules.

```bash
npx expo start
```

Kemudian:
1. Tekan `i` untuk membuka di iOS Simulator
2. Atau scan QR code dengan Expo Go app di iPhone fisik

**Catatan:** MMKV dan beberapa native modules mungkin tidak berfungsi di Expo Go.

## Available Scripts

- `npm start` - Start Expo development server
- `npm run ios` - Run di iOS simulator (development build)
- `npm run android` - Run di Android emulator
- `npm run web` - Run di browser
- `npm run lint` - Lint codebase
- `npm run reset-project` - Reset project ke blank template

## Project Structure

```
├── app/                    # Expo Router screens
│   ├── _layout.tsx        # Root layout
│   ├── index.tsx          # Home screen
│   └── modal.tsx          # Modal screen
├── src/
│   ├── firebaseConfig.ts  # Firebase configuration
│   └── storage/
│       ├── AuthContext.tsx      # Authentication context
│       ├── mmkvCredentials.ts   # MMKV credentials storage
│       └── mmkvUser.ts          # MMKV user data storage
├── components/            # Reusable components
└── constants/            # App constants & themes
```

## Troubleshooting

### Build Gagal di iOS

```bash
# Clear build cache
cd ios
rm -rf build/
pod deintegrate
pod install
cd ..
npx expo run:ios
```

### Simulator Tidak Terbuka

```bash
# List available simulators
xcrun simctl list devices

# Boot specific simulator
xcrun simctl boot "iPhone 15 Pro"

# Then run
npm run ios
```

### Error saat Prebuild

```bash
# Clean dan rebuild
rm -rf ios/ android/
npx expo prebuild --clean
```

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.
