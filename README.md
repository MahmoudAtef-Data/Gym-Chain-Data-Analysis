# 🏋️ Gym-Chain-Data-Engineering-Analytics

---

## 📌 Phase 1: Foundation & Project Management (مرحلة التأسيس وإدارة المشروع)

### 📊 Project Tracking via ClickUp (تتبع وإدارة المهام)
* تم تخطيط وتقسيم جميع مراحل المشروع (من أول فهم المتطلبات وحتى بناء التقارير) باستخدام منصة **ClickUp** لضمان سير العمل بأسلوب **Agile** احترافي وتتبع الـ **Tasks** والـ **Subtasks** بدقة.

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

### 🗺️ Data Pipeline Flow (خط سير البيانات الأساسي)
يسير تدفق البيانات عبر المراحل التالية لضمان الفصل التام بين بيئة التشغيل والبيئة التحليلية:
* **Source DB (OLTP/OLAP):** تحتوي على البيانات الخام الأصيلة المتولدة من نظام التشغيل.
* **Staging Area (SA):** يتم سحب الداتا الخام إليها وعمل **ETL** أولي، وتجهيز الـ **SQL Views** لمعالجة وتصفية البيانات.
* **Data Warehouse (DWH):** يستقبل البيانات الجاهزة والمعالجة من الـ **Views** لتصبح مهيأة تماماً للتحليل.

> 💡 **Load Methods (طرق تحميل البيانات):** 
> * يتم استخدام أسلوب **Truncate & Insert** لتجديد البيانات بالكامل بشكل دوري.
> * يتم استخدام أسلوب **Drop, Create, Insert** في حالات إعادة بناء الهيكل الإنشائي للجداول بشكل ديناميكي.

### 📂 3. Design & Create Staging Area (تصميم وبناء منطقة الإنزال الافتراضية)
* **Create DB:** إنشاء قاعدة بيانات خاصة بالـ **Staging Area (SA)** لتكون منطقة وسيطة للبيانات.
* **Create Tables:** بناء جداول مطابقة لهيكل البيانات الخام داخل الـ **SA**.
* **Move Data (ELT):** نقل البيانات الخام من قاعدة البيانات التشغيلية **OLTP** إلى الـ **Staging Area**.
* **Views & Denormalize:** إنشاء **SQL Views** داخل الـ **SA** لدمج الجداول (**Denormalization**) وتنظيف وتظبيط الداتا دون التعديل على الجداول الأساسية.

### 🔍 4. Data Profiling & Table Consolidation (قراءة وفهم البيانات ودمج الجداول)
تم فحص الجداول الخام بدقة، ولوحظ أن البيانات مجزأة ومفصولة (**Separated**) عبر جداول متعددة رغم أنها تعبر عن نفس الكيان (Entity). لتقليل عمليات الـ Join المعقدة وتسريع الاستعلامات التحليلية وتحسين الأداء، تم دمج الجداول المتشابهة كالتالي:
* **👤 جدول الأبعاد للمشتركين (Customer Dimension):** تم دمج جدول `Customer` مع جدول `Region` وجدول `Geography` لتجميع كل بيانات المشتركين وأماكنهم الجغرافية في **جدول واحد فقط**.
* **📦 جدول الأبعاد للمنتجات (Product Dimension):** تم دمج جدول `Product` مع جدول `Product Subcategory` لتجميع كافة تفاصيل المنتجات وفئاتها في **جدول واحد فقط**.
* **💰 جدول الحقائق للمبيعات (Sales Fact Table):** تم دمج جدول `Sales Header` مع جدول `Sales Details` وجدول `Product Cost History` لإنشاء جدول مبيعات مركزي متكامل يحتوي على كل الحركات المالية والتكاليف التاريخية في **جدول واحد فقط**.

### 🗄️ 5. Design & Create Data Warehouse (تصميم وبناء مستودع البيانات)
* **Create DWH:** إنشاء قاعدة بيانات الـ **Data Warehouse (DWH)** النهائية والمجهزة للتحليل.
* **Create Tables in DWH:** بناء جداول الحقائق (**Fact Tables**) وجداول الأبعاد (**Dimension Tables**).
* **Data Movement:** نقل وتحميل البيانات الجاهزة والمعالجة من الـ **SQL Views** إلى الـ **DWH** مباشرة.

