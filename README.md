# Organisasi dan Arsitektur Komputer
# Makro
Apa Itu Makro di Assembly?
Makro adalah cara pintar untuk menulis potongan kode yang sering dipakai berulang-ulang, supaya tidak perlu ngetik ulang instruksi yang sama terus.
  Fungsinya:
Bikin kode lebih rapi dan modular.
Menghemat waktu nulis dan menghindari typo dari ngulang-ngulang instruksi

## hasil running
![Screenshot 2025-04-14 145153](https://github.com/user-attachments/assets/c8910fe7-d012-49a2-93af-b131c5b1f2ea)


## Penjelasan kode
1. Macro tulis_string
%macro tulis_string 2
    mov eax, 4          ; syscall write
    mov ebx, 1          ; file descriptor 1 (stdout)
    mov ecx, %1         ; pointer ke string
    mov edx, %2         ; panjang string
    int 0x80            ; panggil kernel
%endmacro







