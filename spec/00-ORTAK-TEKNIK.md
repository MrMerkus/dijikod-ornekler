# Ortak teknik sözleşme — bütün örnek siteler

Bu dosya üç sitenin de uyacağı kurallardır. Site spec'i bunun üstüne kimlik ve içerik ekler.
Çelişki olursa **site spec'i kazanır**, ama teknik kurallar tartışmasızdır.

## 1. Dosya yapısı

Her site kendi klasöründe:

```
<slug>/
  index.html          ← TEK dosya. Bütün CSS ve JS bunun içinde inline.
  gorseller/
    OKU.md            ← fotoğraf sözleşmesi (spec'te verilen tabloyu buraya yaz)
```

- **Build aracı yok, npm yok, bundler yok, framework yok.** Ne React, ne Tailwind CDN.
- CSS `<style>` içinde, JS `<script>` içinde, ikisi de aynı `index.html` dosyasında.
- Tek dış kaynak izni: **Google Fonts `<link>` etiketi**. Başka hiçbir CDN, hiçbir kütüphane.
- Dosya `file://` ile çift tıklanarak açıldığında da düzgün çalışmalı (sunucu gerektirmemeli).

## 2. Fotoğraflar — devir sözleşmesi

Fotoğraflar **sonra** gelecek. Kod onları bekleyecek şekilde yazılır:

- Her `<img>` etiketi `gorseller/<ad>.jpg` yolunu gösterir, `width`/`height` veya
  `aspect-ratio` ile yeri baştan ayrılır (sayfa fotoğraf gelince zıplamamalı).
- Fotoğraf yokken **boş görünmez**: her görsel kutusunun altında markanın renklerinde bir
  CSS degrade tutucu durur, üzerinde ince harflerle ne geleceği yazar (örn. "Mekân — 16:9").
  Bunu `background` ile yap; `<img>` yüklenemezse tutucu görünür kalır.
- `gorseller/OKU.md` dosyasına spec'teki fotoğraf tablosunu aynen yaz: dosya adı, en-boy
  oranı, ne fotoğrafı olduğu. Baran bu klasörü doldurup üzerine kopyalayacak — **kodda tek
  satır değişmemeli.**
- `loading="lazy"` ilk ekran dışındaki bütün görsellerde, `alt` metni Türkçe ve anlamlı.

## 3. Tipografi

- Fontlar Google Fonts'tan, `&display=swap` ile. Site spec'i hangi ikiliyi kullanacağını söyler.
- Akışkan ölçek, medya sorgusu yok:

```css
:root{
  --step--1: clamp(.875rem, .85rem + .12vw, .9375rem);
  --step-0 : clamp(1rem, .96rem + .22vw, 1.125rem);
  --step-1 : clamp(1.25rem, 1.16rem + .43vw, 1.5rem);
  --step-2 : clamp(1.56rem, 1.41rem + .76vw, 2rem);
  --step-3 : clamp(1.95rem, 1.71rem + 1.24vw, 2.66rem);
  --step-4 : clamp(2.44rem, 2.05rem + 1.93vw, 3.55rem);
  --step-5 : clamp(3.05rem, 2.46rem + 2.95vw, 4.74rem);
}
```

