# راهبرد تست

## Backend

- parse همه DocType JSONها و compile Python.
- تست واحد قواعد prefix، طول و overflow کد.
- تست نصب، migrate و uninstall روی سایت واقعی.
- تست هم‌زمانی allocation کد.
- تست مجوز Company، Account و endpointها برای هر Role.

## Flutter

- تست BLoC/Cubit با Repository fake.
- تست envelope موفق و خطای Frappe.
- widget test ورود، انتخاب شرکت، loading/failure و ایجاد حساب.
- integration test روی سایت staging.

## تست‌های طلایی حسابداری

- جمع بدهکار و بستانکار برابر.
- Invoice، Payment، Cancel/Amend و بستن دوره.
- Opening balance و مهاجرت کدهای قدیمی.
- گرد کردن و نمایش ریال/تومان.

تأیید این تست‌ها باید با سناریوی مصوب حسابدار انجام شود.
