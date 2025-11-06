# 04_Grup_LED_Senaryosu

Bu proje, **STM32F407-Discovery** kartı üzerinde 4 adet farklı renkte LED (Kırmızı, Mavi, Yeşil, Sarı) kullanarak iki aşamalı, sıralı bir aydınlatma senaryosu gerçekleştirir.

Projenin amacı, `HAL_Delay()` fonksiyonu ile farklı zamanlamalar oluşturarak LED gruplarının sıralı ve birlikte çalışmasını sağlamaktır. Senaryo, LED'lerin önce tek tek, sonra çiftler halinde yanması üzerine kuruludur.

---

### 🎯 Proje Senaryosu

Animasyon, iki ana grup halinde çalışır ve sürekli tekrar eder:

**Grup 1 (Kırmızı & Mavi):**
1.  **Kırmızı LED (PA1)** 5 saniye boyunca tek başına yanar.
2.  Ardından **Mavi LED (PA5)** de yanar. Kırmızı LED sönmez, ikisi birlikte 2 saniye daha yanarlar.
3.  2 saniyenin sonunda her iki LED (Kırmızı ve Mavi) aynı anda söner.

**Grup 2 (Yeşil & Sarı):**
4.  **Yeşil LED (PA2)** 5 saniye boyunca tek başına yanar.
5.  Ardından **Sarı LED (PA3)** de yanar. Yeşil LED sönmez, ikisi birlikte 2 saniye daha yanarlar.
6.  2 saniyenin sonunda her iki LED (Yeşil ve Sarı) aynı anda söner.
7.  Döngü `while(1)` sayesinde başa döner ve Grup 1'den tekrar başlar.

**Zamanlama:**
* **Tekli Yanma Süresi (Kırmızı / Yeşil):** 5000 ms (5 saniye)
* **İkili Yanma Süresi (Kırmızı+Mavi / Yeşil+Sarı):** 2000 ms (2 saniye)
* **Sönme Süresi:** Aralarda bekleme yoktur, bir grup söndükten hemen sonra diğeri başlar.

---

### 🛠️ Gerekli Donanım

* **1x** STM32F407-Discovery Geliştirme Kartı
* **1x** Kırmızı LED
* **1x** Mavi LED
* **1x** Yeşil LED
* **1x** Sarı LED
* **4x** 220 Ohm Direnç (LED'ler için ön direnç)
* Breadboard ve Jumper kablolar

---

### 🔌 Devre Şeması

LED'lerin anot (uzun) bacakları STM32 pinlerine, katot (kısa) bacakları ise direnç üzerinden GND hattına bağlanmalıdır.

| LED | Direnç | STM32 Pini |
| :--- | :--- | :--- |
| Kırmızı LED | 220 Ohm | `PA1` |
| Yeşil LED | 220 Ohm | `PA2` |
| Sarı LED | 220 Ohm | `PA3` |
| Mavi LED | 220 Ohm | `PA5` |
| (Tümü) | - | `GND` |

<img width="473" height="404" alt="Pin_Baglantilari" src="https://github.com/user-attachments/assets/39f386d1-f1e7-4f13-b418-1070236beaa6" />


### Kod Bloğu

<img width="1065" height="460" alt="04" src="https://github.com/user-attachments/assets/4aede860-2109-4b4e-b063-ce0742c0e79d" />

