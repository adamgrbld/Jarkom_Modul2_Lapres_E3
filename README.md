# Jarkom_Modul2_Lapres_E3

## Configurasi awal
Melakukan semua konfigurasi pada Modul UML

## Soal Shift

**1. Membuat alamat http://semerue03.pw**

- MALANG
  * apt-get install bind9 -y
  * nano /etc/bind/named.conf.local
  
    ![1a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_1a.png)
  * mkdir /etc/bind/jarkom
  * cp /etc/bind/db.local /etc/bind/jarkom/semerue03.pw
  * nano /etc/bind/jarkom/semerue03.pw
  
    ![1b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_1b.png)
  * service bind9 restart

- GRESIK & SIDOARJO
  * nano /etc/resolv.conf
  
    ![1c](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_1c.png)
   * ping semerue03.pw
   
     ![1gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_1gr.png)
     ![1sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_1sid.png)
     
**2. Membuat alias http://www.semeruyyy.pw**

- MALANG
  * nano /etc/bind/jarkom/semerue03.pw
  
    ![2a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_2a.png)
    
- GRESIK & SIDOARJO
  * ping www.semerue03.pw
  
    ![2gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_2gr.png)
    ![2sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_2sid.png)
    
**3. Membuat subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO**

- MALANG
  * nano /etc/bind/jarkom/semerue03.pw
    
    ![3a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_3a.png)
  * service bind9 restart

- GRESIK & SIDOARJO
  * ping penanjakan.semerue03.pw
  
     ![3gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_3gr.png)
     ![3sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_3sid.png)
     
**4. Reverse domain untuk domain utama**

- MALANG
  * nano /etc/bind/named.conf.local
  
    ![4a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_4a.png)
  * cp /etc/bind/db.local /etc/bind/jarkom/71.151.10.in-addr.arpa
  * nano /etc/bind/jarkom/71.151.10.in-addr.arpa
  
    ![4b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_4b.png)
   * service bind9 restart
   
- GRESIK
  * Server Awal (Bukan IP MALANG)
    + apt-get update
    + apt-get install dnsutils
  * Server Malang (IP MALANG)
    + host -t PTR 10.151.71.34
    
      ![4c](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_4c.png)
      
**5. Membuat DNS Server Slave pada MOJOKERTO**

- MALANG
  * nano /etc/bind/named.conf.local
  
    ![5a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_5a.png)
  * service bind9 restart
  
- MOJOKERTO
  * apt-get update
  * apt-get install bind9 -y
  * nano /etc/bind/named.conf.local
  
    ![5b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_5b.png)
  * service bind9 restart
  
- MALANG
  * service bind9 stop
- GRESIK & SIDOARJO
  * nano /etc/resolv.conf
  
    ![5c](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_5c.png)
  * ping semerue03.pw
  
    ![5gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_5gr.png)
    ![5sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_5sid.png)
    
**6. Membuat subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO**

- MALANG
  * nano /etc/bind/jarkom/semerue03.pw
  
    ![6a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6a.png)
  * nano /etc/bind/named.conf.options
  
    ![6b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6b.png)
  * nano /etc/bind/named.conf.local
  
    ![6c](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6c.png)
  * service bind9 restart
  
- MOJOKERTO
  * nano /etc/bind/named.conf.options
  
    ![6d](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6d.png)
  * nano /etc/bind/named.conf.local
  
    ![6e](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6e.png)
  * mkdir /etc/bind/delegasi
  * cp /etc/bind/db.local /etc/bind/delegasi/gunung.semerue03.pw
  * nano /etc/bind/delegasi/gunung.semerue03.pw
  
    ![6f](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6f.png)
  * service bind9 restart
  
- GRESIK & SIDOARJO
  * ping gunung.semerue03.pw
  
    ![6gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6gr.png)
    ![6sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_6sid.png)
    
**7. Membuat subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO**

- MOJOKERTO
  * nano /etc/bind/delegasi/gunung.semerue03.pw
  
    ![7a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_7a.png)
  * service bind9 restart
  
- GRESIK & SIDOARJO
  * ping naik.gunung.semerue03.pw
  
    ![7gr](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_7gr.png)
    ![7sid](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_7sid.png)
    
**8. Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw. Dan dapat mengakses alamat http://semeruyyy.pw/index.php/home**

