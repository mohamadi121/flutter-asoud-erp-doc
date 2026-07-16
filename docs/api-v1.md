# قرارداد API نسخه ۱

Base path:

```text
/api/method/asoud_erp.api.v1
```

## راه‌اندازی اولیه شرکت

اطلاعات راه‌اندازی هر شرکت در `ASOUD Company Setup` و به‌صورت company-scoped نگهداری می‌شود.
نقش‌های فعال دفتر تنظیمات کسب‌وکار هستند و مجوز یا Role کاربران Frappe را تغییر نمی‌دهند.

```text
GET  /api/method/asoud_erp.api.v1.setup.get_setup_status
POST /api/method/asoud_erp.api.v1.setup.save_office
GET  /api/method/asoud_erp.api.v1.setup.get_company_settings
POST /api/method/asoud_erp.api.v1.setup.update_company_settings
GET  /api/method/asoud_erp.api.v1.setup.get_enabled_roles
POST /api/method/asoud_erp.api.v1.setup.update_enabled_roles
```

`get_setup_status` در صورت ارسال `company` وضعیت همان شرکت و در غیر این صورت آخرین setup قابل دسترس
را برمی‌گرداند. پاسخ شامل `office_saved`، `accounting_saved`، `roles_saved` و `complete` است.

`save_office` یک Company استاندارد با ارز ذخیره‌سازی `IRR` ایجاد می‌کند و نوع دفتر، شناسه ملی و
کد اقتصادی را در setup همان شرکت نگه می‌دارد. ایجاد Company هم‌نام مجاز نیست.

`update_company_settings` مقادیر `display_currency`، `fiscal_year_start_month`، `chart_template` و
`auto_generate_detail_code` را می‌پذیرد. این API فقط انتخاب الگوی سرفصل را ذخیره می‌کند و به‌تنهایی
ادعای ساخت درخت حساب‌ها ندارد.

`update_enabled_roles` آرایه نقش‌های فعال دفتر را می‌پذیرد و همیشه `System Manager` را در تنظیمات
فعال نگه می‌دارد؛ این عملیات هیچ Roleای را به User تخصیص نمی‌دهد.

## پاسخ استاندارد

```json
{
  "ok": true,
  "data": {},
  "meta": {"api_version": "v1"}
}
```

خطا:

```json
{
  "ok": false,
  "error": {"code": "VALIDATION_ERROR", "message": "متن قابل نمایش"},
  "meta": {"api_version": "v1"}
}
```

## تنظیمات

### دریافت تنظیمات

```text
GET /api/method/asoud_erp.api.v1.setup.get_settings
```

### ذخیره تنظیمات

```text
POST /api/method/asoud_erp.api.v1.setup.update_settings
```

Body:

```json
{
  "display_currency": "Toman",
  "auto_generate_detail_code": true,
  "detail_code_digits": 5
}
```

## تفصیلی شناور

## گروه‌های تفصیلی

### دریافت گروه‌ها

```text
GET /api/method/asoud_erp.api.v1.detail_group.list_detail_groups
```

گروه‌های پایه شامل مشتریان `10000`، تأمین‌کنندگان `20000`، پرسنل `30000`،
بانک‌ها `40000`، صندوق‌ها `50000`، مراکز هزینه `60000`، پروژه‌ها `70000`
و سایر `90000` هستند.

### اتصال حساب معین به گروه تفصیلی

```text
POST /api/method/asoud_erp.api.v1.detail_group.save_account_mapping
```

پارامترها: `company`، `account` و `detail_group`.

## کد سرفصل‌ها

### دریافت سرفصل‌های شرکت

```text
GET /api/method/asoud_erp.api.v1.account.list_accounts
```

پارامتر الزامی: `company`. پاسخ بر اساس کد حساب مرتب است و فیلد
`asoud_level` را برای نگاشت گروه، کل و معین در Flutter برمی‌گرداند.

### پیش‌نمایش کد بعدی

```text
GET /api/method/asoud_erp.api.v1.account.preview_next_code
```

پارامترها: `company`، `level` و برای سطوح غیرگروه `parent_account`.

### ایجاد حساب با کد خودکار

```text
POST /api/method/asoud_erp.api.v1.account.create_account
```

Backend کد نهایی را تولید می‌کند؛ Flutter فقط الگو و حساب والد را ارسال می‌کند.

