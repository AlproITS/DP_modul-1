# Modul 1 Dasar Pemrograman (Control Flow)
## Daftar Isi

- [Control Flow](#control-flow)
- [Percabangan](#percabangan)
    + [If](#percabangan-if)
    + [If-Else](#percabangan-if-else)
    + [If-Else if](#percabangan-if-elseif)
    + [Case Switch](#percabangan-case-switch)
- [Perulangan](#perulangan)
    + [While](#perulangan-while)
    + [For](#perulangan-for)
    + [Do-While](#perulangan-do-while)

# Control Flow
Control Flow adalah cara kita mengatur jalan penyataan, instruksi, dan pemanggilan fungsi  suatu program. Tanpa control flow, program kita hanya bergerak dari atas ke bawah saja (**sequential**). control flow bahasa C ada 2, yaitu percabangan (**selection**) dan perulangan (**repetition**).

# Percabangan
Percabangan memungkinkan kita untuk menentukan kode manakah yang akan kita eksekusi berdasarkan suatu kondisi. Percabangan di bahasa C ada 4, yaitu `if`, `if-else`, `if-else-if`, dan `switch`.

## Percabangan IF

Sintaks yang digunakan dalam percabangan menggunakan if adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>){

		//kode yang akan dieksekusi jika kondisi tersebut benar

}
```
Cara kerja percabangan if yaitu memeriksa dan mengevaluasi suatu kondisi untuk menentukan apakah instruksi selanjutnya dalam bracket akan dijalankan atau tidak oleh program.
- Jika kondisi tersebut bernilai **TRUE (1)**, kode yang di dalam bracket akan **dieksekusi**. 
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode yang di dalam bracket **tidak akan dieksekusi**.
### Contoh
Sebagai contoh, di dashboard mobil terdapat indikator bahan bakar yang akan **menyala jika bahan bakar yang tersisa kurang dari level tertentu (misal kurang dari 10 liter)** dengan kondisi “Apakah bahan bakar kurang dari 10 liter?”.

Pada kasus ini terdapat kondisi
- **Jika bahan bakar kurang dari 10 liter** maka nyalakan lampu indikator.
```c
#include <stdio.h>
int main(void)
{
    int gasoline = 0;
    gasoline = 3;
    if (gasoline < 10) //jika bahan bakar kurang dari 10 liter
    {
        //apa yang perlu dilakukan ketika kondisi terpenuhi?
        printf("Lampu Indikator menyala!\n");
    }
}
```
## Percabangan If Else

Sintaks yang digunakan dalam percabangan menggunakan if-else adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>){

		//kode yang akan dieksekusi jika kondisi tersebut benar

}else{

		//kode yang akan dieksekusi jika kondisi tersebut salah

}
```
Cara kerja percabangan if-else yaitu memeriksa kondisi dalam if.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket if**.
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode di bawah **else** lah **yang akan dijalankan**.
### Contoh
Sebagai contoh, kita ingin mencari tahu apakah seseorang absen dari kelas atau tidak. **Apabila ia tidak hadir, maka absensinya akan dicoret (bernilai X)**, dan **apabila hadir, maka absensinya akan di centang (bernilai V)**.

Sehingga dari kasus tersebut, didapat dua alternatif kondisi.
- **Apabila ia hadir, maka muncul V**
- **Apabila ia tidak hadir, maka muncul X**
```c
#include <stdio.h>
#define DATANG 1
int main(void)
{
    int hadir = DATANG;
    if (hadir) //jika orang tersebut hadir
    {
        printf("V\n");
    }else{
        printf("X\n");
    }
}
```
## Percabangan If-Elseif

Sintaks yang digunakan dalam percabangan menggunakan if-else if adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>){

		//kode yang akan dieksekusi jika kondisi tersebut benar

}else if (<Ekspresi/Kondisi>){

		//kode yang akan dieksekusi jika kondisi tersebut salah

}
// boleh menambahkan else{} apabila perlu
```
Cara kerja percabangan if-else yaitu memeriksa kondisi dalam if.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket if**.
- Apabila kondisi pertama tidak memenuhi, maka ia akan memerika kondisi didalam else if, apabila bernilai **TRUE (1)**, maka ia akan **menjalankan perintah dalam bracket tersebut**, apabila tidak maka ia akan menjalankan sequence selanjutnya.
- Apabila kita menyediakan statement else diakhir, maka ketika **seluruh kondisi** if dan else if tidak memenuhi atau **FALSE (0)**, maka secara otomatis ia akan **menjalankan perintah di dalam else** tersebut.

## Percabangan Case Switch

Selain penggunaan statemen if untuk memilih diantara banyak alternatif, terdapat pula statemen switch yang memiliki fungsi yang sama, untuk memilih diantara banyak alternatif berdasarkan sebuah kondisi. Kondisi pada statemen switch berisi ekspresi yang dapat menggunakan sebuah variable tunggal bertipe int atau char yang akan diperiksa nilainya di setiap blok case.

Sintaks untuk Case Switch:
```c
switch(ekspresi) {

   case ekspresi-konstan  :
      statement;
      break;

   case ekspresi-konstan  :
      statement;
      break;  
   /* anda bisa memiliki jumlah case sebanyak mungkin */
   
   // default ketika tidak ada case yang memenuhi
   default : 
        statement(s);
}
```
Setiap blok, case harus ditambahkan statement **``break``**, karena apabila tidak maka ia akan tetap menjalankan blok case dibawahnya hingga bertemu break lain atau pada akhir blok switch.
### Contoh
```c
#include <stdio.h>
int main(void)
{
    char platNomor;
    printf("Masukkan huruf awal plat nomor anda: ");
    scanf("%c", &platNomor);
    switch(platNomor)
    {
        case 'L':
            printf("Surabaya");
            break;
        case 'B':
        case 'b':
            printf("Jakarta");
            break;
        case 'D':
            printf("Bandung");
            break;
        case 'N':
            printf("Malang/Lumajang");
            break;
        default:
            printf("Karakter plat nomor tidak diketahui");
    } 
    return 0;
}
```
Dalam contoh diatas, **ekspresi** yang digunakan adalah **PlatNomor**, dimana **case-case** nya adalah, huruf plat nomor tersebut, L,B,D,N, dan sebagainya

# Perulangan
Perulangan atau looping memungkinkan kita untuk mengeksekusi potongan kode berulang-ulang hingga mencapai suatu kondisi. Ada 3 jenis perulangan dalam bahasa C, yaitu `while`, `do - while`, dan `for`.

## Perulangan While

