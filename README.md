# Modul 1 Dasar Pemrograman (Control Flow)
## Daftar Isi

- [Control Flow](#control-flow)
- [Percabangan](#percabangan)
    + [If](#percabangan-if)
    + [If-Else](#percabangan-if-else)
    + [If-Else if](#percabangan-if-elseif)
    + [Switch-Case](#percabangan-switch-case)
    + [Operator Kondisional ( ? : )](#operator-kondisional--)
- [Perulangan](#perulangan)
    + [While](#perulangan-while)
    + [Do-While](#perulangan-do-while)
    + [For](#perulangan-for)
- [Break and Continue](#break-and-continue)
- [Infinite Loop](#infinite-loop)
- [Latihan Soal](#latihan-soal)

# Control Flow
Control Flow adalah cara kita mengatur jalan penyataan, instruksi, dan pemanggilan fungsi  suatu program. Tanpa control flow, program kita hanya bergerak dari atas ke bawah saja (**sequential**). control flow bahasa C ada 2, yaitu percabangan (**selection**) dan perulangan (**repetition**).

# Percabangan
Percabangan memungkinkan kita untuk menentukan kode manakah yang akan kita eksekusi berdasarkan suatu kondisi. Percabangan di bahasa C ada 4, yaitu `if`, `if-else`, `if-else if`, dan `switch`.

## Percabangan If

Sintaks yang digunakan dalam percabangan menggunakan `if` adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>) {

    //kode yang akan dieksekusi jika kondisi tersebut benar

}
```
Cara kerja percabangan if yaitu memeriksa dan mengevaluasi suatu kondisi untuk menentukan apakah instruksi selanjutnya dalam bracket akan dijalankan atau tidak oleh program.
- Jika kondisi tersebut bernilai **TRUE (1)**, kode yang di dalam bracket akan **dieksekusi**. 
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode yang di dalam bracket **tidak akan dieksekusi**.

Contoh

Sebagai contoh, di dashboard mobil terdapat indikator bahan bakar yang akan **menyala jika bahan bakar yang tersisa kurang dari level tertentu (misal kurang dari 10 liter)** dengan kondisi “Apakah bahan bakar kurang dari 10 liter?”.

Pada kasus ini terdapat kondisi
- **Jika bahan bakar kurang dari 10 liter** maka nyalakan lampu indikator.
```c
#include <stdio.h>
int main()
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
Output
```
Lampu Indikator menyala!
```

## Percabangan If Else

Sintaks yang digunakan dalam percabangan menggunakan `if-else` adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>) {

    //kode yang akan dieksekusi jika kondisi tersebut benar

}else {

    //kode yang akan dieksekusi jika kondisi tersebut salah

}
```
Cara kerja percabangan if-else yaitu memeriksa kondisi dalam if.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket if**.
- Sebaliknya jika kondisi tersebut bernilai **FALSE (0)**, kode di bawah **else** lah **yang akan dijalankan**.

Contoh

Sebagai contoh, kita ingin mencari tahu apakah seseorang absen dari kelas atau tidak. **Apabila ia tidak hadir, maka absensinya akan dicoret (bernilai X)**, dan **apabila hadir, maka absensinya akan di centang (bernilai V)**.

Sehingga dari kasus tersebut, didapat dua alternatif kondisi.
- **Apabila ia hadir, maka muncul V**
- **Apabila ia tidak hadir, maka muncul X**
```c
#include <stdio.h>
#define DATANG 1

int main()
{
    int hadir = DATANG;
    if (hadir) //jika orang tersebut hadir
    {
        printf("V\n");
    } else {
        printf("X\n");
    }
}
```
Output
```
V
```

## Percabangan If-Else if

Sintaks yang digunakan dalam percabangan menggunakan `if-else if` adalah sebagai berikut.
```c
if (<Ekspresi/Kondisi>) {

    //kode yang akan dieksekusi jika kondisi tersebut benar

}else if (<Ekspresi/Kondisi>) {

    //kode yang akan dieksekusi jika kondisi tersebut salah

}
// boleh menambahkan else{} apabila perlu
```
Cara kerja percabangan if-else yaitu memeriksa kondisi dalam if.
- Jika kondisi tersebut bernilai **TRUE (1)**, Program akan **menjalankan kode di dalam bracket if**.
- Apabila kondisi pertama tidak memenuhi, maka ia akan memerika kondisi didalam else if, apabila bernilai **TRUE (1)**, maka ia akan **menjalankan perintah dalam bracket tersebut**, apabila tidak maka ia akan menjalankan sequence selanjutnya.
- Apabila kita menyediakan statement else diakhir, maka ketika **seluruh kondisi** if dan else if tidak memenuhi atau **FALSE (0)**, maka secara otomatis ia akan **menjalankan perintah di dalam else** tersebut.

## Percabangan Switch-Case

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
        statement;
}
```
Setiap blok, case harus ditambahkan statement **``break``**, karena apabila tidak maka ia akan tetap menjalankan blok case dibawahnya hingga bertemu break lain atau pada akhir blok switch.

Contoh

```c
#include <stdio.h>

int main()
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

## Operator Kondisional (` ? : `)

Operator kondisional mempunyai bentuk sintaks

```
(ekspresi/kondisi) ? (ekspresi jika TRUE) : (ekspresi jika FALSE);
```
Operator kondisional adalah satu-satunya operator ternary dalam bahasa C. Operator kondisional bertingkah seperti layaknya percabangan `if - else`. Ekspresi/kondisi yang akan dievaluasi diletakkan sebelum tanda tanya (`?`). Apabila menghasilkan TRUE, akan menjalankan bagian di kiri tanda titik dua. Jika FALSE, akan menjalankan bagian di kanan tanda titik dua.

Contoh :

```c
#include <stdio.h>

int main()
{
    int mark;
    
    scanf("%d", &mark);
    printf(mark >= 75 ? "Lulus\n" : "Tidak Lulus\n");
    return 0;
}
```

Program di atas ekuivalen dengan :

```c
#include <stdio.h>

int main()
{
    int mark;
    
    scanf("%d", &mark);
    if (mark >= 75) {
        printf("Lulus\n");
    }
    else {
        printf("Tidak Lulus\n");
    }
    return 0;
}
```

# Perulangan

Perulangan atau looping memungkinkan kita untuk mengeksekusi potongan kode berulang-ulang hingga mencapai suatu kondisi. Ada 3 jenis perulangan dalam bahasa C, yaitu `while`, `do - while`, dan `for`.

## Perulangan While

Perulangan `while` adalah bentuk perulangan yang paling sederhana. Sintaksnya adalah sebagai berikut.

```c
//initial value misal, i = 0
while (<Ekspresi/Kondisi>) {
    // Potongan kode yang ingin dieksekusi
    .
    .
    .
    // increment/decrement misalnya, i++
}
```
Cara kerja perulangan while mirip dengan if. Jika pada **if** potongan kode akan dieksekusi **sekali saja** apabila ekspresi/kondisi bernilai **TRUE**, pada **while** potongan kode akan **terus dieksekusi** hingga ekspresi/kondisi menghasilkan **FALSE**.

Contoh

```c
#include <stdio.h>

int main()
{
    int i = 0;
    while (i < 10)
    {
        printf("Hello World! ke-%d \n",i);
        i++;
    }
    return 0;
}
```

Sehingga pada contoh diatas :

- Pada awalnya, **variabel `i`** bernilai 0. 
- Sequence selanjutnya adalah while, dan i bernilai kurang dari 10 (**TRUE**), maka kode didalam while akan dijalankan, yakni print Hello world ke-i. 
- Setelah melakukan print hello world, variabel **i** akan di increment, dan kembali ke statement while untuk memeriksa apakah **i** masih kurang dari 10 setelah diincrement
- Karena setelah **`i`** di-increment nilainya masih 1 dan kurang dari 10, maka while akan dijalankan lagi hingga **`i`** bernilai 10 yang berarti tidak memenuhi kondisi while.

## Perulangan Do-While

Sintaks dari perulangan `do – while` adalah sebagai berikut.
```c
do {
    // Potongan kode yang dieksekusi.
    .
    .
    // increment/decrement
} while (<Ekspresi/Kondisi>)
```

Cara kerja dari perulangan `do – while` mirip dengan perulangan while. Hanya saja, pada perulangan `do – while`, potongan kode dijamin akan dieksekusi tepat satu kali sebelum mengevaluasi ekspresi/kondisi.

Contoh

```c
#include <stdio.h>
int main()
{
    int num = 0;
    do
    {
        printf("Num sekarang adalah %d\n",num);
        printf("Masukkan bilangan integer positif (-1 untuk keluar ): ");
        scanf("%d", &num);
    } while (num != -1);
    return 0;
}
```

## Perulangan For

Perulangan `for` merupakan perulangan paling rumit diantara perulangan lainnya. Sintaksnya adalah sebagai berikut.

```c
for (init_statement; kondisi/ekspresi; end_statement) {
    //  Potongan kode yang dieksekusi
    .
    .
}
```

Cara kerjanya adalah sebagai berikut :
- Bagian `init_statement` digunakan untuk inisialisasi variabel yang akan digunakan dalam perulangan. Bagian ini hanya dijalankan sekali saka pada saat awal perulangan.
- Selanjutnya `kondisi/ekspresi` akan dievaluasi. Jika menghasilkan **TRUE**, maka akan mengeksekusi potongan kode. Jika menghasilkan **FALSE**, perulangan berhenti.
- Setelah potongan kode selesai dieksekusi, akan mengeksekusi bagian `end_statement`. Biasanya bagian ini digunakan sebagai **increment/decrement**.
- Lalu akan **mengevaluasi ekspresi/kondisi lagi**, dan begitu seterusnya.

Contoh

```c
#include <stdio.h>
int main()
{
    int i;
    //    init;condition; increment
    for (i = 0; i < 10  ; i++) {
        printf("Hello World!\n");
    }
}
```
1. Awalnya i bernilai 0
2. For statement akan memeriksa nilai i apakah kurang dari 10
3. Apabila **TRUE** maka jalankan kode dalam for block, yakni print hello world
4. Setelah command dalam block for selesai dijalankan, maka variabel i akan diincrement, dan di periksa lagi.
5. Apabila i kurang dari 10, maka command dalam block dieksekusi, apabila tidak maka for loop akan berhenti

## Perulangan/Percabangan Bersarang (Nested)

Percabangan dan Perulangan juga dapat dibuat secara bersarang (membuat percabangan/perulangan di dalam percabangan/perulangan), tentu saja menyesuaikan kebutuhan. Contoh berikut adalah perulangan `for` bersarang.
```c
int i, j;
for (i = 1; i <= 10; ++i) {
    // Statement yang ingin dijalankan pada level terluar

    for (j = 1; j <= 10; j++) {
        // Statement yang ingin dijalankan pada level terdalam

        // Percabangan di dalam perulangan
        if (i == 10) {
            // Lakukan sesuatu
        }
    }
    // Statement yang ingin dijalankan pada level terluar
}
```

# Break and Continue
Keyword `break` dan `continue` digunakan untuk mengendalikan (kontrol) alur pada perulangan. Berikut penjelasannya.
## Break
Perintah `break` digunakan untuk **menghentikan** perulangan (secara paksa). Apabila perintah `break` pada suatu perulangan dijalankan, maka perulangan tersebut akan **dihentikan (secara paksa) dari titik dimana perintah break muncul**.

Contoh

```c
#include <stdio.h>

int main()
{
	int i;
	for (i = 1; i <= 6; i++) {
		printf("%d\n", i);
		//   Jika i adalah 4, maka keluar dari perulangan
		if (i == 4) {
			break;
		}
	}
	return 0;
}
```

## Continue

Kebalikan dari perintah break, perintah `continue` digunakan untuk **melanjutkan perulangan**. Pada perulangan, apabila menemui perintah `continue`, maka perintah-perintah di bawah `continue` akan **diabaikan** dan **kembali akan mengevaluasi ekspresi/kondisi**. Sedangkan pada perulangan for akan langsung mengekekusi bagian end_statement kemudian mengevaluasi ekspresi/kondisi.

Contoh

```c
#include <stdio.h>

int main()
{
	int i;
    for (i = 1; i <= 6; i++) {
	    // Jika i adalah 4, maka abaikan perintah printf()
        if (i == 4) {
            continue;
        }
        printf("%d\n",i);
    }
    return 0;
}
```

# Infinite Loop

Infinite loop adalah kasus dimana perulangan tidak akan pernah berhenti. Hal ini terjadi karena perulangan tidak akan pernah menemui kondisi yang membuatnya berhenti. Contoh di bawah akan menghasilkan infinite loop.

```c
#include <stdio.h>

int main()
{
    int i;
    for (i = 1; i <= 100; i--) {
        // Perulangan tak akan pernah berhenti
    }
}
```

# Latihan Soal
_Harap tidak melakukan tindakan **plagiarisme** dalam pengerjaan !_

1. Buat program yang mencetak kata `Ganjil` untuk bilangan ganjil, dan kata `Genap` untuk bilangan genap dari sebuah input, contoh

    Input

    ```
    1
    ```

    Output

    ```
    Ganjil
    ```

2. Buat program untuk mencetak asterisk, `*`, untuk bilangan genap, dan bilangan aslinya untuk bilangan ganjil, dari n buah bilangan mulai 1 s.d n, contoh

    Input

    ```
    6
    ```

    Output

    ```
    1 * 3 * 5 *
    ```
    
3. Buat program untuk mencetak asterisk, `*`, untuk bilangan prima, dan angka asli untuk bilangan non-prima dari n buah bilangan mulai 2 s.d n, contoh

    Input

    ```
    10
    ```

    Output

    ```
    * * 4 * 6 * 8 9 10
    ```

## Referensi
- https://www.tutorialspoint.com/cprogramming/c_decision_making.htm
- https://en.wikipedia.org/wiki/Control_flow
- https://training.ia-toki.org/
