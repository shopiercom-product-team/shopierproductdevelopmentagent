# Shopier — DESIGN.md (Storev3 Design System)

> **Kaynaklar:**
> 1. Figma › `Shopier-Test-Figma` › **"Storev3 - Design system"** sayfası ve "Storev3 Kopya" sayfasındaki *Kurallar*, *Notification Bar*, *Spacing Note* bölümleri.
> 2. **Canlı storefront incelemesi** — `shopier.com/studiomuse` (Muse Studio), mobil 393 px ve desktop 1440 px. Hesaplanmış CSS değerleri ve sitedeki `--c-*` CSS değişkenleri okundu.
>
> **Kapsam:** Shopier mağaza (storefront) deneyimi — alıcı tarafı: dükkan ana sayfası, arama, ürün detay, sepet, checkout, giriş, hakkında, alt sayfalar (bottom sheet'ler).
> **Kimler için:** Ürün ekibi + yapay zekâ asistanları (Claude vb.). Prototip, mockup veya kod üretirken **bu dosya tek doğruluk kaynağıdır.**
> **Çelişki kuralı:** Figma ile canlı site farklıysa ikisi de belirtildi. Yeni tasarımda **Figma (hedef)** esas alınır; canlıya birebir uyum gereken işlerde **Canlı** değeri kullanılır.
>
> **Font geçişi:** Design system **Urbanist**'e taşındı. Canlı sitede geçiş tamamlanana kadar Gilroy görünür. **Tüm yeni tasarım ve prototiplerde Urbanist kullanılır.** Boyut, satır yüksekliği, ağırlık ve boşluk değerleri değişmedi (Bölüm 3).

---

## 0. Yapay zekâ için çalışma talimatı (önce bunu oku)

1. **Sadece burada tanımlı token'ları kullan.** Listede olmayan renk, font boyutu, radius veya boşluk uydurma. Gerekirse en yakın token'ı seç ve belirt.
2. **Önce mevcut component'i ara** (Bölüm 6 ve 7). Aynı işi yapan component varsa yenisini icat etme.
3. **Mobil önce.** Çerçeve 393 × 852, içerik 349 px, yan boşluk 22 px.
4. **Tek birincil aksiyon.** Bir alanda yalnızca bir dolu mor (`brand-500`) buton olur.
5. **Font her zaman Urbanist.** Canlı siteden ölçüm alırken Gilroy görsen bile çıktıda Urbanist kullan.
6. **Metinler Türkçe**, Shopier ses tonunda (Bölüm 10). Fiyat formatı Bölüm 10.2'de.
7. Seçim, onay, form ve bilgi gösterimi için **bottom sheet** kalıplarını kullan (Bölüm 7). Mobilde modal/dialog yerine bottom sheet tercih edilir.
8. Emin olmadığın konuda Bölüm 13 "Açık noktalar"a bak ve varsayımını belirt.
9. Teslim etmeden önce Bölüm 12 kontrol listesini uygula.

---

## 1. Tasarım ilkeleri

| İlke | Ne anlama geliyor |
|---|---|
| **Ürün sahnede** | Arayüz sakin ve nötr; renk ve vurgu ürün fotoğrafına ait. Bol beyaz alan, ince gri çizgiler. |
| **Tek net aksiyon** | Mor yalnızca birincil aksiyon, seçili durum, link ve marka için. |
| **Yumuşak ve dost canlısı** | Pill butonlar, yuvarlatılmış kartlar, düz yüzeyler. |
| **Okunur fiyat** | Fiyat koyu ve belirgin; indirim kırmızı ile ayrışır; para birimi ve kuruş daha küçük yazılır. |
| **Tutarlı ritim** | 22 px kenar, 349 px kolon, tekrarlanan dikey boşluklar. |
| **Mobilde alttan açılır** | Seçim, filtre, onay ve bilgi ekranları bottom sheet olarak gelir. |

---

## 2. Renkler

### 2.1 Token tablosu

| Token | HEX | Canlı CSS değişkeni | Kullanım |
|---|---|---|---|
| `brand-500` | `#6700FF` | `--c-primary`, `--c-btn-active` | Birincil buton, seçili tick, link, logo |
| `ink-900` | `#0B0F34` | `--c-black` | Ana metin, başlık, ikon, seçili tab, input değeri |
| `ink-800` | `#292D33` | — | Koyu ikon zemini (sosyal medya) |
| `ink-700` | `#2F3352` | `--c-black-2`, `--c-price`, `--c-badge`, `--c-chip` | Ürün adı, fiyat, badge/chip metni, **seçili chip zemini** |
| `ink-600` | `#414561` | — | Ara ton (seyrek) |
| `ink-500` | `#545670` | `--c-product-info-desc`, `--c-follow-store-link`, `--c-search-icon` | Açıklama metni, dükkan sloganı, footer linkleri, arama ikonu |
| `ink-400` | `#787A8E` | `--c-quantity-active`, `--c-checkout-product-count`, `--c-shop-app-text` | Üçüncül metin, varyant, adet sayısı, aktif +/- çerçevesi, copyright |
| `ink-300` | `#9C9EAC` | `--c-secondary`, `--c-btn-passive`, `--c-price-discount`, `--c-input-label-secondary` | Placeholder, input etiketi, pasif buton, seçili olmayan tab, **eski fiyat** |
| `ink-250` | `#9FA0A5` | — | Nötr gri |
| `line-300` | `#D0D0D7` | `--c-input-border`, `--c-select-border`, `--c-radio-border`, `--c-border-1`, `--c-favorite` | Input/box/radio kenarlığı, progress track |
| `line-250` | `#D3D3D9` | — | Alternatif kenarlık |
| `line-200` | `#E2E2E5` | `--c-border-2`, `--c-product-image-border`, `--c-product-info-tab-border`, `--c-sheet-footer-border` | Ayraç, kart/görsel kenarı, tab alt çizgisi, sticky bar üst çizgisi |
| `line-150` | `#E5E5E8` | `--c-quantity-passive`, `--c-select-disabled` | Pasif +/- çizgisi, **disabled select zemini** |
| `surface-200` | `#F1F1F1` | `--c-select-hover`, `--c-input-loading`, `--c-swiper-thumbs-navigation-bg` | Select hover, input yükleniyor, galeri ok zemini |
| `surface-150` | `#EEEEEE` | `--c-badge-bg-hover` | Badge hover |
| `surface-100` | `#F7F7F7` | `--c-badge-bg`, `--c-chip-bg`, `--c-quantity-bg`, `--c-follow-store-bg`, `--c-shop-app-bg` | Notification bar, badge, chip, +/- zemini, arama kutusu, dükkan kartı |
| `surface-0` | `#FFFFFF` | — | Sayfa, kart, sheet, input |
| `overlay` | `#0B0F34` @ %50 | — | Bottom sheet / modal arkası |
| `neutral-tint` | `#9FA0A5` @ %9 | — | Sheet içi arama inputu zemini |
| `sale-500` | `#EE3124` | `--c-red`, `--c-badge-discount` | İndirim oranı/metni **ve hata** (input hata kenarı, hata metni) |
| `sale-50` | `#EE3124` @ %10 | — | İndirim badge zemini |
| `shop-red` | `#F20E45` | — | **"shop by shopier" (Shop uygulaması) logosu.** Arayüzde hata rengi olarak kullanılmaz. |
| `red-logo` | `#F9022F` | `--c-red-logo` | Kırmızı logo varyantı (canlı CSS) |
| `sheet-handle` | `#D9D9D9` | `--c-sheet-swiper-btn-bg` | Bottom sheet tutamacı |
| `dot-active` | `#000000` / %30 | — | Görsel slider dot'ları (tek siyah kullanımı) |

### 2.2 Renk kuralları

- **Metin hiyerarşisi:** `ink-900` (başlık/değer) → `ink-700` (ürün/fiyat) → `ink-500` (açıklama) → `ink-400` (yardımcı) → `ink-300` (placeholder/pasif). Metinde `#000000` kullanılmaz.
- **Mor tasarrufu:** Dolu `brand-500` yalnızca birincil butonda. İkincil aksiyon outline olur.
- **Kırmızı (`sale-500`) yalnızca indirim ve hata içindir.**
- **Seçili chip** koyu (`ink-700` zemin, beyaz metin); seçili radio/checkbox ise mor tick'tir.

---

## 3. Tipografi

**Font:** `Urbanist` (tek aile, Google Fonts'ta ücretsiz, variable font). Ağırlıklar: Light 300 / Light Italic, Regular 400, Medium 500, SemiBold 600, Bold 700.
> CSS: `font-family: "Urbanist", -apple-system, "Segoe UI", sans-serif;`
> Yükleme: `https://fonts.googleapis.com/css2?family=Urbanist:ital,wght@0,300..700;1,300&display=swap`
> Figma'da ağırlık adları Urbanist'in yazımıyla seçilir: "SemiBold" (Gilroy'daki "Semibold" değil).

**Geçiş notu:** Canlı site şu an Gilroy kullanıyor (400–700). Aşağıdaki tüm boyut, satır yüksekliği ve ağırlık değerleri iki fontta da aynıdır; yalnızca aile değişir. Urbanist, Gilroy'a göre biraz daha dar ve daha düşük x-yüksekliğine sahip olabilir. Bu yüzden geçişte kırpılan/taşan metinler (ürün adı, buton, fiyat) gözle kontrol edilmeli, ancak **değerler değiştirilmemeli.**

### 3.1 Tip skalası

| Token | Boyut / satır | Ağırlık | Kullanım |
|---|---|---|---|
| `display-32` | 32 / 40 | Bold | **Sayfa başlığı**: "Alışveriş sepetiniz", "Ara" |
| `display-28` | 28 / 35 | Bold | Dükkan adı (desktop) |
| `title-24` | 24 / 30 | SemiBold | Desktop bölüm başlığı ("Bu ürünleri beğenebilirsiniz") |
| `quote-24` | 24 / 29 | Light (Italic) | Hakkında sayfası alıntısı |
| `title-23` | 23 / 28 | Bold | **Dükkan adı (mobil)**, hakkında banner başlığı |
| `title-22` | 22 / 28 | Bold | Ürün adı (desktop ürün detay) |
| `title-20` | 20 / 25 | SemiBold (Figma: Bold) | **Bottom sheet başlığı** |
| `price-20` | 20 | Medium | Ürün detay fiyatı (desktop) |
| `name-18` | 18 / 24 | Bold | **Ürün adı (mobil ürün detay)** |
| `price-18` | 18 | Medium | **Ürün detay fiyatı (mobil)**; eski fiyat 18 Regular |
| `total-18` | 18 / 22 | SemiBold | "Genel toplam", sepet toplamı |
| `button-18` | 18 / 22 | SemiBold | **Tüm butonlar** |
| `body-16-b` | 16 / 20 | Bold | Checkout bölüm başlığı ("İletişim", "Teslimat", "Fatura") |
| `body-16-sb` | 16 / 20–22 | SemiBold | Kategori tab'ı, seçili ürün tab'ı, kart başlığı, "Tümünü temizle" |
| `body-16` | 16 / 24 | Medium | **Input değeri/placeholder, sheet metni** (notification 16/20) |
| `body-15` | 15 / 20 | Bold | **Liste kartı fiyatı** |
| `body-15-m` | 15 / 18 | Medium | İletişim satırı, fiyat input'u |
| `body-14-b` | 14 / 17 | Bold | Dükkan menüsü ("Hakkında", "İletişim") |
| `body-14-sb` | 14 / 17–20 | SemiBold | Footer başlığı, text-link buton, foto üstü indirim |
| `body-14` | 14 / 17–20 | Medium | Ürün adı (kart 14/19), açıklama (14/20), chip, input etiketi (14/21), badge (14/20) |
| `body-14-r` | 14 / 17–20 | Regular | Uzun içerik (Hakkında), onboarding listesi |
| `caption-13` | 13 | Medium | "Kaydol / Giriş Yap" küçük linki |
| `caption-12` | 12 / 14–18 | Medium | Liste badge'i ("%15 İndirim", "Son ürün"), küçük checkbox metni, "2 adet" |
| `legal-12` | 12 / 16 | Regular | Yasal onay metni (belge adı Bold) |
| `price-currency` | fiyat − 2…3 px | aynı ağırlık | "TL" ve ",00" fiyattan küçük yazılır (Bölüm 10.2) |

### 3.2 Kurallar

- Varsayılan gövde ağırlığı **Medium**'dur. Uzun okuma metni (Hakkında) Regular.
- Butonlar her zaman `button-18` SemiBold.
- Harf aralığı 0. ALL CAPS yalnızca kupon kodu gibi verilerde.
- **Taşan metin:** "…" yerine **28 px sağdan gradient fade** (`linear-gradient(90deg, rgba(255,255,255,0) 0, #fff 28px)`). Ürün adı kartta max 2 satır. Uzun açıklama 5 satırdan sonra fade + **"Daha fazla"** (14 Medium `ink-500`).

---

## 4. Boşluk, grid ve yerleşim

### 4.1 Spacing skalası (px)

`5 · 8 · 10 · 12 · 15 · 16 · 17 · 18 · 20 · 22 · 25 · 30 · 39 · 40 · 50 · 64 · 70 · 150`

| Token | Değer | Tipik kullanım |
|---|---|---|
| `space-5` | 5 | **Sheet içi liste seçenekleri arası**, sheet'te iki buton arası |
| `space-8` | 8 | İkon–metin arası |
| `space-10` | 10 | Chip yatay aralığı, logo/banner yokken ek iç boşluk |
| `space-12` | 12 | Chip satır aralığı, sayfa içi iki buton arası, ikon–metin (iletişim satırı) |
| `space-15` | 15 | Input/chip iç yatay padding, notification üst padding |
| `space-19` | 19 | **Mobil ürün grid kolon arası**, input sol padding |
| `space-20` | 20 | Main layout ↔ barlar (sabit), notification yatay padding |
| `space-22` | 22 | **Mobil kenar boşluğu** (`--p-container`) |
| `space-30` | 30 | **Mobil grid satır arası**, desktop grid kolon arası, büyük görsel ↔ sağ kolon |
| `space-39` | 39 | Desktop grid satır arası |
| `space-40` | 40 | Bottom sheet dikey ritmi |
| `space-64` | 64 | **Desktop kenar boşluğu** |

### 4.2 Breakpoint ve çerçeveler

| Platform | Çerçeve | İçerik | Kenar | Ürün grid'i |
|---|---|---|---|---|
| Mobil | 393 × 852 | 349 px | 22 px | 2 × 165 px, kolon 19, satır 30 |
| Desktop | 1440 / 1920 | max 1634 px | 64 px | 6 kolon (~194 px), kolon 30, satır 39 |

Breakpoint'ler: `578 · 768 · 1024 (lg — mobil/desktop eşiği) · 1200 · 1440 · 1728`.

### 4.3 Sabit yerleşim kuralları

- **Header:** 55 px (`--header-height`), içinde 50 px nav (`--nav-height`), beyaz, sabit (fixed).
  - Dükkan/ürün sayfası: logo + arama, sipariş takibi (kamyon), hesap ve sepet ikonları (sayı rozetli).
  - Sepet sayfası: logo + arama + hesap (sepet ve kamyon yok).
  - Alt sayfalar (Hakkında): yalnızca logo.
  - Checkout: header yok, en üstte Teslimat/Ödeme adım göstergesi.
- **Sticky aksiyon barı:** beyaz, üstte 1 px `line-200`, ortada 349 × 50 buton. Sepette 80 px yükseklik; ürün detayda 70.
- **Spacing Note:** Main layout ile üstündeki barlar (progress, notification, ücretsiz kargo) arası **20 px**. Logo ve banner yoksa component içine **+10 px**.
- Desktop ürün detayı: solda 458 × 458 görsel + 60 × 60 thumbnail şeridi, **30 px** boşluk, sağda 349 px bilgi kolonu.

---

## 5. Radius, kenarlık, gölge, görsel

### 5.1 Radius

| Token | Değer | Kullanım |
|---|---|---|
| `radius-5` | 5 | Liste badge'i, sepet/özet ürün görseli (80 px), desktop thumbnail |
| `radius-6` | 6 | Foto üstü badge |
| `radius-8` | 8 | **Küçük outline buton ("Takip et")**, geri linki |
| `radius-9` | 9 | 138 px kart görseli, onboarding bilgi kutusu |
| `radius-10` | 10 | **Mobil ürün kartı görseli**, toast içi buton |
| `radius-11` | 11 | **Input / select / box**, filtre grubu kutusu, özet kutusu |
| `radius-14` | 14 | **Desktop ürün kartı görseli** |
| `radius-16` | 16 | Ürün detay görseli, notification bar, toast, dükkan kartı, hakkında banner, arama inputu (16 köşe) |
| `radius-18` | 18–18.25 | Filtre chip'i (36 px), sheet arama inputu (37 px) |
| `radius-20` | 20 | Bottom sheet üst köşeleri, desktop modal, process tab, kategori chip'i (34 px), tutamaç |
| `radius-pill` | 27.5 | Butonlar, sheet içi seçenek satırları, checkbox satırı (50 px) |
| `radius-full` | 9999 | Avatar/logo, +/- daire butonlar, dot'lar, loader |

### 5.2 Kenarlık

- Her zaman **1 px**. Input/select/radio: `line-300`. Görsel/ayraç/kart: `line-200`.
- **Hata:** input/select kenarı `sale-500` (#EE3124).
- Focus'ta kenar rengi değişmez (canlıda görünür bir focus stili yok; bkz. Bölüm 13).
- Aktif thumbnail: 1 px `ink-700`. Dükkan logosu (dükkan kartında): 1 px `ink-900`.

### 5.3 Gölge

- Varsayılan: **gölge yok.**
- **İstisna — yüzen katmanlar:** Arama autocomplete dropdown'u ve "Sepete eklendi" toast'ı `box-shadow: 0 0 10px 0 #E2E2E5` kullanır. Başka yerde gölge kullanma.

### 5.4 Görsel boyutları

| Boyut | Nerede |
|---|---|
| 80 × 80 | Mobil dükkan logosu (avatar), sepet/özet ürün görseli |
| 116 × 116 | Desktop dükkan logosu |
| 50 × 50 | Dükkan kartı logosu |
| 32 × 32 | Hakkında banner'ındaki logo |
| 138 × 138 | Mobil "Bu ürünleri beğenebilirsiniz" kartı |
| 165 × 165 | Mobil ürün listesi |
| ~194 / 226 kare | Desktop liste / benzer ürünler |
| 349 × 349 | Mobil ürün detay görseli |
| 458 × 458 | Desktop ürün detay görseli |
| 60 × 60 | Desktop thumbnail |
| 393 × 100 / 1440 × 200 | **Dükkan banner'ı** (mobil / desktop) |
| 349 × 262 | Hakkında sayfası banner kartı |
| 200 × 200 | Hakkında içerik görseli (radius 16) |
| 349 × 196, 800 × 450 | 16:9 banner |

- Görseller `object-fit: cover`, kenar 1 px `line-200`.
- Slider dot'u 8 px: aktif `#000`, pasif %30. 1–5 görselde dot, 5'ten fazlasında thumbnail şeridi.

---

## 6. Temel component'ler

### 6.1 Butonlar

| Varyant | Görünüm | Kullanım |
|---|---|---|
| `primary` | `brand-500` dolgu, beyaz metin | Ana aksiyon: "Sepete ekle", "Siparişi tamamla", "Uygula", "Kapat" |
| `primary-disabled` | `ink-300` dolgu, beyaz metin | Form/filtre seçilmeden ("İlerle", "Uygula") |
| `primary-outline` | Beyaz, 1 px `brand-500`, mor metin | İkincil: "Hemen al", "Vazgeç", "Paylaş", "Sepetten kaldır" |
| `outline-disabled` | Beyaz, 1 px `ink-300`, gri metin | Pasif ikincil |
| `follow` (küçük outline) | 80 × 30 (desktop 102), radius 8, 1 px `ink-900`, 14 Medium `ink-900` | "Takip et" |
| `text-link` | Zeminsiz, 14 SemiBold `brand-500` | "E-postayla ilerle" |
| `text-clear` | Zeminsiz, 16 SemiBold; pasifken `ink-300`, aktifken `brand-500` | "Tümünü temizle" |
| `back-link` | Sol ok (24) + 14 Medium `ink-900` | "Ana sayfa", "Alışverişe devam et" |
| `icon-circle` | 35–40 px daire, `surface-100` zemin veya 1 px `ink-400` çerçeve | +/-, çöp, "…" |

- **Ölçü:** 349 × 50, radius 27.5, `button-18` SemiBold.
- **Hover (desktop):** Birincil butonda fareyi takip eden radial gradient (`#9D5CFF → #6200F5`). Prototipte basit karşılığı: hover'da `#7A1FFF`.
- **Loading:** Buton yerinde kalır, metin yerine spinner gelir (padding 6 px).
- **Aralık:** Sayfa içinde iki buton arası **12 px**. Bottom sheet içinde **5 px**. Sheet'te "Vazgeç" bir gruptan sonra geliyorsa ~20 px.
- **Sıra:** Birincil üstte. Ürün detayda "Sepete ekle" (dolu) üstte, "Hemen al" (outline) altta.
- **Yasak:** Kare köşe, gölge, aynı alanda iki dolu mor buton.

### 6.2 Input'lar

Ortak: 349 × 55, beyaz, 1 px `line-300`, radius 11, sol padding 19, değer `body-16` `ink-900`, placeholder `ink-300`.

| Varyant | Detay |
|---|---|
| Text | Placeholder ("E-posta", "Adres", "Sipariş numarası") |
| Floating label | Üstte etiket 14/21 `ink-300`, altında değer 16/24 ("Cep telefonu", "Ülke") |
| Telefon | `+90` prefix (16 Medium `ink-900`) + `5xx` placeholder; sağda ülke seçici ("Türkiye" + 24 px aşağı ok) |
| Select | Sağda 24 px `arrow-down`; açılınca **aranabilir seçim sheet'i** (7.6) açılır |
| Select disabled | Zemin `line-150` (#E5E5E8), metin `ink-300` (ör. İl seçilmeden "İlçe") |
| Half (yan yana) | 2 × 166 px, arada 17 px (Ad/Soyad, İl/İlçe, Ay/Yıl) |
| Fiyat aralığı | 2 × ~164 px; placeholder "En düşük"/"En yüksek" 15 Medium, sağda "TL" |
| Adet (stepper) | "Adet" + 35 px `-`/`+` daireler (`surface-100`); pasif ikon `line-150` |
| Checkbox satırı | 349 × 50 pill (radius 27.5), metin 12 Medium, sağda 24 px mor tick ("Fatura ve teslimat adreslerim aynı.") |
| Radio satırı | 349 × 50 pill, metin 16 Medium, sağda boş daire → seçilince mor tick |
| **Hata** | Kenar `sale-500`; altında yardımcı metin 14 SemiBold `sale-500` |
| Yükleniyor | Zemin `surface-200` |

### 6.3 Chip'ler

| Varyant | Stil | Kullanım |
|---|---|---|
| `filter-chip` | 36 h, padding 0 15, radius 18.24, `surface-100` zemin, 14 Medium `ink-700` | Filtre seçenekleri |
| `filter-chip` seçili | Zemin `ink-700`, metin beyaz | |
| `filter-chip` disabled | Metin üstü çizili | Stokta olmayan seçenek |
| `category-chip` | 34 h, radius 20, 1 px `ink-900`, 14 Medium `ink-900` | Arama sayfası kategori filtresi |
| `category-chip` seçili | Zemin `ink-700`, metin beyaz | "Tümü" |

Chip aralığı: yatay 10, dikey 12.

### 6.4 Badge'ler

| Badge | Stil |
|---|---|
| Foto üstü (`OnPhoto_*`: Son ürün, Yeni, Tükendi, Dijital ürün) | 80 × 24, zemin `surface-100` (detayda %72 opak), radius 6, 14 Medium `ink-700` |
| Foto üstü indirim | Aynı zemin, "%9" 14 SemiBold `sale-500` |
| Liste indirim | 20 h, zemin `sale-50`, radius 5, 12 Medium `sale-500` ("%15 İndirim") |
| Liste bilgi | 20 h, zemin `surface-100`, 1 px `#F4F4F4`, radius 5, 12 Medium `ink-700` ("Son ürün") |
| Foto altı | 24 h, `surface-100`, radius 6 ("Ücretsiz kargo", "3 iş günü içinde kargoda") |
| Sepet sayacı | Sepet ikonunun içinde 13 Bold `ink-900` |

### 6.5 Tab'lar

| Tab | Stil |
|---|---|
| **Kategori tab'ı** (dükkan ana sayfası) | Yatay kaydırmalı, 16 SemiBold; seçili `ink-900` + 2 px `ink-900` alt çizgi, diğerleri `ink-300`; tam genişlik 1 px `line-200` taban |
| **Ürün bilgi tab'ı** ("Ürün açıklaması" / "Teslimat bilgisi") | 349 px, 16; seçili SemiBold `ink-900` + 2 px alt çizgi, diğeri Medium `ink-300`; taban 1 px `line-200` |
| Figma `tab_narrow` / `tab_large` | 349 / 393 px eşit bölünmüş varyantlar |

### 6.6 Notification bar & toast

- **Notification bar:** 349 px, `surface-100` (veya %85), radius 16 (kapatılabilir: 20), padding 15/20, metin 16/20 Medium `ink-900`. Varyantlar: düz, ikonlu, kapatılabilir, aksiyon butonlu (beyaz, radius 10, 34 h).
- **Toast ("Sepete eklendi"):** Header'ın altında **sabit (fixed)** yüzen bar. `surface-100`, radius 16, gölge `0 0 10px #E2E2E5`. Solda tick ikonu + "Sepete eklendi" (16 Medium), sağda beyaz küçük buton "Siparişi tamamla" (radius 10). Birkaç saniye sonra kendiliğinden kapanır.

### 6.7 Ürün kartları

| Kart | Ölçü | Detay |
|---|---|---|
| Liste kartı (mobil) | 165 × ~250 | Görsel 165², radius 10, 1 px `line-200`. Altında 9 px boşlukla badge (opsiyonel) → ad 14/19 Medium `ink-700` (padding-left 4) → fiyat 15 Bold + "TL" 12 Bold; eski fiyat 15 Regular `ink-300` üstü çizili |
| Liste kartı (desktop) | ~194 / 226 | Görsel radius **14**, ad 14/18 |
| Benzer ürün (mobil) | 138 px | Görsel radius 10; yatay kaydırma, aralık 19 |
| Ürün detay görseli | 349² (desktop 458²) | Radius 16, foto üstü badge sağ üstte, dot'lar altta |
| Sepet satırı | 349 | 80² görsel (radius 5) + ad 14/17 Medium + sağda fiyat 14 Bold (kuruş/TL 12) ve eski fiyat. Altında 35 px `-`, adet, `+` ve sağda `…` (1 px `ink-400` daireler). Satır altı 1 px `line-200` |
| Özet satırı (checkout) | 311 | 80² görsel + ad + fiyat + "2 adet" 12 Medium |

### 6.8 Header, arama, footer

- **Header:** Bölüm 4.3'e bak. Logo `shopierlogo_113px` (mobilde ~92 × 27).
- **Arama (desktop):** Header'da 349 × 36 `surface-100`, radius 16.
- **Footer:** Üstte "Sipariş takibi" satırı (78 h, alt çizgi `line-200`). Altında dükkan adı (14 SemiBold), slogan ve e-posta (14 Medium `ink-500`), "Koşullar" başlığı ve linkler (Alışveriş Güvenliği, Ön Bilgilendirme Formu, Mesafeli Satış Sözleşmesi, Kişisel Verilerin Korunması — 14 Medium `ink-500`, satır aralığı 25).
- **Checkout/sepet footer'ı:** "Gizlilik ve Koşullar" (14 SemiBold) + "Copyright © {yıl} Shopier" + "Tüm hakları saklıdır." (14 Medium `ink-400`), ortalı, üstte 1 px `line-200`.

### 6.9 Progress bar, adım göstergesi

- **Progress bar:** Kart `surface-100` (desktop %85), radius 16. Track `line-300`, dolgu `ink-900`, radius 2. Mesaj 14/20 Medium ortalı.
- **Checkout adım göstergesi:** 260 × 72, `surface-100` %85, radius 20. İki adım ("Teslimat", "Ödeme"): ikon + 14 Medium; aktif `ink-900`, pasif `ink-300`. Aralarında ince bağlantı çizgisi.

### 6.10 Loader

- 53 px dönen halka içinde iki adet 9 px `brand-500` nokta (`animation: spin`). Liste sonunda sonsuz kaydırma yüklemesinde kullanılır.

---

## 7. Desen ve ekran component'leri (canlı siteden)

### 7.1 Dükkan üst alanı (`store-information`)

- **Banner'lı (varsayılan):** Banner 393 × 100 (desktop 1440 × 200). Banner'ın alt kenarına taşan 80 px yuvarlak logo (desktop 116), sağda "Takip et" (follow butonu).
- Altında: dükkan adı `title-23` Bold `ink-900` (desktop 28/35) → slogan 14/17 Medium `ink-500` (desktop 16) → menü: **"Hakkında" • "İletişim" • ⓘ** (14 Bold `ink-900`, araya `•`). ⓘ "Dükkan bildirisi" sheet'ini açar.
- **Banner'sız varyant:** Logo, ad ve "Takip et" ortalı dizilir.
- Altında kategori tab'ı (6.5), sonra sonuç satırı: "89 ürün" (14 Medium `ink-300`) solda, sağda 24 px **sırala** ve **filtrele** ikonları (aktif filtre varsa ikonda mor nokta).

### 7.2 Sırala sheet'i

- Başlık "Sırala" `title-20`. Seçenekler radio satırı (349 × 50 pill, 1 px `line-300`, aralık 5): "Fiyat, artan", "Fiyat, azalan", "Listeleme tarihi, artan", "Listeleme tarihi, azalan".
- Sabit footer: solda "Tümünü temizle" (`text-clear`) → altında "Uygula" (seçim yokken `primary-disabled`).

### 7.3 Filtrele sheet'i

- Başlık "Filtrele". Her filtre grubu ayrı **kutu**: 345 genişlik, 1 px `line-300`, radius 11, padding 20/19. Kutunun içinde başlık (16 Medium `ink-900`, ör. "Kategori", "Renk", "Ölçü", "Avantajlı ürünler", "Stok") ve altında `filter-chip` listesi. Uzun gruplar genişletilebilir.
- "Fiyat": başlık + iki fiyat aralığı input'u.
- Footer: Sırala ile aynı ("Tümünü temizle" + "Uygula").

### 7.4 Arama ekranı

- Tam ekran açılır (sağdan). Başlık "Ara" `display-32`.
- Satır: geri oku + arama inputu (36 h, `surface-100`, radius 16, sağda ⓧ temizle) + sırala/filtrele ikonları.
- Altında yatay kaydırmalı `category-chip` satırı ("Tümü" seçili).
- **Autocomplete:** Input'un altına yapışık dropdown (`surface-100`, alt köşeler 16, gölge `0 0 10px #E2E2E5`). Satırlar 37 h, 14 Medium. Yazılan kısım `ink-300`, tamamlanan kısım `ink-700`. Ürün önerilerinde sağda "Ürün" etiketi (14 Bold).
- Sonuç: "21 ürün ⓧ" + standart 2 kolon grid.
- **Boş durum:** "Bu arama için sonuç bulunmuyor." (14 Medium `ink-300`, sola hizalı).

### 7.5 Bottom sheet sistemi

**Ortak yapı:** Genişlik 393, beyaz, üst köşeler radius 20, max yükseklik ~%75 ekran (639 px). Tutamaç 50 × 5 `sheet-handle`, radius 20, üstten 9 px. Başlık `title-20` ortalı. İçerik 22 px kenar. Sabit footer'da buton(lar). Arka plan `overlay`. Taşan içerik kayar, altta beyaz fade.

| Sheet tipi | İçerik |
|---|---|
| **Durum / bilgi** (Figma 5 tip) | İkon (48) ± başlık ± metin (16 Medium) + 1 veya 2 buton. Dikey ritim: tutamaç→ikon 40, ikon→metin 47 (başlıkla 37), metin→buton 40–45, buton→alt 45 |
| **Onay** | Başlık + metin + "Action" (dolu) / "Vazgeç" (outline) |
| **Seçim listesi** (Sırala) | Radio satırları + "Tümünü temizle" + "Uygula" |
| **Filtre** | Gruplu chip kutuları + footer |
| **Aranabilir seçim** (İl/İlçe/Ülke) | 7.6 |
| **Aksiyon listesi** (sepet "…") | Outline butonlar alt alta, aralık 5: "Paylaş", "Sepetten kaldır"; en altta ayrık "Vazgeç" |
| **Form** (Sipariş takibi) | Başlık + sola hizalı açıklama (16/19 Medium) + input + "İlerle" (pasif→aktif) + "Vazgeç" |
| **İletişim bilgileri** | İletişim satırları (7.7) + "Kapat" |
| **Dükkan bildirisi** | Başlık + ortalı metin (16/20 Medium, üst/alt fade mask) + "Kapat" |

> Mobil dışı (≥1024) karşılığı ortalanmış **modal**: ~337 px genişlik, beyaz, radius 20, aynı içerik.

### 7.6 Aranabilir seçim sheet'i

- Başlık (ör. "İl"). Altında arama inputu: 349 × 37, zemin `neutral-tint` (#9FA0A5 %9), radius 18.
- Liste: radio satırları (50 h pill, aralık 5), seçili satırda mor tick.

### 7.7 İletişim satırı

- 349 × 55 box (radius 11, 1 px `line-300`). Solda 24 px ikon (telefon / zarf), 12 px boşluk, değer (15 Medium `ink-900`, fade ile kırpılır). Sağda "Kopyala" (15 Medium `brand-500`) + kopyala ikonu (aralık 7.5).

### 7.8 Ürün detay sayfası

Mobil sıra:
1. Görsel slider (349², radius 16) + foto üstü badge + dot'lar.
2. Ad (`name-18` Bold `ink-900`) + sağda favori (kalp) ve paylaş ikonları (24). Favori giriş gerektirir; misafir kullanıcı giriş sayfasına yönlendirilir.
3. Fiyat (`price-18` Medium `ink-700` + "TL" 16) + eski fiyat (18 Regular `ink-300`, üstü çizili).
4. (Varsa) varyant select'leri → **Adet** stepper.
5. "Sepete ekle" (dolu) + 12 px + "Hemen al" (outline).
6. Ürün bilgi tab'ı → açıklama (14/20 Medium `ink-500`, 5 satır + "Daha fazla"). "Teslimat bilgisi" tab'ında kargo metni.
7. **Dükkan kartı** (7.9).
8. "Bu ürünleri beğenebilirsiniz" (16 SemiBold; desktop 24) + yatay kaydırmalı 138 px kartlar.

Desktop: solda 458² görsel + thumbnail şeridi, sağda 349 px kolon (ad 22/28, fiyat 20).

### 7.9 Dükkan kartı (`follow-store`)

- 349 × 88, `surface-100`, radius 16, iç padding ~11. Solda 50 px logo (1 px `ink-900` çerçeve), yanında dükkan adı (16/22 SemiBold `ink-900`) ve "Tüm ürünler" linki (14 Medium `ink-500`). Sağda "Takip et" butonu. Ürün detay ve checkout sonunda kullanılır.

### 7.10 Sepet sayfası

- "‹ Alışverişe devam et" back-link → başlık "Alışveriş sepetiniz" (`display-32`) → toplam "8.600,00 TL" (18 SemiBold) + "( 2 ürün )" (16 SemiBold `ink-300`).
- Sepet satırları (6.7).
- Özet: "Ara toplam", "Kargo", indirim satırları ("Etiket indirimi", "-800,00 TL") 16 Medium; **"Genel toplam"** 18 SemiBold. Değerler sağa hizalı.
- Sticky "Siparişi tamamla" barı (80 h).

### 7.11 Checkout (Teslimat adımı)

- Üstte adım göstergesi (6.9).
- Bölümler `body-16-b` başlıkla: **İletişim** (sağda küçük "Kaydol / Giriş Yap" linki) → E-posta, Cep telefonu. **Teslimat** → Ad/Soyad (half), Ülke, İl/İlçe (half; İlçe il seçilene kadar disabled), Adres. **Fatura** → checkbox satırı "Fatura ve teslimat adreslerim aynı.", fatura tipi select'i ("Bireysel fatura"), "TC kimlik no (Zorunlu değil)". **Not** → "Satıcıya notunuz (Tercihen)".
- Yasal metin (`legal-12`, belge adı Bold) sticky butonun üstünde.
- Sticky "Ödemeye geç".
- **Özet** kutusu: 1 px `line-300`, radius 11. Başlıkta dükkan adı + "2 ürün" (`ink-400`) + "Ürünleri gizle" linki; ürün satırları; toplamlar. Altında dükkan kartı.
- Bölümler arası ~40 px, input'lar arası 17 px.

### 7.12 Giriş / onboarding (`shop by shopier`)

- Üstte geri oku, ortada **"shop by shopier"** logosu ("shop" `shop-red`, "by shopier" mor).
- Başlık: "**Giriş yapın** veya **Hesap oluşturun**" (18, Bold/Regular karışık, `ink-500`). Açıklama 18 Regular ortalı.
- Telefon input'u (6.2) → "İlerle" (pasif → aktif) → "E-postayla ilerle" (`text-link`).
- Avantaj kutusu: `surface-100`, radius 9; satırlar 24 px ikon + 14 Regular `ink-400` ("Adres ve ödeme yöntemi kaydetme", "Bağımsız satıcıları ve ürünlerini takip etme", "Kolay kargo takibi").

### 7.13 Hakkında sayfası

- Back-link "‹ Ana sayfa".
- Banner kartı 349 × 262 (radius 16, 1 px `line-200`). Sol altta 32 px logo + dükkan adı (23 Bold beyaz).
- Büyük tırnak işareti (“) ortalı `ink-900`, ardından gövde metni 14/17 Regular `ink-900`, paragraflar arası ~17.
- İmza satırı 14 SemiBold ("— Selin & İpek – Muse Studio Kurucuları").
- Ortalanmış 200² görsel (radius 16), alıntı `quote-24` Light ortalı.
- Süreç listesi: madde başlığı 14 SemiBold + ":" ve açıklama 14 Regular, 21 px girinti.

---

## 8. İkonografi

- **Stil:** Outline, yuvarlak uçlu, çizgi **1.5 px** (büyük daire ikonlarda 1). Seçili durumda dolu varyant.
- **Renk:** varsayılan `ink-900`; arama ikonu (input içinde) `ink-500`; pasif `ink-300`; seçili `brand-500`.

| Boyut | Kullanım |
|---|---|
| 16 | Satır içi bilgi, küçük ok |
| 18 | Liste oku |
| **24** | **Varsayılan**: header, input, sırala/filtre, favori, paylaş, iletişim |
| 35–40 | Dairesel aksiyon (+/-, çöp, "…") |
| 48 | Sheet / hata sayfası durum ikonu |
| 60 | Video oynat |

**Set:** search, truck (sipariş takibi), person, shopping-bag (sayılı), info-circle, sort (üç çizgi), filter (slider), close-circle (ⓧ), arrow-left/right/down, heart (line/filled), share-export, tag, tick-circle, circle-empty, plus/minus, trash, more (…), box, card, phone, mail, copy, Instagram, LinkedIn.
- Sırala/filtre ikonunda aktif durum için sağ üstte mor nokta.

---

## 9. Marka

- `shopier` logosu: mor (şeffaf), beyaz (şeffaf), beyaz (mor zemin), app ikonu. `Seperators/shopierlogo_donotalter` değiştirilmez.
- **Shop uygulaması:** "shop by shopier" lockup'ı — "shop" `shop-red` (#F20E45), "by shopier" `brand-500`. Yalnızca giriş/hesap akışında kullanılır.
- Logo yalnızca kendi renklerinde. Gölge, gradient veya döndürme uygulanmaz.

---

## 10. İçerik ve dil

### 10.1 Ton

- Türkçe, "siz" hitabı, kibar ve net. Ör.: "Adresi silmek istediğinizden emin misiniz?", "Bu dükkan, satışlarına geçici bir süre ara vermiştir. Lütfen daha sonra tekrar deneyin."
- **Buton metinleri:** Kısa, fiil odaklı, yalnızca ilk harf büyük — "Sepete ekle", "Hemen al", "Siparişi tamamla", "Ödemeye geç", "Uygula", "İlerle", "Tamam", "Kapat", "Vazgeç", "Kopyala", "Takip et".
- **Placeholder'larda isteğe bağlılık parantezle:** "(Zorunlu değil)", "(Tercihen)".

### 10.2 Fiyat formatı

| Bağlam | Format | Örnek |
|---|---|---|
| Liste / ürün detay | Binlik nokta, **kuruşsuz**, "TL" daha küçük | `4.200 TL` (TL 12 px) |
| Sepet / checkout / özet | **Kuruşlu**, ",00" ve "TL" fiyattan 2 px küçük | `8.400,00 TL` |
| İndirim satırı | Eksi işaretli | `-800,00 TL` |
| Eski fiyat | `ink-300`, üstü çizili, aynı satırda sağda (sepette altında) | ~~`4.600 TL`~~ |
| İndirim oranı | Foto üstü `%9`, listede `%15 İndirim` | |
| Ürün adedi | `( 2 ürün )`, `2 adet`, `89 ürün` | |

Arayüzde `₺` yerine **TL** kullanılır.

### 10.3 Hata ve boş durumlar

- Hata mesajı ne olduğunu ve ne yapılabileceğini söyler; teknik detay vermez; genel ifade tercih edilir.
- Boş arama: "Bu arama için sonuç bulunmuyor."
- Dükkan kapalı/tatilde: bottom sheet bilgi tipi (ⓘ + metin + "Tamam").
- Yasal metin: "Aşağıdaki butona tıklayarak … okuduğumu beyan ederim." Belge adı Bold veya link.

---

## 11. Durum ve davranış kalıpları

| Durum | Kalıp |
|---|---|
| Sepete ekleme başarılı | **Toast** (6.6) + header'daki sepet sayacı artar |
| Kampanya / bilgi | Notification bar |
| Onay gerektiren aksiyon | Onay sheet'i (başlık + metin + ikili buton) |
| Başarı | Durum sheet'i, tick ikonu + "Tamam" |
| Bloklayıcı hata | Dükkan sayfasına yönlendirme + notification bar, ya da durum sheet'i |
| Seçim gerektiren aksiyon | Seçim yapılana kadar `primary-disabled`; "Tümünü temizle" `ink-300` → seçimle `brand-500` |
| Form hatası | Input kenarı + yardımcı metin `sale-500` |
| Giriş gerektiren aksiyon (favori) | Giriş sayfasına yönlendir (`?redirect=`) |
| Stok sınırı | `+` butonu pasif (`line-150`) |
| Tükenen varyant | Chip üstü çizili |
| Uzun metin | 28 px fade + "Daha fazla" |
| Liste devamı | Sonsuz kaydırma + loader (6.10) |
| Hover (desktop) | Birincil buton radial gradient; select `surface-200`; badge `surface-150` |

---

## 12. Teslim öncesi kontrol listesi

- [ ] Renkler Bölüm 2 token'larından mı? Kırmızı yalnızca indirim/hata için mi? `shop-red` arayüzde kullanılmamış mı?
- [ ] Font Urbanist mi (Gilroy değil)? Boyut/ağırlık Bölüm 3'te mi? Gövde Medium mu?
- [ ] Mobilde 22 px kenar / 349 px kolon; desktop'ta 64 px kenar mı?
- [ ] Grid: mobil 2 × 165 (19 / 30), desktop 6 kolon (30 / 39) mu?
- [ ] Tek dolu mor buton mu? Butonlar 50 px pill, 18 SemiBold mu? Sheet içinde buton aralığı 5, sayfada 12 mi?
- [ ] Input'lar 55 px, radius 11, `line-300` mü? Hata durumu `sale-500` mü?
- [ ] Gölge yalnızca toast/autocomplete'te mi?
- [ ] Mobilde seçim/onay/bilgi için bottom sheet kullanıldı mı (tutamaç, 20 radius, sabit footer)?
- [ ] Fiyat formatı bağlama uygun mu (liste kuruşsuz, sepet kuruşlu; TL küçük)?
- [ ] Taşan metinde fade kullanıldı mı?
- [ ] Mevcut component yeniden icat edilmedi mi (Bölüm 6–7)?
- [ ] Mobil ve desktop karşılığı düşünüldü mü?

---

## 13. Açık noktalar

1. **Figma'da Variables/Styles yok.** Canlı sitedeki `--c-*` değişkenleri (Bölüm 2.1) fiilî token setidir; Figma'ya aynı isimlerle Variable olarak işlenmesi önerilir.
2. **Figma ↔ canlı farkları:**
   - **Font ailesi:** Figma component'leri Urbanist (hedef), canlı Gilroy (geçiş sürüyor). Figma'daki Typography dokümantasyon frame'inde hâlâ "Font family: Gilroy" yazıyor; güncellenmesi önerilir.
   - Sheet başlığı: Figma 20 Bold, canlı 20 SemiBold.
   - Kategori tab'ında seçili olmayan sekme: Figma Medium, canlı SemiBold.
   - "Takip et": Figma'da pill badge, canlıda 30 px radius 8 outline buton.
   - Ürün detay fiyatı: canlıda Medium, Bold değil.
   - Dükkan adı: canlıda 23 px (Figma skalasında 22).
3. **Focus stili** canlıda görünür değil (yalnızca outline 2 px şeffaf). Erişilebilirlik için öneri: focus'ta kenar `ink-900` veya 2 px `brand-500` halka.
4. **Ödeme adımı, sipariş onayı ve hata sayfaları** bu incelemede canlıda gezilmedi; gerçek kişisel veri ve ödeme gerektiriyor. Kurallar Figma'dan alındı.
5. Varyant seçimli ürün (renk/beden select) bu dükkanda bulunamadı; Figma `box_dropdown` kalıbı geçerli.
6. Erişilebilirlik:
   - `ink-300` beyaz üzerinde ~2.7:1; yalnızca placeholder/pasif metinde kullanılmalı.
   - `ink-400` ~4.2:1, küçük metinde AA sınırının altında.
   - `brand-500` 6.9:1, uygun.
7. Dark mode yok; storefront yalnızca açık temadır.

---

## Ek A — CSS değişkenleri

```css
:root {
  /* Brand & semantic */
  --brand-500: #6700FF;
  --sale-500: #EE3124; --sale-50: rgba(238,49,36,.10);   /* indirim + hata */
  --shop-red: #F20E45;                                   /* yalnızca "shop" logosu */
  /* Ink */
  --ink-900:#0B0F34; --ink-800:#292D33; --ink-700:#2F3352; --ink-600:#414561;
  --ink-500:#545670; --ink-400:#787A8E; --ink-300:#9C9EAC; --ink-250:#9FA0A5;
  /* Lines & surfaces */
  --line-300:#D0D0D7; --line-250:#D3D3D9; --line-200:#E2E2E5; --line-150:#E5E5E8;
  --surface-200:#F1F1F1; --surface-150:#EEEEEE; --surface-100:#F7F7F7; --surface-0:#FFFFFF;
  --neutral-tint: rgba(159,160,165,.09);
  --overlay: rgba(11,15,52,.50); --sheet-handle:#D9D9D9;
  --float-shadow: 0 0 10px 0 #E2E2E5;   /* yalnızca toast & autocomplete */

  /* Type */
  --font-sans: "Urbanist",-apple-system,"Segoe UI",sans-serif;

  /* Radius */
  --r-5:5px; --r-6:6px; --r-8:8px; --r-9:9px; --r-10:10px; --r-11:11px; --r-14:14px;
  --r-16:16px; --r-18:18px; --r-20:20px; --r-pill:27.5px; --r-full:9999px;

  /* Spacing */
  --s-5:5px; --s-8:8px; --s-10:10px; --s-12:12px; --s-15:15px; --s-17:17px; --s-19:19px;
  --s-20:20px; --s-22:22px; --s-30:30px; --s-39:39px; --s-40:40px; --s-50:50px; --s-64:64px;

  /* Layout */
  --header-height:55px; --nav-height:50px; --p-container:22px; --p-container-desktop:64px;
  --btn-h:50px; --input-h:55px; --chip-h:36px; --icon:24px;
}
```

## Ek B — Tailwind `theme.extend`

```js
colors: {
  brand: { 500: '#6700FF' },
  sale: { 50: 'rgba(238,49,36,.10)', 500: '#EE3124' },
  shop: { red: '#F20E45' },
  ink: { 900:'#0B0F34', 800:'#292D33', 700:'#2F3352', 600:'#414561', 500:'#545670', 400:'#787A8E', 300:'#9C9EAC', 250:'#9FA0A5' },
  line: { 300:'#D0D0D7', 250:'#D3D3D9', 200:'#E2E2E5', 150:'#E5E5E8' },
  surface: { 0:'#FFFFFF', 100:'#F7F7F7', 150:'#EEEEEE', 200:'#F1F1F1' },
},
fontFamily: { sans: ['Urbanist','system-ui','sans-serif'] },
borderRadius: { xs:'5px', sm:'6px', follow:'8px', card:'10px', input:'11px', 'card-lg':'14px', lg:'16px', chip:'18px', sheet:'20px', pill:'27.5px' },
boxShadow: { float: '0 0 10px 0 #E2E2E5' },
screens: { sm:'578px', md:'768px', lg:'1024px', xl:'1200px', '2xl':'1440px', '3xl':'1728px' },
```

## Ek C — Hızlı reçeteler (HTML/CSS)

```html
<!-- Birincil + ikincil buton (sayfa içi, 12 px) -->
<div style="display:flex;flex-direction:column;gap:12px;width:349px">
  <button style="height:50px;border-radius:27.5px;background:var(--brand-500);color:#fff;font:600 18px/22px var(--font-sans);border:0">Sepete ekle</button>
  <button style="height:50px;border-radius:27.5px;background:#fff;color:var(--brand-500);border:1px solid var(--brand-500);font:600 18px/22px var(--font-sans)">Hemen al</button>
</div>

<!-- Liste kartı fiyatı -->
<div style="font:700 15px/20px var(--font-sans);color:var(--ink-700)">4.200 <span style="font-size:12px">TL</span>
  <s style="font-weight:400;color:var(--ink-300)">4.600 <span style="font-size:12px">TL</span></s></div>

<!-- Filtre chip'i (normal / seçili) -->
<span style="display:inline-flex;align-items:center;height:36px;padding:0 15px;border-radius:18px;background:var(--surface-100);font:500 14px/18px var(--font-sans);color:var(--ink-700)">Sehpa</span>
<span style="display:inline-flex;align-items:center;height:36px;padding:0 15px;border-radius:18px;background:var(--ink-700);font:500 14px/18px var(--font-sans);color:#fff">Aydınlatma</span>

<!-- Bottom sheet iskeleti -->
<div style="width:393px;background:#fff;border-radius:20px 20px 0 0;padding:9px 22px 34px">
  <div style="width:50px;height:5px;border-radius:20px;background:var(--sheet-handle);margin:0 auto 20px"></div>
  <div style="text-align:center;font:600 20px/25px var(--font-sans);color:var(--ink-900);margin-bottom:24px">Sırala</div>
  <!-- seçenekler: 349×50 pill, gap 5 -->
  <!-- footer: Tümünü temizle + Uygula -->
</div>

<!-- Toast -->
<div style="width:349px;padding:12px 16px;border-radius:16px;background:var(--surface-100);box-shadow:var(--float-shadow);display:flex;justify-content:space-between;align-items:center;font:500 16px/20px var(--font-sans);color:var(--ink-900)">
  ✓ Sepete eklendi <button style="background:#fff;border:0;border-radius:10px;padding:6px 8px;font:inherit">Siparişi tamamla</button>
</div>
```

---
*Sürüm 1.2 — Font ailesi Urbanist olarak güncellendi (design system geçişi; canlı hâlâ Gilroy). Ölçü ve boşluk değerleri v1.1 ile aynı. v1.1: Figma Storev3 + canlı storefront incelemesi (studiomuse).
