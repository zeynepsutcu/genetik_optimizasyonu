# Kargo Kutusu Tasarımı Optimizasyonu (Genetik Algoritma)

Bu proje, bir e-ticaret firmasının ürün gönderimlerinde kullanacağı **optimum kargo kutusu boyutlarını** belirlemek için geliştirilmiştir. **Genetik Algoritma (GA)** kullanılarak, malzeme maliyeti ve hacim dengesini sağlayan en iyi Genişlik ($x_1$) ve Yükseklik ($x_2$) değerleri hesaplanmaktadır.

## Senaryo ve Problem Tanımı

Firma, kutunun iç hacmini maksimize ederken, yüzey alanından kaynaklanan malzeme maliyetini minimize etmek istemektedir.

* **Amaç Fonksiyonu:**
    $$y = x_1 \cdot x_2 - 0.1x_1^2 - 0.1x_2^2$$
    *(Burada $x_1 \cdot x_2$ hacim faktörünü, negatif terimler ise malzeme maliyetini temsil eder.)*

* **Değişken Sınırları:**
    * **$x_1$ (Genişlik):** 10 cm - 40 cm
    * **$x_2$ (Yükseklik):** 5 cm - 20 cm

* **Kısıtlar:**
    1.  **Raf Sığdırma:** $x_1 \cdot x_2 \le 600$ (Taban alanı 600 cm²'yi geçemez)
    2.  **Minimum Genişlik:** $x_1 \ge 15$ (Kutu çok dar olamaz)

## Algoritma Detayları

Projede kısıtlı optimizasyon problemini çözmek için aşağıdaki genetik yöntemler kullanılmıştır:

* **Kodlama:** Gerçel Sayı Kodlaması (Real-value encoding)
* **Seçilim:** Turnuva Seçimi (Tournament Selection - Size: 3)
* **Çaprazlama:** Aritmetik Çaprazlama (Ebeveynlerin ağırlıklı ortalaması)
* **Mutasyon:** Gaussian Mutasyon (Rastgele gürültü ekleme ve sınırlandırma)
* **Ceza Yöntemi:** Kısıtları ($x_1 \ge 15$ ve $Alan \le 600$) ihlal eden bireylere ceza puanı uygulanarak elenmeleri sağlanmıştır.

## 🚀 Kurulum ve Kullanım

1.  Gerekli kütüphaneleri yükleyin:
    ```bash
    pip install numpy matplotlib
    ```
2.  `Project.ipynb` dosyasını Jupyter Notebook ile çalıştırın.

## 📊 Sonuç Özeti

Algoritma 100 nesil sonunda kısıtları sağlayan en optimum boyutlara yakınsamıştır.
* **Yaklaşık Sonuç:** Genişlik ($x_1$) ve Yükseklik ($x_2$) değerleri, $x_1 \cdot x_2 \approx 600$ sınırına dayanarak fonksiyonu maksimize eden noktalarda dengelenmiştir.
