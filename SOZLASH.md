# O'quv Markaz Bot — Sozlash Yo'riqnomasi

## 📁 Fayllar
```
papka/
├── bot.py              ← Asosiy bot
├── webapp.html         ← Admin Web App
├── oquvchilar.xlsx     ← Excel ma'lumotlar
├── users.json          ← Avtomatik yaratiladi
├── davomat.json        ← Avtomatik yaratiladi
├── analitika.json      ← Avtomatik yaratiladi
└── bot.log             ← Log fayl
```

---

## ⚙️ 1-QADAM: bot.py sozlash

```python
BOT_TOKEN  = "7123456789:AAFxxxx"   # @BotFather dan
ADMIN_IDS  = [123456789]            # Sizning Telegram ID

# O'qituvchilar (ixtiyoriy):
TEACHERS = {
    987654321: "Biloliddin",  # Bu ID Biloliddin varag'ini ko'radi
    987654322: "Aziz",        # Bu ID Aziz varag'ini ko'radi
}

JADVAL_VARAQLAR = ["Biloliddin", "Aziz"]  # Excel varaq nomlari
```

---

## 🌐 2-QADAM: Web App ulash (ixtiyoriy)

Web App uchun `webapp.html` ni internetga chiqarish kerak.

### Variant A: GitHub Pages (bepul)
1. GitHub.com da yangi repo yarating
2. `webapp.html` faylini yuklang
3. Settings → Pages → Branch: main → Save
4. URL olasiz: `https://username.github.io/repo/webapp.html`
5. `bot.py` da:
   ```python
   WEBAPP_URL = "https://bilol1ddin.github.io/web-app/"
   ```

### Variant B: Lokal (test uchun)
```bash
# Papkada turib:
python -m http.server 8080
# http://localhost:8080/webapp.html
```

---

## 🚀 3-QADAM: Ishga tushirish

```bash
pip install "python-telegram-bot[job-queue]" openpyxl
python bot.py
```

---

## 👨‍🏫 O'qituvchi qo'shish

1. O'qituvchi Telegram ID sini biling (botga /start bossangiz ID chiqadi)
2. `bot.py` da `TEACHERS` ga qo'shing:
   ```python
   TEACHERS = {
       111222333: "Biloliddin",
   }
   ```
3. Botni qayta ishga tushiring

O'qituvchi faqat o'z guruhini ko'radi:
- `/belgilay` — faqat o'z guruhi
- `/stat` — faqat o'z guruhi statistikasi

---

## 📱 Buyruqlar

### O'quvchi
| Buyruq | Tavsif |
|--------|--------|
| /start | Ro'yxatdan o'tish / jadval ko'rish |
| /davomat | Davomat va reyting |
| /sovga | Sovg'a o'yini haqida |
| /reset | Qayta ro'yxatdan o'tish |

### O'qituvchi
| Buyruq | Tavsif |
|--------|--------|
| /belgilay | O'z guruhining davomati |
| /stat | Guruh statistikasi |

### Admin
| Buyruq | Tavsif |
|--------|--------|
| /belgilay | Barcha guruhlar davomati |
| /stat | To'liq statistika |
| /analitika | Xabar yuborish tahlili |
| /elon | Barcha o'quvchilarga e'lon |
| /loteriya | Oylik sovg'a o'yini |
| /test | Eslatmani hozir sinash |
| /royxat | O'quvchilar ro'yxati |
| /reload | Excel qayta o'qish |

---

## ❓ Tez-tez so'raladigan savollar

**Davomat belgilanmayapti?**
→ O'quvchilar /start bosib ro'yxatdan o'tishi kerak
→ /belgilay ni bosing, guruh chiqsa — ishlayapti

**Excel o'zgartirilsa nima qilish kerak?**
→ Hech narsa. Bot har safar Excelni qayta o'qiydi
→ Yoki /reload buyrug'ini yuboring

**O'quvchi ikki fanda bo'lsa?**
→ Excelda ikki qatorda bo'ladi — bot ikkalasini ham ko'rsatadi

**Eslatma Yakshanbada yuborilmayapti?**
→ Bu to'g'ri. Yakshanba dam olish kuni
