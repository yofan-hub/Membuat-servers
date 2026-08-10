# Membuat Server 

Dokumentasi proses membuat server menggunakan Ubuntu Server,
mengaktifkan akses SSH, menggunakan domain, dan menghubungkan
server ke internet menggunakan Cloudflare Tunnel dan mencoba WebServer.
## Progress

- [x] Ubuntu Server sudah terinstall
- [x] Ubuntu Server sudah berjalan
- [x] SSH sudah dikonfigurasi
- [x] Domain sudah dibeli
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

## 6. Membuat ip menjadi statis

lakukan ip a untuk mencatat ip dan juga ip route

#Edit File Konfigurasi Netplan

ls /etc/netplan/
 sudo nano /etc/netplan/00-installer-config.yaml

 etwork:
  ethernets:
    enp0s3:
      dhcp4: true
      dhcp6: true
      match:
        macaddress: 08:00:27:d9:db:a8
      set-name: enp0s3
  version: 2

  ubah dhcp4 dan 6 menjadi false dan tambahkan ip dan gateway yang sudah di catat hingga menjadi

  network:
  ethernets:
    enp0s3:
      dhcp4: false
      dhcp6: false
      match:
        macaddress: 08:00:27:d9:db:a8
      set-name: enp0s3
      addresses:
        - 192.168.1.13/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 1.1.1.1
  version: 2

lalu lakukan
sudo netplan apply
