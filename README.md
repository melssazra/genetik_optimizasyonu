# 🚚 Genetik Algoritma ile Nakliye Rotası Optimizasyonu

Bu proje, bir lojistik firmasının rota seçimi sırasında **yakıt tüketimi ve süre maliyetini optimize etmek** için Genetik Algoritma (GA) kullanımını göstermektedir.

---

## 📌 Optimizasyon Problemi

### Amaç Fonksiyonu (Uygunluk)
Negatif toplam maliyeti maksimize etmek amaçlanmıştır (Maksimum uygunluk = Minimum maliyet).

$$y = -2x_1 - 3x_2 + 0.1x_1x_2$$

### Değişkenler
* **$x_1$**: Ortalama hız (km/h). **Aralık:** $[40, 100]$
* **$x_2$**: Araç yük kapasitesi (ton). **Aralık:** $[2, 10]$

### Kısıtlar (Ceza Mekanizması)
Uygunluk skorunu düşüren kısıtlar (Motor Gücü ve Minimum Hız):
1.  Motor gücü limiti: $$x_1 \cdot x_2 \le 700$$
2.  Minimum hız şartı: $$x_1 \ge 60$$

---

## 🧬 Genetik Algoritma Parametreleri ve Yapısı

| Parametre | Seçilen Değer / Yöntem | Açıklama |
| :--- | :--- | :--- |
| **Popülasyon Büyüklüğü** | 20 | Genetik çeşitliliği sağlar (Kod çıktısındaki birey sayısından çıkarılmıştır). |
| **Nesil Sayısı** | 15 | Algoritmanın döngü sayısı. |
| **Seçim Yöntemi** | Rank Temelli Seçim | Uygunluk değerine göre sıralama yaparak seçim olasılığı atar. |
| **Çaprazlama Yöntemi** | İki Noktalı Çaprazlama | Kromozomları iki farklı noktadan keserek genetik değişimi artırır. |
| **Mutasyon İhtimali** | 0.4 | Rastgele genetik değişimi tetikleme olasılığı. |
| **Mutasyon Büyüklüğü** | 0.16 | Mutasyon sırasında bireylere uygulanacak maksimum değişim büyüklüğü. |
| **Kısıt Kontrolü** | Ceza Fonksiyonu | İhlal edilen her kısıt için uygunluktan ceza puanı düşülür (Kodda ceza $100$ ile çarpılmıştır). |

---

## 💡 Elde Edilen Çözüm

Gerçekleştirilen 15 nesillik evrim sonunda bulunan en iyi çözüm değerleri:

* **Optimal Ortalama Hız ($x_1$):** 69.86 km/h
* **Optimal Yük Kapasitesi ($x_2$):** 9.92 ton
* **En İyi Uygunluk ($y$):** -100.189 (En düşük maliyeti temsil eder)

---
