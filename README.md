# 🏋️ Gym-Chain-Data-Engineering-Analytics

---

## 📌 Phase 1: Foundation & Requirements Gathering (مرحلة التأسيس وجمع البيانات)

### 🎯 Overview (نظرة عامة)
* **Project Nature:** مشروع متكامل (End-to-End) بيربط بين مهام الـ **Data Engineer** والـ **Data Analyst** لإنشاء بنية تحتية قوية للبيانات.
* **Business Domain:** المشروع مصمم خصيصاً لتحليل بيانات حقيقية لـ **Gym Chain** (سلسلة صالات رياضية).

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

| ClickUp Workflow |
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/clickup_workflow.png.jpeg) |



## 🏗️ Phase 2: Architectural Pipeline & Engineering Design (تصميم وبناء خط سير البيانات)

### 🚀 Choose Data Pipeline Approach (اختيار أسلوب نقل البيانات)
لتأمين البيانات وضمان عدم التأثير على نظام التشغيل اليومي، تم اختيار أسلوب فصل الطبقات:
$$\text{DB} \longrightarrow \text{Staging Area} \longrightarrow \text{DWH}$$


|Pipeline Architecture|
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Pipeline%20Architecture.png) |

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
* **💰 بيانات المبيعات والتكاليف:** هناخد جدول Sales Header` و جدول `Sales Details` وجدول ``Product Cost History` ونجمع الـ 3 جداول في **جدول واحد**.










### 📂 Design & Create Staging Area (تصميم وبناء منطقة الإنزال)

#### 1. إنشاء الـ Staging Area:
* تم إنشاء قاعدة البيانات باسم: `Heavy Power Nutrition Staging` لتكون المنطقة الوسيطة.

#### 2. نقل الداتا من الـ OLAP إلى الـ SA:
* **إنشاء الجداول:** تم إنشاء جداول فارغة جاهزة لاستقبال الداتا داخل الـ SA.
* **Stored Procedures:** تم بناء وعمل *Stored Procedures* عشان تعمل نقل ذكي وديناميكي (**Dynamic**) للداتا من الـ OLAP إلى الـ SA.
* **Load Method Approach:** يتم استخدام أسلوب الـ **Drop ⬅️ Create ⬅️ Insert**؛ وذلك لضمان منع حدوث أي تكرار في البيانات أثناء عملية النقل.

---

|SA SQL CODE|
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/sa_sql_code.png) |

---

#### 3. إنشاء الـ Views:
* تم بناء وإنشاء الـ **Views** بحيث تحتوي على الـ **Denormalize Data**.
* تم تطبيق عملية دمج الجداول المفصولة (**Separated**) إلى جداول موحدة (Table) بناءً على خطة الـ Denormalization.

---
### 📊 Project Views Documentation

| View Dim Customer | View Dim Product | View Dim Fact Sales | View Dim Fact Return |
| :---: | :---: | :---: | :---: |
| ![Customer](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/vwDimCustomer.png) | ![Product](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/vwDimproduct.png) | ![Sales](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/vwfSales.png) | ![Return](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/vwftReturns.png) |





### 🛠️ Data Cleaning & Overcoming Data Challenges (معالجة مشاكل البيانات)

#### 1. مشكلة تكرار الخصم في جدول المبيعات (Sales Denormalization):
* **المشكلة:** عند عمل `Denormalize` لجدول الـ `Sales Header` وجدول `Sales Details`، نلاحظ حدوث مشكلة عند حساب قيمة الـ `Sales Amount`؛ بسبب تكرار الـ `Discount Amount` بنفس القيمة على أكثر من Row لنفس المنتج.
الحل:** للتغلب على هذه المشكلة نقوم بعمل Relocated
لتوزيع الخصم بشكل صحيح وصحيح على مستوى السطور دون تكرار القيمة الإجمالية
---


|Relocated SQL CODE|
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/discount%20precentage%20_%20discount%20value%20_%20%20net%20sales.png) |
---

#### 2. التعامل مع جدول التكاليف (Product Cost History):
* **الخطوة:** في جدول الـ `Product Cost History`، تم تحديد وفلترة الأعمدة المطلوبة فقط، حيث إننا بحاجة إلى عمود الـ `Unit Cost` بس.
* **الآلية:** بيتم جلب الـ `Unit Cost` بناءً واعتماداً على الـ `Year` والـ `Month No` والـ `Country Code` والـ `Product Key`.

