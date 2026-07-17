# راه‌اندازی توسعه

## Backend

پیش‌نیازها برای baseline فعلی:

- Python 3.14 یا جدیدتر
- Frappe 16.21 تا قبل از 17
- ERPNext 15.117 یا patch سازگار در major 15

```bash
bench get-app https://github.com/mohamadi121/frappe-erp-next-2.git
bench --site your-site.local install-app asoud_erp
bench --site your-site.local migrate
```

پس از نصب، تنظیم کدینگ باید برای هر Company با کاربر مجاز ایجاد شود.

## Flutter

```bash
flutter pub get
flutter analyze
flutter test
flutter run --dart-define=ERPNEXT_BASE_URL=https://erp.example.com
```

هیچ credentialی از خط فرمان build وارد نمی‌شود. کاربر داخل اپ وارد می‌شود.

## محیط‌ها

- development و staging باید سایت‌های مجزا داشته باشند.
- تغییر Backend ابتدا روی staging با backup قابل بازیابی تست می‌شود.
- نسخه Core، Frappe app و Flutter در release note با هم ثبت می‌شوند.
