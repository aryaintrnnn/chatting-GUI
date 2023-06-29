
# Chatting App with GUI (Python)

Sebuah aplikasi chatting dengan tampilan GUI dan menggunakan bahasa pemograman python.


## Penjelasan

* Client

```bash

1. Impor modul:
   - `socket`: Digunakan untuk komunikasi jaringan menggunakan soket.
   - `threading`: Digunakan untuk mengatur thread terpisah untuk tugas-tugas yang berbeda.
   - `tkinter`: Modul GUI bawaan Python.
   - `tkinter.scrolledtext`: Digunakan untuk membuat area teks yang dapat di-scroll di GUI.
   - `simpledialog` dari tkinter: Digunakan untuk memunculkan dialog sederhana untuk memasukkan nickname.

2. Mendefinisikan HOST dan PORT:
   - `HOST = '127.0.0.1'`: Menetapkan alamat loopback IP (localhost) sebagai host.
   - `PORT = 9090`: Menetapkan nomor port yang akan digunakan untuk koneksi soket.

3. Kelas Client:
   - Metode `__init__(self, host, port)`: Inisialisasi objek client. Membuka koneksi soket ke server, meminta pengguna untuk memasukkan nickname melalui dialog, dan memulai dua thread terpisah untuk GUI dan menerima pesan.
   
   - Metode `gui_loop(self)`: Mengatur tampilan GUI menggunakan Tkinter. Ini mencakup label, area teks untuk pesan chat, area masukan, dan tombol kirim. Metode ini juga mengatur jendela utama Tkinter dan menangani penutupannya.
   
   - Metode `write(self)`: Mengirim pesan yang ditulis oleh pengguna melalui soket ke server. Mengambil isi dari area masukan, menyimpannya dalam format pesan yang sesuai, dan mengirimkannya melalui soket.
   
   - Metode `stop(self)`: Menutup koneksi soket, menghentikan aplikasi, dan menutup jendela GUI.
   
   - Metode `receive(self)`: Menerima pesan dari server secara terus-menerus. Jika pesan yang diterima adalah 'NICK', mengirim nickname pengguna ke server. Jika bukan, menampilkan pesan tersebut di area teks GUI.

4. Membuat objek Client:
   - Membuat objek client dengan menggunakan HOST dan PORT yang telah ditentukan sebelumnya.
```

* server

```bash
1. Impor modul:
   - `socket`: Digunakan untuk komunikasi jaringan menggunakan soket.
   - `threading`: Digunakan untuk mengatur thread terpisah untuk klien yang terhubung.

2. Mendefinisikan HOST dan PORT:
   - `HOST = '127.0.0.1'`: Menetapkan alamat loopback IP (localhost) sebagai host.
   - `PORT = 9090`: Menetapkan nomor port yang akan digunakan untuk koneksi soket.

3. Membuat soket server:
   - `server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`: Membuat objek soket menggunakan alamat IPv4 (AF_INET) dan protokol TCP (SOCK_STREAM).
   - `server.bind((HOST, PORT))`: Mengikat (bind) soket ke alamat dan port yang ditentukan.
   - `server.listen()`: Mengaktifkan soket server untuk menerima koneksi.

4. Membuat daftar klien dan daftar nickname:
   - `clients = []`: Daftar untuk menyimpan objek soket klien yang terhubung.
   - `nicknames = []`: Daftar untuk menyimpan nickname dari setiap klien yang terhubung.

5. Metode `broadcast(message)`: Mengirim pesan ke semua klien yang terhubung. Metode ini akan mengirim pesan ke setiap objek soket klien dalam daftar `clients`.

6. Metode `handle(client)`: Menangani pesan yang diterima dari klien tertentu. Metode ini akan menerima pesan dari klien, mencetak pesan beserta nickname klien yang mengirimnya, dan mengirim pesan tersebut ke semua klien yang terhubung menggunakan metode `broadcast()`. Jika ada kesalahan dalam menerima pesan, seperti koneksi terputus, klien akan dihapus dari daftar `clients` dan nickname klien juga akan dihapus dari daftar `nicknames`.

7. Metode `receive()`: Menunggu koneksi baru dari klien. Metode ini akan menerima koneksi baru menggunakan metode `accept()` pada soket server. Setelah koneksi diterima, nickname klien akan diminta dan disimpan dalam daftar `nicknames`. Objek soket klien juga akan disimpan dalam daftar `clients`. Selanjutnya, pesan bergabung akan dikirim ke semua klien menggunakan metode `broadcast()`. Metode ini juga memulai thread terpisah untuk menangani pesan dari klien yang terhubung dengan memanggil metode `handle()`.

8. Membuat objek server:
   - `print("Server telah jalan")`: Menampilkan pesan bahwa server telah berjalan.
   - `receive()`: Memulai menerima koneksi dari klien menggunakan metode `receive()`.
```

## Usage

* Buka CMD/PowerShell/Terminal

![App Screenshot](https://media.discordapp.net/attachments/1117660142108946462/1123877865583296602/image.png)

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123877975994150983/image.png)

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123877986169536552/image.png)

* Ketik dan input cd D:\Coding\Python\chatting-GUI

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123878623816982568/image.png)

* Sesuaikan D:\Coding\Python\chatting-GUI dengan tempat anda menyimpan file

* Ketik dan input py server.py hingga sesuai pada foto di bawah

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123879129574551573/image.png)

* Buka window/tab baru CMD/Terminal/PowerShell

* Ketik dan input cd D:\Coding\Python\chatting-GUI

* Sesuaikan D:\Coding\Python\chatting-GUI dengan tempat anda menyimpan file

* Ketik dan input py client.py maka akan muncul window baru

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123879674360115210/image.png)

* Ketik nama anda, lalu tekan oke

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123880019937210398/image.png)

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123880048462676089/image.png)

* Lakukan step 5 - 9 sekali lagi maka aplikasi chatting anda siap di gunakan

![App Screenshot](https://cdn.discordapp.com/attachments/1117660142108946462/1123880609773781002/image.png)