---



|UnitCost SQL CODE|
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Unit%20Cost.png) |
---

---

### 🗄️ Design & Create Data Warehouse - DWH (بناء مستودع البيانات)

#### 1. إنشاء جداول الـ DWH:
* تم إنشاء 4 جداول فارغة بنفس أسماء وأعمدة وخصائص الـ 4 جداول اللي في الـ Views (الجداول المجهزة والمنظفة).

---


|Create DWH SQL CODE|
| :---: |
| ![ClickUp](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/CREATE.png) |
---

#### 2. نقل البيانات من الـ SA Views إلى الـ DWH:
* **آلية النقل:** بيتم نقل الداتا من الـ `Views` الخاصة بالـ Staging Area إلى جداول الـ `DWH` مباشرة.
* **Load Method Approach:** الـ Approach اللي تم استخدامه في الـ Load Method لعملية الـ Movement هو أسلوب: **Truncate ⬅️ Insert**.

---


| SA TO DWH 1 | SA TO DWH 2 | SA TO DWH 3 |
| :---: | :---: | :---: | :---: |
| ![SA TO DWH 1](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/SA%20TO%20DWH%201.png) | ![SA TO DWH 2](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/SA%20TO%20DWH%202.png) | ![SA TO DWH 3](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/SA%20TO%20DWH%203.png) 




### 📝 SQL Work Documentation (توثيق عمليات قواعد البيانات)(DWH) على الـ SQL.

#### 📸 لقطة شاشة   للـ SQL:

### 📄 Documentation & Reports

| Doc 1 | Doc 2 | Doc 3 | Doc 4 | Doc 5 |
| :---: | :---: | :---: | :---: | :---: |
| ![Doc 1](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Full%20Architecture%20Overview%20%E2%80%94%20OLAP%20%E2%86%92%20SA%20%E2%86%92%20DWH.png) | ![Doc 2](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Full%20Architecture%20Overview%20%E2%80%94%20OLAP%20%E2%86%92%20SA%20%E2%86%92%20DWH%201.png) | ![Doc 3](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Full%20Architecture%20Overview%20%E2%80%94%20OLAP%20%E2%86%92%20SA%20%E2%86%92%20DWH%202.png) | ![Doc 4](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Full%20Architecture%20Overview%20%E2%80%94%20OLAP%20%E2%86%92%20SA%20%E2%86%92%20DWH%203.png) | ![Doc 5](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/Full%20Architecture%20Overview%20%E2%80%94%20OLAP%20%E2%86%92%20SA%20%E2%86%92%20DWH%204.png) |







### 📊 Get Data from DWH to Power BI (سحب الداتا من المخزن للباور بي آي)

#### 1. الاتصال بالـ DWH:
* تم عمل **Import Connection** بين الـ **Power BI** والـ **DWH** لسحب الجداول الأربعة النظيفة (Fact Sales, Fact Returns, Dim Customer, Dim Product).

#### 2. بناء الـ Data Model:
* تم عمل **Calendar Table** مخصص (Date Dimension) عشان يخدم كل الحسابات الزمنية (Year, Quarter, Month, MTD, YTD...).
* تم بناء العلاقات (**Relationships**) بين جداول الحقائق وجداول الأبعاد بصيغة **Star Schema**.

---

| Data Model |
| :---: |
| ![Data Model](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DATA%20MODEL.jpg) |

---

### 🛠️ Integrate Between Git, VS & Power BI (الربط بين أدوات التحكم والمطورين)

* تم حفظ ملف الباور بي آي بصيغة **.pbip** بدل الصيغة التقليدية **.pbix**، عشان يتوافق مع نظام الـ **Version Control**.
* تم تجهيز بيئة العمل على **Visual Studio**، وتشغيل **Git** داخل الفولدر لمتابعة كل تعديل بيتم على الملفات (DAX Measures, Model Relationships, Report Layout).
* الربط ده بيسمح بعمل **Commits** واضحة لكل تغيير، وده بيسهّل الرجوع لأي نسخة سابقة من المشروع.


