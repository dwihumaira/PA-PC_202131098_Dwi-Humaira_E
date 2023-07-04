
# UAS 
Dwi Humaira Hafizah Faturahma
(202131098)


## Teori


1. Konversi Gambar ke Ruang Warna Keabuan (Grayscale):
Gambar input dikonversi ke ruang warna keabuan menggunakan fungsi `cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)`. Konversi ini dilakukan untuk mengurangi kompleksitas pemrosesan dan fokus pada informasi intensitas keabuan.

2. Reduksi Noise menggunakan Gaussian Blur:
Fungsi `cv2.GaussianBlur(image, (5, 5), 0)` digunakan untuk mereduksi noise pada gambar keabuan. Metode ini menerapkan filter Gaussian pada gambar untuk menghaluskan dan mengurangi noise sebelum deteksi tepi.

3. Deteksi Tepi menggunakan Canny Edge Detection:
Fungsi `cv2.Canny(blurred, 50, 150)` digunakan untuk mendeteksi tepi pada gambar yang telah direduksi noise. Metode Canny Edge Detection ini bekerja dengan menemukan perbedaan intensitas piksel yang signifikan dalam gambar.

4. Threshold dan Deteksi Garis menggunakan Hough Transform:
Fungsi `cv2.HoughLinesP(edges, 1, np.pi/180, threshold=100, minLineLength=100, maxLineGap=50)` digunakan untuk mendeteksi garis pada gambar dengan menggunakan Hough Transform. Parameter-parameter yang digunakan seperti threshold, minLineLength, dan maxLineGap dapat diatur untuk mengatur sensitivitas dan ketepatan deteksi.

5. Menggambar Garis Deteksi pada Gambar Asli:
Setelah mendapatkan garis-garis deteksi, fungsi `cv2.line(image, (x1, y1), (x2, y2), (0, 0, 255), 3)` digunakan untuk menggambar garis-garis tersebut pada gambar asli. Ini memungkinkan kita untuk melihat visualisasi dari marka jalan yang telah terdeteksi.

Dengan kombinasi teknik-teknik ini, source code tersebut mencoba untuk mendeteksi marka jalan pada gambar input dan menandai garis-garis deteksi tersebut pada gambar.

# Tahapan

1. Pertama, kita mengimpor library yang diperlukan, yaitu `cv2` (OpenCV) dan `numpy` (untuk operasi numerik).

2. Kemudian, kita mendefinisikan fungsi `detect_lane_markings` yang akan digunakan untuk mendeteksi marka jalan pada gambar. Fungsi ini akan menerima input berupa gambar dan mengembalikan gambar dengan garis marka jalan yang terdeteksi.

3. Di dalam fungsi `detect_lane_markings`, pertama-tama kita mengubah gambar ke ruang warna keabuan menggunakan `cv2.cvtColor` dengan parameter `cv2.COLOR_BGR2GRAY`.

4. Selanjutnya, kita mengurangi noise pada gambar menggunakan metode Gaussian blur. Ini dilakukan dengan memanggil `cv2.GaussianBlur` dan memberikan gambar keabuan sebagai input.

5. Setelah mengurangi noise, kita melakukan deteksi tepi menggunakan metode Canny edge detection dengan memanggil `cv2.Canny`. Parameter 50 dan 150 adalah threshold yang digunakan untuk menentukan kekuatan tepi.

6. Setelah mendapatkan tepi, kita menggunakan metode HoughLinesP untuk mendeteksi garis pada gambar. Fungsi `cv2.HoughLinesP` akan mengembalikan array yang berisi koordinat titik awal dan akhir dari garis yang terdeteksi.

7. Selanjutnya, kita menggambar garis deteksi pada gambar asli menggunakan `cv2.line`. Setiap garis dalam array hasil deteksi akan digambar dengan warna merah (0, 0, 255) dan ketebalan garis sebesar 3 piksel.

8. Terakhir, fungsi `detect_lane_markings` akan mengembalikan gambar dengan garis marka jalan yang terdeteksi.

9. Di bagian utama kode, kita membaca gambar dengan menggunakan `cv2.imread` dan menyimpannya dalam variabel `image`.

10. Kemudian, kita memanggil fungsi `detect_lane_markings` dengan gambar sebagai argumen, dan hasilnya disimpan dalam variabel `result`.

11. Terakhir, kita menampilkan hasil deteksi marka jalan dengan menggunakan `cv2.imshow`, dan menunggu tombol keyboard ditekan dengan `cv2.waitKey`. Setelah tombol keyboard ditekan, kita menutup jendela tampilan menggunakan `cv2.destroyAllWindows`.

Dengan menggunakan algoritma ini, kita dapat mendeteksi marka jalan pada gambar dan menampilkan gambar dengan garis marka jalan yang terdeteksi.

