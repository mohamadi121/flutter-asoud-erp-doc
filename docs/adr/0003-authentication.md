# ADR-0003: احراز هویت کاربرمحور

- وضعیت: MVP پذیرفته‌شده؛ تولید نیازمند ارتقا
- تاریخ: 2026-07-15

## تصمیم MVP

Flutter با username/password به endpoint رسمی login متصل و session cookie را فقط در حافظه نگهداری می‌کند. API Key/Secret مشترک از build حذف می‌شود.

## هدف تولید

OAuth2 Authorization Code + PKCE و Secure Storage پس از آماده‌شدن تنظیمات client و redirect URI در هر پلتفرم.
