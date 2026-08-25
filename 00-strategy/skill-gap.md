# Beceri Boşluk Analizi

> Canlı dosya. Her 30 günde bir yeniden puanla, eski puanı silme.
> Puanlar özdeğerlendirme; dışarıdan doğrulanana kadar hipotez.

**Başlangıç:** 2026-08-25
**Kalibrasyon:** 2026-08-25 (Hafta 1)

---

## Puan tablosu

| # | Eksen | İlk tahmin | **Kalibre** | Gün 30 | Gün 60 | Gün 90 | Hedef |
|---|---|---|---|---|---|---|---|
| 1 | Growth domain | 8 | **6** | | | | 7 |
| 2 | AI orkestrasyonu | 6 | **5** | | | | 8 |
| 3 | Veri akıcılığı | 3 | **3** | | | | 7 |
| 4 | Kod okuryazarlığı | 1 | **1** | | | | 5 |
| 5 | Deneycilik | 4 | **2** | | | | 5 |
| 6 | Kamusal kanıt | 0 | **0** | | | | 7 |
| 7 | Piyasa mekaniği | 2 | **2** | | | | 6 |

**Kalibrasyonda ne değişti:** Dört eksenden üçü ilk tahminimin altına indi.
Bu kötü haber değil — yanlış puandan yapılan plan, düşük puandan yapılan
plandan daha tehlikeli. Aşağıda her düzeltmenin gerekçesi var.

---

## ⚠️ Kalibrasyonun en önemli sonucu: kıdem hedefi düştü

**Veri:** 1-3 yıl deneyim, küçük-orta ölçekli hesaplar, ekip yönetimi yok.

`AI Operations Manager` ve `Growth System Architect` ilanları tipik olarak 4+ yıl
ve ekip/sistem sorumluluğu istiyor. Bu unvanları 1-3 yıllık bir profille hedeflemek,
çoğu başvurunun okunmadan elenmesi demek.

**Düzeltilmiş hedef:** bir kademe aşağı, ama aynı yönde:

| Eski hedef | Yeni hedef |
|---|---|
| AI Operations Manager | Growth Marketing Manager (AI odaklı ilanlar) |
| Growth System Architect | Marketing Operations / Growth Operations (specialist) |
| — | Performance Marketing Manager, AI-native şirketlerde |

**Ama asıl kaldıraç değişmedi — hatta güçlendi.**

1-3 yıllık bir profilde referans ve unvan seni taşımaz. Seni taşıyacak tek şey
**kanıt**. Ve şu anda AI-native growth sisteminin kamusal kanıtına sahip olan
insan sayısı — herhangi bir kıdem seviyesinde — çok az. Arbitraj burada.

Bu, 12 aylık bir yol. İlk uluslararası rol muhtemelen büyük bir sıçrama değil,
yatay ya da yarım kademe bir hamle olacak. Sıçrama ikinci rolde gelir.
**6. eksen bu yüzden planın merkezinde.**

---

## 1. Growth domain — 6/10 → 7/10

**Var olan:** Paid acquisition (Meta, Google, TikTok), creative testing, kampanya
yapısı, breakeven/TBM hesabı, kâr metrikleri, GA4 raporlama. 1-3 yıl, çoklu marka.

**Neden 8 değil 6:** İlk tahminim daha uzun bir deneyim varsayıyordu. 1-3 yıl ve
küçük-orta hesaplar sağlam bir temel ama "domain uzmanı" değil. Büyük bütçede
karar vermiş biriyle aynı odada farkedilir.

**Yapılacak:** Aktif çalışma yok. Bu eksen işini yaptıkça kendiliğinden büyüyor.
Buraya ayrılacak her saat 6. eksene gitmeli.

---

## 2. AI orkestrasyonu — 5/10 → 8/10

**Var olan:** Günlük Claude Code kullanımı, çalışan pazarlama skill'leri, bağlı
MCP'ler, çok adımlı iş akışlarını agent'a devretme.

**Neden 6 değil 5:** **Agent'ın ürettiği yanlış bir çıktı müşteriye ulaştı.**
Bu, sistemde doğrulama katmanı olmadığının kanıtı. Skill'leri yazabiliyorsun ama
yanlış olduklarını yakalayacak mekanizman yok — ve bu, orkestrasyon becerisinin
tam da ölçüldüğü yer.

**Ama bu olayın ikinci bir yüzü var ve orası çok değerli.**

Çoğu insanın "AI ile şunu yaptım" hikâyesi var. Neredeyse hiç kimsenin
"AI şunu yanlış yaptı, müşteriye gitti, şöyle düzelttim, artık şu guardrail var"
hikâyesi yok. İkincisi çok daha zor taklit edilir ve yargı kapasitesini
gösteren tek şey.

