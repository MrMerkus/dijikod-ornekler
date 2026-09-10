# Site 2 — Kuaför: "Atelier Vera"

Klasör: `kuafor/` · Dosya: `kuafor/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Atelier Vera** — Nişantaşı'nda saç, renk ve makyaj stüdyosu. Altı koltuk,
randevuyla çalışır. Kurucu Vera Demirtaş, on beş yıl Londra'da çalışmış, uzmanlığı
**renk** — özellikle balyaj ve doğal ton geçişleri. Saçın yanında gelin ve özel gün
makyajı da yapılıyor.

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

1. **Hero** — tam ekran değil, `78svh`. **Solda metin, sağda `hero.jpg` (14:9 yatay,
   stüdyonun geniş iç mekânı)** — kenara kadar taşar, tam yükseklik doldurur (`object-fit:
   cover`). Mobilde alt alta. Üstte çok ince nav: Hizmetler · Stüdyo · İletişim +
   "Randevu" butonu.
   H1: **"rengin ustalığı"** — Syne, küçük harf, `--step-5`.
   Altında: "Nişantaşı'nda, altı koltuklu bir renk atölyesi. Randevuyla çalışıyoruz."
   Tek birincil buton: "Randevu Al" (WhatsApp). Yanında ince metin bağlantı: "Fiyatları gör ↓"

2. **Manifesto** — tam genişlik, ortalanmış, çok boşluklu. Üç kısa cümle, `--step-3`:
   aceleye getirmemek, saçın geçmişini okumak, doğal görünen renk. Aralarında bolca boşluk.
   **Cümlelerin arasına `cizim-1.jpg`** (elle çizilmiş fön makinesi ve tarak illüstrasyonu,
   beyaz zeminli) küçük ve sessiz yerleşir — maksimum 180px genişlik, `mix-blend-mode:
   multiply` ile zemine oturur. Fotoğraf değil, işaret gibi durur.

3. **Hizmetler ve fiyatlar** — sitenin kalbi, yapışkan bölünmüş düzen.
   Sol (yapışkan): hizmet başlığı + iki cümle açıklama + "Süre: ~3 saat" bilgisi.
   Sağ (kayan): o hizmetin fotoğrafı ve fiyat satırı.
   **Dört hizmet ve fotoğrafları:**
   - **Renk ve Balyaj** → `hizmet-sac.jpg` (4:5). "₺4.500'den başlar"
   - **Kesim ve Şekillendirme** → `mekan-1.jpg` (4:3). "₺1.200'den başlar"
   - **Makyaj** (gelin ve özel gün) → `hizmet-makyaj.jpg` (4:5). "₺2.800'den başlar"
   - **Bakım ve Onarım** → `anlati.jpg` (3:4). "₺1.900'den başlar"
   Altında küçük not: "Kesin fiyat, ilk görüşmede saçınız görüldükten sonra verilir."

4. **Stüdyo** — önce/sonra bölümünün yerine geçer. Üç fotoğraflı asimetrik galeri:
   `mekan-2.jpg` (4:3) büyük solda, `mekan-1.jpg` (4:3) ve `hero.jpg` sağda küçük.
   Üzerine gelince diğerleri hafif sönümlenir (`opacity:.4`), üzerine gelinen netleşir.
   Yanında iki cümle: altı koltuk, randevu arası temizlik, kapıdan müşteri alınmaması.
   **Önce/sonra fotoğrafı ve stilist portresi yok** — o bölümler kaldırıldı, uydurma
   fotoğrafla doldurulmaz.

5. **Müşteri sözleri** — ekip bölümünün yerine. Fotoğrafsız, üç kısa alıntı, ince çizgiyle
   ayrılmış, her birinin altında ad ve hizmet ("Elif K. · Balyaj"). Bu bölümde `cizim-2.jpg`
   (kuaför illüstrasyonu) sağ üstte küçük ve soluk (opacity .5, maks 140px) durur.

6. **Bilgi** — iki sütun. Solda adres (Teşvikiye Mah. Vali Konağı Cad. No:87, Şişli/İstanbul),
   saatler tablosu, "şu an açık/kapalı" rozeti. Sağda harita tutucusu + "Yol Tarifi Al".
   Altında iptal politikası: "Randevunuzu 24 saat önceden bildirerek değiştirebilirsiniz."

7. **Kapanış** — koyu blok (`#2B2724`), ters kontrast, sayfanın tek koyu bölümü.
   "randevunuzu ayıralım." + WhatsApp butonu + telefon.

8. **Footer** — ince, tek satır.

**Saatler:** Salı–Cumartesi 10:00–19:00 · Pazar–Pazartesi kapalı.

## Fotoğraf sözleşmesi (`kuafor/gorseller/OKU.md`)

Fotoğraflar **klasörde mevcut**. Kod bu adları ve oranları kullanır; dosya silinirse
sayfa bozulmaz, tutucu görünür.

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 14:9 (1400×900) | Stüdyonun geniş iç mekânı, açık renk, kemerli aynalar |
| `mekan-1.jpg` | 4:3 (1200×900) | Salon çalışırken, koltuklar dolu |
| `mekan-2.jpg` | 4:3 (1200×900) | Ahşap ve sıcak ışıklı bölüm, aynalar |
| `hizmet-sac.jpg` | 4:5 (900×1125) | Fön ve şekillendirme, stilist çalışırken |
| `hizmet-makyaj.jpg` | 4:5 (900×1125) | Makyaj paleti ve fırçalar, detay |
| `anlati.jpg` | 3:4 (900×1200) | Makas, tarak ve alet detayı |
| `cizim-1.jpg` | ~3:4 (700×933) | Fön makinesi illüstrasyonu, beyaz zemin |
| `cizim-2.jpg` | 1:1 (700×700) | Kuaför illüstrasyonu, beyaz zemin |
| `og.jpg` | 1200×630 | Paylaşım görseli |
