# قرارداد API نسخه ۱

Base path:

```text
/api/method/asoud_erp.api.v1
```

## Envelope موفق Frappe

مقدار برگشتی whitelisted method توسط Frappe زیر `message` قرار می‌گیرد:

```json
{
  "message": {
    "ok": true,
    "data": {},
    "meta": {"api_version": "v1"}
  }
}
```

خطاها از exception و status استاندارد Frappe استفاده می‌کنند؛ پاسخ جعلی `{ok:false}` با HTTP 200 تولید نمی‌شود. Flutter تنها پیام امن و قابل نمایش را از خطا map می‌کند.

## حساب‌ها

### درخت حساب‌ها

```text
GET /api/method/asoud_erp.api.v1.account.list_accounts?company=<company>
```

فیلدهای هر گره:

```json
{
  "id": "Cash - ASD",
  "account_number": "10101",
  "account_name": "Cash",
  "parent_account": "Current Assets - ASD",
  "is_group": false,
  "root_type": "Asset",
  "disabled": false,
  "asoud_level": "Ledger",
  "children": []
}
```

### ایجاد حساب

```text
POST /api/method/asoud_erp.api.v1.account.create_account
```

```json
{
  "company": "ASOUD",
  "account_name": "بانک‌ها",
  "level": "Ledger",
  "parent_account": "موجودی نقد و بانک - ASD",
  "auto_code": true,
  "account_number": null
}
```

کد نهایی فقط از پاسخ create معتبر است.

## تنظیمات کدینگ

```text
GET  /api/method/asoud_erp.api.v1.settings.get_settings?company=<company>
POST /api/method/asoud_erp.api.v1.settings.update_settings
```

تغییر تنظیمات نیازمند نقش مدیریتی و دسترسی به Company است.

## عملیات استاندارد

- Login: `POST /api/method/login`
- Logout: `POST /api/method/logout`
- Company list: REST استاندارد `Company` با مجوز کاربر
