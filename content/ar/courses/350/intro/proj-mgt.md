---
# Page title
title: Project Management

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Project Management

# Page summary for search engines.
summary: Second programming course for MIS majors utilizing Python to build data-driven business applications.

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 4

draft: False
diagram: True

---

تتمحور إدارة المشروع حول ضمان تنفيذ المشروع وفقًا للمواصفات وضمن ميزانية الوقت والموارد.  يتضمن ذلك التأكد من أن كل عضو في الفريق يعرف ما يفترض أن يفعله.

 سنبتعد عن إدارة المشاريع التقليدية ونستخدم نهجًا أكثر مرونة. يتمثل الاختلاف الرئيسي في النهج المرن  أنه
- من المتوقع أن تتغير متطلبات التطوير  وبالتالي يستخدم الفريق الأدوات ويعمل مع توقع إمكانية تغيير المتطلبات.
- مشاركة العملاء والمطورين في إدارة المشروع ضرورية للنجاح.  يجب أن يكون للمطورين مبادرة لاختيار المهام التي يعملون عليها والمشاركة في تحديث المتطلبات والإبلاغ عن التقدم المحرز في عملهم.

تم أيضًا تغيير دور مدير المشروع بشكل طفيف:

 - قد يساهم في المشروع مثل أي مطور آخر من خلال العمل على المتطلبات واقتراح متطلبات جديدة.
 - يضمن وجود مهام كافية لإبقاء الجميع مشغولين
 - توجيه المشروع من خلال تحديد أولويات المهام ومراقبة التقدم وحل المشكلات.
 - كما نمنح مدير المشروع مسؤولية دمج عمل أعضاء الفريق في المشروع.  قد تختار الفرق المختلفة مهام سير عمل مختلفة.
 - تهيئة بيئة المشروع حيث يمكن لأعضاء الفريق التعاون.

### انشاء مشروع/ريبو GitHub

هناك طريقتان رئيسيتان يمكن لمدير المشروع من خلالهما إنشاء مشروع:

 1. إنشاء ريبو (Repository) فارغ جديد إما من GitHub أو دفع (Push) مشروع جديد من Replit.com إلى GitHub.
 2. عمل (Fork) مشروع قائم موجود على GitHub ، والذي من شأنه أن يسمح للفريق بالبناء على هذا المشروع الحالي.

 بمجرد إنشاء المشروع ، سيكون الأمر يتعلق بالتنسيق مع أعضاء الفريق وتعيين المهام والتعاون لضمان تسليم المشروع للنظام الذي كان من المفترض بناؤه.  يقدم GitHub عددًا من الأدوات المفيدة لتمكين مديري المشاريع من إدارة المشاريع ، والتي سنناقشها في القسم التالي.

## أدوات إدارة المشروع

 بمجرد إعداد المشروع ، تتوفر الأدوات التالية التي يستخدمها كل من مدير المشروع وأعضاء الفريق للتنسيق:

### 1. مشكلات GitHub

 يمكن أن تمثل مشكلة GitHub أشياء كثيرة في مشروع برمجي.  سواء كانت ميزة تحتاج إلى البناء ، أو خطأ يحتاج إلى إصلاح ، أو فكرة يجب مناقشتها ، أو وثائق يجب كتابتها ، أو أي مهمة أخرى (البرمجة أو التنسيق أو غير ذلك) التي يحتاج فريق المشروع إلى إكمالها أو مناقشتها ، يمكن تمثيلها  باستخدام مشكلة في GitHub.  يوضح الشكل التالي مثالاً لمشروع على GitHub يسمى **Ruby on Rails** حيث يتعاون المئات من المطورين.  يمكنك معرفة كيف تصف بعض المشكلات المشكلات التي تحتاج إلى إصلاح وغيرها من طلبات الميزات.  البعض لديه مناقشات مرتبطة بهم والبعض الآخر ينتظرون مطورًا لبدء العمل عليها:

{{< figure src="courses/350/issues.png" caption="Example Issue List from Ruby on Rails Project" >}}

من الطرق الجيدة لبدء قائمة المشكلات تحويل متطلبات المشروع إلى قائمة بالمشكلات على GitHub.  ولكن عند القيام بذلك ، يجب عليك التأكد من أن كل مشكلة تصف مهمة محددة للغاية.  سينظر أعضاء الفريق إلى قائمة المشكلات ويحددون المهمة التي يمكنهم العمل عليها.  على سبيل المثال ، يحتوي المشروع المستخدم لترجمة موقع الويب الحالي على قائمة المشكلات التالية:

{{< figure src="courses/350/translate-issues.png" caption="Example Issue List from Ruby on Rails Project" >}}

يمكنك أن ترى أن القائمة بسيطة للغاية ، بالنظر إلى أن المشروع بسيط.  كل مشكلة تمثل ترجمة ملف واحد.  ستكون هذه أداة تنسيق مفيدة للغاية بين أعضاء الفريق ، حيث يمكن لأحد الأعضاء اختيار ترجمة أحد الملفات عن طريق تعيين المشروع لأنفسهم.  سيسمح هذا للأعضاء الآخرين بمعرفة أن هذه المهمة قيد العمل على أحد زملائهم في الفريق وأنهم بحاجة إلى البحث عن مهمة أخرى لإكمالها.  يمكن لمديري المشروع أيضًا اختيار تعيين المشكلة لأعضاء محددين حتى يعرفوا أن المهمة هي مسؤوليتهم.  يوضح الشكل التالي كيف يمكن تعيين المهام:

{{< figure src="courses/350/translate-issues.png" caption="Assigning an Issue to A Team Member or to Yourself" >}}

