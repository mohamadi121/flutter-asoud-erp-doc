# ارتقای ERPNext بدون تغییر هسته

ریپازیتوری `frappe-erp-next-1` آینه upstream است و نباید commit اختصاصی ASOUD دریافت کند.

نمونه همگام‌سازی:

```bash
git remote add upstream https://github.com/frappe/erpnext.git
git fetch upstream version-15
git checkout main
git merge --ff-only upstream/version-15
git push origin main
```

اگر `--ff-only` شکست خورد، ابتدا وجود commit اختصاصی در Core بررسی شود؛ conflict نباید با patch تصادفی در Core حل شود.

## دروازه ارتقا

1. backup و تست restore
2. نصب/migrate افزونه در staging
3. تست permission و قرارداد API
4. تست ایجاد، لغو و گزارش سند حسابداری
5. تست Flutter روی نسخه staging
6. سپس ارتقای production
