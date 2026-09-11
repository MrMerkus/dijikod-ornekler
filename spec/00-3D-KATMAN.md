# 3D katman sözleşmesi — bütün siteler

`00-ORTAK-TEKNIK.md` hâlâ geçerlidir. Bu dosya onun **üstüne** 3D katmanı ekler ve
yalnızca aşağıda açıkça yazan maddelerde onu ezer.

## 0. Karar

Baran'ın kararı: **karma model.** Sayfanın açılış bölümünde (hero) gerçek WebGL 3B
sahne, sayfanın geri kalanında CSS 3B derinlik efektleri. Sinematik açılış + her
telefonda akıcı gövde.

## 1. Ortak teknik sözleşmenin tek istisnası

`00-ORTAK-TEKNIK.md` §1 "Google Fonts dışında hiçbir CDN, hiçbir kütüphane" diyor.
**Bu kural yalnızca Three.js için, yalnızca tek bir satırda esnetilmiştir:**

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

- Sürüm **r128 sabittir.** Bu klasik (UMD) yapıdır, global `THREE` tanımlar ve
  `file://` ile çift tıklanınca çalışır. Daha yeni sürümler yalnızca ES module olarak
  gelir; `file://` altında ES module CORS'a takılır. **Sürümü yükseltme.**
- `type="module"` kullanma, `import` kullanma, importmap kullanma.
- Başka hiçbir CDN, hiçbir ek kütüphane yok. GLTF/OBJ model dosyası yok — bütün 3B
  nesneler Three.js'in kendi geometrileriyle **prosedürel** kurulur.
- Tek dosya kuralı duruyor: bütün CSS ve JS hâlâ `index.html` içinde inline.

## 2. Hero 3B sahne — zorunlu davranışlar

1. **Geri düşüş (fallback) şart.** `window.THREE` tanımsızsa (internet yok, CDN
   engelli, WebGL kapalı) hero **bozulmaz**: mevcut fotoğraf/degrade hero'su yerinde
   kalır ve sayfa hiçbir şey kaybetmemiş gibi görünür. Kontrol sırası:
   `window.THREE` var mı → WebGL bağlamı alınabiliyor mu → ancak ikisi de evetse
   canvas görünür yapılır. Canvas başlangıçta `opacity:0`, sahne hazır olunca
   600ms'de açılır.
2. **Metin canvas'ın içine çizilmez.** Başlık, alt başlık ve butonlar normal HTML
   olarak canvas'ın üstünde durur. SEO ve erişilebilirlik bundan zarar görmeyecek.
3. `prefers-reduced-motion: reduce` → sahne **tek kare** çizilir ve döngü hiç
   başlamaz. Nesne hareketsiz ama görünür kalır.
4. **Görünmeyince durur.** `IntersectionObserver` ile hero ekrandan çıkınca
   `cancelAnimationFrame`, geri girince devam. Sekme arkaplandayken de durur
   (`document.visibilitychange`).
5. **Piksel oranı sınırı:** `renderer.setPixelRatio(Math.min(devicePixelRatio, 1.5))`.
   Genişlik ≤768px ise geometri bölüntü sayıları yarıya iner.
6. Işıklandırma: en fazla üç ışık (ambient + bir yönlü + bir vurgu). Gölge haritası
   (`castShadow`) **kapalı** — pahalı, bu sahnelerde kazancı yok.
7. Etkileşim: fare/dokunma ile nesne yatayda çevrilebilir (basit kendi yazdığın
   pointer sürükleme; `OrbitControls` yok, o ayrı dosya). Bırakınca yavaş kendi
   dönüşüne döner. Dokunmada sayfa kaydırması engellenmez — `touch-action: pan-y`.
8. `WebGLRenderer({ antialias:true, alpha:true, powerPreference:'high-performance' })`,
   arka plan şeffaf, hero'nun CSS degradesi altından görünür.
9. Pencere yeniden boyutlanınca kamera `aspect` ve renderer boyutu güncellenir;
   `resize` olayı 150ms geciktirilir (debounce).
10. Sahne kodu tek bir `initHero3D()` fonksiyonu içinde, dosyanın en altında, kendi
    IIFE'sinde. Küresel değişken sızdırma.

## 3. CSS 3B katmanı — gövde

Hero'nun altında kalan bölümlerde WebGL **yok**. Derinlik şunlarla kurulur:

- **Katmanlı parallax:** `perspective` + `translateZ` tekniğiyle veya
  `animation-timeline: scroll()` ile arka plan katmanı ön plandan yavaş kayar.
  `animation-timeline` desteklenmiyorsa (Firefox varsayılanı) IntersectionObserver
  ile hafif `transform` yedeği; ikisi de yoksa katmanlar **sabit ve düzgün** görünür.
- **Eğilen kartlar:** menü/hizmet/ürün kartları fareyle üstüne gelince kartın
  merkezine göre en fazla **8 derece** `rotateX/rotateY` eğilir, `transform-style:
  preserve-3d`, yumuşak geçiş. Dokunmatik cihazda bu efekt **kapalı**
  (`@media (hover:hover) and (pointer:fine)`).
- **Derinlikli başlık bölümleri:** bölüm geçişlerinde hafif `perspective` + `scale`
  ile içeri girme; süre ve yumuşama `00-ORTAK-TEKNIK.md` §4'teki değerler.
- `prefers-reduced-motion: reduce` altında bu üçü de tamamen kapanır.
- **Yasak duruyor:** kaydırma çalma, yandan uçan öğeler, bekleme ekranı.

## 4. Boyut ve teslim

- `00-ORTAK-TEKNIK.md` §9'daki **120 KB sınırı Three.js'i saymaz** (o dış dosya).
  `index.html`'in kendisi 150 KB'ı geçmeyecek.
- Teslim kontrolüne şunlar eklenir:
  11. İnternet kesikken sayfa açıldığında hero **bozulmuyor**, konsolda yakalanmamış
      hata yok.
  12. `prefers-reduced-motion` açıkken sahne hareketsiz ama görünür.
  13. 390px genişlikte hero canvas taşmıyor, yatay kaydırma yok.
  14. Hero ekrandan çıkınca animasyon döngüsü duruyor (kodda kanıtlanabilir olmalı).

## 5. Dokunulmayacaklar

- `index-2d.html` dosyaları **2B yedektir.** Hiçbir şerit onlara dokunmaz, okumaz,
  taşımaz, silmez.
- Kök dizindeki `index.html` (vitrin sayfası) ana döngünün işidir, şeritler dokunmaz.
- Bir şerit yalnızca kendi klasöründe yazar.
