# Ürün yorumları · Tasarım notu

Sahibi: Tasarım ajanı · Tur 1 · 31.10.2026 · Ekran seti: `tasarim.html`
Kaynak: `referanslar/DESIGN.md` (Storev3 v1.2) ve `referanslar/design-md-kararlari.md`. Figma design system linki `ayarlar.md`'de doldurulmadığı için Figma okunmadı; yalnızca DESIGN.md kullanıldı.
Yön: Onaylı araştırmanın B seçeneği. Siparişe bağlı, doğrulanmış yorum (yıldız, metin, fotoğraf), sipariş sonrası davetle yazma, satıcının herkese açık cevabı. Satıcı yorumu silemez; moderasyon Shopier'de.

## Ekran listesi

Mobil (393 × 852):

| # | Ekran | Açıklama |
|---|---|---|
| 1.1 | Ürün detay · puan özeti | Ürün adının altında yıldız, ortalama ("4,6") ve "128 yorum" text-link'i. Link sayfayı Yorumlar bölümüne kaydırır. |
| 1.2 | Ürün detay · Yorumlar bölümü | Ürün bilgi tab'ından sonra, dükkan kartından önce. Ortalama, 5→1 dağılım, puan filtresi chip'leri, en fazla 3 yorum, "Tüm yorumları gör" (outline). |
| 1.3 | Tüm yorumlar | Alt sayfa: "Ürüne dön" back-link'i, `display-32` başlık, chip filtreleri, sonuç satırında sırala ikonu, uzun yorumda fade ve "Daha fazla", sonsuz kaydırma ve loader. |
| 1.4 | Sırala sheet'i | 7.2 kalıbı: En yeni (varsayılan), En eski, En yüksek puan, En düşük puan. |
| 1.5 | Yorum fotoğrafı sheet'i | Ürün detay görseli kalıbı (349², radius 16, dot'lar) ve yorumun kısa özeti, "Kapat". |
| 2.1 | Yorum yaz · boş | Davet bağlantısıyla açılan sayfa. Ürün satırı, puan seçici, metin alanı, fotoğraf ekleme, yasal metin. Puan seçilmeden "Yorumu gönder" `primary-disabled`. |
| 2.2 | Yorum yaz · dolu | Puan ve etiketi ("Çok beğendim"), metin ve sayaç, fotoğraflar (biri yükleniyor). |
| 2.3 | Hata · gönderilemedi | Durum sheet'i. Form içeriği korunur. "Tekrar dene" (dolu) ve "Vazgeç" (outline), aralık 5. |
| 2.4 | Hata · form | Metin 10 karakterden kısa ve fotoğraf yüklenemedi: kenar ve yardımcı metin `sale-500`. |
| 2.5 | Başarı | Durum sheet'i: tick, "Teşekkürler, yorumunuz alındı", "Ürüne git". |
| 2.6 | Hata · bağlantı geçersiz | Bloklayıcı hata için durum sheet'i: süresi dolmuş ya da kullanılmış davet bağlantısı. "Dükkana git". |
| 3.1 | Boş durum · yorum yok | Puan satırı gizlenir. Bölümde "Bu ürün için henüz yorum yok." ve kimin yorum yazabileceği bilgisi. |
| 3.2 | Boş durum · filtre sonucu yok | "Bu filtreye uygun yorum bulunmuyor." ve "Tüm yorumları göster" text-link'i. |
| 3.3 | Yükleniyor | Yorumlar bölümünde loader (6.10). Ürün sayfası yorumları beklemez. |
| 3.4 | Hata · yorumlar yüklenemedi | Aksiyon butonlu notification bar: "Yorumlar şu an yüklenemedi." ve "Tekrar dene". |

Desktop (1440, %50 ölçekte):

| # | Ekran | Açıklama |
|---|---|---|
| 4.1 | Desktop · ürün detay | Sağ kolonda puan satırı. Altta iki kolon: solda 349 px özet, dağılım ve chip'ler; sağda yorum listesi. Sheet'ler desktop'ta ortalanmış modal olur (7.5). |

