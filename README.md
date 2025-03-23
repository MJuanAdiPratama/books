# Books

M Juan Adi Pratama - 1122140109  
Flutter project yang menjalankan operasi asyncronous dan integrasi API.

## Laporan Praktikum

### Soal no 1
menambahkan nama panggilan pada title app sebagai identitas hasil pekerjaaan.

```dart
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Juan',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      home: const FuturePage(),
    );
  }
```

### Soal no 2

Implementasi pencarian buku menggunakan Google Books API.
[Lihat contoh buku Mantappu Jiwa](https://www.google.co.id/books/edition/Mantappu_Jiwa_Buku_Latihan_Soal/TzCyDwAAQBAJ)

![Hasil Pencarian Buku](/images/soal2.png)

### Soal no 3

```dart
    onPressed: () {
        setState(() {});
        getData()
        .then((value) {
            result = value.body.toString().substring(0, 450);
            setState(() {});
        })
        .catchError((_) {
            result = 'An error occured';
            setState(() {});
        });
    },
```

#### Penjelasan:

- **Substring**: Untuk mengambil 450 karakter dari awal respons.
- **Catch Error**: Untuk menangkap jika terjadi error pada pemanggilan data.
- **Set State**: Untuk memperbarui UI.

#### Demo

<img src="images/soal3.gif" alt="Capture no 3" width="300">

### Soal no 4

#### Langkah 1

```dart
Future<int> returnOneAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 1;
  }

Future<int> returnTwoAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 2;
  }

Future<int> returnThreeAsync() async {
    await Future.delayed(const Duration(seconds: 3));
    return 3;
  }
```

#### Langkah 2

```dart
Future count() async {
    int total = 0;
    total = await returnOneAsync();
    total += await returnTwoAsync();
    total += await returnThreeAsync();
    setState(() {
      result = total.toString();
    });
  }
```

#### Penjelasan:

- **Fungsi returnOneAsync()**: Untuk mengembalikan nilai 1 setelah 3 detik.
- **Fungsi returnTwoAsync()**: Untuk mengembalikan nilai 2 setelah 3 detik.
- **Fungsi returnThreeAsync()**: Untuk mengembalikan nilai 3 setelah 3 detik.
- **Fungsi count() async**:  Untuk menghitung total dari ketiga angka tersebut, Setelah total dihitung hasilnya diubah menjadi teks dan ditampilkan di UI menggunakan setState(), jadi total waktu proses 9 detik.

#### Demo

<img src="images/soal4.gif" alt="Capture no 4" width="300">

### Soal no 5

#### Langkah 2

```dart
  late Completer completer;

  Future getNumber() {
    completer = Completer<int>();
    calculate();
    return completer.future;
  }

  Future calculate() async {
    await Future.delayed(const Duration(seconds: 5));
    completer.complete(42);
  }
```

#### Penjelasan:

- **late Completer**: Menggunakan late karena akan diinisialisasi nanti. Completer untuk mengontrol penyelesaian dari Future secara manual.
- **getNumber()**: Membuat objek integer untuk menangkap hasil yang akan diterima, memanggil fungsi calculate untuk memulai proses perhitungan, mengembalikan future yang akan diselesaikan setelah proses selesai.
- **calculate()**: Menunggu 5 detik menggunakan Future.delayed(), setelah itu completer.complete(42) diaktifkan, yang berarti future di dalam getNumber() selesai dan menghasilkan angka 42.

#### Demo

<img src="images/soal5.gif" alt="Capture no 5" width="300">

### Soal no 6

#### Langkah 5 dan 6

```dart
  calculate2() async {
    try {
      await new Future.delayed(const Duration(seconds: 5));
      completer.complete(42);
    } catch (_) {
      completer.completeError({});
    }
  }

  getNumber()
    .then((value) {
        setState(() {
            result = value.toString();
        });
    })
    .catchError((e) {
        result = 'An error occured';
    });
```

#### Penjelasan:

- **Perbedaan**:

1. Penanganan Error

    - Sebelumnya: Tidak ada penanganan error
    - Sekarang: Menggunakan try-catch untuk menangkap error yang mungkin terjadi

2. Complete Error

    - Sebelumnya: Hanya bisa menyelesaikan dengan hasil yang sukses, seperti completer.complete(42).
    - Sekarang: Selain menyelesaikan dengan hasil sukses, juga bisa menyelesaikan dengan error menggunakan completer.completeError().

    - **Fungsi getNumber()**: jika terjadi kesalahan di fungsi calculate(), error tersebut akan diteruskan (propagate) dan ditangkap. Jika ada error, pesan kesalahan akan ditampilkan di antarmuka pengguna (UI).

#### Demo

<img src="images/soal5.gif" alt="Capture no 6" width="300">

### Soal no 7

#### Demo

<img src="images/soal4.gif" alt="Capture no 6" width="300">

### Soal no 8

#### Perbedaaan Langkah 1 & 4

```dart
    // Langkah 1
    FutureGroup<int> futureGroup = FutureGroup<int>();
    futureGroup.add(returnOneAsync());
    futureGroup.add(returnTwoAsync());
    futureGroup.add(returnThreeAsync());
    futureGroup.close();
    futureGroup.future.then((List<int> value) {
      int total = 0;
      for (var element in value) {
        total += element;
      }
      setState(() {
        result = total.toString();
      });
    });

    // Langkah 4
    final futures = Future.wait<int>([
      returnOneAsync(),
      returnTwoAsync(),
      returnThreeAsync(),
    ]);
```

#### Penjelasan:

- **Perbedaan**:

1. Fleksibilitas:

- FutureGroup: Bisa menambah Future secara dinamis
- Future.wait: Future harus ditentukan saat deklarasi

2. Sintaks:

- FutureGroup: Perlu inisialisasi, penambahan, dan penutupan
- Future.wait: Lebih ringkas dengan satu baris code

### Soal no 9

#### Demo

<img src="images/soal9.gif" alt="Capture no 6" width="300">