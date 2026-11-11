# دفتر الحسابات

التطبيق ملف واحد (`index.html`). **الكود فقط** هو اللي على GitHub. البيانات بتتحفظ على موبايلك (المتصفح) وعلى جوجل درايف بتاعك (مجلد خاص بالتطبيق). مفيش أي بيانات بتترفع على GitHub.

## 1) ارفع الكود على GitHub
1. أنشئ مستودع (Repository) جديد على github.com. الأفضل **Private** لو خطتك تسمح بـ Pages، أو Public لأن الكود لا يحتوي بيانات.
2. ارفع الملفات دي في جذر المستودع: `index.html` و `manifest.webmanifest` و `sw.js` و `icon-192.png` و `icon-512.png` و `.gitignore`.
3. من **Settings → Pages**: Source = *Deploy from a branch*، Branch = `main` و Folder = `/ (root)`، ثم Save.
4. بعد دقيقة يظهر الرابط: `https://اسم-حسابك.github.io/اسم-المستودع/`

## 2) جهّز تسجيل الدخول بجوجل (مرة واحدة)
1. ادخل https://console.cloud.google.com وأنشئ مشروعًا جديدًا.
2. **APIs & Services → Library**: فعّل **Google Drive API**.
3. **OAuth consent screen**: اختر External، اكتب اسم التطبيق وإيميلك، وأضف إيميلك في **Test users**.
4. **Credentials → Create credentials → OAuth client ID**: النوع **Web application**.
   - في **Authorized JavaScript origins** أضف: `https://اسم-حسابك.github.io` (بدون المسار وبدون `/` في الآخر).
5. انسخ الـ **Client ID** (آخره `.apps.googleusercontent.com`).
6. إمّا تكتبه في بوابة الدخول أول مرة تفتح التطبيق، أو تحطه ثابتًا في `index.html` في السطر `const GCID='';` وترفع الملف تاني.

## 3) الاستخدام
- افتح الرابط على الموبايل ← **تسجيل الدخول بحساب جوجل** ← ثبّته على الشاشة الرئيسية (Add to Home Screen).
- بعد الدخول، المزامنة بتتم تلقائيًا مع جوجل درايف (مجلد التطبيق المخفي appDataFolder). على موبايل تاني سجّل بنفس الحساب وهتنزل البيانات.
- البيانات الأساسية دايمًا موجودة محليًا على الموبايل، فالتطبيق يشتغل بدون نت.

## ملاحظات أمان
- لا ترفع ملفات النسخ الاحتياطية (`backup-*.json`) على GitHub — الـ `.gitignore` بيمنعها.
- التطبيق بيطلب صلاحية `drive.appdata` فقط: يشوف مجلده الخاص ولا يشوف باقي ملفاتك على درايف.
- حساب التطبيق في وضع Testing: لازم تضيف إيميلك في Test users، وممكن الدخول يتطلب إعادة تأكيد كل فترة.