Satıcı tarafı (yorumlara cevap yazma, kural ihlali bildirme, yorum listesi ve bildirimler): **kapsam dışı, kaynak bekleniyor** (`design-md-kararlari.md` 2. karar). Ekranlarda satıcı cevabı yalnızca alıcının gördüğü hâliyle var.
Davet mesajı (e-posta, SMS ya da Shop bildirimi) DESIGN.md kapsamında değil; tasarlanmadı.

## Kullanılan mevcut component'ler

- Header (4.3): dükkan ve ürün sayfasında tam; yorum yazma sayfasında yalnızca logo (alt sayfa kalıbı).
- Butonlar (6.1): `primary`, `primary-disabled`, `primary-outline`, `text-link`, `text-clear`, `back-link`.
- Sticky aksiyon barı (4.3), 70 px.
- Ürün bilgi tab'ı (6.5), dükkan kartı (7.9), ürün detay görseli ve dot'lar (6.7, 5.4).
- `filter-chip` ve seçili hâli (6.3): puan filtresi, yatay kaydırmalı.
- Liste bilgi badge'i (6.4): "Doğrulanmış alıcı", 16 px tick-circle ikonuyla.
- Progress bar track ve dolgusu (6.9): puan dağılım çubukları (track `line-300`, dolgu `ink-900`, radius 2).
- Loader (6.10): bölüm yükleme, sonsuz kaydırma, fotoğraf yükleme.
- Notification bar, aksiyon butonlu varyant (6.6): yükleme hatası.
- Bottom sheet sistemi (7.5): Sırala (seçim listesi), durum/bilgi (başarı, gönderim hatası, geçersiz bağlantı), yorum fotoğrafı.
- Radio satırı (6.2), form hatası kalıbı (6.2), yasal metin `legal-12` (7.11).
- Özet satırı (6.7): yorum yazma sayfasındaki ürün satırı (80² görsel, radius 5), `line-300` çerçeveli kutuda (7.11 özet kutusu).
- Boş durum metni (7.4 arama boş durumu kalıbı: 14 Medium `ink-300`, sola hizalı).

## Yeni component önerileri (Öneri · onay bekliyor)

Hepsi mevcut token'lardan türetildi. Ekranlarda kesikli mor "Öneri · onay bekliyor" etiketiyle işaretli. Sayfanın üstündeki kutuyla etiketler gizlenebilir.

1. **Yıldız ikonu ve puan gösterimi.** Bölüm 8 ikon setinde yıldız yok. Öneri: 24 px grid'de yıldız; gösterimde 16 px, dolu `ink-900`, boş `line-300`, aralık 2. Renk için sarı ya da başka bir ton uydurulmadı.
2. **Puan özeti.** Ortalama `display-32` Bold (32/40) `ink-900`, altında 16 px yıldızlar ve "128 yorum" (12 Medium `ink-400`). Sağda 5 satırlık dağılım: etiket 14 Medium, progress track, adet 14 Medium `ink-400`, satır aralığı 8.
3. **Yorum kartı.** Üstte yıldızlar ve tarih (12 Medium `ink-400`), ad (14 SemiBold `ink-900`) ve "Doğrulanmış alıcı" badge'i, varyant (12 Medium `ink-400`), metin (14/20 Medium `ink-500`, 5 satırdan sonra fade ve "Daha fazla"), 60² fotoğraflar (radius 5, aralık 10). Kartlar arası 1 px `line-200`, dikey padding 20.
4. **Satıcı cevabı kutusu.** Yorum kartının içinde, `surface-100` zemin, radius 11, padding 15. Başlık "<Dükkan adı>'nun cevabı" (14 SemiBold) ve tarih; metin 14/20 Medium `ink-500`.
5. **Puan seçici (form).** 5 × 40 px yıldız, aralık 12; boş hâl 1.5 px `ink-300` çizgi, seçili hâl dolu `ink-900`. Altında seçime göre etiket (14 Medium `ink-900`): 1 Hiç beğenmedim, 2 Beğenmedim, 3 İdare eder, 4 Beğendim, 5 Çok beğendim. Seçim yokken yardım metni 14 Medium `ink-400`.
6. **Çok satırlı metin alanı.** Input token'larıyla: 349 × 150, 1 px `line-300`, radius 11, padding 15/19, değer 16/24 Medium. Sağ altta sayaç 12 Medium `ink-400` ("96 / 1000"). Hata hâli 6.2 ile aynı.
7. **Fotoğraf ekleme.** 80² kareler (radius 5, aralık 10). "Ekle" karesi: `surface-100` zemin, 1 px `line-300`, 24 px plus ve 12 Medium `ink-500` metin. Eklenen fotoğrafın sağ üstünde 24 px close-circle (beyaz zemin). Yükleniyor: `surface-200` zemin ve loader. Hata: 1 px `sale-500` kenar ve "Yüklenemedi". Altında 12 Medium `ink-400` bilgi satırı.