### 📝 6. Create Document of SQL Work (توثيق شغل السيكول)
* **الخطوة:** عمل توثيق (**Documentation**) شامل ومفصل لكل العمليات والـ **Scripts** اللي تمت أثناء عملية الـ **ETL** على السيكول.

---

## 📈 Phase 3: Business Intelligence & DevOps Integration (ذكاء الأعمال والربط البرمجي)

### 📊 7. Get Data from DWH to Power BI (ربط السيكول بالباور بي آي)
* **Data Connection:** سحب الجداول النظيفة والمنظمة من الـ **DWH** إلى الـ **Power BI**.
* **Data Model:** بناء وتصميم الـ **Data Model** (العلاقات بين الجداول) داخل الباور بي آي.

### 🛠️ 8. Integrate Between Git, VS & Power BI (ربط أدوات التحكم والمطورين)
* **Save File as .pbip:** حفظ ملف الباور بي آي بصيغة **Power BI Project (.pbip)** المعتمدة في المشاريع الكبيرة.
* **Install Visual Studio (VS):** تجهيز بيئة المطورين لإدارة وتعديل أكواد المشروع محلياً.
* **Initialize Git:** تشغيل نظام **Git** داخل الفولدر لتتبع كل سطر بيتكتب.
* **Integration:** الربط الكامل بين **Git** و **VS** و **Power BI** لمتابعة التغييرات وحفظ الشغل (**Version Control**).

### 🎨 9. Calculations, Visualization & Documentation (الحسابات، الداشبورد والتوثيق)
* **Create Calculations using AI in VS:** كتابة وعمل معادلات الـ **DAX** وتظبيط الـ **Measures** والـ **Calculations**.
* **Visualization:** تصميم الداشبورد والتقارير التفاعلية (**Dashboard**) لعرض المؤشرات بشكل بصري ممتاز.
* **Document for Power BI Report:** عمل توثيق (**Documentation**) شامل لكل المعادلات والشغل المالي والإداري اللي اتعمل جوه الـ **Power BI**.

---
## 🏗️ Phase 2: Architectural Pipeline & Engineering Design (تصميم وبناء خط سير البيانات)

### 🚀 Choose Data Pipeline Approach (اختيار أسلوب نقل البيانات)
لتأمين البيانات وضمان عدم التأثير على نظام التشغيل اليومي، تم اختيار أسلوب فصل الطبقات:
$$\text{DB} \longrightarrow \text{Staging Area} \longrightarrow \text{DWH}$$

* **قاعدة البيانات الأساسية (DB):** قاعدة البيانات اللي فيها الـ Data خام (OLAP).
* **منطقة الإنزال (Staging Area - SA):** بياخد الداتا من الـ DB وبيعمل لها ETL، ويحطها في Views جاهزة للشغل داخل الـ SQL Area.
* **مستودع البيانات (DWH):** بتاخد الداتا من الـ Views جاهزة للشغل، ومسؤولة عن الـ VIS (التقارير والمؤشرات) وينبثق منها الـ Calculations والـ Documentations، بجانب الـ Documentation الخاص بالـ SQL Area.

> 💡 **Load Methods (طرق تحميل البيانات):** 
> * **Truncate & Insert**
> * **Drop, Create, Insert**

---

### 🔍 Data Profiling & Table Consolidation (قراءة وفهم البيانات ودمج الجداول)

#### 1. قراءة الداتا وفهم الجداول وما تحتويه:
* لاحظنا إن الداتا مفصولة (**Separated**)، يعني فيه أكتر من جدول مهتمين بنفس الشيء، وهنا لازم نجمعهم في **Table واحد**.

#### 2. خطة دمج وتجميع الجداول:
* **👤 بيانات المشتركين والجغرافيا:** هناخد جدول `Customer` وجدول `Region` وجدول `Geography` ونجمع الـ 3 جداول في **جدول واحد**.
* **📦 بيانات المنتجات:** هناخد جدول `Product` وجدول `Product Subcategory` ونجمعهم في **جدول واحد**.
* **💰 بيانات المبيعات والتكاليف:** هناخد جدول `Sales Details` وجدول `Sales Header` وجدول `Product Cost History` ونجمع الـ 3 جداول في **جدول واحد**.



