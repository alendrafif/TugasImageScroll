# Affirmations App - Android Jetpack Compose

Aplikasi Android yang menampilkan daftar afirmasi positif dengan gambar dan teks inspiratif. Aplikasi ini dibangun menggunakan **Jetpack Compose** dengan pola arsitektur yang clean dan mudah dipahami.
## ✨ Fitur

- **Scrollable List** - Daftar afirmasi yang dapat di-scroll menggunakan LazyColumn
- **Card Layout** - Setiap afirmasi ditampilkan dalam bentuk card yang menarik
- **Image & Text** - Kombinasi gambar dan teks inspiratif untuk setiap afirmasi
- **Material Design 3** - Menggunakan komponen Material Design terbaru
- **Responsive Design** - Layout yang menyesuaikan dengan berbagai ukuran layar
- **Resource Management** - Pengelolaan string dan drawable resources yang terorganisir

## 🛠️ Teknologi yang Digunakan

- **Kotlin** - Bahasa pemrograman utama
- **Jetpack Compose** - UI toolkit modern untuk Android
- **Material Design 3** - Sistem desain Google
- **LazyColumn** - Untuk efficient scrolling performance
- **Data Class** - Untuk model data yang immutable
- **Resource System** - Android resources untuk string dan drawable

## 📋 Persyaratan

- **Android Studio** Hedgehog (2023.1.1) atau yang lebih baru
- **Minimum SDK** 24 (Android 7.0)
- **Target SDK** 34 (Android 14)
- **Kotlin** 1.9.0 atau yang lebih baru

## 🚀 Cara Instalasi

1. **CloneRepository**:
   ```bash
   git clone https://github.com/username/affirmations-app.git
   ```

2. **Buka di Android Studio**

3. **Sync Project** dengan Gradle files

4. **Build dan Run** aplikasi di emulator atau device

## 📁 Struktur Project

```
app/
├── src/main/java/com/example/affirmations/
│   ├── MainActivity.kt              # Activity utama
│   ├── model/
│   │   └── Affirmation.kt          # Data class untuk model afirmasi
│   ├── data/
│   │   └── Datasource.kt           # Sumber data afirmasi
│   └── ui/theme/
│       ├── Theme.kt                # Konfigurasi tema
│       ├── Color.kt                # Definisi warna
│       └── Type.kt                 # Typography
├── res/
│   ├── values/
│   │   └── strings.xml             # String resources untuk afirmasi
│   ├── drawable/                   # Gambar-gambar afirmasi
│   │   ├── image1.jpg
│   │   ├── image2.jpg
│   │   └── ...
│   └── mipmap/                     # App icons
└── build.gradle.kts                # Build configuration
```

## 🏗️ Arsitektur Aplikasi

### Components Overview

#### 1. **MainActivity**
- Entry point aplikasi
- Setup tema dan surface container
- Memanggil `AffirmationsApp` composable

#### 2. **AffirmationsApp**
- Composable utama yang mengatur aplikasi
- Mengambil data dari `Datasource`
- Meneruskan data ke `AffirmationList`

#### 3. **AffirmationList**
- Menampilkan list afirmasi menggunakan `LazyColumn`
- Efficient scrolling untuk performa yang optimal
- Mengatur spacing antar item

#### 4. **AffirmationCard**
- Komponen card individual untuk setiap afirmasi
- Menampilkan gambar dan teks
- Menggunakan Material Design card

### Data Flow

```
Datasource.loadAffirmations() 
    ↓
AffirmationsApp 
    ↓
AffirmationList 
    ↓
AffirmationCard (untuk setiap item)
```

## 📊 Model Data

### Affirmation Data Class
```kotlin
data class Affirmation(
    @StringRes val stringResourceId: Int,    // Resource ID untuk teks afirmasi
    @DrawableRes val imageResourceId: Int    // Resource ID untuk gambar
)
```

### Datasource
```kotlin
class Datasource {
    fun loadAffirmations(): List<Affirmation> {
        return listOf(
            Affirmation(R.string.affirmation1, R.drawable.image1),
            Affirmation(R.string.affirmation2, R.drawable.image2),
            // ... dan seterusnya
        )
    }
}
```

## 🎨 UI Components

### AffirmationCard Features
- **Image Display**:
  - Full width dengan height 194dp
  - ContentScale.Crop untuk aspect ratio yang konsisten
- **Text Styling**:
  - Typography: `headlineSmall`
  - Padding: 16dp
  - Support untuk multi-language

### LazyColumn Benefits
- **Performance**: Hanya render item yang visible
- **Memory Efficient**: Recycle views otomatis
- **Smooth Scrolling**: Optimized untuk large datasets

## 🌐 Internationalization

Aplikasi mendukung multi-bahasa melalui:
- **String Resources** (`res/values/strings.xml`)
- **Localized Resources** (`res/values-id/strings.xml` untuk Bahasa Indonesia)
- **Context-aware string loading**

Contoh penambahan bahasa Indonesia:
```xml
<!-- res/values-id/strings.xml -->
<resources>
    <string name="affirmation1">Saya mampu melakukan hal-hal luar biasa.</string>
    <string name="affirmation2">Saya percaya pada kemampuan diri sendiri.</string>
</resources>
```

## 🔧 Kustomisasi

### Menambah Afirmasi Baru

1. **Tambahkan gambar** di `res/drawable/`
2. **Tambahkan teks** di `res/values/strings.xml`:
   ```xml
   <string name="new_affirmation">Your inspiring text here</string>
   ```
3. **Update Datasource**:
   ```kotlin
   Affirmation(R.string.new_affirmation, R.drawable.new_image)
   ```

### Mengubah Styling

#### Card Appearance
```kotlin
Card(
    modifier = modifier,
    elevation = CardDefaults.cardElevation(defaultElevation = 4.dp),
    colors = CardDefaults.cardColors(containerColor = MaterialTheme.colorScheme.surface)
) {
    // content
}
```

#### Image Styling
```kotlin
Image(
    // ... other parameters
    modifier = Modifier
        .fillMaxWidth()
        .height(200.dp)  // Ubah tinggi gambar
        .clip(RoundedCornerShape(8.dp)), // Tambahkan rounded corners
    contentScale = ContentScale.Crop
)
```


