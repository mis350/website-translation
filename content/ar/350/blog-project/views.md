---
# Page title
title: View Functions

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Views

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 5

draft: False

---

{{% callout note %}}
انتقل إلى الفرع (branch) **5-views** من **malmarz/isom350-blog** github repo لمشاهدة تنفيذ هذه الخطوة
{{% /callout %}}


المشاهدات (Views) هي وظائف تأخذ طلب HTTP من خادم الويب ، وتعالج الطلب ، ثم تعيد استجابة HTTP المناسبة.  إنها الوظيفة المسؤولة عن معالجة المهام الرئيسية لتطبيق الويب الخاص بنا ، كما أنها مسؤولة عن إنشاء صفحة HTML التي سيتم إرجاعها إلى العميل.

في [مقدمة موجزة عن Django]({{< ref "dev-process#4--create-view-function" >}})، قدمنا ​​نظرة عامة على الشكل المبسط لوظيفة العرض (view) وما يتعين عليهم القيام به.  يوفر Django أيضًا وسائل أخرى يمكننا من خلالها إنشاء وظائف عرض لأداء المهام القياسية بأدنى حد من كتابه الترميز (code).

تتمثل إحدى الوظائف الرئيسية في تطبيق الويب المستند إلى CRUD ، مثل مشروع المدونة الذي نعمل عليه ، في قدرته على عرض:

 1. تفاصيل عنصر واحد مخزنة في قاعدة البيانات الخاصة بنا
 2. قائمة (من القائمة المصفاة) بالعناصر المخزنة في قاعدة البيانات الخاصة بنا.

في حالتنا ، العنصر الموجود في قاعدة البيانات الخاصة بنا هو منشور المدونة.  نريد الوسائل التي يمكننا من خلالها عرض تفاصيل منشور مدونة واحد وأيضًا قائمة منشورات المدونة المتاحة.  يكاد يكون هذا مطلبًا عالميًا في جميع تطبيقات الويب.  يدرك Django هذا الأمر ، وقد جعل إنشاء وظائف عرض لقائمة وجهات نظر تفصيلية للكائنات (Object) أمرًا سهلاً للغاية.  يوفر طرق عرض (views) جاهزة لأداء وظائف قياسية تسمى طرق العرض العامة (generic views).  لاستخدامها ، يمكنك الاستفادة من تصميم OOP لـ Django وتوسيع العرض المطلوب لاحتياجاتك الخاصة ، تمامًا مثل ما فعلناه مع النماذج وواجهة الإدارة المحسّنة.

لنقم بإنشاء طريقة عرض لعرض منشور واحد.  للقيام بذلك ، نحتاج إلى توسيع [العرض المفصل العام] (https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#detailview).  نقوم فقط بتحديد النموذج الذي نريد عرض تفاصيله وتحديد القالب الذي نريد أن يستخدمه Django لتقديم البيانات.  هذه هي الطريقة التي يتم بها ذلك في views.py:

```python
# أولاً نقوم باستيراد العروضات العامة (generic views)
from django.views import generic
# نستورد أيضًا نموذج المنشور الخاص بنا
from .models import Post

# نقوم الآن بتوسيع العرض التفصيلي لإنشاء وظيفة العرض الخاصة بك
class PostDetailView(generic.DetailView):
  model = Post  # نريد أن نعرض المنشورات
  template_name = 'post_detail.html' # المزيد حول القوالب لاحقًا

```

وانتهينا !.  للحصول على العرض التفصيلي ، يجب على مستخدم الموقع تحديد المنشور الذي يرغبون في عرضه وسيقوم Django بعرض صفحة تحتوي على تفاصيل ذلك المنشور.  في تطبيقات الويب ، يتم تحديد المنشور المطلوب في جزء المسار من عنوان url.  سنقوم لاحقًا بتصميم تطبيقنا لجلب منشور إما بناءً على معرفه (ID) أو Slug الخاص به. لذلك إذا طلب المستخدم `/post/1/`, سيخدم Django تفاصيل المنشور الأول. بالمثل ل `/post/2/` أو `/post/3/`. سنتكلم المزيد عن ذلك عندما نغطي URLs.

دعنا نجهز وظيفة العرض لعرض قائمة المنشورات.  لذلك ، قمنا بتوسيع وظيفة [ListView generic] (https://docs.djangoproject.com/en/3.1/ref/class-based-views/generic-display/#listview) في views.py على النحو التالي:

```python
# نقوم بإنشاء العرض (view) من خلال توسيع ListView
class PostListView(generic.ListView):  
  # ال"QuerySet" تستخدم لجلب قائمة المنشورات
  queryset = Post.objects.filter(status=1).order_by('-created_on')
  # المزيد حول القوالب لاحقًا
  template_name = 'post_list.html'
```

يتمثل الاختلاف الوحيد بين استخدام ListView و DetailedView في أنه في DetailedView قمنا بتحديد نموذج ، وسوف يجلب العرض كائنًا واحدًا من هذا النوع من النماذج.  باستخدام ListView ، نحدد QuerySet.  يشبه QuerySet في Django جملة التحديد في SQL ، حيث يتم استخدامه لجلب مجموعة أو قائمة من العناصر التي تطابق معايير معينة.  هنا ، يتم استخدام QuerySet لجلب كائنات Post ، التي لها الحالة = 1 (أي المشاركات المنشورة) ، ويجب أن يتم ترتيبها أولاً بأحدث.  ثم يخبر القالب Django بكيفية إظهارها.

QuerySets هي واحدة من أهم ميزات Django وتكمل نماذج قاعدة بيانات Django.  يسمح لنا بالتحكم في البيانات التي يتم جلبها من قاعدة البيانات.  لمزيد من المعلومات حول كيفية العمل مع كائنات قاعدة البيانات ومجموعات QuerySets ، يرجى الرجوع إلى [توثيق Django على QuerySets] (https://docs.djangoproject.com/en/3.1/topics/db/queries/).

بمجرد الانتهاء ، سيبدو ملف view.py كما يلي:
```python
from django.views import generic
from .models import Post

# قم بانشاء العرض (views) هنا
class PostListView(generic.ListView):
  queryset = Post.objects.filter(status=1).order_by('-created_on')
  template_name = 'post_list.html'

class PostDetailView(generic.DetailView):
  model = Post
  template_name = 'post_detail.html'
```

الآن تم إنشاء وظيفة العرض ، لكنها لم تعرض بعد لمستخدمينا.  لا يمكنهم الوصول إليه من المستعرضات الخاصة بهم.  لذلك ، يجب علينا توصيل وظيفة العرض بعنوان URL لموقع الويب وتعيين مسار لها كما سنفعل في الخطوة التالية.

 لمزيد من المعلومات حول استخدام [عرض Django العام ، يرجى الرجوع إلى وثائق Django] (https://docs.djangoproject.com/en/3.1/topics/class-based-views/generic-display/).