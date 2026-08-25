# 90 Günlük Yol Haritası

**Başlangıç:** 2026-08-25 · **Bitiş:** 2026-11-23
**Bütçe:** ~7 saat/hafta × 12 hafta ≈ 84 saat

---

## Haftalık ritim

Her hafta aynı beş blok. Sırayı değiştirme, blokları birleştirme.

| Blok | Süre | İş |
|---|---|---|
| **Build** | 2.0s | Skill / agent / otomasyon — eline geçen bir şey |
| **Bridge** | 2.0s | SQL → kod okuryazarlığı |
| **Write** | 1.5s | Vaka çalışması / İngilizce post |
| **Market** | 1.0s | JD analizi, outreach, network |
| **Log** | 0.5s | `weekly-log.md` + haftanın gözden geçirmesi |

**Kural:** Build saatleri öğrenmeye kaymaz. Öğrenme Bridge bloğunda yapılır.
Bu ikisinin karışması en yaygın başarısızlık biçimi — sürekli hazırlanıp hiç
üretmemek.

---

## BLOK 1 — Gün 1-30: Kanıt Üret

> Bu blokta neredeyse hiç yeni şey öğrenmiyorsun. Elindekini görünür kılıyorsun.
> Tek hedef: 30. günün sonunda dışarıdan bakan biri ne yaptığını görebilsin.

### Hafta 1 — Temel
- [x] `the-weekly-loop` repo iskeleti kur
- [x] git init + GitHub'a **public** push — [repo](https://github.com/hakansagiroglubusiness/the-weekly-loop)
- [x] `skill-gap.md` puanlarını birlikte kalibre et
- [x] `target-roles.md` — Tier A 11 şirket araştırıldı, coğrafi politika filtresiyle
- [x] GitHub profili: README yayında; bio elle yapıştırılacak
- [x] **Mevcut incident'ı yaz** — [incidents.md](../40-automations/incidents.md).
      Kök neden: kampanya isim eşleşmesi. Uyarı vermedi, sunumda yakalandı,
      sonrasında hiçbir şey değişmedi.

### Hafta 2 — Markadan arındırma
> **Incident'tan gelen plan değişikliği:** guardrail çalışması Hafta 7'ye
> planlanmıştı. Ama artık hatanın tam şeklini biliyoruz, tahmin etmiyoruz.
> `weekly-report` skill'i mutabakat ve tamlık kontrolüyle **doğar** — sonradan
> eklenmez. Bilinen bir hatayı yazılmamış bir skill'e taşımak anlamsız.

- [ ] Mevcut skill'leri export et → `20-skills/`
- [ ] `weekly-report`'u marka-bağımsız hale getir
- [ ] **Mutabakat kontrolü:** rapor toplamı ile platform toplamı eşleşmiyorsa
      rapor üretilmez, durur
- [ ] **Tamlık kontrolü:** beklenen her kampanya raporda çıktı mı
- [ ] **Kaynak çözülmezse uydurma yok:** eksik veri "eksik" olarak raporlanır
- [ ] İkinci skill migrate edilir
- [ ] Temiz kurulum testi: başka bir dizinde çalışıyor mu

### Hafta 3 — Plugin v1
- [ ] Kalan 2 skill migrate edilir (toplam 4)
- [ ] Plugin paketleme + kurulum talimatı
- [ ] `README.md` son hali
- [ ] İlk İngilizce launch postu (LinkedIn + X)

### Hafta 4 — İlk vaka
- [ ] Case 1 "The Handover" yazılır
- [ ] Sistem diyagramı
- [ ] Anonimleştirme kontrolü (marka adı yok, mutlak rakam yok)
- [ ] Yayın + LinkedIn profili güncellemesi

**🚪 Gün 30 kapısı**
Public repo canlı · Plugin kurulabilir · 1 vaka yayında · 3+ İngilizce post

---

## BLOK 2 — Gün 31-60: Teknik Köprü + Sistemleştirme

### Hafta 5 — SQL temel
> **Kalibrasyon notu:** sorular bilerek kohort ve retention üzerinden seçilecek.
> Böylece 3. eksen (veri) ve 5. eksen (deneycilik) aynı saatte ilerler. Öğrenilen
> şey değişmiyor, sadece hangi soruyu sorduğun değişiyor.

