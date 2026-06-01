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

🖥 Google'dan bitta rasm yuklaganimizda soniyalar ichida nimalar sodir bo'ladi? (OSI modeli amalda)

Tasavvur qiling, brauzeringizda Google'ga kirdingiz va bitta rasm ustiga bosdingiz. Rasm ekranda paydo bo'lguncha ma'lumotlar OSI modelining barcha 7 ta qavatidan ikki marta (pastga va tepaga) o'tishga ulguradi.

Keling, barcha 7 ta qavatni birma-bir, zanjirni uzmasdan ko'rib chiqamiz:

🛑 1-QISM: Sizdan Google'ga so'rov ketishi (Encapsulation)
Siz rasm ustiga bosganingizda, so'rovingiz yuqoridan pastga qarab qadoqlanadi:
7. Application (Ilova qavati): Chrome brauzeri HTTPS protokoli orqali: "Menga shu rasmni ber" deb so'rov yaratadi.
6. Presentation (Taqdimot qavati): So'rov matni internetda xavfsiz borishi uchun SSL/TLS yordamida shifrlanadi.
5. Session (Seanslar qavati): Kompyuteringiz va Google serveri o'rtasida aloqa seansi (virtual ko'prik) ochiladi.
4. Transport (Transport qavati): Ma'lumot TCP protokoli orqali maxsus qutiga (Segmentga) joylanadi va Google'ning 443-portiga yo'naltiriladi.
3. Network (Tarmoq qavati): Segment ustiga sizning va Google'ning IP-manzillari yozilib, Paket holatiga keltiriladi. Routerlar uni eng qisqa yo'ldan jo'natadi.
2. Data Link (Kanal qavati): Paket ichki tarmoq uchun MAC-manzillar bilan o'ralib, Freymga aylanadi.
1. Physical (Jismoniy qavat): Hamma narsa Bitlarga (0 va 1) o'girilib, simlar orqali elektr signali bo'lib Google serveriga yetib boradi.

🔄 2-QISM: Google javob qaytarishi (Decapsulation)
Google so'rovni ko'rib, rasmni sizga yuborganda, jarayon pastdan tepaga qarab ishlaydi:

1. Physical (Jismoniy qavat): Kelgan bitlar kompyuteringiz tarmoq kartasi (Wi-Fi yoki LAN) tomonidan qabul qilinadi.
2. Data Link (Kanal qavati): Freymlar ochilib, MAC-manzil aynan siznikiligi tekshiriladi va xatolar tuzatiladi.
3. Network (Tarmoq qavati): IP-paketlar ochiladi va maqsadli IP-manzil sizniki ekanligi tasdiqlanadi.
4. Transport (Transport qavati): Google'dan bo'lak-bo'lak bo'lib kelgan barcha TCP segmentlari tartib raqami bo'yicha (1, 2, 3...) bitta butun fayl qilib qayta yig'iladi.
5. Session (Seanslar qavati): Rasm to'liq yetib kelgach, o'sha ochilgan aloqa seansi muvaffaqiyatli yopiladi.
6. Presentation (Taqdimot qavati): Shifrlangan baytlar ochiladi (decryption) va brauzer tushunadigan JPG/PNG rasm formatiga keltiriladi.
7. Application (Ilova qavati): Chrome brauzeringiz rasmni ekranda chiroyli qilib ochib beradi. Muvaffaqiyat! 😻

💡 Xulosa: Biz har safar internetda bitta tugmani bosganimizda, ushbu 7 ta qavat ko'z ochib yumguncha soniyaning kichik bo'laklarida tepaga va pastga ishlab ulguradi. Tarmoq texnologiyalarining go'zalligi va mukammalligi ham shunda!
