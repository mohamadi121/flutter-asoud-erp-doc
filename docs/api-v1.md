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

## کد سرفصل‌ها

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
