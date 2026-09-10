# Site 1 — Restoran: "Nar Teras · Pizza & Bar"

Klasör: `restoran/` · Dosya: `restoran/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Nar Teras** — Caddebostan sahilinde, denize bakan çatı terasında pizza ve
kokteyl mekânı. Kuruluş 2016. Taş fırında pizza, yanında atıştırmalık, arkasında ciddi
bir kokteyl barı. Akşam ağırlıklı; hava iyiyse teras, değilse alt kat salon açık.
Gün batımı saatinde rezervasyonsuz masa bulunmaz.

**Anlatının merkezi:** akşamüstü. Site bir menü listesi değil, güneş batarken terasta
başlayan bir akşamın anlatısı. Pizza fotoğrafı satmıyor — o saatin havası satıyor.

## Görsel kimlik

Bu site **koyu, editoryal ve sıcak** olacak. Dergi sayfası gibi, kart yığını gibi değil.

| Rol | Değer |
| --- | --- |
| Zemin | `#14110F` (kömürleşmiş kahve-siyah, saf siyah değil) |
| Yüzey | `#1E1A17` |
| Metin | `#F3EDE4` (kirli krem) |
| İkincil metin | `#A39687` |
| Vurgu | `#E0562A` (gün batımı turuncusu) — az kullan, sadece CTA ve tek kelime vurgusu |
| İkinci vurgu | `#7A2E2E` (nar kırmızısı), sadece degrade ve çizgilerde |

- Fontlar: **Instrument Serif** (başlıklar, geniş ve ferah) + **Inter** (gövde).
- Başlık karakteri: büyük punto, sıkı harf aralığı (`letter-spacing:-.02em`), satır yüksekliği 1.05.
- Doku: sayfanın tamamına %3 opaklıkta SVG grain (`feTurbulence`, `baseFrequency=.8`),
  `mix-blend-mode: overlay`, `pointer-events:none`. Bu, koyu zemini "matbaa" hissine sokar.
- Köşe yarıçapı **çok az**: 2–4px. Bu site yuvarlak değil, keskin.
- Gün batımı hissi: hero'nun altında yavaşça nefes alan turuncu radyal degrade (`@property`
  ile animasyonlu), 12 saniyelik döngü, çok belirsiz. Fark edilmemeli, hissedilmeli.

## Düzen mantığı — diğer ikisinden farkı

**Dikey editoryal akış.** Bölümler tam genişlik, aralarında bol nefes. Menü **kart değil,
liste**: yemek adı solda, fiyat sağda, arada noktalı çizgi — gerçek bir menü kartı gibi.
Izgara kullanılan tek yer galeri.

## Bölümler

