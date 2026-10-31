# Shopier Ürün Geliştirme Akışı

Slack'te yazılan bir özellik fikrini araştırma → tasarım → PRD → prototip → CTO değerlendirmesi → Jira sırasıyla ilerleten ajan akışı. Her aşama PM onayıyla geçer; Prototip ve CTO değerlendirmesinde ayrıca Product Lead onayı gerekir.

## Nasıl kullanılır

1. PM `#claude` kanalına özelliği bir mesaj olarak yazar. Mesajı yazan kişi o özelliğin PM'idir.
2. Herhangi biri o mesajın thread'ine `Başlat` yazar.
3. Akış her 5 dakikada bir thread'i okur; çıktıları thread'e koyar ve onay ister.
4. Her aşamada PM etiketlenir. Araştırma, Tasarım ve PRD'de PM'in onayı yeter; Prototip ve CTO değerlendirmesinde PM'den sonra İmge Aksoy (Product Lead) da etiketlenir. Cevap: `Onay` ya da `Revize: <yorum>`.
5. Bütün aşamalar onaylanınca Shopier Test Board'da (STB) Epic ve Story'ler açılır, linkler thread'e gelir.

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `CLAUDE.md` | El kitabı: roller, onay kapısı, zincir, Slack protokolü |
| `ayarlar.md` | Kanal, kişiler, Jira projesi |
| `.claude/agents/` | Araştırma, Tasarım, PRD, Prototip, Jira ajanları |
| `.claude/skills/akis-turu/` | Koordinatör'ün tur talimatı (zamanlanmış görev bunu çalıştırır) |
| `referanslar/` | DESIGN.md (Storev3), design-md kararları, PRD yöntemi |
| `ozellikler/<kisa-ad>/` | Her özelliğin durum defteri ve çıktıları |

## Notlar

- Zamanlanmış görev Claude masaüstü uygulaması açıkken çalışır; kapalıyken kaçan tur uygulama açılınca çalışır.
- CTO değerlendirmesi şimdilik manuel: ajan yok, PM ve Product Lead onayıyla geçer. İleride `shopier-product:cto-teknik-degerlendirme` skill'i bu aşamaya bağlanabilir.
- Tasarım ajanı satıcı paneli ekranı tasarlamaz (DESIGN.md yalnızca alıcı storefront'unu kapsıyor).
