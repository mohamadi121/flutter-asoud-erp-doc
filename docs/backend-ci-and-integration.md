# CI بک‌اند و اتصال Flutter

## کنترل‌های خودکار افزونه

Workflow مخزن `frappe-erp-next-2` در هر Push و Pull Request این موارد را اجرا می‌کند:

1. بررسی قابل‌کامپایل بودن تمام فایل‌های Python
2. بررسی کیفیت و importها با Ruff
3. اجرای تست قرارداد پاسخ API با Pytest

این CI جایگزین تست یکپارچه Frappe نیست. تست یکپارچه پس از نصب افزونه روی سایت آزمایشی انجام می‌شود.

## قرارداد پاسخ ASOUD

متدهای اختصاصی در کلید `message` پاسخ Frappe، یکی از دو قالب زیر را برمی‌گردانند:

```json
{"ok": true, "data": {}, "meta": {"api_version": "v1"}}
```

```json
{"ok": false, "error": {"code": "VALIDATION_ERROR", "message": "..."}, "meta": {"api_version": "v1"}}
```

Flutter این قرارداد را با `AsoudApiResponse` باز می‌کند و خطاهای بک‌اند را به `ApiException` تبدیل می‌کند.

## مراحل تست یکپارچه بعدی

1. ایجاد سایت آزمایشی Frappe/ERPNext
2. نصب `asoud_erp`
3. اجرای `bench --site <site> migrate`
4. ساخت API Key برای کاربر آزمایشی با کمترین سطح دسترسی
5. اجرای Flutter با `ERPNEXT_BASE_URL` و کلیدهای آزمایشی
6. تست ایجاد دفتر، تنظیمات تعهدی و تولید خودکار کد حساب
