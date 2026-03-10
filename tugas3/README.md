### NAMA : Nadin Nabil Hafizh Ayyasy
### NRP : 5025231061
### Kelas : Pemrograman Perangkat Bergerak

### 1. Stateless vs Stateful Widget

#### MyApp (StatelessWidget)

`MyApp` adalah root widget aplikasi yang menggunakan **StatelessWidget**. Widget ini tidak memiliki state yang berubah-ubah dan hanya berfungsi untuk konfigurasi awal aplikasi seperti tema dan home page.

#### RowColumnPage (StatelessWidget)

`RowColumnPage` adalah halaman utama yang juga menggunakan **StatelessWidget**. Widget ini menampilkan layout statis yang tidak memerlukan perubahan state.

#### CounterCard (StatefulWidget)

`CounterCard` adalah widget yang menggunakan **StatefulWidget** karena memiliki data yang berubah (counter). StatefulWidget memiliki:

- **Widget class** (`CounterCard`): Mendefinisikan widget
- **State class** (`_CounterCardState`): Menyimpan dan mengelola state/data yang berubah
- **setState()**: Method untuk memperbarui UI ketika data berubah

### 2. Widget-Widget yang Digunakan

#### MaterialApp

Widget root yang menyediakan struktur Material Design:

```dart
MaterialApp(
  title: 'Flutter Demo',
  theme: ThemeData(...),
  home: const RowColumnPage(),
)
```

#### Scaffold

Menyediakan struktur dasar halaman dengan AppBar dan Body:

```dart
Scaffold(
  appBar: AppBar(...),
  body: Column(...)
)
```

#### AppBar

Header aplikasi di bagian atas:

```dart
AppBar(
  title: const Text('My First App'),
  backgroundColor: Colors.orange[200],
  centerTitle: true,
)
```

- `title`: Judul yang ditampilkan
- `backgroundColor`: Warna latar belakang (orange 200)
- `centerTitle`: Menempatkan judul di tengah

#### Column

Widget layout vertikal yang menyusun children dari atas ke bawah:

```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.center,
  mainAxisAlignment: MainAxisAlignment.center,
  children: <Widget>[...]
)
```

- `crossAxisAlignment`: Alignment horizontal (center)
- `mainAxisAlignment`: Alignment vertikal (center)

#### Container

Widget serbaguna untuk styling dan positioning:

```dart
Container(
  width: MediaQuery.of(context).size.width,
  margin: EdgeInsets.fromLTRB(20.0, 5.0, 20.0, 10.0),
  padding: EdgeInsets.all(20.0),
  color: Colors.lightBlue[100],
  child: ...
)
```

- `width`: Lebar container
- `margin`: Jarak luar (left: 20, top: 5, right: 20, bottom: 10)
- `padding`: Jarak dalam (20 dari semua sisi)
- `color`: Warna background

**Terdapat 4 Container dalam aplikasi:**

1. Container dengan AspectRatio (biru muda) - untuk gambar
2. Container pink untuk teks pertanyaan
3. Container kuning untuk baris icon
4. Container cyan untuk counter

#### AspectRatio

Mempertahankan rasio aspek 1:1 (persegi) untuk container gambar:

```dart
AspectRatio(
  aspectRatio: 1.0,
  child: Container(...)
)
```

#### Image.network

Menampilkan gambar dari URL:

```dart
Image.network(
  'https://picsum.photos/200',
  fit: BoxFit.cover,
  width: 500,
)
```

- `fit: BoxFit.cover`: Gambar memenuhi container
- `width`: Lebar maksimal gambar

#### Text

Menampilkan teks:

```dart
Text('What image is that', style: TextStyle(fontSize: 16))
Text("Counter here: $_counter", style: TextStyle(fontSize: 16))
```

- `style`: Styling teks (ukuran font, warna, dll)
- `$_counter`: String interpolation untuk menampilkan nilai variabel

#### Row

Widget layout horizontal yang menyusun children dari kiri ke kanan:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  crossAxisAlignment: CrossAxisAlignment.start,
  children: <Widget>[...]
)
```

- `mainAxisAlignment.spaceEvenly`: Membagi ruang secara merata
- `crossAxisAlignment.start`: Alignment vertikal di atas

**Terdapat 2 Row dalam aplikasi:**

1. Row untuk 3 kolom icon + text (Food, Scenery, People)
2. Row untuk counter dan tombol increment

#### Icon

Menampilkan icon Material Design:

```dart
Icon(Icons.food_bank)
Icon(Icons.landscape)
Icon(Icons.people)
Icon(Icons.add, color: Colors.black, size: 16)
```

- `Icons.*`: Berbagai icon bawaan Flutter
- `color`: Warna icon
- `size`: Ukuran icon

#### IconButton

Tombol dengan icon yang dapat diklik:

```dart
IconButton(
  onPressed: _incrementCounter,
  icon: Icon(Icons.add, color: Colors.black, size: 16),
)
```

- `onPressed`: Fungsi yang dipanggil saat tombol diklik
- `icon`: Icon yang ditampilkan

### 3. Layout Structure

Struktur layout aplikasi:

```
Scaffold
└── Column (vertikal)
    ├── Container 1: AspectRatio → Image (gambar)
    ├── Container 2: Text (pertanyaan)
    ├── Container 3: Row (horizontal)
    │   ├── Column: Icon + Text (Food)
    │   ├── Column: Icon + Text (Scenery)
    │   └── Column: Icon + Text (People)
    └── CounterCard (StatefulWidget)
        └── Row
            ├── Text (counter value)
            └── IconButton (increment button)
```

### 4. MediaQuery

Digunakan untuk mendapatkan ukuran layar:

```dart
MediaQuery.of(context).size.width
MediaQuery.of(context).size.height
```

Memastikan widget responsive terhadap ukuran layar perangkat.

### 5. State Management (CounterCard)

Contoh sederhana state management:

- **State variable**: `int _counter = 0`
- **Method**: `void _incrementCounter()`
- **setState()**: Memberitahu Flutter untuk rebuild widget dengan nilai baru
- Setiap kali tombol + diklik, counter bertambah dan UI diperbarui
