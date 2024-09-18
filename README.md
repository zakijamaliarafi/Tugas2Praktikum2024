# Tugas Pertemuan 2

Nama : Zaki Jamali Arafi

NIM : H1D022048

Shift Baru: D

# Penjelasan Proses Passing Data dari Form ke Tampilan

1. Pengumpulan Data pada FormData
    - Di dalam class `FormDataState`, terdapat tiga `TextEditingController`: `_namaController`, `_nimController`, dan `_tahunController`.
    - Masing-masing controller ini terhubung dengan `TextFormField` di form untuk mengumpulkan data input dari pengguna.

2. Validasi Input
    - Sebelum melakukan passing data, melakukan validasi input menggunakan `_formKey.currentState!.validate()`.
    - Jika validasi berhasil, lanjut ke proses passing data.

3. Persiapan Data
    - Setelah validasi berhasil, mengambil nilai dari setiap controller:
      String nama = _namaController.text;
      String nim = _nimController.text;
      int tahun = int.parse(_tahunController.text);
      

4. Passing Data melalui Constructor
    - Menggunakan `Navigator.of(context).push()` untuk berpindah ke halaman `TampilData`.
    - Saat membuat instance `TampilData`, meneruskan data sebagai parameter constructor:
      Navigator.of(context).push(MaterialPageRoute(
        builder: (context) => TampilData(nama: nama, nim: nim, tahun: tahun)
      ));


5. Penerimaan Data di TampilData
    - Class `TampilData` memiliki constructor yang menerima parameter `nama`, `nim`, dan `tahun`:
      const TampilData({
        Key? key,
        required this.nama,
        required this.nim,
        required this.tahun,
      }) : super(key: key);
    - Data yang diterima kemudian disimpan sebagai properti class.

6. Penggunaan Data di TampilData
    - Di dalam method `build()` dari `TampilData`, menggunakan data yang telah diterima untuk menampilkan informasi:
      Text("Nama: $nama"),
      Text("NIM: $nim"),
      Text("Umur: $umur tahun"),

Dengan pendekatan ini, data input yang dimasukkan oleh pengguna di form `FormData` dapat diteruskan dan ditampilkan di halaman `TampilData`. Proses ini menjaga pemisahan logika input dan tampilan hasil, sambil memastikan alur data yang terstruktur dan efisien.
## Screenshot
Contoh :
<img src="form.png" alt="form" width="300"/>
<img src="hasil.png" alt="hasil" width="300"/>
