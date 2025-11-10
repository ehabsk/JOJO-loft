# JOJO-loft
pigeon-system
# 🕊️ نظام إدارة تربية الحمام (Pigeon Breeding Management System)

نظام متكامل وحديث لإدارة مزارع الحمام يوفر إدارة الآباء والمواليد والبيض مع إمكانية إنشاء شهادات ميلاد احترافية ومزامنة تلقائية للبيانات في السحابة.

---

## 🎯 المميزات الرئيسية

- **إدارة الآباء والأمهات**: تسجيل بيانات كاملة (اسم، كود، جنس، نوع، لون، صورة، ملاحظات)
- **تسجيل البيض**: تتبع البيض المخصب مع تايمر تلقائي لفترة الحضانة (18 يوم)
- **إدارة المواليد**: تسجيل المواليد الجديدة مع بيانات الأبوين والجنس والنوع واللون
- **شهادات ميلاد احترافية**: توليد شهادات ميلاد مع QR Code قابل للمسح والتحقق
- **مزامنة تلقائية**: بياناتك تُحفظ مباشرة في قاعدة بيانات Supabase في السحابة
- **عمل بدون إنترنت**: البيانات تُحفظ محلياً أولاً ثم تُزامن تلقائياً عند الاتصال
- **QR Code**: كل مولود يحصل على كود QR يحتوي على جميع بياناته
- **تحديث الحالة**: تغيير حالة الطيور (حي، متوفي، مباع، أصبح أباً)
- **ترقية المواليد**: تحويل أي مولود إلى "أب" أو "أم" تلقائياً
- **تصدير PDF**: تحميل شهادات الميلاد كملفات PDF جاهزة للطباعة

---

## 🛠️ التقنيات المستخدمة

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla JS)
- **Backend**: Supabase (Firebase Alternative)
- **Database**: PostgreSQL (عبر Supabase)
- **QR Code**: QR Code Styling Library
- **PDF Export**: html2pdf.js
- **Storage**: LocalStorage (احتياطي) + Supabase Storage (سحابة)

---

## 📋 متطلبات التشغيل

- متصفح حديث (Chrome, Firefox, Edge)
- حساب GitHub (لتسجيل الدخول في Supabase)
- اتصال إنترنت لأول مرة (للمزامنة)

---

## 🚀 دليل التثبيت السريع

### الخطوة 1: إنشاء حساب Supabase
1. اذهب إلى [supabase.com](https://supabase.com)
2. سجل دخول باستخدام GitHub
3. أنشئ مشروع جديد (اختر خطة Free)
4. اختر منطقة Frankfurt (الأقرب للوطن العربي)

### الخطوة 2: إنشاء جداول قاعدة البيانات
افتح **SQL Editor** في لوحة التحكم وشغّل هذا الكود:

```sql
CREATE TABLE parents (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name TEXT,
    code TEXT UNIQUE,
    gender TEXT,
    type TEXT,
    color TEXT,
    status TEXT DEFAULT 'حي',
    notes TEXT,
    image TEXT,
    created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE chicks (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name TEXT,
    code TEXT UNIQUE,
    male_name TEXT,
    female_name TEXT,
    gender TEXT,
    type TEXT,
    birth_date DATE,
    color TEXT,
    ring_number TEXT,
    status TEXT DEFAULT 'حي',
    notes TEXT,
    image TEXT,
    created_at TIMESTAMPTZ DEFAULT NOW()
);




الالخطوة 3: الحصول على مفاتيح API

    اذهب إلى Project Settings → API
    انسخ Project URL و anon public key
    افتح ملف pigeon_system.html في المتصفح
    أدخل المفاتيح في تبويب "الإعدادات"
    اضغط "اختبار الاتصال" ✅


