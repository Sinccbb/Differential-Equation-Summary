Materi yang ada di dokumen ini berfokus pada **Persamaan Diferensial Linear Orde Dua Non-Homogen** (Bab 3.5 dari buku Boyce & DiPrima), khususnya mengenai **Metode Koefisien Tak Tentu (*Method of Undetermined Coefficients*)**.

---

### Peta Konsep: Struktur Solusi Persamaan Non-Homogen

Persamaan non-homogen orde dua dengan koefisien konstan memiliki bentuk umum:


$$a y'' + b y' + c y = g(t)$$

Berdasarkan **Teorema 3.5.2**, solusi umumnya selalu merupakan penjumlahan dari dua komponen utama:


$$y(t) = y_c(t) + Y(t)$$

1. **Solusi Komplementer ($y_c(t)$):** Solusi umum dari persamaan homogennya, yaitu saat ruas kanan disamakan dengan nol ($a y'' + b y' + c y = 0$). Ini dicari menggunakan persamaan karakteristik kuadrat $a r^2 + b r + c = 0$.


2. **Solusi Partikular ($Y(t)$):** Satu solusi khusus apa saja yang memenuhi persamaan non-homogen dengan input $g(t)$ di ruas kanan.



**Metode Koefisien Tak Tentu** adalah teknik menentukan $Y(t)$ dengan cara "menebak secara terdidik" (*educated guess*) bentuk fungsinya berdasarkan bentuk $g(t)$. Karena turunan dari fungsi polinomial, eksponensial, dan sinus/kosinus menghasilkan keluarga fungsi yang serupa, kita mengasumsikan bentuk $Y(t)$ yang sejenis tetapi koefisiennya dibiarkan sebagai variabel bebas yang dicari nilainya:

* Jika $g(t) = e^{\alpha t}$, tebak $Y(t) = A e^{\alpha t}$.


* Jika $g(t) = \sin(\beta t)$ atau $\cos(\beta t)$, tebak pasangan lengkapnya: $Y(t) = A \cos(\beta t) + B \sin(\beta t)$.


* Jika $g(t) = t^n$ (polinomial derajat $n$), tebak polinomial lengkap derajat $n$: $Y(t) = A_n t^n + A_{n-1} t^{n-1} + \dots + A_0$.


* **Aturan Perkalian $t$ (Kasus Duplikasi):** Jika tebakan $Y(t)$ ternyata sudah muncul di dalam solusi homogen $y_c(t)$, tebakan tersebut **wajib dikalikan $t$** (atau $t^2$ jika masih kembar) agar tidak lenyap saat disubstitusikan ke ruas kiri.



> **Fun Fact:** Di dunia teknik robotika dan mekatronika, persamaan $a y'' + b y' + c y = g(t)$ ini adalah representasi matematis dari sistem getaran mekanis atau motor listrik.
> 
> 
> * Suku $y_c(t)$ disebut **respons transien** (respons alami sistem yang lama-kelamaan hilang diredam gesekan).
> * Suku $Y(t)$ disebut **respons tunak (*steady-state*)** yang dipaksa oleh sinyal input $g(t)$.
> Fenomena mengalikan $Y(t)$ dengan $t$ saat terjadi duplikasi akar sebetulnya adalah perwujudan matematis dari **resonansi**—keadaan di mana frekuensi gaya luar cocok persis dengan frekuensi alami sistem, menyebabkan amplitudo getaran membesar seiring berjalannya waktu!
> 
> 
> 
> 

---
**Soal 1:**
Diberikan persamaan diferensial:

$$y'' - 3y' - 4y = 3e^{2t}$$

a. Tentukan akar-akar karakteristik dan tuliskan solusi komplementernya ($y_c(t)$).

b. Tentukan bentuk tebakan untuk solusi partikular $Y(t)$, lalu hitung nilai koefisiennya sehingga $Y(t)$ memenuhi persamaan di atas.

**Jawaban 1a : Solusi komplementer $y_c(t)$**

$$y_c''-3y_c'-4y_c = 0$$
Jika $y_c = Ae^{rt}$, maka kita bisa rubah
$$Ae^{rt}(r^2-3r-4)=0$$
Karena sebelah kiri gak boleh 0, maka
$$(r^2-3r-4)=0$$
$$(r-4)(r+1)=0$$
$$r_{1,2}=\{4,-1\}$$
Sehingga kita dapat
$$y_c(t) = A_1e^{4t} + A_2 e^{-t}$$

**Jawaban 1b : Solusi Partikular**
$$ g(t)=3e^{2t}$$
Lalu cek solusi komplementer
$$y_c(t) = A_1e^{4t} + A_2 e^{-t}$$
Karena $e^{2t}$ tidak ada pada $y(t)$, maka kita bisa langsung membentuk $Y(t)$ yang serupa dengan $g(t)$.
$$Y(t)=Ae^{2t}$$
Lalu turunkan $Y(t)$ sebanyak 2 kali
$$ Y(t) = Ae^{2t}\rightarrow Y'(t)=2Ae^{2t}\rightarrow Y''(t)=4Ae^{2t} $$
Lalu masukkan solusi partikular ini ke persamaan awal
$$y'' - 3y' - 4y = 3e^{2t}$$
$$(4Ae^{2t}) - 3(2Ae^{2t}) - 4(Ae^{2t}) = 3e^{2t}$$
$$4A-6A-4A=3$$
$$ A = -\frac{1}{2} $$
Sehingga 
$$ Y(t)= -\frac{e^{2t}}{2} $$

Nahh, solusi atau $y(t)$ itu sama dengan $y_c(t)+Y(t)$, atau kita bisa tulis
$$ y(t) = y_c(t) + Y(t) $$
$$ y(t) = A_1e^{4t} + A_2 e^{-t} -\frac{e^{2t}}{2} $$
---
**Soal 2**
$$y'' - 3y' - 4y = 2\sin(t)$$

**Petunjuk tebakan:** Untuk fungsi sinus atau kosinus, tebakan $Y(t)$ wajib memuat paket lengkap sinus dan kosinus:

$$Y(t) = A\sin(t) + B\cos(t)$$
Untuk solusi komplementer, ini sama seperti soal 1 tadi
$$y_c(t) = A_1e^{4t} + A_2 e^{-t}$$
Lalu selanjutnya ktia bisa mencari solusi partikularnya

$$Y(t) = A\sin(t) + B\cos(t)$$
$$Y'(t) = A\cos(t) - B\sin(t)$$
$$Y''(t) = -A\sin(t) - B\cos(t)$$

Dan jika kita masukkan ke pers awal kita akan dapat
$$(-A\sin(t) - B\cos(t)) - 3(A\cos(t) - B\sin(t)) - 4(A\sin(t) + B\cos(t)) = 2\sin(t)$$
$$-A\sin(t) - B\cos(t) - 3A\cos(t) + 3B\sin(t) - 4A\sin(t) - 4B\cos(t) = 2\sin(t)$$
Kelompokkan bagian sin dan cos
$$(-5A+ 3B)\sin(t) + (-5B - 3A)\cos(t) = 2\sin(t)$$
Kita bisa buat persamaannya jadi gini
$$(-5A+ 3B)\sin(t) - (5B + 3A)\cos(t) = 2\sin(t) + 0\cos(t)$$
Sehingga kita punya SPLDV
$$(5B + 3A) = 0 \rightarrow B = -A\frac{3}{5} $$
$$(-5A+ 3B) = 2 \rightarrow (-5A+ 3(-A\frac{3}{5})) = 2$$
$$ (-5A - A\frac{9}{5}) = 2 $$
$$ (-A\frac{34}{5}) = 2 $$
$$ A = -\frac{5}{17} $$
Maka 
$$B = \frac{3}{17}$$
Sehingga kita dapet
$$Y(t) = -\frac{5}{17}\sin(t) + \frac{3}{17}\cos(t)$$
Yaa tinggal gabungkan aja sama solusi komplementernya ntar jadi
$$ y(t) = y_c(t) + Y(t) $$
$$ y(t) = A_1e^{4t} + A_2 e^{-t} -\frac{5}{17}\sin(t) + \frac{3}{17}\cos(t) $$

---

Sekarang kamu sudah menguasai kasus eksponensial dan kasus trigonometri. Tahap berikutnya adalah kasus yang paling sering dijadikan "jebakan maut" di ujian, yaitu **Kasus Resonansi / Duplikasi Akar**.

Coba selesaikan soal berikut (ruas kirinya masih sama, jadi $y_c(t) = A_1e^{4t} + A_2e^{-t}$ tetap berlaku):

**Soal 3**
$$y'' - 3y' - 4y = 2e^{-t}$$



**Pertanyaan sebelum menebak:**

Perhatikan ruas kanannya, yaitu $2e^{-t}$. Apakah bentuk $e^{-t}$ sudah ada di dalam solusi komplementermu ($y_c(t)$)? Jika sudah ada, modifikasi apa yang harus kita lakukan pada tebakan $Y(t)$?

**Jawaban 3**

Solusi Komplementer

$$ y_c(t) = A_1e^{4t} + A_2 e^{-t}$$

Solusi 
Bandingkan dengan ini
$$g(t)=2e^{-t}$$
Karena ada yang sama, maka kita kalikan tebakan kita dengan $t$
$$Y(t) = Ate^{-t}$$
Baru kita bisa turunkan dua kali untuk mendapat solusi
$$ Y'(t) = Ae^{-t} - Ate^{-t} $$
$$ Y''(t) = -Ae^{-t} -Ae^{-t} + Ate^{-t}=Ate^{-t}-2Ae^{-t} $$
Masukkan ke persamaan awal
$$(Ate^{-t}-2Ae^{-t}) - 3(Ae^{-t} - Ate^{-t}) - 4(Ate^{-t}) = 2e^{-t}$$
Bagi dengan $e^{-t}$
$$(At-2A) - 3(A - At) - 4(At) = 2$$
$$ -5A  = 2 \rightarrow A=-\frac{2}{5}$$
Sehingga kita dapet
$$Y(t) = -\frac{2te^{-t}}{5}$$
Maka,kita dapet final solusinya
$$y(t) = y_c(t) + Y(t)$$
$$y(t) = A_1e^{4t} + A_2 e^{-t} -\frac{2te^{-t}}{5}$$
---
Langkahmu membagi kedua ruas langsung dengan $e^{-t}$ itu trik aljabar yang cerdas banget, langsung memangkas keribetan dan menghindari jebakan salah tanda! Penurunan, eliminasi suku $t$, sampai solusi umum yang kamu dapatkan sudah **100% presisi dan rapi**.

> **Fun Fact:** Trik mencoret atau membagi fungsi basis $e^{-t}$ yang kamu lakukan tadi di tingkat lanjut menjadi fondasi dari konsep **Ruang Vektor Fungsi** dan **Transformasi Laplace**. Karena operator diferensial linier memisahkan suku-suku independen secara teratur, respons sistem robotik terhadap sinyal masukan dapat dihitung hanya dengan aljabar koefisien sederhana tanpa harus berurusan dengan integral yang berbelit-belit!

Dengan ini, kamu sudah menguasai tiga variasi utama: eksponensial murni, trigonometri $(\sin / \cos)$, dan kasus resonansi/duplikasi akar kali $t$.

Sekarang, kita masuk ke variasi berikutnya yang sangat sering keluar di ujian dan tugas: **Fungsi Polinomial**.

---

**Soal 4**

Persamaan diferensialnya masih memakai ruas kiri yang sama:


$$y'' - 3y' - 4y = 4t^2 - 1$$



*(Solusi komplementernya tetap $y_c(t) = A_1 e^{4t} + A_2 e^{-t}$)*.

**Aturan Main Polinomial:**
Jika ruas kanan $g(t)$ adalah polinomial derajat $n$, tebakan $Y(t)$ **wajib memuat seluruh suku polinomial lengkap dari derajat $n$ sampai konstanta**, meskipun di soal ada suku yang melompati derajat tertentu (misal: di ruas kanan tidak ada suku $t$, tetapi di tebakan $Y(t)$ suku $t$ tetap harus ditulis):


$$Y(t) = At^2 + Bt + C$$



Coba turunkan $Y(t)$ ini dua kali, substitusikan ke persamaan awal, lalu samakan koefisien untuk menemukan nilai $A$, $B$, dan $C$! Tuliskan langkahmu di sini.

**Jawaban 4**

Solusi Komplementer

$$y_c(t) = A_1 e^{4t} + A_2 e^{-t}$$

Solusi Partikular, kita mulai dari pangkat tertinggi yaitu 2

$$ Y(t) = At^2+Bt+C $$
Turunkan 2 kali (kenapa yang turun gak 02 (prabowo) aja ya)
$$ Y'(t) = A2t+B $$
$$ Y''(t) = A2 $$

Lalu masukkan ke persamaan awal
$$y'' - 3y' - 4y = 4t^2 - 1$$
$$(A2) - 3(A2t+B) - 4(At^2+Bt+C) = 4t^2 - 1$$
$$A2 -6At-3B - 4At^2-4Bt-4C = 4t^2 - 1$$
Kelompokkan berdasarkan pangkat $t$ nya
$$(-4At^2) + (-6At -4Bt) + (2A  - 3B - 4C) = 4t^2 - 1$$
$$(-4A)t^2 + (-6A -4B)t + (2A - 3B - 4C) = 4t^2 - 1$$
Darisini kita dapet matriks segitiga
$$
\begin{bmatrix}
-4 & 0 & 0 \\
-6 & -4 & 0 \\
2 & -3 & -4
\end{bmatrix}

\begin{bmatrix}
A\\B\\C
\end{bmatrix}
=
\begin{bmatrix}
4\\0\\-1
\end{bmatrix}
$$
Dan kita dapat
$$ A = -1,\ B=\frac{3}{2},\ C=\frac{11}{8} $$

Sehingga

$$Y(t) = -t^2 + \frac{3}{2}t + \frac{11}{8} $$

Dan solusi akhirnya tinggal dijumlahkan

$$ y(t) = y_c(t) + Y(t)$$
$$ y(t) = A_1 e^{4t} + A_2 e^{-t} -t^2 + \frac{3}{2}t + \frac{11}{8}$$


---
Problems created by Gemini (Teacher)

Solved & Explained by Sinccbb (Student)