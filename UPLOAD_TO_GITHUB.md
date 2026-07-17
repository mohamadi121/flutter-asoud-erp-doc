# انتشار

انتشار دستی ZIP منسوخ شده است. تغییرات این مخزن باید با Git، پس از بازبینی و تست پیوندها، commit و روی شاخه تعیین‌شده push شوند.

```bash
git status
git diff --check
git add README.md CHANGELOG.md docs
git commit -m "docs: align architecture and API contracts"
git push origin main
```
