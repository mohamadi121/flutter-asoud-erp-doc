# ADR-0001: افزونه به‌جای تغییر Core

- وضعیت: پذیرفته‌شده
- تاریخ: 2026-07-15

## تصمیم

هسته ERPNext از upstream رسمی آینه می‌شود. تمام کد اختصاصی ASOUD در Frappe app مستقل `asoud_erp` قرار می‌گیرد.

## پیامد

- ارتقای patchهای ERPNext با fast-forward ممکن می‌ماند.
- migration و rollback افزونه مستقل است.
- هر نیاز بدون extension point باید ADR جداگانه داشته باشد؛ ورود مستقیم patch به Core ممنوع است.
