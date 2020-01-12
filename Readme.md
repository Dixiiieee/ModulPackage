## Tugas PackageModul

Membuat Package dan Modul berdasarkan tugas sebelumnya dengan struktur sebagai berikut : 
- daftar_nilai.py (berisi modul untuk : tambah_data, ubah_data, hapus_data dan cari_data)
- view_nilai.py (berisi modul untuk : cetak_daftar_nilai, cetak_hasil_pencarian)
- input_nilai.py (berisi modul untuk input_data yang meminta pengguna memasukkan data)
- main.py (berisi program utama (menu pilihan yang memanggil semua menu yang ada)

### Syntax dalam daftar_nilai.py

``` python 
from view.input_nilai import *

dataMhs = {}

def tambah_data():
    global dataMhs
    nama = input_nama()
    nim = input_nim()
    nilaiTugas = input_nilaiTugas()
    nilaiUts = input_nilaiUas()
    nilaiUas = input_nilaiUas()
    nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
    dataMhs[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
    print("\nData Berhasil Ditambahkan!")
    return dataMhs

def ubah_data():
    nama = input("Masukkan Nama: ")
    if nama in dataMhs.keys():
        nim           = input_nim()
        nilaiTugas    = input_nilaiTugas()
        nilaiUts      = input_nilaiUts()
        nilaiUas      = input_nilaiUas()
        nilaiAkhir    = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMhs[nama]  = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Di Update!")
    else:
        print("Data tidak ditemukan!")

def hapus_data():
    nama = input("Masukkan Nama:  ")
    if nama in dataMhs.keys():
        del dataMhs[nama]
        print("Data",nama,"Telah dihapus!")
    else:
        print("Data Mahasiswa Tidak Ada".format(nama))
```
        

### Syntax dalam view_nilai.py

``` python
from model.daftar_nilai import *

def cetak_daftar_nilai():
    if dataMhs.items():
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        i = 0
        for x in dataMhs.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2],
                                                                                        x[1][3], x[1][4], i))
        print("==================================================================")
    else:
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        print("|                          TIDAK ADA DATA!                       |")
        print("==================================================================")

def cetak_hasil_pencarian():
    nama = input("Masukkan Nama        : ")
    if nama in dataMhs.keys():
        print("\n                   DAFTAR NILAI MAHASISWA                   ")
        print("==============================================================")
        print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
        print("==============================================================")
        print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMhs[nama][0], dataMhs[nama][1],
                                                                            dataMhs[nama][2], dataMhs[nama][3],
                                                                            dataMhs[nama][4]))
        print("==============================================================")
    else:
        print("Datanya {0} Tidak Ada ".format(nama))
```

### Syntax dalam input_nilai.py

``` python
def input_nama():
    global nama
    nama = input("Masukkan Nama        : ")
    return nama

def input_nim():
    global nim
    nim = input("Masukkan NIM         : ")
    return nim

def input_nilaiTugas():
    global nilaiTugas
    nilaiTugas = int(input("Masukkan Nilai Tugas : "))
    return nilaiTugas

def input_nilaiUts():
    global nilaiUts
    nilaiUts = int(input("Masukkan Nilai UTS   : "))
    return nilaiUts

def input_nilaiUas():
    global nilaiUas
    nilaiUas = int(input("Masukkan Nilai UAS   : "))
    return nilaiUas
```
### Syntax dalam main.py

``` python
from view.view_nilai import *

while True:
    c = input("\nA)dd, E)dit, S)earch, D)elete L)ist, Q)uit: ")

    if (c.lower() == 'a'):
        tambah_data()

    elif (c.lower() == 'e'):
        ubah_data()

    elif (c.lower() == 's'):
        cetak_hasil_pencarian()

    elif (c.lower() == 'd'):
        hapus_data()

    elif (c.lower() == 'l'):
        cetak_daftar_nilai()

    elif (c.lower() == 'q'):
        break

    else:
        print("Menu yang anda maksud tidak tersedia, Silahkan pilih menu yang tersedia")
```

### Hasil Output
![abc](https://user-images.githubusercontent.com/56240134/72216687-088b5f80-3557-11ea-9d79-7c0bc92ec5a8.png)
![abcd](https://user-images.githubusercontent.com/56240134/72216689-0a552300-3557-11ea-873f-4b270654f99e.png)
