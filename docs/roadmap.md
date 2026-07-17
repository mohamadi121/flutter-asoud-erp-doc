# وضعیت و نقشه راه

## این checkpoint

- `implemented`: جداسازی Core و app اختصاصی.
- `implemented`: API نسخه‌دار فهرست/ایجاد حساب و تنظیمات per-company.
- `implemented`: تولید کد سروری با sequence مستقل.
- `implemented`: Flutter login session، انتخاب Company و اتصال درخت حساب.
- `unit-tested`: قواعد کد و stateهای Flutter تا حد پوشش موجود.
- `not integration-tested`: نصب app و مسیر انتهابه‌انتها روی سایت واقعی.

## مرحله بعد

1. ساخت bench staging و تست نصب/migrate.
2. تست concurrency تولید کد روی MariaDB.
3. تأیید template حساب‌ها با حسابدار.
4. انتخاب نهایی مدل تفصیلی با آزمایش Party/Accounting Dimension.
5. اتصال Journal Entry استاندارد و approval workflow.
6. گزارش دفتر کل، معین و تراز آزمایشی.

## خارج از این checkpoint

- سامانه مؤدیان و صورتحساب الکترونیکی
- VAT و گزارش‌های قانونی
- حقوق، مالیات حقوق و بیمه
- دفاتر تجاری الکترونیکی
- بانک، چک و خزانه‌داری بومی

تا تکمیل و تأیید این بخش‌ها، عبارت «کاملاً منطبق با قوانین ایران» نباید در محصول استفاده شود.