## Varsayımlar

- Yorum yazma yalnızca sipariş sonrası davet bağlantısıyla açılır. Ürün sayfasında herkese açık "Yorum yaz" butonu yok. Bağlantı tek kullanımlıktır; misafir alıcı da giriş yapmadan yazabilir.
- Davet bir sipariş ürünü için tek sayfa açar. Siparişte birden fazla ürün varsa her ürün için ayrı bağlantı ya da sıralı sayfalar gerekir; ekranlarda tek ürün gösterildi.
- Alıcı adı siparişten gelir ve "Ad S." biçiminde, kısaltılmış olarak yayımlanır. Alıcı adını değiştiremez.
- Puan zorunlu, metin en az 10 en çok 1000 karakter, fotoğraf en fazla 5 adet, her biri en çok 10 MB. Bu sınırlar örnektir; PRD'de kesinleşmeli.
- Yorum gönderildikten sonra Shopier'in kontrolünden geçip yayımlanır (ön moderasyon). Bu yüzden başarı metni "kontrol edildikten sonra yayımlanacak" diyor.
- Ürün detayında en fazla 3 yorum gösterilir, kalanı "Tüm yorumlar" sayfasında. Varsayılan sıralama "En yeni".
- Ortalama tek ondalıkla ve virgülle yazılır ("4,6"). Yıldızlar yuvarlanmış tam yıldızla gösterildi (4,6 → 5 dolu). Yarım yıldız istenirse ayrı öneri gerekir.
- Yorumu olmayan üründe ad altındaki puan satırı gizlenir; Yorumlar bölümü boş durum metniyle görünür.
- Puan filtresinde 0 yorumlu seçenek de seçilebilir ve boş durumu gösterir (3.2). Alternatif: 0 yorumlu chip'i hiç göstermemek.
- Yorumlar bölümü ayrı bölüm olarak tasarlandı. Alternatif: ürün bilgi tab'ına üçüncü sekme "Yorumlar (128)" eklemek. Bölüm daha görünür olduğu için tercih edildi.
- Header'daki "shopier" logosu ve görseller yer tutucudur.

## Bölüm 12 kontrol listesi sonucu

