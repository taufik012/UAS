# UAS Semester 1

Nama  : Taufik Hidayat

NIM   : 312210674

Kelas : TI.22.B2

## Soal UAS

![Soal](https://user-images.githubusercontent.com/115480692/210613432-4aec9f6e-bda3-42c5-8663-08226bb7442e.png)


## Berikut adalah programnya :

* daftar_nilai.py

berisi modul untuk tambah data, ubah data, cari data, hapus data

a = {}

def tambah(nama, nim, tugas, uts, uas):
    akhir = tugas * 30 / 100 + uts * 35 / 100 + uas * 35 / 100
    a[nama] = nim, tugas, uts, uas, akhir

def hapus(nama):
    if nama in a.keys():
        del a[nama]
        return True
    else:
        print("Nama {0} Tidak Ditemukan".format(nama))
        return False

def ubah(nama):
    if nama in a.keys():
        del a[nama]
        print("Ubah Data")
        from view.input_nilai import input_data
        input_data()

    else:
        print("Nama{0} Tidak Ditemukan".format(nama))

def cari(nama):
    if nama in a.keys():
        print("=================================================================================")
        print("|                            DAFTAR NILAI MAHASISWA                             |")
        print("=================================================================================")
        print("|      Nama      |     NIM     |  Tugas  |   UTS   |   UAS   |    Akhir    |")
        print("=================================================================================")
        print("| {0:14s} | {1:11s} | {2:7d} | {3:7d} | {4:7d} | {5:7f}   |"
              .format(nama, a[nama][1], a[nama][2], a[nama][3], a[nama][4], a[nama][5]))
        print("=================================================================================")
    else:
        print("Nama {0} Tidak Ditemukan".format(nama))
        
        
* view_nilai.py
 
berisi modul untuk cetak daftar nilai, cetak hasil pencarian 

from model.daftar_nilai import a


def header():
    print("   Program Input Nilai   ")
    print("===========================")


def kode_salah():
    print("KODE YANG ANDA MASUKKAN SALAH!")


def tampilkan():
    if a.items():
        print("=================================================================================")
        print("|                            DAFTAR NILAI MAHASISWA                             |")
        print("=================================================================================")
        print("| No |      Nama      |     NIM     |  Tugas  |   UTS   |   UAS   |    Akhir    |")
        print("=================================================================================")
        i = 0
        for b in a.items():
            i += 1
            print("| {no:2d} | {0:14s} | {1:11s} | {2:7d} | {3:7d} | {4:7d} | {5:7f}   |"
                  .format(b[0][: 14], b[1][0], b[1][1], b[1][2], b[1][3], b[1][4], no=i))
        print("=================================================================================")
    else:
        print("=================================================================================")
        print("|                            DAFTAR NILAI MAHASISWA                             |")
        print("=================================================================================")
        print("| No |      Nama      |     NIM     |  Tugas  |   UTS   |   UAS   |    Akhir    |")
        print("=================================================================================")
        print("|                                TIDAK ADA DATA                                 |")
        print("=================================================================================")


def cari():
    from view.input_nilai import cari
    cari()
    
    
* input_nilai.py

berisi modul untuk input data yang diminta pengguna untuk memasukkan data

def input_data():
    from model.daftar_nilai import tambah
    nama = input("Masukkan Nama    : ")se
    nim = input("Masukkan NIM     : ")
    tugas = int(input("Nilai Tugas      : "))
    uts = int(input("Nilai UTS        : "))
    uas = int(input("Nilai UAS        : "))
    tambah(nama, nim, tugas, uts, uas)

def ubah_data():
    from model.daftar_nilai import ubah
    ubah(nama=input("Masukkan Nama    : "))

def hapus_data():
    from model.daftar_nilai import hapus
    hapus(nama=input("Masukkan Nama    : "))

def cari():
    from model.daftar_nilai import cari
    cari(nama=input("Masukkan Nama    : "))
    
    
* main.py

berisi program utama (menu pilihan yang memanggil semua menu yang ada)

from view.input_nilai import input_data, ubah_data, hapus_data

header()
while True:
    c = input("[(L)ihat, (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar] : ")
    if c.lower() == "l":
        tampilkan()
    elif c.lower() == "t":
        input_data()
    elif c.lower() == "c":
        cari()
    elif c.lower() == "u":
        ubah_data()
    elif c.lower() == "h":
        hapus_data()
    elif c.lower() == "k":
        print()
        print("Terima Kasih")
        break
    else:
        kode_salah()
