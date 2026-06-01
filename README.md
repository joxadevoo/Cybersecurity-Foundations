# 🏛️ Kiberxavfsizlik Asoslari (Cybersecurity Foundations)

Ushbu repository mening kiberxavfsizlik (Blue Team) yo'nalishidagi ilk qadamlarim, nazariy konspektlarim va amaliy laboratoriya qaydlarimni jamlash uchun ochildi.

## 📅 O'rganish rejasi va joriy holat:
- [x] GitHub va Shaxsiy Portfolio sozlash
- [ ] Kompyuter tarmoqlari (Networking) asoslari — *Hozirgi bosqich*
- [ ] Linux operatsion tizimi va CLI buyruqlari
- [ ] Python va Bash skriptlari

---

## 🌐 1-Mavzu: Kompyuter tarmoqlari (Konspekt)

### OSI Modeli (7 ta qatlam)
Men bugun tarmoqlar qanday ishlashini tushunish uchun OSI modelini ko'rib chiqdim. U 7 ta qatlamdan iborat:
1. **Physical (Jismoniy)** — Kabellar, bitlar va elektr signallari.
2. **Data Link** — MAC adreslar va kalitlar (Switches).
3. **Network** — IP adreslar va routerlar (Routing).
4. **Transport** — TCP va UDP protokollari (Ma'lumot yetkazish).
5. **Session** — Aloqa seanslarini boshqarish.
6. **Presentation** — Ma'lumotni formatlash va shifrlash.
7. **Application (Ilova)** — HTTP, DNS, FTP (Foydalanuvchi ko'radigan dasturlar).

*Qayd: Kiberxavfsizlikda har bir qatlamda qanday hujumlar bo'lishini bilish muhim.*

---
# 🖥️ Google'dan rasm yuklanganda soniyalar ichida nimalar sodir bo'ladi? (OSI modeli amalda)

Tasavvur qiling, brauzeringizda Google'ga kirdingiz va bitta rasm ustiga bosdingiz. Rasm ekranda paydo bo'lguncha ma'lumotlar OSI modelining barcha 7 ta qavatidan ikki marta (pastga va tepaga) o'tishga ulguradi.

Keling, barcha 7 ta qavatni birma-bir, zanjirni uzmasdan tarmoq ma'muri nigohi bilan ko'rib chiqamiz:

---

## 🛑 1-QISM: Sizdan Google'ga so'rov ketishi (Encapsulation — Qadoqlash)

Siz rasm ustiga bosganingizda, so'rovingiz yuqoridan pastga qarab bosqichma-bosqich qadoqlanadi:

* **7. Application (Ilova qavati):** Chrome brauzeri **HTTPS** protokoli orqali: *"Menga shu rasmni ber"* deb so'rov (Data) yaratadi.
* **6. Presentation (Taqdimot qavati):** So'rov matni internetda xavfsiz borishi uchun **SSL/TLS** yordamida shifrlanadi va umumiy formatga keltiriladi.
* **5. Session (Seanslar qavati):** Kompyuteringiz va Google serveri o'rtasida aloqa seansi (virtual ko'prik) ochiladi va boshqariladi.
* **4. Transport (Transport qavati):** Ma'lumot **TCP** protokoli orqali ketma-ketlik raqamlari bilan maxsus qutiga (**Segmentga**) joylanadi va Google'ning `443`-portiga yo'naltiriladi.
* **3. Network (Tarmoq qavati):** Segment ustiga sizning va Google'ning IP-manzillari yozilib, **Paket** holatiga keltiriladi. Routerlar uni eng qisqa yo'ldan jo'natish xaritasini tuzadi.
* **2. Data Link (Kanal qavati):** Paket ichki tarmoq (lokal router va kompyuter) uchun manba va maqsad **MAC-manzillari** bilan o'ralib, **Freymga** aylanadi.
* **1. Physical (Jismoniy qavat):** Hamma narsa **Bitlarga (0 va 1)** o'girilib, kabellar orqali elektr signali yoki Wi-Fi orqali radio to'lqin bo'lib Google serveriga yo'l oladi.



---

## 🔄 2-QISM: Google javob qaytarishi (Decapsulation — Qutilarni ochish)

Google so'rovni qabul qilib, so'ralgan rasmni sizga qayta yuborganda, jarayon kompyuteringizda pastdan tepaga qarab ishlaydi:

1.  **Physical (Jismoniy qavat):** Kelgan elektromagnit signallar yoki yorug'lik impulslari tarmoq kartasi (Wi-Fi yoki LAN) tomonidan qaytadan **0 va 1 (Bitlar)** ko'rinishida qabul qilinadi.
2.  **Data Link (Kanal qavati):** Freymlar ochiladi, kelgan xatolar tekshiriladi va sarlavhadagi **MAC-manzil** aynan sizning qurilmangizga tegishli ekanligi tasdiqlanadi.
3.  **Network (Tarmoq qavati):** IP-paketlar qutisi ochiladi. Google'dan kelgan paket tarkibidagi maqsadli **IP-manzil** sizniki ekanligi aniqlanib, tarmoq sarlavhalari yechiladi.
4.  **Transport (Transport qavati):** Google serveridan bo'lak-bo'lak (bo'g'in-bo'g'in) bo'lib kelgan barcha **TCP segmentlari** o'zining tartib raqami bo'yicha (`1, 2, 3...`) qaytadan bitta butun fayl holatiga yig'iladi.
5.  **Session (Seanslar qavati):** Rasm fayli kompyuterga to'liq va xatosiz yetib kelgach, ikki qurilma o'rtasida ochilgan virtual aloqa seansi muvaffaqiyatli yopiladi.
6.  **Presentation (Taqdimot qavati):** Shifrlangan baytlar kalit yordamida ochiladi (**Decryption**) va tizim hamda brauzer tushunadigan tayyor grafik formatga (`JPG`/`PNG`/`WEBP`) o'giriladi.
7.  **Application (Ilova qavati):** Chrome brauzeringiz tayyor rasm piksellarini ekranda chiroyli qilib render qiladi va ochib beradi. Muvaffaqiyat! 😻

---

## 💡 Xulosa

> Biz har safar internetda bitta havolaga o'tganimizda yoki tugmani bosganimizda, ushbu **7 ta qavat** ko'z ochib yumguncha soniyaning kichik bo'laklarida tepaga va pastga millionlab marta ishlab ulguradi. Tarmoq texnologiyalarining go'zalligi va mukammalligi ham aynan mana shu algoritmlarning zanjir kabi uzviyligidadir!
