# نظام التسجيل والطاقة الاستيعابية — مدارس الأندلس (مجمع المنار)

موقع لمتابعة عدد الفصول والطاقة الاستيعابية والطلاب الحاليين والمقاعد الشاغرة، مع صفحات مستقلة لقائمة الانتظار والمنسحبين.
يعمل على GitHub Pages، والبيانات محفوظة في Firebase (Firestore) مع تسجيل دخول بحساب Google.

## إعداد Firebase (مرة واحدة)

1. افتح https://console.firebase.google.com وأنشئ مشروعاً جديداً (Analytics غير ضروري).
2. **Build ← Authentication ← Get started ← Sign-in method**: فعّل **Google**.
3. في Authentication ← **Settings ← Authorized domains**: أضف `USERNAME.github.io` (اسم مستخدم GitHub).
4. **Build ← Firestore Database ← Create database**: اختر الوضع **Production** وأقرب منطقة (مثلاً `me-central2` أو `europe-west`).
5. في Firestore ← تبويب **Rules**: الصق محتوى الملف `firestore.rules` واضغط **Publish**.
6. في Firestore ← تبويب **Data**: أنشئ مجموعة `config` ثم مستنداً بالمعرّف `roles` يحوي:
   - `editors` من نوع **array** وفيه بريدك (بأحرف صغيرة).
   - `viewers` من نوع **array** (يمكن تركه فارغاً).
7. **Project settings ← Your apps ← أيقونة الويب `</>`**: سجّل تطبيقاً، وانسخ قيم `firebaseConfig` إلى الملف `firebase-config.js`.

## أول تشغيل

- افتح الموقع وسجّل الدخول بحساب Google المضاف في `editors`.
- اضغط **إنشاء العام 1448 هـ بالبيانات الأولية**.
- أضف بقية المستخدمين من صفحة **المستخدمون والصلاحيات**.

## الملفات

| الملف | الوصف |
|---|---|
| `index.html` | الموقع كاملاً |
| `firebase-config.js` | إعدادات مشروع Firebase (ليست سرية) |
| `firestore.rules` | قواعد الحماية: القراءة لمن في القائمتين، والتعديل لقائمة `editors` فقط |
| `logos/` | شعار الشركة وشعارات الأقسام |
