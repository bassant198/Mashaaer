# مَشَاعِر — تشغيل ونشر

## 1) Firebase
أنشئي مشروعًا في Firebase Console، ثم:
- Authentication → Sign-in method → فعّلي Anonymous.
- Firestore Database → Create database.
- أضيفي Web App وانسخي بيانات config.

## 2) البيئة
انسخي `.env.example` إلى `.env.local` وضعي قيم Firebase.

## 3) Firestore Rules
لنسخة أولى سريعة استخدمي القواعد التالية، ثم شدديها عند الإطلاق العام:

```txt
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /rooms/{roomId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## 4) تشغيل
```bash
npm install
npm run dev
```

## 5) النشر
يمكن نشر المشروع على Vercel أو Netlify أو Firebase Hosting. بعد النشر، الرابط مثل:
`https://YOUR-DOMAIN/?room=ABC123`

شاركي نفس الرابط مع خطيبك. أنتِ وخطيبك تدخلان باسم كل واحد فيكما، وكل جهاز يحتفظ بسؤال مستقل ويتم تحديث الغرفة لحظيًا.

## ملاحظة
بنك الأسئلة الحالي يولد 1200 سؤالًا منظمًا داخل `src/questions.js` عبر 20 قسمًا × 60 سؤالًا. يمكن استبداله لاحقًا ببنك تحريري أكبر من 2000 سؤال دون تغيير محرك اللعبة.
