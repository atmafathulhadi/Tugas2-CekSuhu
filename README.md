
# Aplikasi Konversi Suhu

Aplikasi Konversi Suhu ini adalah aplikasi berbasis Java Swing yang memungkinkan pengguna untuk mengonversi suhu dari satu unit ke unit lainnya, seperti Celsius, Fahrenheit, Reamur, dan Kelvin.

## Fitur

- Mengonversi suhu antara berbagai satuan, seperti:
  - Celsius ke Fahrenheit, Reamur, dan Kelvin
  - Fahrenheit ke Celsius, Reamur, dan Kelvin
  - Reamur ke Celsius, Fahrenheit, dan Kelvin
  - Kelvin ke Celsius, Fahrenheit, dan Reamur
- Input suhu yang validasi otomatis (hanya angka dan desimal)
- Tombol "Konversi" untuk memproses konversi suhu
- Tombol "Hapus" untuk menghapus input dan hasil konversi
- Tombol "Keluar" untuk menutup aplikasi

## Struktur Kode Utama

Berikut adalah deskripsi singkat dari beberapa bagian kode yang utama:

### 1. Inisialisasi Komponen GUI
Kode berikut menginisialisasi komponen GUI seperti `JComboBox`, `JButton`, dan `JLabel` untuk keperluan input dan output aplikasi.

```java
private JComboBox<String> pilihanKonversi;
private JButton tombolKonversi;
private JLabel hasilLabel;
```

### 2. Konfigurasi Aplikasi
Pada konstruktor `KS()`, aplikasi mengatur ukuran jendela, judul, lokasi, dan menambahkan berbagai event listener untuk tombol-tombol di aplikasi.

### 3. Logika Konversi Suhu
Metode `konversiSuhuActionPerformed` menangani logika konversi suhu. Berdasarkan pilihan yang dipilih pada `JComboBox`, aplikasi melakukan perhitungan konversi suhu dan menampilkan hasil pada `jLabel3`.

```java
private void konversiSuhuActionPerformed(java.awt.event.ActionEvent evt) {
    try {
        double suhu = Double.parseDouble(inputSuhu.getText());
        String jenisKonversi = (String) comboBoxKonversi.getSelectedItem();
        double hasil = 0;

        switch (jenisKonversi) {
            case "Celcius ke Fahrenheit":
                hasil = (suhu * 9/5) + 32;
                break;
            case "Celcius ke Reamur":
                hasil = suhu * 4/5;
                break;
            case "Celcius ke Kelvin":
                hasil = suhu + 273.15;
                break;
            // ... kasus konversi lainnya ...
            default:
                jLabel3.setText("Jenis konversi tidak valid!");
                return;
        }
        jLabel3.setText("Hasil: " + hasil);
    } catch (NumberFormatException e) {
        jLabel3.setText("Input tidak valid!");
    }
}
```

### 4. Validasi Input
Event listener `KeyAdapter` memastikan hanya angka dan titik desimal yang bisa diinputkan pada `inputSuhu` untuk mencegah kesalahan format input.

```java
inputSuhu.addKeyListener(new KeyAdapter() {
    @Override
    public void keyTyped(KeyEvent e) {
        char c = e.getKeyChar();
        if (!Character.isDigit(c) && c != '.') {
            e.consume(); 
        }
    }
});
```

### 5. Tombol Reset dan Keluar
- Tombol "Hapus" membersihkan input dan hasil konversi.
- Tombol "Keluar" menutup aplikasi.

```java
jButton2.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent evt) {
        inputSuhu.setText(""); 
        jLabel3.setText(""); 
    }
});

exit.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent evt) {
        System.exit(0);
    }
});
```

## Cara Menjalankan Aplikasi

1. Pastikan Anda sudah memiliki JDK terinstal.
2. Kompilasi file `KS.java`:
   ```bash
   javac KS.java
   ```
3. Jalankan aplikasi:
   ```bash
   java KS
   ```

## Screenshot

![S]([screenshot.png](https://github.com/atmafathulhadi/Tugas2-CekSuhu/blob/main/S.png))

---

Dengan README ini, Anda dapat lebih mudah memahami fungsi dan cara kerja aplikasi konversi suhu di Java Swing.


## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    10    |
|  2  | Logika Program   |    10    |
|  3  | Kesesuaian UI    |    20    |
|  4  | Constructor      |    10    |
|  5  | Memenuhi Variasi |    50    |
|     | *TOTAL*        | *100* |