- PROBOLINGGO
  * apt-get install apache2
  * apt-get install php-dev
  * cd /etc/apache2/sites-available
  * cp 000-default.conf semerue03.pw.conf
  * nano semerue03.pw.conf

    ![8a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_8a.png)
    ![8b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_8b.png)
    ![8c](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_8c.png)
    ![8d](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_8d.png)
  * service apache2 restart
  * a2ensite semerue03.pw.conf
  * cd /var/www
  * mkdir semerue03.pw
  * wget
  * unzip
  * mv semeru.pw /var/www/semerue03.pw
  * mv penanjakan.semeru.pw /var/www/semerue03.pw
  * mv semeru /var/www/naik.gunung.semerue03.pw
  * service apache2 restart
  * a2ensite semerue03.pw.conf
  
- BROWSER
  * masukkan *semerue03.pw*
   
    ![8fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_8fin.png)
    
**9. Mengaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home**

- PROBOLINGGO
  * a2enmod rewrite
  * service apache2 restart
  * nano /var/www/semerue03.pw/.htaccess
    
    ![9a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_9a.png)
  * nano /etc/apache/sites-available/semerue03.pw.conf
    
    ![9b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_9b.png)
  * a2ensite semerue03.pw.conf
  * service apache2 restart
    
- BROWSER
  * masukkan *semeruyyy.pw/home*
    
    ![9fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_9fin.png)

**10. Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder**

- PROBOLINGGO
  * download dan unzip di /var/www/
  * service apache2 restart
  * cd /var/www
  * cat penanjakan.semerue03.pw/
  * ls penanjakan.semerue03.pw/
  * cp 000-default.conf penanjakan.semerue03.pw.conf
  
- BROWSER
  * masukkan *penanjakan.semerue03.pw/public*
    
    ![10fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_10fin.png)

**11. Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan**

- PROBOLINGGO
  * nano /etc/apache2/sites-available/penanjakan.semerue03.pw.conf
  
    ![11a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_11a.png)

- BROWSER
  * masukkan *penanjakan.semerue03.pw/css*
  
    ``` css dapat diganti dengan nama file lain di directory public ```
  
    ![11fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_11fin.png)

**12. Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache**

- PROBOLINGGO
  * nano /etc/apache2/sites-available/penanjakan.semerue03.pw.conf
  
    ![12a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_12a.png)

- BROWSER
  * masukkan *penanjakan.semerue03.pw/public/asdf*
  
    ``` asdf tidak terdapat di directory public, sehingga menunjukkan error ```
  
    ![12fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_12fin.png)

**13. Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js**

- PROBOLINGGO
  * nano /etc/apache2/sites-available/penanjakan.semerue03.pw.conf
  
    ![13a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_13a.png)

- BROWSER
  * masukkan *penanjakan.semerue03.pw/js*
  
    ![13fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_13fin.png)

**14. Web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw**

- PROBOLINGGO
  * download dan unzip di /var/www
  * nano /etc/apache2/sites-available/naik.gunung.semerue03.pw.conf
  
    ``` configurasi jadi satu di no 15 ```

**15. Membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya**

- PROBOLINGGO
  * htpasswd /etc/apache2/.htpasswd semeru
  * nano /etc/apache2/sites-available/naik.gunung.semerue03.pw.conf
  
    ![15a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_15a.png)

- BROWSER
  * masukkan *naik.gunung.semerue03.pw:8888*
  
    ![15fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_15fin.png)

**16. Setiap mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw**

- PROBOLINGGO
  * cd /etc/apache2/sites-available/
  * nano 000-default.conf
  
    ![16a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_16a.png)
    
- BROWSER
  * masukkan *10.151.71.36*, dan berikut merupakan hasil dari IP yang dimasukkan
  
    ``` 10.151.71.36 merupakan IP PROBOLINGGO ```
  
    ![16fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_16fin.png)

**17. Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg**

- PROBOLINGGO
  * nano .htaccess pada /var/www/penanjakan.semerue03.pw
    
    ![17a](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_17a.png)
  * nano /etc/apache2/sites-available/penanjakan.semerue03.pw.conf
  
    ![17b](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_17b.png)
    
- BROWSER
  * masukkan *penanjakan.semerue03.pw/public/images/[namafile].jpg*
  
    ``` namafile dapat diisi apa saja dengan catatan mengandung substring semeru ```
    
    berikut hasilnya, semua akan diarahkan ke *semeru.jpg*
    
     ![17fin](https://github.com/adamgrbld/Jarkom_Modul2_Lapres_E3/blob/main/image/m2_17fin.png)
