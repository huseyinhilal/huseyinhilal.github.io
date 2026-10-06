# Huseyin Hilal Blog

Hugo ile yazılmış kişisel blog + geliştirici günlüğü.
Canlı adres: https://huseyinhilal.github.io/

## Nasıl çalışıyor?

Tek repo, tek dal (`main`). Bu repoda sadece **kaynak** var (markdown yazılar, ayarlar, tema).
`main`'e push ettiğinde `.github/workflows/hugo.yaml` çalışır: GitHub siteyi kendi sunucusunda
derler ve yayınlar. `public/` klasörü repoya **girmez** (submodule yok, ikinci repo yok).

```
content/
  posts/      -> öğrendiklerin (makale tarzı yazılar)
  journal/    -> günlük kayıtların
  about.md    -> Hakkımda sayfası
archetypes/   -> "hugo new" komutunun kullandığı şablonlar
themes/hugo-blog-awesome/  -> tema (v1.21.0, repoya doğrudan kopyalandı)
hugo.toml     -> site ayarları
```

## Günlük kullanım

Terminali bu klasörde aç (VS Code'da: Terminal > New Terminal).

**Yeni yazı:**
```
hugo new content posts/sql-joins.md
```

**Yeni günlük kaydı:**
```
hugo new content journal/2026-10-06.md
```

**Yazarken önizleme** (http://localhost:1313 adresinden, kaydettikçe yenilenir):
```
hugo server
```
`hugo server` diske bir şey yazmaz, sadece önizlemedir. Ctrl+C ile kapatılır.

**Yayınlama:**
```
git add .
git commit -m "yeni yazı: sql joins"
git push
```
1-2 dakika sonra site güncellenir. Durumu GitHub'da **Actions** sekmesinden izleyebilirsin.

## Front matter (yazının başlığı)

```
+++
date = '2026-10-06T21:00:00+03:00'
draft = false
title = 'SQL Joins'
tags = ['sql', 'database']
+++
```

- `draft = true` yaparsan yazı yayınlanmaz (`hugo server -D` ile yerelde görürsün).
- `date` gelecekte bir tarihse yazı o tarihe kadar görünmez.
- Repo herkese açık olduğu için taslaklar da GitHub'da okunabilir.

## Sık karşılaşılanlar

| Sorun | Çözüm |
|---|---|
| Yazı sitede yok | `draft = true` mu? Tarih gelecekte mi? Actions yeşil mi? |
| Actions kırmızı | Actions > başarısız iş > "Build" adımındaki hata mesajını oku |
| Site 404 | Settings > Pages > Source = **GitHub Actions** mı? Repo public mi? |
| Kod blokları renksiz | ```` ```java ```` gibi dil adı yazdığından emin ol |