- Gövde metni `--step-0`, satır yüksekliği 1.6. Başlıklarda `text-wrap: balance`,
  paragraflarda `text-wrap: pretty` (Firefox'ta yok sayılır, sorun değil).
- Türkçe karakterler (ğ ı ş ç ö ü İ) her fontta kontrol edilmiş olmalı; `lang="tr"` şart.

## 4. Hareket

- **Reveal deseni:** `animation-timeline: view()` kullan, ama **Firefox'ta bayrak arkasında**
  olduğu doğrulandı. Bu yüzden `@supports (animation-timeline: view())` ile sar ve
  desteklenmeyen tarayıcı için IntersectionObserver yedeğini yaz. İkisi de yoksa içerik
  **görünür** kalmalı — asla `opacity:0` takılı kalmasın.
- Hareket ince olsun: `translateY(24px) → 0` ve `opacity 0 → 1`, süre 600–900ms,
  yumuşama `cubic-bezier(.16,1,.3,1)`, listelerde 60–80ms kademeli gecikme.
- **Yasak:** kaydırma çalma (scrolljacking), yandan uçarak giren öğeler, daktilo efekti,
  otomatik açılan pop-up, sayfa yüklenirken bekleme ekranı.
- `prefers-reduced-motion: reduce` altında bütün animasyonlar kapanır, içerik son halinde
  görünür.

## 5. Mobil ve dönüşüm — hepsinde zorunlu

Türkiye'de yerel esnaf sitesinde dönüşümü belirleyen şey bu ikisi:

- **Sabit WhatsApp butonu**, sağ altta. Jenerik yeşil daire **değil**: markanın renklerinde,
  özel çizilmiş inline SVG. Masaüstünde hover'da "WhatsApp'tan yazın" metnine açılır.
  Bağlantı: `https://wa.me/905XXXXXXXXX?text=<önceden yazılmış Türkçe mesaj>` — numara
  yer tutucu `905XXXXXXXXX` kalır, `OKU.md`'de belirtilir.
- **Mobilde alt sabit çubuk** (yalnızca ≤768px): iki eşit buton — **Ara** (`tel:`) ve
  **Yol Tarifi** (Google Maps araması). `backdrop-filter: blur(16px)` ile cam etkisi,
  **`-webkit-backdrop-filter` öneki şart** (Safari). Sayfanın altına çubuk yüksekliği kadar
  `padding-bottom` ekle ki içerik altında kalmasın.
- Bütün dokunulabilir öğeler en az 48×48px.
- `100svh` kullan, `100vh` kullanma (mobil tarayıcı çubuğu zıplatıyor).

## 6. Çalışma saatleri

Her sitede haftalık saat tablosu ve **o anki durumu JS ile hesaplayan** bir rozet olacak:
"Şu an açık · 23:00'te kapanıyor" veya "Şu an kapalı · yarın 09:00'da açılıyor". Saatler
JS içinde tek bir nesnede tanımlı olsun ki değiştirmesi kolay olsun.

## 7. Erişilebilirlik ve performans

- `:focus-visible` için görünür, markaya uygun bir çerçeve. `outline:none` tek başına yasak.
- Fotoğraf üzerindeki metinlerde kontrast garantisi: koyu degrade katman veya `text-shadow`.
- Semantik HTML: `<header> <nav> <main> <section> <footer>`, tek `<h1>`, başlık sırası atlamaz.
- `<meta name="viewport" content="width=device-width, initial-scale=1">`, `<title>`,
  `<meta name="description">`, Open Graph etiketleri (og:title, og:description, og:image).
- JSON-LD yapısal veri: `LocalBusiness` (restoran için `Restaurant`, kuaför için
  `HairSalon`, kafe için `CafeOrCoffeeShop`), adres ve `openingHours` dahil.
- Favicon: inline SVG data URI, markanın harfi veya işareti.

## 8. İçerik kuralları

- Bütün metin **Türkçe** ve **gerçekçi** olacak. "Lorem ipsum" yasak, "Başlık buraya" yasak.
- İşletmeler kurgusaldır ama gerçek gibi yazılır: gerçek semt adları, makul fiyatlar,
  gerçekçi hizmet isimleri. İçerikte gerçek ürün/marka adı geçebilir (kahve çekirdeği
  markası, boya markası gibi) — sorun değil.
- Telefon `0212 XXX XX XX` biçiminde yer tutucu, adres gerçek semt + uydurma sokak.
- **Yasak klişeler:** "Hakkımızda" başlıklı metin duvarı, "Kaliteli hizmet, uygun fiyat"
  tarzı içi boş cümleler, Bootstrap üçlü kart dizilimi, stok ikon setleri. İkonlar inline
  SVG olarak, 1.5px çizgi kalınlığında elle çizilir.

## 9. Teslim kontrolü

Şerit işini bitirdiğinde bunların hepsi doğru olmalı:

1. `index.html` tek dosya, Google Fonts dışında dış bağımlılık yok.
2. Tarayıcıda açıldığında konsolda hata yok.
3. 390px genişlikte yatay kaydırma yok, hiçbir öğe taşmıyor.
4. Fotoğraflar yokken sayfa boş veya bozuk görünmüyor.
5. `prefers-reduced-motion` açıkken bütün içerik görünür.
6. `gorseller/OKU.md` yazılmış.
7. Toplam dosya boyutu 120 KB'ı geçmiyor.