### 🎨 Calculations, Visualization & Documentation (الحسابات، الداشبورد والتوثيق)

#### 1. DAX Measures & Calculations:
* تم بناء مجموعة من الـ **Measures** الأساسية والمتقدمة، منها:
  * **Total Net Sales**, **Total Cost**, **Gross Profit**, **Profit Margin %**
  * مقاييس زمنية: **YTD Sales**, **MTD Sales**, **Sales Growth % (YoY)**
  * مقاييس تحليلية: **AOV (Average Order Value)**, **CAC (Customer Acquisition Cost)**

---

| DAX Measures |
| :---: |

| ![DAX 1](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DAX%201.jpeg) | ![DAX 2](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DAX%202.jpeg) | ![DAX 3](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DAX%203.jpeg) | ![DAX 4](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DAX%204.jpeg) | ![DAX 5](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DAX%205.jpeg) |
---

#### 2. Dashboard Design (تصميم الداشبورد):
* تم تصميم داشبورد تفاعلي بيغطي أربع محاور رئيسية: **Costs Overview, Sales Performance, Product Movement, Geographic Distribution**.
* تم استخدام **Slicers, Bookmarks, Tooltips** عشان تجربة مستخدم أفضل لصانع القرار.

---

| Dashboard Overview |
| :---: |


| ![REVENUE](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/REVENUE.png) | ![CUSTOMER](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/CUSTOMER.png) | ![PRODUCT](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/PRODUCT.png) | ![TIME](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/TIME.png) | ![RETURN](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/RETURNS.png) | ![DETAILS](https://github.com/MahmoudAtef-Data/Gym-Chain-Data-Analysis/blob/main/DETAILS.png) |
---

#### 3. Power BI Work Documentation:
* تم عمل توثيق شامل لكل الـ **DAX Measures** ومنطق كل حساب، بالإضافة لتوثيق العلاقات في الـ **Data Model**.

---

| Power BI Documentation |
| :---: |
| ![Power BI Doc]() |

---

## 💡 Phase 4: Key Business Insights & Recommendations (أهم النتائج والتوصيات)

| المشكلة المكتشفة | الأثر على العمل والتجارة | الحل المقترح والموصى به |
|---|---|---|
| ارتفاع التكاليف التشغيلية (Costs) | تقليص صافي الأرباح وعرقلة النمو رغم زيادة حجم المبيعات الإجمالي | مراجعة العقود اللوجستية والاعتماد على الأتمتة لخفض المصاريف الثابتة والمتغيرة |
| ركود بعض المنتجات (No Sales) | تجميد السيولة النقدية وتكدس المخازن وتعرض المنتجات للتلف | إطلاق حملات تصفية سريعة، والاعتماد على نظام Just-In-Time في الشراء والتصنيع المستقبلي |
| انخفاض متوسط الفاتورة (AOV) | ضعف الاستفادة القصوى من العميل الحالي وارتفاع تكلفة الاستحواذ (CAC) | وضع حوافز شرائية مثل الشحن المجاني المشروط أو الخصومات التراكمية الذكية |
| تركز المبيعات جغرافيًا (Revenue) | مخاطرة عالية للغاية في حال تأثر أو ركود هذه الأسواق الرئيسية | توسيع الخطة التسويقية واستهداف المناطق الواعدة التي أظهرت المؤشرات ضعف التواجد فيها حاليًا |

---

## 🧰 Tech Stack

| Category | Tools |
|---|---|
| Database & ETL | SQL Server, T-SQL, Stored Procedures |
| Data Warehousing | Star Schema Design (Fact & Dimension Tables) |
| BI & Visualization | Power BI Desktop, DAX |
| Version Control | Git, GitHub, Visual Studio (.pbip) |
| Project Management | ClickUp |

---

## 📬 Contact

**Mahmoud Atef**
Data Analyst | BI Developer | DAX | SQL | ETL | Python

* GitHub: [MahmoudAtef-Data](https://github.com/MahmoudAtef-Data)
* LinkedIn: *[ضيف رابط البروفايل بتاعك هنا]*

⭐ لو المشروع عجبك، متنساش تدي Star للريبو!
















