# Site 2 — Kuaför: "Atelier Vera"

Klasör: `kuafor/` · Dosya: `kuafor/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Atelier Vera** — Nişantaşı'nda üst segment saç ve renk stüdyosu. Altı koltuk,
randevuyla çalışır, kapıdan müşteri almaz. Kurucu Vera Demirtaş, on beş yıl Londra'da
çalışmış, uzmanlığı **renk** — özellikle balyaj ve doğal ton geçişleri. Ekipte üç stilist.

**Anlatının merkezi:** sakinlik ve ustalık. Bu bir "güzellik salonu" değil, bir atölye.
Aceleye getirilmez, randevu bir seans sürer, fiyat da ona göredir. Site bunu özür dilemeden
söyler.

## Görsel kimlik

Bu site **açık, ferah ve lüks** olacak — restoranın tam zıddı. Bolca beyaz alan, ince
çizgiler, sessiz renkler. Lüks burada altın yaldızla değil, **boşlukla** anlatılır.

| Rol | Değer |
| --- | --- |
| Zemin | `#F7F4F0` (sıcak kirli beyaz) |
| Yüzey | `#FFFFFF` |
| Metin | `#2B2724` |
| İkincil metin | `#8A8078` |
| Vurgu | `#B9A48C` (kum-taupe) — çizgiler, altı çizili vurgular |
| Koyu blok | `#2B2724` (sadece kapanış bölümü ters kontrast için) |

- Fontlar: **Syne** (başlıklar — karakterli, geniş, moda dergisi hissi) + **Outfit** (gövde).
- Başlıklarda harf aralığı ferah, `letter-spacing:.01em`; büyük başlıklarda küçük harf kullan
  (`text-transform:none`), bağırmıyor.
- Çizgi dili: 1px `#E4DED6` ayırıcılar. Kutu yok, gölge yok, kart yok — bölümler **çizgiyle**
  ayrılır. Gölge yerine ince kenarlık.
- Köşe yarıçapı: fotoğraflarda 0 (tam keskin), butonlarda tam yuvarlak (`999px`). Bu karşıtlık
  kimliğin imzası.
- Hiçbir yerde grain, glow veya degrade patlaması yok. Bu site **temiz**.

## Düzen mantığı — diğer ikisinden farkı

**Bölünmüş ekran ve yapışkan sütun.** Hizmetler bölümünde sol sütun `position:sticky` ile
sabit kalır (hizmet adı ve açıklaması), sağ sütun kayar (fotoğraflar ve fiyatlar). Restoranın
dikey akışına ve kafenin ızgarasına hiç benzemez. Sayfa ikiye bölünmüş hissi verir.

## Bölümler

1. **Hero** — tam ekran değil, `78svh`. Sol yarıda metin, sağ yarıda tek dikey fotoğraf
   (kenara kadar taşan, üstten alta tam yükseklik). Mobilde alt alta.
   Üstte çok ince nav: Hizmetler · Ekip · İletişim + "Randevu" butonu.
   H1: **"rengin ustalığı"** — Syne, küçük harf, `--step-5`.
   Altında: "Nişantaşı'nda, altı koltuklu bir renk atölyesi. Randevuyla çalışıyoruz."
   Tek birincil buton: "Randevu Al" (WhatsApp). Yanında ince metin bağlantı: "Fiyatları gör ↓"

2. **Manifesto** — tam genişlik, ortalanmış, çok boşluklu. Üç kısa cümle, `--step-3`:
   aceleye getirmemek, saçın geçmişini okumak, doğal görünen renk. Aralarında bolca boşluk.
   Bu bölümde fotoğraf yok — kasıtlı bir sessizlik.

3. **Hizmetler ve fiyatlar** — sitenin kalbi, yapışkan bölünmüş düzen.
   Sol (yapışkan): hizmet başlığı + iki cümle açıklama + "Süre: ~3 saat" bilgisi.
   Sağ (kayan): o hizmetin fotoğrafı ve fiyat satırı.
   Dört hizmet: **Balyaj · Renk Yenileme · Kesim ve Şekillendirme · Bakım ve Onarım**.
   Fiyatlar "₺4.500'den başlar" biçiminde, saç uzunluğuna göre değiştiği notuyla.
   Altında küçük not: "Kesin fiyat, ilk görüşmede saçınız görüldükten sonra verilir."

4. **Önce / sonra** — dört çift fotoğraf. Kaydırıcı (slider) yapma, JS ağırlaşır: yan yana
   iki fotoğraf, üzerlerinde ince "önce" / "sonra" etiketi. Üzerine gelince sonra fotoğrafı
   hafif büyür. Altında müşterinin tek cümlelik yorumu ve adı ("Elif K.").

5. **Ekip** — üç kişi. Fotoğraf (3:4), ad, uzmanlık, tek cümle. Kart değil: fotoğrafın altında
   sadece metin, çerçeve yok.

6. **Bilgi** — iki sütun. Solda adres (Teşvikiye Mah. Vali Konağı Cad. No:87, Şişli/İstanbul),
   saatler tablosu, "şu an açık/kapalı" rozeti. Sağda harita tutucusu + "Yol Tarifi Al".
   Altında iptal politikası: "Randevunuzu 24 saat önceden bildirerek değiştirebilirsiniz."

7. **Kapanış** — koyu blok (`#2B2724`), ters kontrast, sayfanın tek koyu bölümü.
   "randevunuzu ayıralım." + WhatsApp butonu + telefon.

8. **Footer** — ince, tek satır.

**Saatler:** Salı–Cumartesi 10:00–19:00 · Pazar–Pazartesi kapalı. (Pazartesi kapalı olması
gerçekçi ve karakter katıyor.)

## Fotoğraf sözleşmesi (`kuafor/gorseller/OKU.md`)

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 3:4 | Stüdyo içi veya saç detayı, doğal ışık, sakin |
| `hizmet-balyaj.jpg` | 4:5 | Balyaj sonucu, arkadan çekim |
| `hizmet-renk.jpg` | 4:5 | Renk uygulaması sırasında |
| `hizmet-kesim.jpg` | 4:5 | Kesim sonrası, portre |
| `hizmet-bakim.jpg` | 4:5 | Bakım uygulaması, detay |
| `once-1.jpg` … `once-4.jpg` | 3:4 | Önce fotoğrafları |
| `sonra-1.jpg` … `sonra-4.jpg` | 3:4 | Sonra fotoğrafları |
| `ekip-1.jpg` … `ekip-3.jpg` | 3:4 | Stilist portreleri |
| `og.jpg` | 1200×630 | Paylaşım görseli |