- [ ] SELECT / WHERE / GROUP BY / JOIN — kendi GA4 verinde
- [ ] 10 gerçek soru yaz, 10 sorguyla cevapla — en az 5'i kohort/retention
- [ ] Her sorguyu `90-lab/sql/` altına kaydet

### Hafta 6 — SQL derinlik
- [ ] CTE, window function, date truncation
- [ ] Kohort sorgusu
- [ ] **Ölçüt:** "Geçen ayın kohortunun D30 retention'ı" — yardımsız, tek sorgu

### Hafta 7 — Eval + guardrail
- [ ] Her skill için 5 eval vakası (girdi + bilinen doğru çıktı)
- [ ] Skill'lerin yanlış cevap verdiği girdileri bul ve yaz
- [ ] Guardrail'leri dokümante et: neyi asla yapmamalı, ne insan onayı ister
- [ ] `10-playbooks/` — ilk playbook yazılır

### Hafta 8 — Gözetimsiz çalışan bir şey
- [ ] Zamanlanmış agent: haftalık raporu kendi çeksin, yazsın, göndersin
- [ ] 7 gün dokunmadan izle
- [ ] Kırılan her şeyi `40-automations/incidents.md`'ye yaz
- [ ] Case 2 taslağı bu incident'larla **Hafta 1'de yazılan olay** birleştirilerek çıkar

**🚪 Gün 60 kapısı**
SQL bağımsız yazılıyor · Skill'lerde eval var · 1 otomasyon gözetimsiz çalıştı · Case 2 taslak

---

## BLOK 3 — Gün 61-90: Piyasaya Çıkış

### Hafta 9 — Case 2 + ürün dili
> **Kalibrasyon notu:** 5. eksen 2/10'dan başlıyor, 4'ten değil. Bu hafta tek
> başına yetmez; Hafta 5-6'daki SQL sorularının kohort/retention seçilmesi bu
> yüzden. Hedef 7 değil **5** — "dili konuşabiliyor ve doğru soruyu soruyor"
> seviyesi. Uzmanlık ikinci 90 günde.

- [ ] Case 2 "What the agent got wrong" yayınlanır
- [ ] A/B istatistiği: anlamlılık, örneklem büyüklüğü, peeking problemi
- [ ] Aktivasyon / retention / North Star — ürün growth dili
- [ ] Ajans metriklerini ürün metriklerine çeviren bir not yaz
      (ROAS → CAC → LTV → payback → D30 retention zinciri)

### Hafta 10 — Hedefleme
- [ ] Hedef liste 20 → 40
- [ ] Her JD'yi kır: her gereksinim için repodan bir kanıt linki
- [ ] Kanıtı olmayan gereksinimleri işaretle — bunlar sonraki 90 günün planı
- [ ] Konumlanma cümlesini JD diline göre keskinleştir

### Hafta 11 — Başvuru hattı
- [ ] Haftada 5 **hedefli** başvuru (toplu değil, her biri o şirkete yazılmış)
- [ ] Haftada 2 insan konuşması (soğuk mesaj, topluluk, eski bağlantı)
- [ ] Her başvuruyu `target-roles.md`'de takip et

### Hafta 12 — Prova + retro
- [ ] Mülakat provası: sistem tasarımı anlatımı, vaka sunumu
- [ ] "Agent neyi yapamaz?" sorusuna hazırlıklı cevap
- [ ] `skill-gap.md` yeniden puanlanır
- [ ] 90 günün retrosu + sonraki 90 günün planı

**🚪 Gün 90 kapısı**
2 vaka yayında · Plugin'in dış kullanıcısı var · 15+ hedefli başvuru · 5+ konuşma · SQL 7/10

---

## Erken uyarı işaretleri

Bunlardan biri görülürse durup yeniden dengele:

| İşaret | Ne anlama geliyor |
|---|---|
| Build saatleri sürekli öğrenmeye kayıyor | Kaçış davranışı. Üretmek öğrenmekten daha korkutucu geliyor. |
| Hafta 3'te hâlâ hiçbir şey public değil | Blok 1 kaydı. Blok 2 ve 3 bunun üstüne kurulu — plan çöker. |
| Vaka çalışması sürekli "biraz daha iyileştireyim"de | Mükemmeliyetçilik. Yayınla, sonra düzelt. |
| Başvuru yok ama liste büyüyor | Hazırlık, eylemin yerine geçiyor. |
| `weekly-log.md` 2 hafta boş | Sistem takip edilmiyor. Her şey burada görünür. |