**Plan değişikliği:** Case 02 artık Hafta 8'in otomasyonunu beklemiyor.
Elinde zaten gerçek bir olay var. `40-automations/incidents.md`'ye **bu hafta**
yazılmalı — detaylar her geçen gün siliniyor.

**Boşluk:**
- Eval yok — skill'in ne zaman yanlış olduğunu ölçmüyorsun
- Guardrail yazılı değil — kafanda var, dokümante değil
- Versiyonlama yok — skill değişince neyin bozulduğunu bilmiyorsun
- Hata davranışı tanımsız — veri gelmeyince agent muhtemelen uyduruyor

---

## 3. Veri akıcılığı — 3/10 → 7/10

**Var olan:** GA4 arayüzü, platform panelleri, Dataslayer'ın çektiği hazır tablolar.

**Boşluk:** Ham veriye hiç inmemişsin. Sheets'te ciddi modelleme de yok. Yani
sıfırdan başlıyoruz — bu, Hafta 5-6'nın planlandığı gibi tam iki hafta süreceği
anlamına geliyor, kısaltma şansı yok.

**Neden yine de SQL, Python'dan önce:** sözdizimi küçük, her gün kullandığın
veriyle çalışıyor, tek başına iş çıkarıyor ve mülakatta doğrudan soruluyor.

**Ölçüt (H6 sonu):** "Geçen ayın kohortunun D30 retention'ı" — yardımsız, tek sorgu.

---

## 4. Kod okuryazarlığı — 1/10 → 5/10

**Boşluk:** git (artık başladı), terminal, Python/JS okuma, deploy.

**Hedef bilinçli olarak 5.** 90 saatte mühendis olunmuyor. Ulaşılacak yer:
git ile çalışmak, bir scripti okuyup ne yaptığını anlamak ve küçük düzeltme
yapmak, hata mesajını çözmek, bir şeyi deploy etmek.

Kodu Claude yazıyor; senin işin onu **yargılamak**. Hedef rolün tanımı bu.

---

## 5. Deneycilik — 2/10 → 5/10

**Veri:** Tamamen akuizisyon tarafındasın. Trafik siteye gidiyor, sonrası senin
alanın değil. Landing page/CRO deneyimi bile yok.

**Neden 4 değil 2:** Reklam içi A/B testi yapmak ile ürün deneyi tasarlamak
farklı iki beceri. İlki elinde var, ikincisi yok.

**Neden hedef 7 değil 5:** 2'den 7'ye tek blokta çıkmak gerçekçi değil. 5, "dili
konuşabiliyor ve doğru soruyu sorabiliyor" seviyesi — mülakatta elenmemeye yeter,
uzman olmaya yetmez. Gerisi ikinci 90 günde.

**Bu, planın en zayıf halkası ve mülakatta en çok elendiğin yer olacak.**
Ürün şirketleri "ROAS" değil "D30 retention" konuşuyor. Sen şu an sadece ilkini
konuşuyorsun.

**Plan değişikliği:** Hafta 9 tek başına yetmez. Hafta 5-6'daki SQL çalışmasının
soruları **kohort ve retention üzerinden** seçilecek — böylece iki eksen aynı
saatte ilerler. Öğrenme değil, soru seçimi değişiyor.

---

## 6. Kamusal kanıt — 0/10 → 7/10

**En büyük fiili boşluk ve kalibrasyondan sonra planın en kritik ekseni.**

1-3 yıllık bir profilde unvan ve referans seni taşımaz. Kanıt taşır. Bu eksen
artık "iyi olur" değil, **stratejinin kendisi**.

**İlerleme:** Repo public.
→ https://github.com/hakansagiroglubusiness/the-weekly-loop

**Kalan:** Skill seti, 2 vaka çalışması, düzenli İngilizce üretim.

---

## 7. Piyasa mekaniği — 2/10 → 6/10

**Boşluk:** Hedef şirket listesi doğrulanmadı, uluslararası ağ yok, JD okuma
alışkanlığı yok, mülakat pratiği yok.

**Özel kısıt:** Türkiye'den başvuruyorsun ve gerçek work-from-anywhere ilanları
tüm remote ilanların %5'inden az. Liste "remote" diye değil, **coğrafi politikaya
göre** kurulur.

**İkinci kısıt (kalibrasyondan yeni):** 1-3 yıl deneyimle ilan havuzu zaten dar.
Coğrafi filtre + kıdem filtresi birlikte çok az ilan bırakıyor. Bu yüzden
**başvuru tek kanal olamaz** — build in public ve doğrudan insan teması,
başvuru kadar önemli.
