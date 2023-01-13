# UAS Semester 1

Nama  : Taufik Hidayat

NIM   : 312210674

Kelas : TI.22.B2

## Soal UAS

![Soal](https://user-images.githubusercontent.com/115480692/210613432-4aec9f6e-bda3-42c5-8663-08226bb7442e.png)


## Berikut adalah programnya :

* daftar_nilai.py

berisi modul untuk tambah data, ubah data, cari data, hapus data

    database = {}

    def tambah_data(nama,nim,tugas,uts,uas,akhir):
        database[nama] = nama, nim, tugas, uts, uas, akhir

    def cari_data():
        from view.view_nilai import cari
        cari(input("\nMasukan Nama Yang Ingin dicari = "))

    def hapus_data(nama):
        if nama in database.keys():
            del database[nama]
            return True
        else:
            print(f'Data Dengan Nama {nama} Tidak Ditemukan!')
            return False

    def ubah_data(nama):
        if nama in database.keys():
            del database[nama]
        
        
* view_nilai.py
 
berisi modul untuk cetak daftar nilai, cetak hasil pencarian 

    from model.daftar_nilai import database
    from tabulate import tabulate

    def tampilkan():
        print(tabulate(database.values(), headers=["Nama", "NIM", "Tugas", "UTS", "UAS", "AKHIR"], tablefmt="double_grid"))

    def cari(nama):
        Data_cari = {}
        for key, value in database.items():
            if nama in value:
                Data_cari[key] = value

        print(tabulate(Data_cari.values(), headers=[
            "Nama", "NIM", "Tugas", "UTS", "UAS", "AKHIR"], tablefmt="double_grid"))
    
    
* input_nilai.py

berisi modul untuk input data yang diminta pengguna untuk memasukkan data

    from model.daftar_nilai import tambah_data, hapus_data, ubah_data


    def masukan_data():

        print("|=========================|")
        print("|Silahkan masukkan data : |")
        print("|=========================|")

        nama = input("Masukan Nama = ")
        nim = int(input("Masukan NIM  = "))
        tugas = int(input("Nilai Tugas  = "))
        uts = int(input("Nilai UTS    = "))
        uas = int(input("Nilai UAS    = "))
        akhir = float((0.30 * tugas) + (0.35 * uts) + (0.35 * uas))
        tambah_data(nama,nim,tugas,uts,uas,akhir)

    def hapus():
        hapus_data(input("Masukan Nama yang ingin di Hapus = "))

    def ubah():
        ubah_data(input("Masukan Nama dari Data yang ingin di Ubah = "))
        print("\n:=====================:")
        print(":  Masukan Data Baru  :")
        print(":=====================:")

        nama = input("\nMasukan Nama = ")
        nim = int(input("Masukan NIM = "))
        tugas = int(input("Masukan Nilai Tugas = "))
        uts = int(input("Masukan Nilai UTS = "))
        uas = int(input("Masukan Nilai UAS = "))
        akhir = float((0.30 * tugas) + (0.35 * uts) + (0.35 * uas))
        tambah_data(nama, nim, tugas, uts, uas, akhir)
    
    
* main.py

berisi program utama (menu pilihan yang memanggil semua menu yang ada)

    from view.input_nilai import masukan_data, hapus, ubah
    from view.view_nilai import tampilkan
    from model.daftar_nilai import cari_data

    while True :
        print("-------------------------")
        print("Pilihan Menu : ")
        print("-------------------------")
        print()
        print("1. Tambah Data")
        print("2. Tampilkan semua data")
        print("3. cari Data")
        print("4. hapus data")
        print("5. ubah data")
        print("6. keluar")
        print()

        pilihan = input("Masukkan pilihan menu : ")

        if pilihan == '1':
            masukan_data()

        elif pilihan == '2':
            tampilkan()

        elif pilihan == '3':
            cari_data()

        elif pilihan == '4':
            hapus()

        elif pilihan == '5':
            ubah()

        elif pilihan == '6':
            print("terimakasih")
            break
        else :
            print("silahkan masukkan pilihan yang benar!!!")
            
            
            
            
## Output

![uas 1](https://user-images.githubusercontent.com/115480692/212340641-6cd3d945-5f1e-4f6c-b3f6-b5725ab2e927.png)




![uas 2](https://user-images.githubusercontent.com/115480692/212340820-8ae470b5-078a-4de5-8120-9ae5f6edfdff.png)



