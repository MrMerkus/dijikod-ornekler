# Site 3 — Kafe: "Demlik Kahve"

Klasör: `kafe/` · Dosya: `kafe/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Demlik Kahve** — Kadıköy Moda'da üçüncü dalga kahveci. 2021'de açılmış, kendi
kavurmasını yapıyor. Küçük dükkân, dört masa içeride, sokakta tabure. Sabah erken açar,
akşamüstü kapanır. Filtre kahve ve espresso ciddiye alınır, yanında ev yapımı iki üç tatlı
bulunur. Çekirdek satışı da var, paket olarak.

**Anlatının merkezi:** neşe ve dürüstlük. Ne olduğunu saklamıyor: kahve nereden geliyor, kim
kavurmuş, ne zaman kavrulmuş. Site de aynı: doğrudan, renkli, kendinden emin.

## Görsel kimlik

Bu site **grafik, yüksek kontrastlı ve neşeli** olacak. Restoran koyu ve editoryal, kuaför
açık ve sessiz — bu ise **renkli ve gürültülü**. Poster gibi, dergi ilanı gibi.

| Rol | Değer |
| --- | --- |
| Zemin | `#FFF6E5` (krem) |
| Koyu blok | `#14342B` (koyu orman yeşili) |
| Metin | `#14342B` üzerine krem, krem üzerine koyu yeşil |
| Vurgu | `#FF6B35` (turuncu) — cesurca kullan, korkma |
| İkinci vurgu | `#3A7D5C` (orta yeşil) |

- Fontlar: **Space Grotesk** (başlıklar — teknik ve karakterli) + **DM Sans** (gövde).
- Başlıklar **çok büyük** ve sıkı: `letter-spacing:-.04em`, satır yüksekliği 0.95.
  Bazı kelimeler turuncu, bazıları içi boş kontur (`-webkit-text-stroke: 2px`).
- Köşe yarıçapı **cömert**: 20–28px. Bloklar tombul ve dost canlısı.
- Renkli bloklar kenar kenara oturur; sayfa bir renk yorganı gibi görünür.
- Kayan şerit (marquee): saf CSS `@keyframes` ile, "TAZE KAVRULMUŞ · HER SALI · MODA'DA ·"
  metni sonsuz döner. `prefers-reduced-motion` altında durur.

## Düzen mantığı — diğer ikisinden farkı

**Bento ızgarası.** Farklı boyutta renkli kutular bir ızgaraya oturuyor: biri iki sütun
kaplıyor, biri iki satır, biri kare. Restoranın dikey listesi ve kuaförün bölünmüş ekranıyla
hiç akrabalığı yok. `grid-template-areas` ile kur, mobilde tek sütuna in.

## Bölümler

1. **Hero** — tam ekran değil, içeriğin belirlediği yükseklik. Krem zemin. Nav üstte,
   yuvarlak hap şeklinde bir çubuk içinde (Menü · Çekirdek · Nerede + "Sipariş" butonu).
   H1 devasa, üç satır: **"günün" / "en iyi" / "demliği"** — orta satır turuncu, alt satır
   kontur. Sağ altta küçük bir dönen rozet (CSS `@property` ile yavaş dönen daire içinde
   "MODA · KADIKÖY · 2021 ·" yazısı, SVG `textPath`).
   Altında kısa cümle ve iki buton: "Menüyü Gör" (turuncu dolu) ve "Nerede?" (kontur).

2. **Marquee şerit** — koyu yeşil, ince, sonsuz kayan yazı. Sayfanın nefes noktası.

3. **Bento ızgara — "Bugün ne var"** — beş kutu, farklı boyutlarda:
   - Büyük kutu (2×2): günün filtre kahvesi. Çekirdeğin adı, menşei, tadım notları
     ("Etiyopya Yirgacheffe · yaban mersini, bergamot"), kavurma tarihi.
   - Dikey kutu: espresso bazlı içecekler kısa listesi ve fiyatları.
   - Kare kutu: günün tatlısı, fotoğraf ağırlıklı.
   - Yatay kutu: "Kendi kahveni götür" — paket çekirdek satışı, 250g fiyatı.
   - Küçük kutu: Instagram bağlantısı, tek satır.
   Kutuların renkleri dönüşümlü: krem, koyu yeşil, turuncu, orta yeşil. `:has()` ile üzerine
   gelinen kutu hafif kalkar ve kalın kenarlık kazanır.

4. **Menü** — iki sütun, sade. Solda **Sıcak**, sağda **Soğuk**. Her satır: içecek adı,
   fiyat. Altında küçük not: "Alternatif sütler ücretsiz." Fiyatlar 2026 Kadıköy seviyesinde
   makul: filtre ₺95, latte ₺130 gibi.

5. **Kavurma hikâyesi** — koyu yeşil tam genişlik blok. Solda metin: her salı kavuruyoruz,
   çekirdek en fazla iki hafta önce kavrulmuş olarak satılır, kavurma günü etikette yazar.
   Sağda fotoğraf (1:1), yuvarlatılmış.

6. **Nerede** — krem zemin. Solda adres (Caferağa Mah. Moda Cad. No:41, Kadıköy/İstanbul),
   saat tablosu ve "şu an açık/kapalı" rozeti, ulaşım notu ("Moda İskelesi'ne 4 dakika").
   Sağda harita tutucusu + "Yol Tarifi Al" butonu.

7. **Kapanış** — turuncu tam genişlik blok. "hadi bir kahve." + WhatsApp butonu + telefon.

8. **Footer** — koyu yeşil, ince.

**Saatler:** Her gün 07:30–18:00 · Pazar 09:00–17:00.

## Fotoğraf sözleşmesi (`kafe/gorseller/OKU.md`)

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 4:3 | Dükkânın önü veya tezgâh, gündüz ışığı |
| `bento-kahve.jpg` | 1:1 | Filtre kahve demlenirken |
| `bento-tatli.jpg` | 1:1 | Günün tatlısı, üstten çekim |
| `bento-paket.jpg` | 4:3 | Paket çekirdek, etiketi görünür |
| `kavurma.jpg` | 1:1 | Kavurma makinesi veya çekirdek detayı |
| `og.jpg` | 1200×630 | Paylaşım görseli |
