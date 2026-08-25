# Haftalık Log

> 90. günde bu dosya senin en değerli varlığın olacak. Hem retro, hem mülakat
> malzemesi, hem de planın kayıp kaymadığının tek göstergesi.
>
> Her hafta sonu 5 satır. Uzun yazma. **Boş bırakma.**

**Format:**
```
## Hafta N — tarih aralığı
- **Yaptım:** somut çıktı, link
- **Kırıldı:** ne çalışmadı, neden
- **Öğrendim:** tek cümle, gerçek bir şey
- **Gelecek hafta:** tek öncelik
- **Kapı durumu:** blok hedefine göre nerede
- **Saat:** Build _ / Bridge _ / Write _ / Market _
```

---

## Hafta 1 — 2026-08-25 → 2026-08-31

- **Yaptım:** Repo kuruldu ve public olarak yayınlandı:
  [the-weekly-loop](https://github.com/hakansagiroglubusiness/the-weekly-loop).
  17 dosya, 3 commit. Strateji dosyaları yazıldı (skill-gap, roadmap-90d,
  target-roles). Hedef rol kararı verildi: **AI Operations Manager / Growth
  System Architect** — Growth Engineer değil, çünkü ikincisi gerçek kod ve
  medyan 3.7 yıl mühendislik deneyimi istiyor.
- **Kırıldı:**
  1. `MIGRATION.md` müşteri adları içeriyordu (Blue Diamond, D Diamond, PlanB,
     Medart) ve public push'ta sızacaktı. Gitignore'a alındı. **Ders:** gizlilik
     kontrolü her push'tan önce çalışmalı, bir kez değil.
  2. Mevcut Claude skill'leri diskte değil, workspace tarafında. Export yolu
     H2'de çözülecek.
  3. İlk isim (`growthos`) terk edildi. Repo `the-weekly-loop` oldu; ayrı ürün
     markası (`growth-os`) tamamen düşürüldü — iki benzer isim yerine bir isim.
- **Öğrendim:** Gerçek work-from-anywhere ilanları tüm remote ilanların
  %5'inden az. "Remote" yazan çoğu ilan aslında "remote — US only". Coğrafi
  filtre baştan kurulmazsa aylarca cevapsız başvuru yapılır ve bu yetersizlik
  sanılır.
- **Gelecek hafta:** Skill export + ilk iki skill'in markadan arındırılması.
- **Kapı durumu:** Gün 30 kapısı — 4 maddeden 0'ı tamam (repo canlı ✓ ama
  plugin, vaka ve postlar bekliyor). Hafta 1'in 5 maddesinden 2'si bitti.
- **Saat:** Build 1.5 / Bridge 0 / Write 1.0 / Market 0.5

**Hafta 1 ek çıktılar:**
- Skill-gap kalibre edildi. Dört eksenden üçü ilk tahminin altına indi.
  En önemlisi: 1-3 yıl deneyim, `AI Operations Manager` hedefini erişilemez
  kılıyor. Hedef unvanlar bir kademe indirildi, yön korundu.
- Tier A'daki 11 şirket araştırıldı. **Camunda Türkiye'de EOR üzerinden
  istihdam ediyor (ismen doğrulandı).** Xapo Bank'ta kalibre edilmiş hedef
  unvanla birebir örtüşen canlı ilan var. GitLab elendi — ülkede tüzel
  kişilik şartı.
- GitHub profil README'si yayınlandı.

- **Incident yazıldı.** Haftalık raporda bir kampanyanın tüm metrikleri
  yanlıştı. Muhtemel kök neden: kampanya isim eşleşmesi — isim, platform
  satırlarını kampanyaya bağlayan anahtar. İsim kayınca aritmetik yanlış
  satırlarda çalışıyor ve tertemiz, kendinden emin, tamamen uydurma bir sayı
  üretiyor. **Uyarı vermedi.** Sunum sırasında, canlı yakalandı. Sonrasında
  hiçbir şey değişmedi.
- **Plan değişikliği:** Guardrail çalışması Hafta 7'den Hafta 2'ye çekildi.
  Hatanın şeklini artık biliyoruz; `weekly-report` skill'i mutabakat ve tamlık
  kontrolüyle doğacak, sonradan eklenmeyecek.

**Kalan (bu hafta içinde):**
- [ ] Bio'nun GitHub ayarlarına yapıştırılması
- [ ] LinkedIn linki + şehir bilgisinin profile eklenmesi

---