| Madde | Sonuç |
|---|---|
| Renkler Bölüm 2 token'larından; kırmızı yalnızca hata için; `shop-red` yok | Geçti. Kırmızı yalnızca form ve fotoğraf yükleme hatasında. Yıldız için yeni renk uydurulmadı (`ink-900` / `line-300`). |
| Font Urbanist, boyut ve ağırlıklar Bölüm 3'te, gövde Medium | Geçti. Not: ortalama puan için `display-32` (sayfa başlığı token'ı) kullanıldı; öneri olarak işaretli. |
| Mobilde 22 px kenar, 349 px kolon; desktop'ta 64 px kenar | Geçti. |
| Grid (2 × 165 / desktop 6 kolon) | Uygulanmadı; bu özellikte ürün grid'i yok. |
| Tek dolu mor buton; 50 px pill, 18 SemiBold; sheet içinde 5, sayfada 12 | Geçti. Ürün detayda sticky bar yalnızca sayfa içi butonlar görünmüyorken var (1.2, 1.3, 3.3, 3.4). "Tüm yorumları gör" outline. |
| Input 55 px, radius 11, `line-300`; hata `sale-500` | Geçti. Metin alanı 150 px yükseklikte (çok satırlı olduğu için); öneri olarak işaretli. |
| Gölge yalnızca toast / autocomplete'te | Geçti, gölge yok. |
| Mobilde seçim/onay/bilgi için bottom sheet | Geçti: Sırala, fotoğraf, başarı, gönderim hatası, geçersiz bağlantı. |
| Fiyat formatı | Geçti: ürün detayda kuruşsuz "1.450 TL", TL küçük. |
| Taşan metinde fade | Geçti: uzun yorumda alt fade ve "Daha fazla", fotoğraf sheet'inde sağ fade. |
| Mevcut component yeniden icat edilmedi | Geçti. Yeni olanlar yalnızca DESIGN.md'de karşılığı olmayan 7 öneri. |
| Mobil ve desktop karşılığı | Geçti: desktop ürün detay (4.1); sheet'lerin desktop karşılığı modal. |

Spacing notu: kullanılan boşluklar 2, 5, 8, 10, 12, 15, 20, 22, 25, 30, 37, 40. Yıldızlar arası 2 px ve sheet ikon → başlık 37 px (7.5'teki dikey ritim) skalada yok; ilki ikonun iç boşluğu yerine geçiyor, ikincisi 7.5'ten alındı.

## Açık sorular

1. Yıldız rengi: `ink-900` (sakin, ürün sahnede) mi, `brand-500` mü? DESIGN.md'de sarı ya da puan rengi yok.
2. Moderasyon yayından önce mi (ön moderasyon) yoksa sonra mı? Başarı metni buna göre değişir.
3. Misafir alıcı yorumu tek kullanımlık bağlantıyla mı yazacak? Hesaplı alıcı için "Siparişlerim" içinde de "Yorum yaz" giriş noktası olacak mı? (Sipariş takibi ve hesap ekranları DESIGN.md'de tanımlı değil.)
4. Çok ürünlü siparişte davet tek sayfada tüm ürünleri mi listeleyecek, yoksa ürün başına ayrı mı?
5. Alıcı yorumunu sonradan düzenleyebilecek ya da silebilecek mi? Satıcı cevabına alıcı yanıt verebilecek mi? (Tasarımda yok.)
6. Alıcılar başka bir yorumu "uygunsuz" diye bildirebilecek mi? (Araştırmada bildirim hakkı yalnızca satıcı için.)
7. Varsayılan sıralama mevzuat açısından uygun mu (ör. "Önerilen" yerine "En yeni")? Hukuk teyidi gerekli.
8. Yorumlar ayrı bölüm mü kalsın, yoksa ürün bilgi tab'ına üçüncü sekme mi olsun?
9. Yazı sınırları (10–1000 karakter), fotoğraf sınırları (5 adet, 10 MB) ve yorum süresi (ör. teslimattan sonra 100 gün) ne olacak?
10. Video desteği (araştırmada Etsy örneği) bu fazda yok; doğru mu?
11. Satıcı paneli ekranları (cevap yazma, bildirme) için kaynak ne zaman gelecek?

## Revizyon geçmişi

| Tarih | Tur | Değişiklik |
|---|---|---|
| 31.10.2026 | 1 | İlk sürüm: 15 mobil ekran ve 1 desktop ekran, 7 component önerisi. |
