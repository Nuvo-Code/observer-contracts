# Observer Contracts

 **Observer Contracts**  
Bu repo, **Observer Platformu** için domain event mesajlarının **standartlarını** içerir.  
Laravel (publisher) ve Python (consumer) servisleri arasında **ortak iletişim dili** sağlamak amacıyla tasarlanmıştır.

---

##  Amaç

- Tüm domain event’leri için **tek bir kaynaktan yönetilen** JSON şemalar
- **Sürümleme (v1, v2, …)** desteği → schema evrimine hazır yapı
- Laravel, Python veya başka herhangi bir dilde **bağımsız tüketim** imkanı
- **Idempotent event işleme** için kararlı `event_id` alanı
- **GitHub Pages** ile şemaların web üzerinden erişilebilir olması

---

## Envelope

Her event ortak bir **envelope** içinde taşınır:

```json
{
  "event_id": "018fb94e-9c86-7c2a-bf5f-3a7f6b8d9a21",
  "occurred_at": "2025-09-06T08:00:00Z",
  "version": 1,
  "type": "project.created",
  "data": { ... }
}
```


### Evrim (Versioning)

* v1: İlk sürüm (şu anki hali). 
* v2+: Yeni alanlar eklendiğinde → şema genişler ama mevcut tüketiciler kırılmaz.
* Kural: Alan kaldırma veya tip değiştirme yok, yalnızca ekleme/opsiyonel yapma var.

## GitHub Pages
> Şemalara ve örneklere web üzerinden erişebilirsin:
Bu repo GitHub Actions ile otomatik olarak Pages’e deploy edilir.
[Observer Contracts](https://nuvo-code.github.io/observer-contracts).



