# <h1 align="center">Laporan Praktikum Modul 1 - Codeblocks IDE & Pengenalan Bahas C++ (Bagian Pertama)</h1>
<p align="center">Muhammad Daffa Sha'ib Nandana - 109082500023</p>

## Dasar Teori
Struktur data merupakan cara untuk menyimpan dan mengolah data agar dapat digunakan secara terstruktur dalam program. Pada latihan ini digunakan beberapa konsep dasar pemrograman, yaitu matriks, pointer, reference, array, function, procedure, dan switch-case. Matriks digunakan untuk menyimpan data dalam bentuk baris dan kolom, pointer dan reference digunakan untuk mengakses atau mengubah nilai variabel, sedangkan array digunakan untuk menyimpan beberapa data dengan tipe yang sama. Function dan procedure digunakan untuk membagi program menjadi beberapa bagian agar lebih mudah digunakan dan dipahami



## Unguided 

### 1. Program menerima input dua buah matriks berukuran 3×3, kemudian melakukan operasi penjumlahan, pengurangan, dan perkalian dari kedua matriks tersebut.

#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3];
    int tambah[3][3], kurang[3][3], kali[3][3];

    cout << "Masukkan Matriks A:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cin >> A[i][j];
        }
    }

    cout << "Masukkan Matriks B:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cin >> B[i][j];
        }
    }

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tambah[i][j] = A[i][j] + B[i][j];
            kurang[i][j] = A[i][j] - B[i][j];

            kali[i][j] = 0;
            for (int k = 0; k < 3; k++) {
                kali[i][j] += A[i][k] * B[k][j];
            }
        }
    }

    cout << "\nHasil Penjumlahan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << tambah[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Pengurangan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << kurang[i][j] << " ";
        cout << endl;
    }

    cout << "\nHasil Perkalian:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++)
            cout << kali[i][j] << " ";
        cout << endl;
    }

    return 0;
}

##### Output 1
![Screenshot Output Unguided 1_1] https://github.com/daffaeca-a11y/strukdat-modul-2/blob/main/soal1strukdatmodul2.jpeg

Program di atas menggunakan array dua dimensi untuk menyimpan matriks A dan B dengan ukuran 3×3. Perulangan for digunakan untuk memasukkan dan mengakses setiap elemen matriks. Operasi penjumlahan dilakukan dengan menjumlahkan elemen yang memiliki posisi sama, sedangkan pengurangan dilakukan dengan mengurangkan elemen matriks A dengan B.


### 2. Program digunakan untuk menukar nilai dari tiga variabel dengan memanfaatkan pointer dan reference

A.
#include <iostream>
using namespace std;

void tukar(int *a, int *b, int *c) {
    int temp = *a;
    *a = *b;
    *b = *c;
    *c = temp;
}

int main() {
    int a = 10, b = 20, c = 30;

    cout << "Sebelum ditukar : ";
    cout << a << " " << b << " " << c << endl;

    tukar(&a, &b, &c);

    cout << "Setelah ditukar : ";
    cout << a << " " << b << " " << c << endl;

    return 0;
}

B.
#include <iostream>
using namespace std;

void tukar(int &a, int &b, int &c) {
    int temp = a;
    a = b;
    b = c;
    c = temp;
}

int main() {
    int a = 10, b = 20, c = 30;

    cout << "Sebelum ditukar : ";
    cout << a << " " << b << " " << c << endl;

    tukar(a, b, c);

    cout << "Setelah ditukar : ";
    cout << a << " " << b << " " << c << endl;

    return 0;
}

##### Output 2
![Screenshot Output Unguided 2_1] A. https://github.com/daffaeca-a11y/strukdat-modul-2/blob/main/soal1strukdatmodul2.jpeg B. https://github.com/daffaeca-a11y/strukdat-modul-2/blob/main/soal2Bstrukdatmodul2.jpeg

Program reference memiliki fungsi yang sama dengan pointer, yaitu menukar nilai tiga variabel. Perbedaannya terletak pada parameter fungsi yang menggunakan tanda &. Reference secara langsung mengacu pada variabel asli sehingga perubahan nilai di dalam fungsi akan memengaruhi nilai variabel tersebut.

### 3. Program Mencari Nilai Minimum, Maksimum, dan Rata-rata Array

#include <iostream>
using namespace std;

int cariMinimum(int arr[], int n) {
    int min = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] < min)
            min = arr[i];
    }

    return min;
}

int cariMaksimum(int arr[], int n) {
    int max = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] > max)
            max = arr[i];
    }

    return max;
}

void hitungRataRata(int arr[], int n) {
    int jumlah = 0;

    for (int i = 0; i < n; i++)
        jumlah += arr[i];

    cout << "Nilai rata-rata = " << (double)jumlah / n << endl;
}

int main() {
    int arrA[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = 10;
    int pilihan;

    do {
        cout << "\n--- Menu Program Array ---\n";
        cout << "1. Tampilkan isi array\n";
        cout << "2. Cari nilai maksimum\n";
        cout << "3. Cari nilai minimum\n";
        cout << "4. Hitung nilai rata-rata\n";
        cout << "5. Keluar\n";
        cout << "Pilih menu: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1:
                cout << "Isi array: ";
                for (int i = 0; i < n; i++)
                    cout << arrA[i] << " ";
                cout << endl;
                break;

            case 2:
                cout << "Nilai maksimum = "
                     << cariMaksimum(arrA, n) << endl;
                break;

            case 3:
                cout << "Nilai minimum = "
                     << cariMinimum(arrA, n) << endl;
                break;

            case 4:
                hitungRataRata(arrA, n);
                break;

            case 5:
                cout << "Program selesai.\n";
                break;

            default:
                cout << "Pilihan tidak tersedia.\n";
        }

    } while (pilihan != 5);

    return 0;
}

##### Output 3
![Screenshot Output Unguided 3_1] https://github.com/daffaeca-a11y/strukdat-modul-2/blob/main/soal3strukdatmodul2.jpeg

Program di atas menggunakan array arrA yang berisi {11, 8, 5, 7, 12, 26, 3, 54, 33, 55}. Function cariMinimum() digunakan untuk mencari nilai terkecil dan menghasilkan nilai 3, sedangkan cariMaksimum() digunakan untuk mencari nilai terbesar dan menghasilkan 55. Procedure hitungRataRata() menjumlahkan seluruh elemen array kemudian membaginya dengan jumlah data sehingga diperoleh rata-rata 21,4. Menu program menggunakan switch-case untuk menentukan operasi berdasarkan pilihan pengguna

## Kesimpulan
Kesimpulan dari modul kali ini adalah, matriks dapat digunakan untuk mengolah data dalam bentuk baris dan kolom, sedangkan pointer dan reference dapat digunakan untuk mengubah nilai variabel melalui fungsi. Array dapat digunakan untuk menyimpan kumpulan data dan diolah menggunakan function maupun procedure untuk mendapatkan nilai minimum, maksimum, dan rata-rata.

## Referensi


