# Beceri Boşluk Analizi

> Canlı dosya. Her 30 günde bir yeniden puanla, eski puanı silme — üstüne yaz ki
> ilerleme görünsün. Puanlar özdeğerlendirme; dışarıdan doğrulanana kadar hipotez.

**Hedef rol:** AI Operations Manager / Growth System Architect (uluslararası, remote)
**Başlangıç:** 2026-08-25

---

## Puan tablosu

| # | Eksen | Gün 0 | Gün 30 | Gün 60 | Gün 90 | Hedef |
|---|---|---|---|---|---|---|
| 1 | Growth domain | 8 | | | | 8 |
| 2 | AI orkestrasyonu | 6 | | | | 9 |
| 3 | Veri akıcılığı | 3 | | | | 7 |
| 4 | Kod okuryazarlığı | 1 | | | | 5 |
| 5 | Deneycilik | 4 | | | | 7 |
| 6 | Kamusal kanıt | 0 | | | | 7 |
| 7 | Piyasa mekaniği | 2 | | | | 6 |

---

## 1. Growth domain — 8/10 → 8/10

**Var olan:** Paid acquisition (Meta, Google, TikTok), creative testing, kampanya
yapısı, breakeven/TBM hesabı, kâr metrikleri (MER, ROAS, CM2, LTV:CAC), e-ticaret
funnel'ı, GA4 raporlama.

**Boşluk:** Yok. Bu senin sermayen.

**Yapılacak:** Hiçbir şey öğrenme. Sadece **görünür kıl**. Bu eksende harcanan her
saat, 6. eksene harcanmalı.

---

## 2. AI orkestrasyonu — 6/10 → 9/10

**Var olan:** Günlük Claude Code kullanımı, çalışan pazarlama skill'leri, bağlı
MCP'ler (Meta Ads, TikTok Ads, Dataslayer, GA4, Drive, Vercel), çok adımlı iş
akışlarını agent'a devretme.

**Boşluk — bu bir zanaat boşluğu, bilgi boşluğu değil:**

- **Eval yok.** Skill'in ne zaman yanlış cevap verdiğini ölçmüyorsun. Sadece
  gözle bakıp "iyi görünüyor" diyorsun. Bu, üretim sistemi değil.
- **Guardrail yazılı değil.** Kafanda var ama dokümante edilmemiş. Agent'ın
  neyi asla yapmaması gerektiği, hangi kararın insan onayı istediği belirsiz.
- **Versiyonlama yok.** Skill değişince neyin bozulduğunu bilmiyorsun.
- **Hata davranışı tanımsız.** Veri gelmediğinde, API patladığında, sayı
  saçmaladığında agent ne yapıyor? Muhtemelen uyduruyor.

**Yapılacak (H7):** Her skill'e eval vakası + guardrail bölümü + bilinen hata
modu ekle. Bu, mülakatta "prompt yazan biri" ile "sistem kuran biri" arasındaki
farkı anlatan tek somut şey.

---

## 3. Veri akıcılığı — 3/10 → 7/10

**Var olan:** GA4 arayüzü, platform panelleri, Dataslayer üzerinden veri çekme,
metrik yorumlama.

**Boşluk:** Ham veriye kendi başına ulaşamıyorsun. Birinin sana raporu hazırlaması
gerekiyor. SQL yok, veri modeli anlayışı yüzeysel, atıf modellemesi kara kutu.

**Neden kritik:** SQL, kod dünyasına açılan **en kısa ve en yüksek getirili**
kapı. Mülakatta doğrudan soruluyor. Python'dan önce gelir, çünkü:
(a) sözdizimi küçük, (b) her gün kullanacağın veriyle çalışıyorsun,
(c) tek başına iş çıkarır.

**Ölçüt (H6 sonu):** "Geçen ayın kohortunun 30 günlük retention'ını çıkar"
sorusunu yardımsız, tek sorguda cevapla. JOIN, CTE, window function, date
truncation rahat olmalı.

**Yapma:** Soyut SQL kursu. **Yap:** Kendi GA4 / reklam verinde gerçek soru sor.

---

## 4. Kod okuryazarlığı — 1/10 → 5/10

**Boşluk:** git yok, terminal yüzeysel, Python/JS okunamıyor, deploy bilinmiyor.

**Hedef bilinçli olarak 5 — ve bu bir strateji, tembellik değil.**

90 saatte mühendis olunmuyor. Ama şuna ulaşılıyor:

- git ile çalışma (commit, branch, PR okuma) — **zorunlu**, repo halka açık
- Bir Python scriptini **okuyup ne yaptığını anlamak** ve küçük düzeltme yapmak
- Hata mesajını okuyup ne dediğini çözmek
- Bir şeyi deploy etmek (Vercel zaten bağlı)

Yazar olmana gerek yok. **Okuyup düzeltebilmen** yeterli — çünkü kodu Claude
yazıyor, senin işin onu yargılamak. Bu tam olarak hedef rolün tanımı.

---

## 5. Deneycilik — 4/10 → 7/10

**Var olan:** Reklam tarafında A/B testi, creative testing, bütçe tahsisi.

**Boşluk:** Ajans dünyası akuizisyon ağırlıklı. Ürün-içi growth ayrı bir dil ve
**mülakatta buradan elenirsin**:

- İstatistiksel anlamlılık, güç analizi, örneklem büyüklüğü, peeking problemi
- Aktivasyon / retention / North Star metriği kurma
- Kohort analizi, funnel analizi, feature adoption
- Akuizisyon dışı büyüme kaldıraçları (onboarding, referral, expansion)

**Yapılacak (H9):** Ajans dilinden ürün diline çeviri. "ROAS" diyen biri ile
"D30 retention" diyen biri farklı iki insan gibi duyuluyor; ikisini de konuşman
gerekiyor.

---

## 6. Kamusal kanıt — 0/10 → 7/10

**En büyük fiili boşluk. En hızlı kapanan da bu.**

Şu an dışarıdan bakan biri için sen "Türkiye'de ajansta çalışan bir
performansçısın". Yaptığın AI-native işin **sıfır izi var**: GitHub yok, yazılı
vaka yok, açık kaynak artefakt yok, İngilizce üretim yok.

Yetenek boşluğun yok — **kanıt boşluğun var.** Bu ikisi çok farklı problemler ve
çok farklı çözümleri var. Seninki 30 günde kapanabilir çünkü yeni bir şey
öğrenmeni gerektirmiyor.

**Yapılacak (H1-H4):** Public repo, kurulabilir plugin, 1 vaka çalışması,
İngilizce postlar.

---

## 7. Piyasa mekaniği — 2/10 → 6/10

**Boşluk:** Hedef şirket listesi yok, uluslararası ağ yok, JD okuma alışkanlığı
yok, mülakat pratiği yok, konumlanma cümlesi yok.

**Özel kısıt:** Türkiye'den başvuruyorsun. ABD şirketlerinin çoğu ülke dışına
istihdam yapmıyor. Hedef listesi **"remote"** değil, **"remote — worldwide"**
veya EOR ile çalışan şirketlerle sınırlı olmalı. Bu, listeyi ciddi şekilde
daraltıyor ve baştan filtrelenmezse aylar boşa gider.

**Yapılacak:** `target-roles.md` — her satırda şirket, rol, coğrafi politika,
kaynak link, senin hangi kanıtınla eşleştiği.
