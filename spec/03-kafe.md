# Site 3 — Kafe: "Demlik Kahve"

Klasör: `kafe/` · Dosya: `kafe/index.html`
**Önce `spec/00-ORTAK-TEKNIK.md` okunacak.** Oradaki kurallar bağlayıcıdır.

## İşletme

Kurgusal. **Demlik Kahve** — Kadıköy Moda'da mahalle kahvecisi. 2021'de açılmış. Küçük
dükkân, dört masa içeride, sokakta tabure. Sabah erken açar, akşamüstü kapanır.

**Ayırt edici yanı:** Türk kahvesi ile espresso makinesini aynı ciddiyetle ele alır. Cezve
közde pişer, espresso da doğru çekilir; yanında demli çay ve lokum vardır. "Ya modern
kahveci ya mahalle kahvesi" ikilemini reddediyor, ikisi birden.

**Anlatının merkezi:** neşe ve dürüstlük. Ne olduğunu saklamıyor. Kahve adları karışıyorsa
duvardaki rehbere bakılır, tarif edilir, yapılır. Site de aynı: doğrudan, renkli,
kendinden emin.

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
   yuvarlak hap şeklinde bir çubuk içinde (Menü · Rehber · Nerede + "Sipariş" butonu).
   H1 devasa, üç satır: **"günün" / "en iyi" / "demliği"** — orta satır turuncu, alt satır
   kontur. Sağ altta küçük bir dönen rozet (SVG `textPath`, "MODA · KADIKÖY · 2021 ·").
   **Sağ tarafta `hero.jpg` (3:4 dikey), yuvarlatılmış köşeli, hafif eğik duran bir kart
   gibi** (`transform: rotate(-2deg)`), arkasında turuncu bir blok kayık duruyor.
   Mobilde metnin altına iner. Altında kısa cümle ve iki buton: "Menüyü Gör" (turuncu dolu)
   ve "Nerede?" (kontur).

2. **Marquee şerit** — koyu yeşil, ince, sonsuz kayan yazı:
   "TÜRK KAHVESİ · ESPRESSO · DEMLİ ÇAY · MODA'DA · HER GÜN 07:30'DA ·".

3. **Bento ızgara — "Bugün ne var"** — beş kutu, farklı boyutlarda. Fotoğraflar gerçek,
   tutucu yok:
   - Büyük kutu (2×2), koyu yeşil: **Türk kahvesi** — `kahve-turk.jpg` (1:1). Metin:
     közde pişer, tek/duble, yanında lokum. Fiyat satırı.
   - Kare kutu, krem: **Espresso bazlı** — `kahve-latte.jpg` (1:1). Latte, cappuccino,
     flat white kısa listesi ve fiyatları.
   - Kare kutu, turuncu: **Çay ve tatlı** — `cay-tatli.jpg` (1:1). Demli çay, lokum,
     günün tatlısı.
   - Yatay kutu, orta yeşil: **Mekân** — `mekan-1.jpg` (4:3). "Dört masa içeride,
     sokakta tabure." kısa metin.
   - Küçük kutu, koyu yeşil: Instagram bağlantısı, tek satır.
   `:has()` ile üzerine gelinen kutu hafif kalkar ve kalın kenarlık kazanır.

4. **"Ne içsem?" rehberi** — sitenin imza bölümü ve diğer iki sitede karşılığı yok.
   Solda `menu-rehber.jpg` (yaklaşık 4:5, içecek çeşitleri rehberi görseli), sağda metin:
   "Kahve adları karıştı mı? Panoya bak, tarif et, biz yaparız." Altında dört kısa satır,
   her biri tek cümlelik tarif: Espresso · Americano · Latte · Cappuccino. Fotoğraf krem
   zemin üstünde koyu yeşil çerçeveli, hafif eğik.

5. **Menü** — iki sütun, sade. Solda **Sıcak**, sağda **Soğuk**. Her satır: içecek adı,
   fiyat. Altında küçük not: "Alternatif sütler ücretsiz." Fiyatlar 2026 Kadıköy seviyesinde
   makul: Türk kahvesi ₺85, filtre ₺95, latte ₺130, demli çay ₺40 gibi. Türk kahvesi
   listenin **başında** durur, sitenin merkezinde o var.

6. **Mekân anlatısı** — koyu yeşil tam genişlik blok. Solda metin: sabah yedi buçukta
   açılır, ilk cezve o saatte közde, akşamüstü kapanır; mahalle kahvesi olmakla üçüncü
   dalga olmak arasında bir yerde durur. Sağda `mekan-2.jpg` (4:3), yuvarlatılmış.

7. **Nerede** — krem zemin. Solda adres (Caferağa Mah. Moda Cad. No:41, Kadıköy/İstanbul),
   saat tablosu ve "şu an açık/kapalı" rozeti, ulaşım notu ("Moda İskelesi'ne 4 dakika").
   Sağda harita tutucusu + "Yol Tarifi Al" butonu.

8. **Kapanış** — turuncu tam genişlik blok. "hadi bir kahve." + WhatsApp butonu + telefon.

9. **Footer** — koyu yeşil, ince.

**Saatler:** Her gün 07:30–18:00 · Pazar 09:00–17:00.

## Fotoğraf sözleşmesi (`kafe/gorseller/OKU.md`)

Fotoğraflar **klasörde mevcut**, boyutları aşağıdaki gibidir. Kod bu adları ve oranları
kullanır. Tutucu (placeholder) mantığı yine de kalır: dosya silinirse sayfa bozulmaz.

| Dosya | Oran | Ne |
| --- | --- | --- |
| `hero.jpg` | 3:4 (900×1200) | Espresso fincanı, beyaz porselen, çekirdek yanında |
| `kahve-turk.jpg` | 1:1 (900×900) | Cezvede Türk kahvesi, bakır takım, çekirdek |
| `kahve-latte.jpg` | 1:1 (900×900) | Latte art, ahşap tepsi |
| `cay-tatli.jpg` | 1:1 (900×900) | İnce belli bardakta çay, lokum, yanında kahve |
| `mekan-1.jpg` | 4:3 (1200×900) | Aydınlık köşe, tepside iki fincan |
| `mekan-2.jpg` | 4:3 (1200×900) | Loş akşam, americano fincanları |
| `menu-rehber.jpg` | ~4:5 (1000×1242) | İçecek çeşitleri rehber panosu |
| `og.jpg` | 1200×630 | Paylaşım görseli |
