# امنیت و احراز هویت

## MVP

- ورود با حساب همان کاربر Frappe انجام می‌شود.
- session cookie فقط در حافظه فرایند Flutter نگهداری و هنگام خروج پاک می‌شود.
- رمز عبور، API Key و API Secret در سورس، `dart-define`، GitHub یا log ذخیره نمی‌شوند.
- بستن اپ نیازمند ورود مجدد است تا Secure Storage نادرست شبیه‌سازی نشود.

## هدف تولید

- OAuth2 Authorization Code + PKCE.
- ذخیره refresh/access token در Secure Storage سیستم‌عامل.
- revoke در logout و مدیریت expiry/refresh.
- CORS محدود به originهای مشخص برای Flutter Web.

## مجوز

- Backend از Role، DocPerm، User Permission و permission check سند استفاده می‌کند.
- endpoint فهرست نباید با `frappe.get_all` مجوزها را دور بزند.
- Company در همه queryها و sequenceهای کدینگ الزامی است.
- انتخاب نقش در کلاینت مجوز ایجاد نمی‌کند.
- stack trace و exception داخلی مستقیماً به کاربر نمایش داده نمی‌شود.
