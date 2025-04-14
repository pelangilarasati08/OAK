# Organisasi dan Arsitektur Komputer
# Makro
Apa Itu Makro di Assembly?
Makro adalah cara pintar untuk menulis potongan kode yang sering dipakai berulang-ulang, supaya tidak perlu ngetik ulang instruksi yang sama terus.
  Fungsinya:
Bikin kode lebih rapi dan modular.
Menghemat waktu nulis dan menghindari typo dari ngulang-ngulang instruksi

## hasil running

![Screenshot 2025-04-14 152322](https://github.com/user-attachments/assets/5b674be5-db76-43b6-b3af-d51cde88914e)



## Penjelasan kode
## 1. Macro tulis_string

![Screenshot 2025-04-14 150746](https://github.com/user-attachments/assets/4c571bf1-b66e-478d-9876-55495ed426bb)

Penjelasan:

1.Macro: Macro adalah potongan kode yang bisa dipanggil di tempat lain di dalam program. Pada kode di atas, tulis_string adalah sebuah macro yang membutuhkan dua parameter.

2.Instruksi dalam macro:

* mov eax, 4: Memasukkan nilai 4 ke register eax. Ini mengindikasikan bahwa kita ingin menggunakan syscall write. 4 adalah nomor syscall untuk menulis ke file (dalam hal ini stdout).

* mov ebx, 1: Memasukkan nilai 1 ke register ebx, yang menunjukkan file descriptor untuk stdout (layar).

* mov ecx, %1: Memindahkan nilai parameter pertama (%1, yaitu alamat string yang akan ditulis) ke register ecx. ecx menyimpan alamat atau pointer ke string yang ingin kita tulis.

* mov edx, %2: Memindahkan nilai parameter kedua (%2, yaitu panjang string) ke register edx. edx menyimpan panjang string yang akan ditulis.

* int 0x80: Ini adalah interrupt untuk mengakses layanan sistem (syscall) Linux. Ketika dipanggil dengan eax = 4, kernel akan menulis data dari alamat yang ada di ecx ke file descriptor yang ada di ebx dengan panjang yang ada di edx.

## 2. Section .text

   ![Screenshot 2025-04-14 151146](https://github.com/user-attachments/assets/2d46ab8a-a360-404e-89f5-0cffbc86aedc)

   penjelasan

 * section .text: Bagian ini adalah tempat kode eksekusi program ditulis. Semua instruksi yang akan dijalankan ada di sini.

* global _start: Menandakan bahwa label _start adalah titik awal program, sehingga linker bisa menghubungkannya.

_start: Label _start adalah titik masuk dari program. Di sinilah eksekusi program dimulai.

* tulis_string pesan1, len1: Memanggil macro tulis_string dengan parameter pesan1 dan len1. Ini akan menulis string pesan1 yang memiliki panjang len1 ke layar.

* tulis_string pesan2, len2: Memanggil macro tulis_string lagi dengan parameter pesan2 dan len2. Ini akan menulis string pesan2 ke layar.

* tulis_string pesan3, len3: Memanggil macro tulis_string dengan parameter pesan3 dan len3. Ini akan menulis string pesan3 ke layar.

* Syscall exit:

   -mov eax, 1: Menyiapkan syscall exit, yang memiliki nomor 1.

   -xor ebx, ebx: Mengatur nilai register ebx ke 0 menggunakan operasi XOR. Nilai 0 ini adalah return code untuk program yang mengindikasikan eksekusi sukses.

   -int 0x80: Memanggil syscall dengan nomor 1 (exit), yang akan mengakhiri program dan keluar dengan status kode 0.

  ## 3. Section .data


![Screenshot 2025-04-14 151804](https://github.com/user-attachments/assets/9482da50-1f33-41b9-a25b-bcd335826fc7)


  penjelasan kode

* section .data: Ini adalah tempat untuk mendeklarasikan data yang digunakan dalam program. Data yang didefinisikan di sini adalah string yang akan dicetak oleh program.

* pesan1: Mendefinisikan string 'assembly bellshade' diikuti oleh 0xA (newline) dan 0xD (carriage return). 0xA dan 0xD digunakan untuk membuat string baru (baris baru) di output.

* len1: len1 adalah panjang dari string pesan1. Menggunakan $ - pesan1 untuk menghitung panjang string, di mana $ adalah alamat saat ini (di akhir string pesan1), dan pesan1 adalah alamat awal string. Selisih ini memberikan panjang string.

* pesan2 dan pesan3: Sama seperti pesan1, mendefinisikan dua string lain yang juga diakhiri dengan 0xA dan 0xD untuk memastikan outputnya diakhiri dengan baris baru.

* len2 dan len3: Sama seperti len1, ini menghitung panjang string pesan2 dan pesan3 masing-masing.

  










