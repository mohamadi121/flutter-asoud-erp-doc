# راه‌اندازی توسعه

## Backend

پیش‌نیاز: Frappe Bench سازگار با ERPNext.

```bash
bench get-app /path/to/asoud_erp
bench --site your-site.local install-app asoud_erp
bench --site your-site.local migrate
bench restart
```

## Flutter

```bash
flutter pub get
flutter analyze
flutter test
flutter run --dart-define=ERPNEXT_BASE_URL=https://erp.example.com
```

کلیدهای واقعی فقط در Secret Manager یا تنظیمات امن محیط اجرا قرار می‌گیرند.