### 📂 Design & Create Staging Area (تصميم وبناء منطقة الإنزال)

#### 1. إنشاء الـ Staging Area:
* تم إنشاء قاعدة البيانات باسم: `Heavy Power Nutrition Staging` لتكون المنطقة الوسيطة.

#### 2. نقل الداتا من الـ OLAP إلى الـ SA:
* **إنشاء الجداول:** تم إنشاء جداول فارغة جاهزة لاستقبال الداتا داخل الـ SA.
* **Stored Procedures:** تم بناء وعمل *Stored Procedures* عشان تعمل نقل ذكي وديناميكي (**Dynamic**) للداتا من الـ OLAP إلى الـ SA.
* **Load Method Approach:** يتم استخدام أسلوب الـ **Drop ⬅️ Create ⬅️ Insert**؛ وذلك لضمان منع حدوث أي تكرار في البيانات أثناء عملية النقل.

---

#### 📸 كود بناء الـ Staging Area:
![Staging Area SQL Code](images/sa_sql_code.png)

---

#### 3. إنشاء الـ Views:
* تم بناء وإنشاء الـ **Views** بحيث تحتوي على الـ **Denormalize Data**.
* تم تطبيق عملية دمج الجداول المفصولة (**Separated**) إلى جداول موحدة (Table) بناءً على خطة الـ Denormalization.

---

#### 📸 صور الـ Denormalization والجداول المدمجة:
| Customer Denormalization | Product Denormalization | Sales Denormalization |
| :---: | :---: | :---: |
| ![Customer View](images/customer_view.png) | ![Product View](images/product_view.png) | ![Sales View](images/sales_view.png) |



### 🛠️ Data Cleaning & Overcoming Data Challenges (معالجة مشاكل البيانات)

#### 1. مشكلة تكرار الخصم في جدول المبيعات (Sales Denormalization):
* **المشكلة:** عند عمل `Denormalize` لجدول الـ `Sales Header` وجدول `Sales Details`، نلاحظ حدوث مشكلة عند حساب قيمة الـ `Sales Amount`؛ بسبب تكرار الـ `Discount Amount` بنفس القيمة على أكثر من Row لنفس المنتج.
* **الحل:** للتغلب على هذه المشكلة نقوم بعمل **Allocation** لتوزيع الخصم بشكل صحيح وصحيح على مستوى السطور دون تكرار القيمة الإجمالية.

---

#### 📸 كود حل مشكلة الـ Discount Allocation:
![Discount Allocation SQL Code](images/discount_allocation_code.png)

---

#### 2. التعامل مع جدول التكاليف (Product Cost History):
* **الخطوة:** في جدول الـ `Product Cost History`، تم تحديد وفلترة الأعمدة المطلوبة فقط، حيث إننا بحاجة إلى عمود الـ `Unit Cost` بس.
* **الآلية:** بيتم جلب الـ `Unit Cost` بناءً واعتماداً على الـ `Year` والـ `Month No` والـ `Country Code` والـ `Product Key`.

---

#### 📸 كود معالجة جدول الـ Product Cost History:
![Product Cost SQL Code](images/product_cost_code.png)

---

### 🗄️ Design & Create Data Warehouse - DWH (بناء مستودع البيانات)

#### 1. إنشاء جداول الـ DWH:
* تم إنشاء 4 جداول فارغة بنفس أسماء وأعمدة وخصائص الـ 4 جداول اللي في الـ Views (الجداول المجهزة والمنظفة).

---

#### 📸 كود إنشاء جداول الـ DWH:
![DWH Tables Creation Code](images/dwh_tables_creation.png)

---

#### 2. نقل البيانات من الـ SA Views إلى الـ DWH:
* **آلية النقل:** بيتم نقل الداتا من الـ `Views` الخاصة بالـ Staging Area إلى جداول الـ `DWH` مباشرة.
* **Load Method Approach:** الـ Approach اللي تم استخدامه في الـ Load Method لعملية الـ Movement هو أسلوب: **Truncate ⬅️ Insert**.

---

#### 📸 كود عملية نقل البيانات للـ DWH:
![DWH Data Movement Code](images/dwh_data_movement.png)