تفصیلی شناور از DocType و API اختصاصی خودش استفاده می‌کند و به‌عنوان یک حساب
ERPNext زیر حساب معین ساخته نمی‌شود.


### فهرست

```text
GET /api/method/asoud_erp.api.v1.floating_detail.list_floating_details
```

### ایجاد

```text
POST /api/method/asoud_erp.api.v1.floating_detail.create_floating_detail
```

Body:

```json
{
  "title": "شرکت نمونه",
  "detail_type": "Customer",
  "detail_group": "10000",
  "linked_doctype": "Customer",
  "linked_document": "CUST-0001"
}
```

### غیرفعال‌سازی

```text
POST /api/method/asoud_erp.api.v1.floating_detail.disable_floating_detail
```

API حذف فیزیکی برای تفصیلی دارای گردش مالی ارائه نمی‌شود.

## اشخاص و طرف‌حساب‌ها

### فهرست و جست‌وجو

```text
GET /api/method/asoud_erp.api.v1.party.list_parties
```

### ایجاد یا ویرایش

```text
POST /api/method/asoud_erp.api.v1.party.save_party
```

`party_type` یکی از `Individual` یا `Organization` است. فیلد `roles` آرایه‌ای
از نقش‌های Customer، Supplier، Employee، Shareholder یا Other است. نقش‌های
Customer و Supplier پس از اعتبارسنجی با اسناد متناظر ERPNext همگام می‌شوند.
برای نقش‌های مشتری، تأمین‌کننده و پرسنل، تفصیلی مرتبط در گروه ثابت همان نقش
به‌صورت خودکار ساخته و به پروفایل واحد شخص متصل می‌شود.
نقش Employee تا زمان تکمیل شرکت، تاریخ استخدام و اطلاعات منابع انسانی فقط در
پروفایل ASOUD نگهداری می‌شود و Employee ناقص ساخته نمی‌شود.

## اسناد حسابداری

### فهرست اسناد

```text
GET /api/method/asoud_erp.api.v1.voucher.list_vouchers
```

پارامتر الزامی `company` است. فیلترهای اختیاری `status` و `search` هستند.

### ایجاد یا ویرایش پیش‌نویس

```text
POST /api/method/asoud_erp.api.v1.voucher.save_voucher
```

هر ردیف دقیقاً باید یکی از مقادیر بدهکار یا بستانکار را داشته باشد. حداقل دو
ردیف لازم است و جمع بدهکار و بستانکار باید برابر و بزرگ‌تر از صفر باشد.

### ارسال برای تأیید

```text
POST /api/method/asoud_erp.api.v1.voucher.submit_for_approval
```

### تأیید یا رد

```text
POST /api/method/asoud_erp.api.v1.voucher.approve_voucher
POST /api/method/asoud_erp.api.v1.voucher.reject_voucher
```

تأیید فقط برای `Accounts Manager` و `System Manager` مجاز است. هنگام تأیید،
Backend یک `Journal Entry` استاندارد ERPNext می‌سازد و Submit می‌کند. سند ردشده
دلیل اجباری دارد و پس از اصلاح می‌تواند دوباره برای تأیید ارسال شود.

## گزارش‌های حسابداری

### تراز آزمایشی

```text
GET /api/method/asoud_erp.api.v1.report.trial_balance
```

پارامترها: `company`، `from_date`، `to_date` و `account` اختیاری. پاسخ برای هر
حساب، مانده افتتاحیه بدهکار/بستانکار، گردش دوره و مانده پایان دوره را جداگانه
برمی‌گرداند. جمع ستون‌ها از مجموع حساب‌ها محاسبه می‌شود، نه از خالص مانده‌ها.

### دفتر کل و معین

```text
GET /api/method/asoud_erp.api.v1.report.general_ledger
```

پارامترهای الزامی `company`، `from_date`، `to_date` و `account` هستند. برای دفتر
معین می‌توان `party_type` و `party` را نیز ارسال کرد. پاسخ شامل مانده افتتاحیه،
ردیف‌های `GL Entry` با مانده تجمعی، جمع بدهکار، جمع بستانکار و مانده نهایی است.
اسناد لغوشده در هیچ‌یک از گزارش‌ها محاسبه نمی‌شوند.
