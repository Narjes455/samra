# سَمرة | Samra

لعبة أسئلة جماعية سعودية مجانية بين فريقين على شاشة وحدة. الكل ينضم بجواله عن طريق QR، والشاشة تقسّمهم فريقين بالتساوي.

وفيها **ارسمها**: لعبة رسم وتخمين. كل واحد يرسم من جواله كلمة يختارها من ثلاث، والباقين يخمّنون من جوالاتهم، والشاشة الكبيرة تعرض الرسمة والنقاط.

تصميم وتطوير: نرجس العمري

## الملفات

| الملف | وش فيه |
|---|---|
| `index.html` | الموقع كامل: الصفحة الرئيسية، اللعبة، شاشة الجوال، ملفي |
| `firebase-config.js` | إعدادات Firebase (تلصقينها مرة وحدة) |
| `database.rules.json` | قواعد حماية قاعدة البيانات (تنسخينها في Firebase) |

## إعداد Firebase (مرة وحدة، مجاني)

1. ادخلي [console.firebase.google.com](https://console.firebase.google.com) واضغطي **Add project**، سمّيه `samra`، وطفّي Google Analytics.
2. من القائمة: **Build ← Authentication ← Get started ← Sign-in method**، فعّلي **Anonymous**.
   - هذا يخلي كل جوال ياخذ رقم خاص فيه بدون ما يسجّل اللاعب أي شي.
3. **Build ← Realtime Database ← Create database**، اختاري موقع قريب (مثل `europe-west1`)، وابدئي بـ **locked mode**.
4. في تبويب **Rules** داخل Realtime Database: امسحي اللي فيه، والصقي محتوى ملف `database.rules.json`، واضغطي **Publish**.
5. من ⚙️ **Project settings ← Your apps** اضغطي أيقونة الويب `</>`، سجّلي التطبيق باسم `samra`، وانسخي قيم `firebaseConfig` إلى ملف `firebase-config.js`.
   - تأكدي إن `databaseURL` موجود. إذا ما طلع، سوّي الخطوة ٣ قبل الخطوة ٥.
6. **Authentication ← Settings ← Authorized domains ← Add domain**، وأضيفي `narjes455.github.io`.

## النشر على GitHub Pages

1. سوّي مستودع جديد باسم `samra` في حسابك.
2. ارفعي الملفات الثلاثة.
3. **Settings ← Pages ← Deploy from a branch**، اختاري `main` والمجلد `/ (root)`، واحفظي.
4. بعد دقيقة يصير الرابط: `https://narjes455.github.io/samra/`

## تحديث القواعد (مهم بعد إضافة ارسمها)

كل ما تغيّر ملف `database.rules.json`، انسخيه والصقيه في **Realtime Database ← Rules** واضغطي **Publish**.
القواعد الجديدة تخلي الكلمة السرية والتخمينات ما يشوفها إلا صاحبها والشاشة الكبيرة.

## ملاحظات

- إذا ما انضاف Firebase، الموقع يشتغل عادي على الشاشة وحدها بدون جوالات.
- الاسم والإحصائيات (ألعاب، انتصارات) تنحفظ على الجهاز نفسه.
- الخطة المجانية في Firebase تكفي لعشرات الغرف في نفس الوقت.
