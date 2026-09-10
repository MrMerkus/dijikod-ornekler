# Site 1 — Restoran: "Ocakbaşı Nar"

Klasör: `restoran/` · Dosya: `restoran/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Ocakbaşı Nar** — Beyoğlu Asmalımescit'te, modern yorumlu Anadolu ocakbaşı.
Kuruluş 2016. Küçük, 42 kişilik, açık ocak masanın önünde. Şef Kerem Atalay, Gaziantep
mutfağıyla büyümüş, İstanbul'da çalışmış. Akşam yemeği ağırlıklı, öğle sadece hafta içi.
Rezervasyon şart denecek kadar dolu.

**Anlatının merkezi:** ateş. Site bir menü listesi değil, ocağın etrafında geçen bir akşamın
anlatısı. Yemek fotoğrafı satmıyor — mekânın sıcaklığı satıyor.

## Görsel kimlik

Bu site **koyu, editoryal ve sıcak** olacak. Dergi sayfası gibi, kart yığını gibi değil.

| Rol | Değer |
| --- | --- |
| Zemin | `#14110F` (kömürleşmiş kahve-siyah, saf siyah değil) |
| Yüzey | `#1E1A17` |
| Metin | `#F3EDE4` (kirli krem) |
| İkincil metin | `#A39687` |
| Vurgu | `#E0562A` (köz turuncusu) — az kullan, sadece CTA ve tek kelime vurgusu |
| İkinci vurgu | `#7A2E2E` (nar kırmızısı), sadece degrade ve çizgilerde |

- Fontlar: **Instrument Serif** (başlıklar, geniş ve ferah) + **Inter** (gövde).
- Başlık karakteri: büyük punto, sıkı harf aralığı (`letter-spacing:-.02em`), satır yüksekliği 1.05.
- Doku: sayfanın tamamına %3 opaklıkta SVG grain (`feTurbulence`, `baseFrequency=.8`),
  `mix-blend-mode: overlay`, `pointer-events:none`. Bu, koyu zemini "matbaa" hissine sokar.
- Köşe yarıçapı **çok az**: 2–4px. Bu site yuvarlak değil, keskin.
- Ateş hissi: hero'nun altında yavaşça nefes alan turuncu radyal degrade (`@property` ile
  animasyonlu), 12 saniyelik döngü, çok belirsiz. Fark edilmemeli, hissedilmeli.

## Düzen mantığı — diğer ikisinden farkı

**Dikey editoryal akış.** Bölümler tam genişlik, aralarında bol nefes. Menü **kart değil,
liste**: yemek adı solda, fiyat sağda, arada noktalı çizgi — gerçek bir menü kartı gibi.
Izgara kullanılan tek yer galeri.

## Bölümler

1. **Hero** — tam ekran (`100svh`). Arkada mekân fotoğrafı, üzerine alttan yukarı koyu degrade.
   Üstte ince nav (Menü · Mekân · İletişim + sağda "Rezervasyon" butonu).
   H1: **"Ateşin başında bir akşam"** — Instrument Serif, `--step-5`.
   Altında tek cümle: "Asmalımescit'te, açık ocakta pişen Anadolu mutfağı."
   İki buton: birincil "Rezervasyon Yap" (WhatsApp'a gider), ikincil hayalet buton "Menüyü Gör".
   En altta ince bir "aşağı" işareti, yavaşça nefes alıyor.

2. **Anlatı** — iki sütun. Solda `--step-3` puntoda üç cümlelik metin: ocağın 2016'dan beri
   hiç sönmediği, şefin Gaziantep'ten getirdiği tarifler, günlük değişen menü. Sağda tek
   dikey fotoğraf (3:4), hafif yukarı kayan parallax.

3. **Menü** — sayfanın kalbi. Dört başlık: **Başlangıçlar · Ocaktan · Yanına · Tatlı**.
   Her başlık altında 4–6 yemek. Satır düzeni: `yemek adı ······ ₺fiyat`, altında ince gri
   bir satır malzeme açıklaması. Gerçekçi yaz: "Kaburga şiş — ₺680", "Fırın sütlaç — ₺180".
   Fiyatlar 2026 İstanbul seviyesinde makul olsun. Başlıklar arasında ince yatay çizgi.
   Üstte küçük bir not: "Menü mevsime göre değişir, ocaktan çıkanlar günlüktür."

4. **Mekân** — asimetrik galeri, 5 fotoğraf: biri geniş (16:9), ikisi dikey (3:4), ikisi
   kare. `:has()` ile: birinin üzerine gelince diğerleri sönümlenir
   (`opacity:.35; filter:grayscale(.6)`), üzerine gelinen hafif büyür.

5. **Bilgi** — üç sütun: **Adres** (Asmalımescit Mah. Sofyalı Sk. No:14, Beyoğlu/İstanbul),
   **Saatler** (haftalık tablo + "şu an açık/kapalı" rozeti), **İletişim** (telefon, WhatsApp,
   Instagram). Yanında koyu temalı gömülü harita yerine, harita görselinin tutucusu ve
   üzerinde "Yol Tarifi Al" butonu (Google Maps aramasına gider) — gömülü iframe kullanma,
   tek dosya kuralı ve gizlilik için.

6. **Rezervasyon kapanışı** — tam genişlik, üstte köz turuncusu degrade. Tek cümle:
   "Masanızı ayıralım." Altında büyük WhatsApp butonu ve telefon numarası. Kısa not:
   "6 kişi ve üzeri için lütfen arayın."

7. **Footer** — ince, tek satır: logo (metin olarak "NAR"), telif, "Site: DijiKod" bağlantısı.

**Saatler:** Pzt–Per 18:00–00:00 · Cum–Cmt 18:00–01:00 · Paz 13:00–23:00 · öğle servisi
hafta içi 12:00–15:00.

## Fotoğraf sözleşmesi (`restoran/gorseller/OKU.md`)

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 16:9 | Akşam, ocak başı, alev ve masa. Sıcak ışık |
| `anlati.jpg` | 3:4 | Şef ocakta çalışırken, yakın plan |
| `mekan-1.jpg` | 16:9 | Salonun geneli, dolu bir akşam |
| `mekan-2.jpg` | 3:4 | Masa detayı, yemek ve şarap |
| `mekan-3.jpg` | 3:4 | Ocaktan çıkan şiş, yakın plan |
| `mekan-4.jpg` | 1:1 | Detay: bakır tabak, közlenmiş biber |
| `mekan-5.jpg` | 1:1 | Detay: mekânın duvarı, doku |
| `og.jpg` | 1200×630 | Paylaşım görseli |