1. **Hero** — tam ekran (`100svh`). Arkada `hero.jpg` (14:9, denize bakan teras, ışık
   dizileri), üzerine alttan yukarı koyu degrade. Üstte ince nav (Menü · Mekân · İletişim +
   sağda "Rezervasyon" butonu).
   H1: **"Güneş batarken terasta"** — Instrument Serif, `--step-5`.
   Altında tek cümle: "Caddebostan sahilinde, taş fırında pizza ve kokteyl."
   İki buton: birincil "Rezervasyon Yap" (WhatsApp'a gider), ikincil hayalet buton "Menüyü Gör".
   En altta ince bir "aşağı" işareti, yavaşça nefes alıyor.

2. **Anlatı** — iki sütun. Solda `--step-3` puntoda üç cümlelik metin: terasın 2016'dan beri
   aynı saatte dolduğu, hamurun 48 saat dinlendiği, barın kendi şuruplarını yaptığı. Sağda
   `pizza-tanitim.jpg` (3:4, fırından çıkan pizza dilimi, buharlı), hafif yukarı kayan parallax.

3. **Menü** — sayfanın kalbi. Dört başlık: **Pizzalar · Atıştırmalıklar · Kokteyller ·
   Alkolsüz**. Satır düzeni: `ürün adı ······ ₺fiyat`, altında ince gri bir satır malzeme
   açıklaması. Gerçekçi yaz: "Margherita — ₺420", "Pepperoni — ₺520", "Buffalo kanat — ₺390",
   "Sunset Spritz — ₺450". 2026 İstanbul seviyesinde makul fiyat.
   **Menü bölümünün içine iki fotoğraf gömülür**, kart olarak değil, tam genişlik bant olarak:
   - Pizzalar başlığının altında `menu-pizza.jpg` (~4:5, dokuz pizza çeşidi panosu),
     yanında not: "Dokuz sabit pizza, hafta sonu bir de günün pizzası."
   - Kokteyller başlığının altında `menu-icecek.jpg` (uzun dikey, kokteyl çeşitleri panosu),
     `max-height: 70svh` ile sınırlı, `object-fit: contain`.
   Atıştırmalıklar başlığının yanında küçük kare `menu-atistirmalik.jpg` (1:1).
   Üstte küçük not: "Fırın 23:30'da kapanır, bar 01:00'e kadar açık."

4. **Mekân** — asimetrik galeri, 4 fotoğraf: `mekan-1.jpg` (14:9, geniş — alt kat salon),
   `mekan-2.jpg` (3:4, teras dikey), `bar.jpg` (3:4, bar tezgâhı ve kokteyller),
   `menu-atistirmalik.jpg` (1:1). `:has()` ile: birinin üzerine gelince diğerleri sönümlenir
   (`opacity:.35; filter:grayscale(.6)`), üzerine gelinen hafif büyür.

5. **Bilgi** — üç sütun: **Adres** (Caddebostan Mah. Plaj Yolu Sk. No:22, Kadıköy/İstanbul),
   **Saatler** (haftalık tablo + "şu an açık/kapalı" rozeti), **İletişim** (telefon, WhatsApp,
   Instagram). Yanında harita görselinin tutucusu ve üzerinde "Yol Tarifi Al" butonu —
   gömülü iframe kullanma.
   Ek not: "Teras hava koşullarına bağlıdır; yağmurlu günlerde alt kat salonda ağırlıyoruz."

6. **Rezervasyon kapanışı** — tam genişlik, üstte gün batımı turuncusu degrade. Tek cümle:
   "Masanızı ayıralım." Altında büyük WhatsApp butonu ve telefon numarası. Kısa not:
   "6 kişi ve üzeri için lütfen arayın."

7. **Footer** — ince, tek satır: logo (metin olarak "NAR"), telif, "Site: DijiKod" bağlantısı.

**Saatler:** Pzt–Per 16:00–00:00 · Cum–Cmt 16:00–01:00 · Paz 13:00–00:00.

## Fotoğraf sözleşmesi (`restoran/gorseller/OKU.md`)

Fotoğraflar **klasörde mevcut**. Kod bu adları ve oranları kullanır; dosya silinirse
sayfa bozulmaz, tutucu görünür.

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 14:9 (1400×900) | Denize bakan teras, ışık dizileri, akşamüstü |
| `mekan-1.jpg` | 14:9 (1400×900) | Alt kat salon, menü duvarı |
| `mekan-2.jpg` | 3:4 (900×1200) | Teras, dikey kadraj |
| `bar.jpg` | 3:4 (900×1200) | Bar tezgâhında sıralanmış kokteyller |
| `pizza-tanitim.jpg` | 3:4 (900×1200) | Fırından çıkan pizza dilimi, buharlı |
| `menu-pizza.jpg` | ~4:5 (1000×1226) | Dokuz pizza çeşidi panosu, ahşap zemin |
| `menu-icecek.jpg` | uzun dikey (900×1599) | Kokteyl çeşitleri panosu |
| `menu-atistirmalik.jpg` | 1:1 (900×900) | Kanat ve patates tabakları |
| `og.jpg` | 1200×630 | Paylaşım görseli |

**Kullanılmayan dosya:** `menu-pizza-cesit.jpg` klasörde durur ama kodda kullanılmaz —
`menu-pizza.jpg` ile aynı içeriğin ikinci çekimi. Silme, yedek olarak kalsın.
