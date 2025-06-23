# veri-gizleme-projesi
# 🔐 Görsel Steganografi & Şifreleme Projesi

Bu projede, **gri tonlamalı bir görselin en anlamlı bit (MSB) düzlemi**, renkli bir kapak görselinin **en az anlamlı bit (LSB)** düzlemlerine gömülerek saklanmıştır. Ek olarak, MSB düzlemi **XOR şifreleme** yöntemiyle gizlenmiştir. Projede üç farklı yaklaşım karşılaştırılmıştır.

---

## 📁 Proje Yapısı

📂 steganografi-projesi/
│
├── lena_rgb.jpeg # Kapak (cover) görseli
├── lena_grey.jpeg # Gizlenecek gri (secret) görsel
├── method1_msb_xor_lsb.py # Yöntem 1: MSB + XOR + LSB (1 bit)
├── method2_multibit_xor_lsb.py # Yöntem 2: Çok Bitli LSB + XOR (2-6 bit)
├── method3_simple_lsb.py # Yöntem 3: Basit LSB (1 bit, şifresiz)
└── README.md # Proje açıklaması


---

## ⚙️ Kullanılan Yöntemler

### ✅ Yöntem 1: `method1_msb_xor_lsb.py`
- Sadece **MSB (1 bit)** düzlemi kullanılır.
- XOR şifreleme uygulanır (`anahtar: 170`).
- Blue kanalın LSB'sine gömülür.
- Görsel kalitesi çok yüksek, ama kurtarılan veri sınırlı.

### ✅ Yöntem 2: `method2_multibit_xor_lsb.py`
- MSB’den itibaren **çoklu bit düzlemi (örn. 6 bit)** seçilir.
- XOR ile şifrelenir ve LSB’lere gömülür.
- Gizli görsel çok daha başarılı geri elde edilir.
- Kapak görselde hafif bozulma olabilir.

### ✅ Yöntem 3: `method3_simple_lsb.py`
- Sadece 1-bitlik MSB gömülür.
- XOR şifreleme **yok**.
- En temel LSB steganografi örneğidir.

---

## 🧪 Performans Karşılaştırması

| **Yöntem**                                   | **PSNR (Cover vs Stego)** | **SSIM (Cover vs Stego)** | **PSNR (Secret vs Extracted)** | **SSIM (Secret vs Extracted)** |
|---------------------------------------------|----------------------------|----------------------------|----------------------------------|----------------------------------|
| **Yöntem 1:** MSB + XOR + 1 bit LSB         | 55.93 dB                   | 1.0000                     | 11.41 dB                         | 0.3781                           |
| **Yöntem 2:** Çok Bitli LSB (6 bit) + XOR   | 42.22 dB                   | 0.9990                     | 23.02 dB                         | 0.8254                           |
| **Yöntem 3:** Sadece 1 Bit LSB (MSB gömülü) | 55.93 dB                   | 1.0000                     | 11.41 dB                         | 0.3781                           |

---

## 📦 Gereksinimler

```bash
pip install numpy opencv-python matplotlib scikit-image

 Kullanım
Her yöntemi ayrı ayrı çalıştırabilirsiniz:
python method1_msb_xor_lsb.py
python method2_multibit_xor_lsb.py
python method3_simple_lsb.py

🎯 Amaç

Bu proje, veri gizleme (steganografi) ve basit şifreleme tekniklerini birleştirerek;
Görsel kalitesi ve veri güvenliği arasında denge kurmayı,
Görsel analizle mesajın gizli olup olmadığının fark edilmemesini,
Farklı steganografi tekniklerinin karşılaştırılmasını amaçlar.
