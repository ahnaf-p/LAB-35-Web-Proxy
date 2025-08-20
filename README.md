# LAB-35-Web-Proxy
Rabu 20 Agustus 2025
  
# Web Proxy  
  Secara sederhana, proxy bisa diartikan sebagai server atau program yang bertugas mewakili komputer lain saat meminta konten dari internet maupun intranet. Jadi, bisa dibilang proxy ini semacam perantara sekaligus pelindung ketika kita mengakses jaringan internet. Jenis proxy sendiri ada cukup banyak, misalnya SSL Proxy, Web Proxy, Intercepting Proxy, Reverse Proxy, dan lain-lain. Setiap jenis punya fungsi masing-masing sesuai kebutuhan. Nah, kali ini kita akan bahas salah satu proxy yang sudah tersedia sebagai fitur bawaan di RouterOS MikroTik, yaitu Web Proxy.  

# Konfigurasi Web Proxy
  1. Aktifkan dulu service dari web-proxy pada MikroTik dengan pengaturan pad menu IP > Web Proxy.
  2. Checklist Enable dan tentukan port berapa proxy bekerja, defaultnya 8080.
  ![](IMAGES/)
  3. Sampai sini, web proxy pada Mikrotik sudah aktif sebagai Regular HTTP Proxy. Atau maksudnya jika PC Client ingin mengunakan service proxy ini, maka harus disetting manual pada web browser masing-masing client dengan menunjuk ip mikrotik port 8080.
  4. Agar tidak perlu setting pada browser satu-satu, ubah web proxy Mikrotik sebagai Transparent proxy. Caranya mengunakan NAT untuk membelokan semua traffic browsing HTTP (tcp 80) yang berasal dari client ke fitur internal web proxy yang sudah di aktifkan sebelumnya. Untuk membuatnya, masuk ke menu **IP > FIREWALL>NAT>ADD**  
  ![](IMAGES/)    
  5. Selanjutnya karena semua traffic HTTP dari client sudah masuk ke web proxy, maka bisa diakukan manajemen. Salah satunya adalah melakukan blocking akses client we website tertentu.  
  6. Untuk melakukan block akses client ke website tertentu dapat dilakukan pada menu **Webproxy > Access**
  ![](IMAGES/)
  7. Tambahkan rule web-proxy access baru. Dalam contoh ini, client tidak diperbolehkan akses ke **store.steampowered.com**, isi website yang akan di block pada parameter **dst-host** dengan **action=deny**
  ![](IMAGES/)
*Jika  diperhatikan, penulisan dst-host tidak menggunakan alamat website lengkap akan tetapi menggunakan tanda bintang (*) *di depan dan belakang nama/alamat website. Tanda * dimaksudkan sebagai wildcard untuk menggantikan semua karakter. Dengan ditambahkan wildcard, traffic client yang menuju ke website yang URL-nya terdapat kata "playboy" akan diblock.*
  8. Sekarang coba kita browsing ke **store.steampowered.com**
  ![](IMAGES/)  
