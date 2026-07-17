# مسئولیت مخزن‌ها

## `frappe-erp-next-1`

- آینه شاخه رسمی `frappe/erpnext:version-15` روی شاخه `version-15`.
- بدون فیلد سفارشی، ترجمه اختصاصی یا patch ASOUD.
- ارتقا فقط با دریافت upstream و اجرای تست staging.

## `frappe-erp-next-2`

- Frappe app با package name برابر `asoud_erp`.
- DocTypeها، Custom Fieldها، APIها و قواعد اختصاصی ASOUD.
- دارای `required_apps = ["erpnext"]` و محدود به major نسخه 15.

## `flutter-asoud-erp`

- ورود کاربر، انتخاب شرکت، نمایش درخت حساب‌ها و گردش‌های UI.
- BLoC/Cubit در سطح feature و Repository برای مرز داده.
- فاقد API Secret مشترک یا منطق تولید کد حساب.

## `flutter-asoud-erp-doc`

- قراردادها و ADRهای مشترک میان Flutter و Backend.
- هر وضعیت باید یکی از `planned`، `scaffolded`، `unit-tested`، `integration-tested` یا `released` باشد.
