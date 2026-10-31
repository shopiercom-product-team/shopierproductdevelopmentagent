# Ayarlar

Bu dosyanın sahibi Product Lead'dir. Ajanlar ve Koordinatör bu dosyayı okur, değiştirmez.

## Slack

| Ayar | Değer |
|---|---|
| Kanal | `#claude` · `C0CB3LDUB3R` |
| Product Lead (Patron) | İmge Aksoy · `U0BLV2VFG1Y` |
| Product Manager | Her özellikte, özellik mesajını kanala yazan kişi |
| Başlatma kelimesi | `Başlat` (kanaldaki herhangi biri, özellik mesajının thread'ine) |
| Onay / revize | `Onay` · `Revize: <yorum>` |

## Onay kuralı

| Aşama | Gereken onay |
|---|---|
| 1 · Araştırma | PM |
| 2 · Tasarım | PM |
| 3 · PRD | PM |
| 4 · Prototip | PM → Product Lead (İmge) |
| 5 · CTO değerlendirmesi | PM → Product Lead (İmge) |
| 6 · Jira | Ön koşul: yukarıdaki onayların hepsi |

Yalnızca PM onayı gereken aşamalarda PM'in "Onay"ı aşamayı kapatır; Product Lead'e sunulmaz. Product Lead isterse bu aşamalarda da thread'e yorum yazabilir ama akışı bekletmez.

Özellik mesajını Product Lead yazdıysa o özellikte PM ve Product Lead aynı kişidir; iki onay gereken aşamalarda iki onay da ondan beklenir.

## Jira

| Ayar | Değer |
|---|---|
| Site | `https://shopier.atlassian.net` · cloudId `2a9f61a6-a761-4651-bd4f-2e4b9f34e1fe` |
| Proje | Shopier Test Board · `STB` |
| Issue tipleri | Epic (özellik) · Story (kullanıcı hikayeleri) |

## Figma

| Ayar | Değer |
|---|---|
| Bağlantı | Figma connector'ı (İmge'nin hesabı, bağlı) |
| Design system dosyası | `Shopier-Test-Figma` › "Storev3 - Design system" sayfası · dosya linki: **DOLDURULACAK** |

Link yoksa Tasarım ajanı yalnızca DESIGN.md ile çalışır.

## Kaynaklar

| Kaynak | Yol |
|---|---|
| Design system | `referanslar/DESIGN.md` (Storev3, sürüm 1.2) |
| Design system kararları | `referanslar/design-md-kararlari.md` |
| PRD yöntemi | `referanslar/prd-skill.md` |

## Çalışma

- Akış turu: `akis-turu` skill'i, zamanlanmış görevle her gün, günün her saatinde 5 dakikada bir. Kurulum: `zamanlanmis-gorev.md`.
- Bir aşamada en fazla 5 revize turu; 6.'da Koordinatör durumu Product Lead'e bildirir ve bekler.
