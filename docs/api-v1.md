# قرارداد API نسخه ۱

Base path:

```text
/api/method/asoud_erp.api.v1
```

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
