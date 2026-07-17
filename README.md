# مستندات ASOUD ERP

این مخزن مرجع معماری، قرارداد API، تصمیم‌های فنی و وضعیت واقعی پروژه ASOUD ERP است.

## اجزای سامانه

| مخزن | مسئولیت |
|---|---|
| `mohamadi121/flutter-asoud-erp` | کلاینت Flutter، رابط فارسی و مدیریت وضعیت |
| `mohamadi121/frappe-erp-next-2` | افزونه مستقل Frappe با نام `asoud_erp` و API اختصاصی |
| `mohamadi121/frappe-erp-next-1` | آینه بدون تغییر هسته رسمی ERPNext |
| `mohamadi121/flutter-asoud-erp-doc` | همین مستندات |

هسته ERPNext در پروژه اختصاصی تغییر نمی‌کند. تمام نیازهای ASOUD در افزونه `asoud_erp` قرار می‌گیرند تا ارتقای ERPNext مستقل باقی بماند.

## نسخه مبنا

- ERPNext: شاخه رسمی `version-15`
- Snapshot مبنا: ERPNext `15.117.0`، commit `fb2a4e5f98c8e900648dd4d55de8b91b41a0dab3`
- Python: `>=3.10`
- Frappe: `>=15.40.4,<16.0.0`

## وضعیت صداقت محصول

این checkpoint یک پایه فنی است، نه یک ERP منطبق با تمام مقررات ایران. موارد مالیاتی، سامانه مؤدیان، حقوق و بیمه، دفاتر قانونی و تأیید حسابداری هنوز در دامنه بعدی‌اند و پیش از انتشار باید توسط حسابدار و مشاور مالیاتی ایرانی تأیید شوند.

## فهرست

- [معماری](docs/architecture.md)
- [مسئولیت مخزن‌ها](docs/repositories.md)
- [مدل حساب‌ها](docs/accounting-model.md)
- [قرارداد API v1](docs/api-v1.md)
- [امنیت و احراز هویت](docs/security.md)
- [راه‌اندازی توسعه](docs/development.md)
- [ارتقای ERPNext](docs/upstream-upgrades.md)
- [راهبرد تست](docs/testing.md)
- [نقشه راه و وضعیت](docs/roadmap.md)
- [تصمیم‌های معماری](docs/adr)

پوشه `ASOUD-ERP-checkpoint-01` صرفاً سابقه طراحی اولیه است و مرجع پیاده‌سازی جاری محسوب نمی‌شود.
