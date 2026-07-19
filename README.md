# 🏋️ Gym-Chain-Data-Engineering-Analytics

---

## 📌 Phase 1: Foundation & Project Management (مرحلة التأسيس وإدارة المشروع)

### 📊 Project Tracking via ClickUp (تتبع وإدارة المهام)
* تم تخطيط وتقسيم جميع مراحل المشروع (من أول فهم المتطلبات وحتى بناء التقارير) باستخدام منصة **ClickUp** لضمان سير العمل بأسلوب **Agile** احترافي وتتبع الـ **Tasks** والـ **Subtasks** بدقة.

> 📸 **Project Board Blueprint:**
> ![ClickUp Task Management](https://images2.imgbox.com/71/e6/M6kE15m8_o.png)

### 🎯 Overview (نظرة عامة)
* **Project Nature:** مشروع متكامل (End-to-End) بيربط بين مهام الـ **Data Engineer** والـ **Data Analyst** لإنشاء بنية تحتية قوية للبيانات.
* **Business Domain:** المشروع مصمم خصيصاً لتحليل بيانات حقيقية لـ **Heavy Power Nutrition Gym Chain** (سلسلة صالات رياضية ومكملات غذائية).

### 👥 1. Understanding Business Requirements (فهم متطلبات العمل)
* **الخطوة:** عمل اجتماع (**Meeting**) مباشر مع الـ **Business Owner**.
* **الهدف:** فهم طبيعة العمل، تحديد المشاكل، ومعرفة المؤشرات الأساسية المطلوبة قبل البدء في أي شغل تقني.

---

## 🏗️ Phase 2: Architectural Pipeline & Engineering Design (تصميم وبناء خط سير البيانات)

### 🚀 2. Choose Data Pipeline Approach (اختيار أسلوب نقل البيانات)
* لتأمين البيانات وضمان عدم التأثير على نظام التشغيل اليومي، تم اختيار أسلوب فصل الطبقات (**Decoupled Architecture**).

### 📂 3. Design & Create Staging Area (تصميم وبناء منطقة الإنزال الافتراضية)
* **Create DB:** إنشاء قاعدة بيانات خاصة بالـ **Staging Area (SA)** لتكون منطقة وسيطة للبيانات.
* **Create Tables:** بناء جداول مطابقة لهيكل البيانات الخام داخل الـ **SA**.
* **Move Data (ELT):** نقل البيانات الخام من قاعدة البيانات التشغيلية **OLTP** إلى الـ **Staging Area**.
* **Views & Denormalize:** إنشاء **SQL Views** داخل الـ **SA** لدمج الجداول (**Denormalization**) وتنظيف وتظبيط الداتا دون التعديل على الجداول الأساسية.

### 🗄️ 4. Design & Create Data Warehouse (تصميم وبناء مستودع البيانات)
* **Create DWH:** إنشاء قاعدة بيانات الـ **Data Warehouse (DWH)** النهائية والمجهزة للتحليل.
* **Create Tables in DWH:** بناء جداول الحقائق (**Fact Tables**) وجداول الأبعاد (**Dimension Tables**).
* **Data Movement:** نقل وتحميل البيانات الجاهزة والمعالجة من الـ **SQL Views** إلى الـ **DWH** مباشرة.

### 📝 5. Create Document of SQL Work (توثيق شغل السيكول)
* **الخطوة:** عمل توثيق (**Documentation**) شامل ومفصل لكل العمليات والـ **Scripts** اللي تمت أثناء عملية الـ **ETL** على السيكول.

---

## 📈 Phase 3: Business Intelligence & DevOps Integration (ذكاء الأعمال والربط البرمجي)

### 📊 6. Get Data from DWH to Power BI (ربط السيكول بالباور بي آي)
* **Data Connection:** سحب الجداول النظيفة والمنظمة من الـ **DWH** إلى الـ **Power BI**.
* **Data Model:** بناء وتصميم الـ **Data Model** (العلاقات بين الجداول) داخل الباور بي آي.

### 🛠️ 7. Integrate Between Git, VS & Power BI (ربط أدوات التحكم والمطورين)
* **Save File as .pbip:** حفظ ملف الباور بي آي بصيغة **Power BI Project (.pbip)** المعتمدة في المشاريع الكبيرة.
* **Install Visual Studio (VS):** تجهيز بيئة المطورين لإدارة وتعديل أكواد المشروع محلياً.
* **Initialize Git:** تشغيل نظام **Git** داخل الفولدر لتتبع كل سطر بيتكتب.
* **Integration:** الربط الكامل بين **Git** و **VS** و **Power BI** لمتابعة التغييرات وحفظ الشغل (**Version Control**).

### 🎨 8. Calculations, Visualization & Documentation (الحسابات، الداشبورد والتوثيق)
* **Create Calculations using AI in VS:** كتابة وعمل معادلات الـ **DAX** وتظبيط الـ **Measures** والـ **Calculations**.
* **Visualization:** تصميم الداشبورد والتقارير التفاعلية (**Dashboard**) لعرض المؤشرات بشكل بصري ممتاز.
* **Document for Power BI Report:** عمل توثيق (**Documentation**) شامل لكل المعادلات والشغل المالي والإداري اللي اتعمل جوه الـ **Power BI**.
