# خط مبنای ERPNext برای ASOUD

## تصمیم نسخه

- شاخه اصلی پروژه: ERPNext v15
- نسخه مبنای اولیه برای محیط آزمایشی: `v15.117.0`
- Frappe و ERPNext باید روی major یکسان (`version-15`) باشند.
- تغییرات حسابداری ایرانی در مخزن `frappe-erp-next-2` نگهداری می‌شود و کد هسته ERPNext مستقیماً ویرایش نمی‌شود.

## نقش مخزن

- `frappe-erp-next-2`: افزونه مستقل `asoud_erp`

برای هسته ERPNext مخزن اختصاصی نگهداری نمی‌شود؛ سورس رسمی `version-15`
مستقیماً در محیط Bench دریافت و نسخه دقیق آن در پیکربندی استقرار Pin می‌شود.

## نکته استقرار

دموی سریع `pwd.yml` در Frappe Docker برای نصب افزونه سفارشی مناسب نیست. برای ASOUD باید
محیط توسعه Bench یا Image سفارشی Frappe Docker ساخته شود تا `asoud_erp` هنگام build نصب شود.

## ترتیب نصب آزمایشی

```bash
bench get-app --branch version-15 erpnext https://github.com/frappe/erpnext
bench --site asoud.localhost install-app erpnext
bench get-app /path/to/frappe-erp-next-2
bench --site asoud.localhost install-app asoud_erp
bench --site asoud.localhost migrate
```

قبل از استقرار عمومی، نسخه‌های دقیق Frappe و ERPNext در فایل استقرار Pin می‌شوند.
