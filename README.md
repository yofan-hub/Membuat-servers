# Membuat Server 

Dokumentasi proses membuat server menggunakan Ubuntu Server,
mengaktifkan akses SSH, menggunakan domain, dan menghubungkan
server ke internet menggunakan Cloudflare Tunnel dan mencoba WebServer.
## Progress

- [x] Ubuntu Server sudah terinstall
- [x] Ubuntu Server sudah berjalan
- [] SSH sudah dikonfigurasi
- [] Domain sudah dibeli
- [] Cloudflare sudah dikonfigurasi
- [] Cloudflare Tunnel sudah dibuat

## Tahapan

1. Persiapan Ubuntu Server
2. Konfigurasi SSH
3. Pengujian koneksi SSH
4. Pembelian dan konfigurasi domain
5. Konfigurasi Cloudflare
6. Membuat Cloudflare Tunnel
7. Menghubungkan domain dengan server
8. Pengujian server melalui domain

## 1. Ubuntu Server

Ubuntu Server digunakan sebagai server utama untuk menjalankan
service yang akan diakses melalui jaringan.

## 2. Membeli domain 

membeli domain di domanesia untuk mempermudah ssh dan mengupload web server

## 3. CLoudflare

setelah membeli domain kita harus mentunneling menggunakan cloudflare agar aman
step 1
pergi ke ke cloudflare lalu pergi ke domain dan masukan domain yang sudah dibeli
lalu ganti dengan nameserver yang disediakan oleh cloudflare ke web domain yang sudah dibeli

step 2
mentunneling domain perge ke acces lalu pilih plan zero trust dan lakukan sterusnya 

## 4. ssh

SSH digunakan untuk melakukan remote access ke Ubuntu Server.

## 5. pasang web server

sudo apt update && sudo apt install -y nginx
sudo systemctl status nginx

Masukkan alamat IP Ubuntu Server di chrome bar (misalnya:(http://192.168.1.13:) atau IP lokal baru dari hasil ip a

## 6. Edit Web

cd /var/www/html
sudo nano index.html

## 5. Testing

Setelah seluruh konfigurasi selesai, dilakukan pengujian untuk
memastikan server dapat diakses melalui domain.
