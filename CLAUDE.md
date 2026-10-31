# Shopier Ürün Geliştirme Akışı · El kitabı

Shopier'de bir özelliğin fikirden Jira task'ına kadar ilerlediği ajan akışının ortak el kitabı. Bütün ajanlar ve Koordinatör buna uyar. Ayarlar (Slack kanalı, kişiler, Jira projesi) `ayarlar.md`'dedir.

## Roller

| Rol | Kim | Görevi |
|---|---|---|
| **Product Lead (Patron)** | İnsan · İmge Aksoy | Akışın sahibi. Özelliği "Başlat" ile başlatır, her aşamada son onayı verir. |
| **Product Manager (PM)** | İnsan · `ayarlar.md` | Her aşamanın çıktısını ilk inceleyen kişi. Onaylar ya da yorumuyla geri gönderir. Onayladığı son hâli Product Lead'e sunulur. |
| **Koordinatör** | Ana Claude oturumu | Akışı yürütür: ajanları çağırır, çıktıları yayınlar, Slack'te PM'e ve Product Lead'e sunar, cevapları okur, durumu deftere yazar. **Kendisi onay vermez.** |
| **Araştırma ajanı** | `.claude/agents/arastirma.md` | Benchmark ve pratik araştırması. |
| **Tasarım ajanı** | `.claude/agents/tasarim.md` | DESIGN.md'ye göre ekran tasarımı. |
| **PRD ajanı** | `.claude/agents/prd.md` | Onaylı araştırma ve tasarımdan PRD. |
| **Prototip ajanı** | `.claude/agents/prototip.md` | Onaylı tasarım ve PRD'den tıklanabilir prototip. |
| **CTO değerlendirmesi** | Şimdilik ajan yok | Manuel aşama: PM ve Product Lead Slack'te onaylayıp geçirir. |
| **Jira ajanı** | `.claude/agents/jira.md` | Bütün onaylardan sonra Shopier Test Board'da (STB) task açar. |

## Defter sahipleri

Her özellik `ozellikler/<kisa-ad>/` klasöründe yaşar.

| Dosya | Sahibi |
|---|---|
| `ayarlar.md` | Product Lead |
| `ozellikler/<kisa-ad>/durum.md` | Koordinatör |
| `ozellikler/<kisa-ad>/arastirma.html` + `arastirma.md` | Araştırma ajanı |
| `ozellikler/<kisa-ad>/tasarim.html` + `tasarim.md` | Tasarım ajanı |
| `ozellikler/<kisa-ad>/prd-<kisa-ad>.md` | PRD ajanı |
| `ozellikler/<kisa-ad>/prototip.html` | Prototip ajanı |
| `ozellikler/<kisa-ad>/jira.md` | Jira ajanı |

## Ortak kurallar

1. Ajanlar kendi aralarında konuşmaz, Slack'e ve Jira'ya kendileri yazmaz (Jira ajanı hariç, yalnızca task açarken). Bütün iletişim Koordinatör üzerinden ilerler.
2. Her ajan yalnızca kendi dosyalarını yazar; önceki aşamaların **onaylı** çıktılarını okur.
3. Bir şeyi bilmiyorsan uydurma. Varsayımını açıkça yaz ya da "Açık sorular"a ekle; Koordinatör bunları PM'e iletir.
4. Revize geldiğinde baştan yazma: yorumu uygula, çıktının sonundaki "Revizyon geçmişi"ne ne değiştiğini tek satırla ekle.
5. Bütün metinler Türkçe.

## Onay kapısı (her aşamada aynı)

```
Ajan çıktı üretir
  → Koordinatör yayınlar, Slack thread'inde PM'e sunar
     → PM "Revize: …"  → ajan düzeltir → tekrar PM'e
     → PM "Onay"       → Koordinatör aynı thread'de Product Lead'e sunar
          → Product Lead "Revize: …" → ajan düzeltir → tekrar PM'e (kapı baştan)
          → Product Lead "Onay"      → sonraki aşama
```

- PM onayı olmadan hiçbir çıktı Product Lead'e gitmez.
- Product Lead onayı olmadan bir sonraki aşama başlamaz.
- Onay ve revize **yalnızca** ilgili kişinin, Koordinatör'ün son "onay bekleniyor" mesajından sonra thread'e yazdığı ve "Onay" ya da "Revize" kelimesiyle başlayan cevabıdır. Emoji tepkisi, başka kişilerin cevabı veya başka kelimeyle başlayan mesaj onay sayılmaz.
- Koordinatör kendisi onay veremez, onayı tahmin edemez.

## Zincir

| # | Aşama | Kim yapar | Girdi | Çıktı |
|---|---|---|---|---|
| 0 | Başlatma | Product Lead | Kanala yazılan özellik mesajı + thread'de "Başlat" | `durum.md` |
| 1 | Araştırma | Araştırma ajanı | Özellik tanımı | Benchmark artifact'i |
| 2 | Tasarım | Tasarım ajanı | Onaylı araştırma + DESIGN.md | Tasarım artifact'i |
| 3 | PRD | PRD ajanı | Onaylı araştırma + tasarım | PRD dosyası |
| 4 | Prototip | Prototip ajanı | Onaylı tasarım + PRD | Prototip artifact'i |
| 5 | CTO değerlendirmesi | Manuel (şimdilik boş) | Onaylı PRD + prototip | Yalnızca onay |
| 6 | Jira | Jira ajanı | Bütün onaylı çıktılar | STB'de Epic + Story'ler |

Her aşamanın onay kapısı yukarıdaki gibidir. 6. aşamadan sonra Koordinatör thread'e Jira linklerini yazar ve özelliği "Tamamlandı" yapar.

## Slack protokolü

- Kanal ve kişi kimlikleri `ayarlar.md`'de.
- Koordinatör'ün her mesajı `:robot_face: *Ürün Akışı*` ile başlar ve hiçbir zaman "Onay", "Revize" ya da "Başlat" kelimesiyle başlamaz. (Slack mesajları İmge'nin hesabından gider; insan cevaplarını ayırmak için bu kural şart.)
- Bütün konuşma özellik mesajının thread'inde döner; kanala ayrıca mesaj atılmaz.
- Onay isterken kişiyi `<@ID>` ile etiketle ve cevap biçimini hatırlat: `Onay` ya da `Revize: <yorum>`.
