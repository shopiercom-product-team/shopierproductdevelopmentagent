# Ürün yorumları · Prototip notu

Sahibi: Prototip ajanı · Tur 1 · 31.10.2026 · Dosya: `prototip.html`
Kaynak: onaylı `tasarim.html` / `tasarim.md`, onaylı `prd-urun-yorumlari.md` (v0.2), `referanslar/DESIGN.md` (Storev3 v1.2).

## Nasıl kullanılır

- Tek dosya, 393 px telefon çerçevesi; dış script ve API çağrısı yok, örnek veri sayfanın içinde. Font Urbanist (Google Fonts stylesheet'i).
- Sayfanın üstünde kapatılabilir rehber şeridi vardır.
- **Başlangıç:** "Ürün sayfası" (varsayılan) ya da "Davet bağlantısı" (yorum yaz sayfası).
- **Senaryo seçicisi:** Normal, Yorum yok, Yorumlar yükleniyor (takılı), Yorumlar yüklenemedi, Davet bağlantısı geçersiz, Gönderim başarısız (ilk deneme), Fotoğraf yüklenemiyor.
- Sol paneldeki "hikaye yolları" her hikayenin başlangıç noktasına götürür.
- Örnek veri tutarlıdır: 128 yorum, dağılım 93/22/8/5/0, ortalama 4,6, 24 fotoğraflı yorum; liste bu sayılara göre üretilir, chip sayıları listeyle uyuşur.

## Kapsanan hikayeler

| Hikaye | Prototipte | Nasıl yürünür |
|---|---|---|
| US-1 · Puan ve yorumları görme | Tam | Ürün detay: ad altında puan satırı, "128 yorum" Yorumlar bölümüne kaydırır; ortalama, dağılım, chip'ler, en fazla 3 yorum. Yorumlar ayrı yüklenir (ürün sayfası beklemez). Boş durum, Yükleniyor ve "Tekrar dene" hatası senaryo ile. |
| US-2 · Süzme ve sıralama | Tam | Chip'ler (ürün detay ve Tüm yorumlar), "Tüm yorumları gör", Sırala sheet'i (4 seçenek, Tümünü temizle, Uygula), "Daha fazla", sonsuz kaydırma, filtre sonucu yok durumu ("1 yıldız" chip'i). |
| US-3 · Fotoğrafı büyütme | Tam | Yorumdaki küçük fotoğraf sheet'i açar; fotoğrafa dokunmak sıradakine geçirir, "Kapat" ile kapanır. |
| US-4 · Davetle yorum yazma | Tam | Puan seçici (puan yokken "Yorumu gönder" pasif), metin sayacı, fotoğraf ekle/kaldır (yükleniyor durumu), Hata · form, Hata · gönderilemedi (Tekrar dene / Vazgeç), Başarı ("Ürüne git"), Hata · bağlantı geçersiz ("Dükkana git"). |
| US-5 · Satıcı cevabı | Kısmi | Yalnızca alıcının gördüğü cevap kutusu ("Muse Studio'nun cevabı", tarih) yorum kartlarında var. |

Başlangıç ekranı: Ürün detay (Normal senaryo). Yorum yazma akışı için "Davet bağlantısı".

## Kapsanmayanlar ve nedeni

| Konu | Neden |
|---|---|
| US-6 · Moderasyon ve Akış 4 | Operasyon ekranı tasarlanmadı (PRD Açık soru 18). Gönderilen yorum ürün sayfasındaki listeye eklenmez (ön moderasyon varsayımı). |
| Satıcı paneli: cevap yazma, kural ihlali bildirme, yorum listesi | Tasarlanmadı (PRD Açık soru 9); yeni ekran icat edilmedi. |
| Davet mesajı (e-posta, SMS, Shop bildirimi) | Tasarım kapsamında yok (PRD Açık soru 5). Davet bağlantısına "başlangıç" seçeneğiyle girilir. |
| Desktop (tasarım 4.1) | Prototip mobil 393 px çerçevede; desktop yalnızca statik tasarımda. |
| Sepete ekle, Hemen al, beden chip'leri, Takip et, tab'lar, favori/paylaş | Yorum özelliğinin parçası değil; görsel olarak var, tıklanmaz. |
| "Dükkana git" hedefi | Dükkan sayfası bu özelliğin tasarımında yok; prototipte kesikli çerçeveli "Akış burada biter" kartı gösterilir (ürün arayüzü değil, prototip ucu). Aynı kart "Vazgeç" sonrası da çıkar. |

## PRD–tasarım çelişkileri ve farklar

1. **Fotoğraflı chip'i:** Tasarımda puan filtre chip'lerinin yanında "Fotoğraflı (24)" chip'i var; PRD yalnızca puan filtresinden söz ediyor. Prototip tasarımı izledi, chip var. PM teyidi gerekir.
2. **Sırala sheet'inde "Tümünü temizle":** Tasarımda Sırala sheet'inde "Tümünü temizle" her zaman aktif görünüyor; DESIGN.md 11. bölüm seçimle aktifleşmesini söylüyor. Prototip DESIGN.md'yi izledi (varsayılan dışı seçimde aktif).
3. **Başarı sheet'i metni:** "kontrol edildikten sonra yayımlanacak" ön moderasyonu varsayıyor; PRD'de bu Açık soru 3. Prototip tasarım metnini kullandı.
4. **"Tüm yorumları gör" ve filtre:** PRD hangi filtrenin Tüm yorumlar sayfasına taşınacağını söylemiyor. Prototip seçili filtreyi taşır, sıralama "En yeni" başlar.
5. **Ad altı puan satırı:** Tasarımda yorum varken görünür, PRD ile uyumlu. Yükleme sırasında puan satırı henüz gösterilmez (tasarımda yükleniyor ekranında puan satırı yok); yorumlar yüklenince satır belirir ve sayfa kısa süre kayabilir.

## Prototip varsayımları (tasarım/PRD'de olmayan, yalnızca demo için)

- Normal senaryoda yorum bölümü ~1 sn yüklenir; "Yorumlar yüklenemedi" senaryosunda "Tekrar dene" ikinci denemede başarılı olur; "Gönderim başarısız" senaryosunda "Tekrar dene" başarılı olur; "Fotoğraf yüklenemiyor" senaryosunda eklenen ilk fotoğraf yüklenemez.
- Metin zorunlu sayıldı (en az 10 karakter, tasarımın örnek sınırı); bu PRD'de kesin değil (Açık soru 8). Hata, "Yorumu gönder"e dokunulunca gösterilir.
- Fotoğraf eklemede gerçek dosya seçilmez; "Ekle" bir yer tutucu fotoğraf ekler (en fazla 5).
- Yorum yazma sayfasındaki yasal metin "Ayşe K." adını gösterir (tasarımdaki örnek ad).
- Erişilebilirlik için klavye odak halkası eklendi (DESIGN.md Bölüm 13 madde 3'teki öneri); tasarımda yok.

## Açık sorular

PRD'deki açık soruların tamamı (özellikle 3, 5, 6, 8, 9, 12) geçerlidir. Prototipten çıkanlar:

1. "Fotoğraflı" filtresi kapsamda mı (çelişki 1)?
2. Yorumu moderasyon bekleyen alıcıya, ürün sayfasında "yorumunuz inceleniyor" gibi bir durum gösterilecek mi? Tasarımda yok, prototipte yok.
3. Metin zorunlu mu, yoksa yalnızca puanla gönderilebilir mi? Tasarım "metin en az 10 karakter" varsayıyor; PRD yalnızca puanı zorunlu kılıyor (US-4 ilk senaryo).
4. Alıcı "Vazgeç" dedikten sonra nereye gider (Dükkan mı, ürün mü, bağlantı kapanır mı)? Tasarım ve PRD akışı "akış biter" diyor.

## Revizyon geçmişi

| Tarih | Tur | Değişiklik |
|---|---|---|
| 31.10.2026 | 1 | İlk sürüm: US-1…US-4 tam, US-5 kısmi; 7 senaryo, rehber şeridi. |
