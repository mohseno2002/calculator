# Hydraulics Suite Pro — حزمة الرفع

تطبيق PWA كامل (آلة حاسبة هندسية + هيدروليكا + معالج تصميم + تحويل وحدات) يعمل بدون إنترنت ويُثبَّت على الهاتف.

## محتويات الحزمة
- `index.html` — التطبيق كاملاً (ملف واحد)
- `manifest.json` — تعريف الـ PWA
- `sw.js` — service worker للعمل offline
- `icon-192.png` / `icon-512.png` — أيقونات التطبيق
- `_headers` — ضبط الـ MIME types على Cloudflare Pages

## الرفع على GitHub ثم Cloudflare Pages

### 1) من Termux ارفع الملفات على GitHub
```bash
cd hydraulics-suite
git init
git add .
git commit -m "Hydraulics Suite Pro — PWA"
git branch -M main
git remote add origin https://github.com/mohseno2002/hydraulics-suite.git
git push -u origin main
```
(غيّر اسم الـ repo لو حبيت)

### 2) من Cloudflare Dashboard
1. dash.cloudflare.com ← **Workers & Pages** ← **Create** ← **Pages** ← **Connect to Git**
2. اختر الـ repo
3. إعدادات الـ build:
   - Framework preset: **None**
   - Build command: **(اتركه فارغاً)**
   - Build output directory: **`/`**
4. **Save and Deploy**

خلال دقيقة يطلع رابط مثل `hydraulics-suite.pages.dev`.
أي `git push` بعد ذلك يُنشر تلقائياً.

## التثبيت على الموبايل
افتح الرابط في Chrome ← قائمة ← "إضافة إلى الشاشة الرئيسية". بعدها يعمل كتطبيق مستقل وبدون إنترنت.

## ملاحظات
- السجل (History) محفوظ في `localStorage` — يعمل على الدومين الحقيقي ويبقى بعد الإغلاق.
- لتحديث نسخة الكاش بعد أي تعديل، غيّر رقم `CACHE` في `sw.js` (مثلاً `-v2`).
