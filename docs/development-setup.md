# راه‌اندازی توسعه

پس از نصب یا ارتقای افزونه حتماً migration اجرا شود تا DocType مربوط به setup شرکت همگام گردد:

```bash
bench --site asoud.localhost migrate
```

در اولین اجرای Flutter، برنامه `get_setup_status` را فراخوانی می‌کند و کاربر را به نخستین مرحله ناقص
می‌برد. کاربر API باید دست‌کم مجوز خواندن setup و برای انجام راه‌اندازی نقش `System Manager` یا
`Accounts Manager` داشته باشد.

تست یکپارچه setup پس از نصب ERPNext و افزونه روی سایت آزمایشی اجرا می‌شود:

```bash
bench --site asoud.localhost run-tests --app asoud_erp --doctype "ASOUD Company Setup"
```

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