{{% callout note %}}
تأكد من أنك تقوم دائمًا بتعيين مهمة لنفسك قبل أن تبدأ العمل في مهمة.  إذا لم تكن المهمة في القائمة ، فقم بإنشائها.  سيسمح هذا لأعضاء فريقك بمعرفة ما تعمل عليه.
{{% /callout %}}

قائمة المشكلات هي قائمة ديناميكية.  يجب أن يتغير على أساس يومي / أسبوعي إذا كان المشروع نشطًا.  نظرًا لأن المشكلات تمثل المتطلبات ، فإنها تعكس أيضًا كيفية تغيير المتطلبات باستمرار أثناء تحديث قائمة المشكلات.

#### **من يكتب المشكلات؟**

 يتم تقاسم مسؤولية كتابة المشكلات بين مدير المشروع والمطورين وحتى مستخدمي المشروع.  إذا كان لدى أحد الأعضاء فكرة جديدة يحتاجون إلى كتابتها ، أو إذا اكتشفوا خطأً يحتاج إلى إصلاح ، فإنهم يلتقطون ذلك عن طريق إنشاء مشكلة ووصف الفكرة أو المشكلة.  يحتاج مدير المشروع إلى التأكد من وجود مشكلات كافية في قائمة المشكلات لأعضاء الفريق للعثور على عمل لإكماله ، كما أن مدير المشروع مسؤول أيضًا عن تحديد أولويات العمل.  لكن أولوية المشكلات غير معروضة هنا ، بل تظهر في لوحة المشروع التي سنشرحها بعد ذلك.

{{% callout note %}}
سواء كنت مدير المشروع أو عضوًا في الفريق ، يمكنك إنشاء مشكلات لالتقاط الأفكار والمهام التي تريد أن يعمل عليها الفريق.
{{% /callout %}}

### 2. لوحة المشروع

 تقدم لوحة المشروع نظرة عامة مرئية حول كيفية تقدم المشروع.  تظهر مهام المشروع (المعروفة بالمشكلات على GitHub) كتذاكر.  لذلك ، سنستخدم المصطلحات **المشكلة والمهمة والتذكرة** بالتبادل.  يتم تنظيم التذاكر في ثلاثة أعمدة مختلفة على النحو التالي:

 1. **المهام:** يتم وضع التذاكر التي تم إنشاؤها حديثًا هنا ولا يعمل عليها أحد.  يتضمن ذلك الأخطاء والميزات الجديدة التي قد يرغب المطورون في دمجها في المشروع.  التذاكر الموضوعة في الجزء العلوي من العمود لها أولوية أعلى ، وتقع على عاتق مدير المشروع مسؤولية تنظيم هذه التذاكر حسب الأولوية في هذا العمود.  يتم تشجيع المطورين على اختيار تذاكر للعمل عليها من أعلى عمود **المهام**.

{{< figure src="courses/350/project-board.png" caption="Project Board Showing the Columns and Tickets" >}}

2. **قيد التنفيذ:** يجب نقل التذاكر التي يطالب بها الأعضاء للعمل عليها من قبل العضو الذي يعمل عليها ، حتى يعرف مدير المشروعما يتم العمل عليه.  يوضح لك المقطع التالي كيفية المطالبة بتذكرة للعمل عليها بنفسك:

![](/gifs/claim-ticket.gif)


3. **تم:** تم نقل التذاكر المكتملة هنا ، حيث يعلم مدير المشروع أن هناك طلب سحب يجب دمجه.  بمجرد دمج طلب السحب ، يتم أرشفةالتذكرة.  ما عليك سوى سحب التذكرة التي أكملتها من العمود **قيد التقدم** إلى العمود **تم** ولا تنس إنشاء طلب سحب.


{{% callout note %}}
يجب على مدير المشروع طلب التذاكر في قائمة المهام حسب الأولوية من الأعلى إلى الأسفل.  يتم تشجيع أعضاء الفريق على اختيار التذاكر للعمل عليها من أعلى قائمة المهام.
{{% /callout %}}

يقوم أعضاء الفريق بنقل التذاكر بشكل صحيح من عمود إلى آخر ، سيحصل مدير المشروع بسهولة على فكرة عامة عمن يعمل في أي مهمة.  تشير التذكرة المتبقية لفترة طويلة جدًا إلى وجود مشكلة في هذه المهمة أو في العضو الذي يعمل عليها.  سيتطلب ذلك تدخل مدير المشروع.

**اجتماعات تنسيق أسبوعية أو نصف أسبوعية:** سيكون من المفيد جدًا أن يجتمع الفريق على أساس أسبوعي أو كل أسبوعين حيث يتم عرض لوحة المشروع وتناقش أولوية تذاكر المهام وأي تحديات تواجه المشروع  .  يمكن للأعضاء أيضًا العمل معًا لإيجاد حلول مشتركة أو اقتراح تذاكر جديدة لتضمينها في قائمة المهام ..


## نصائح حول كتابة المشكلات / التذاكر

أفضل طريقة لكتابة أوصاف مهمة مفيدة هي كتابة المشكلات / التذاكر كـ **قصص مستخدم**.  تصف قصص المستخدم وظائف النظام والمهام التي يجب العمل عليها من منظور المستخدم.  إنها توضح ما يفعله المستخدم ولماذا.  يجب أن تصف قصة مستخدم واحد وظيفة واحدة.  إذا كانت الوظيفة معقدة ، فيمكنك تقسيمها إلى قصص مستخدم أصغر.

تعد [مشاركة مدونة حول كيفية كتابة قصص المستخدم] (https://medium.com/innovation-machine/how-and-why-to-write-great-user-stories-f5a110668246) بداية ممتازة لأي شخص يبحث  لتحسين طريقة كتابتهم للتذاكر لمشروع برمجي.
