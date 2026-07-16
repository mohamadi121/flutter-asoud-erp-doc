# مستندات ASOUD ERP

مرجع معماری، مدل حسابداری ایرانی، قراردادهای API و مسیر توسعه ASOUD ERP.

## ریپازیتوری‌ها

| ریپازیتوری | مسئولیت |
|---|---|
| `flutter-asoud-erp` | اپ موبایل Flutter، رابط کاربری و BLoC |
| `flutter-asoud-erp-doc` | مستندات محصول، معماری و API |
| `frappe-erp-next-1` | کد اصلی ERPNext؛ بدون تغییر مستقیم تا حد ممکن |
| `frappe-erp-next-2` | افزونه اختصاصی ASOUD روی Frappe |

## تصمیم‌های قطعی

- مبنای حسابداری: تعهدی
- رابط: فارسی، RTL، موبایل‌محور
- واحد ذخیره‌سازی ERPNext: ریال
- امکان نمایش مبالغ: ریال یا تومان
- فروش مویرگی: ماژول مستقل
- ایجاد و ویرایش هر موجودیت: فرم مشترک
- تفصیلی شناور: راهنمای داخل صفحه، نه مرحله اجباری مستقل
- کد اصلی ERPNext مستقیماً تغییر نمی‌کند مگر با ثبت ADR و دلیل فنی

## فهرست

- [معماری سیستم](docs/architecture.md)
- [مدل حسابداری ایرانی](docs/iranian-accounting-model.md)
- [قرارداد API نسخه ۱](docs/api-v1.md)
- [امنیت و احراز هویت](docs/security.md)
- [راه‌اندازی توسعه](docs/development-setup.md)
- [CI بک‌اند و اتصال Flutter](docs/backend-ci-and-integration.md)
- [خط مبنای ERPNext و روش نصب افزونه](docs/erpnext-baseline.md)
- [نقشه راه](docs/roadmap.md)
- [تصمیم‌های معماری](docs/adr/0001-extension-over-core.md)
