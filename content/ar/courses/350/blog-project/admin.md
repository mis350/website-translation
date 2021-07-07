---
# Page title
title: ادارة واجهه المستخدم

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: ادارة

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: كتاب

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 3

draft: خطا


---

{{% callout note %}}
Switch to branch **3-admin** from **malmarz/isom350-blog** github repo to see this step's implementation
{{% /callout %}}

لتسمح لواجهه الإدارة لمسؤول عن الموقع بإدارة البيانات لتطبيق الويب. ومع ذلك ، قبل أن تتمكن من استخدامه ، يجب أن تخبر Django بنماذج البيانات التي تريد إدارتها ويجب عليك مسؤل واجهة الإدارة.

First, check the file mysite/urls.py, and check whether the following line exists:
```python
urlpatterns = [
    path('admin/', admin.site.urls),    
]
```
 يخبر django أنه إذا قام شخص ما بفتح / path / admin على تطبيق الويب ، سيتم عرض شاشة تسجيل الدخول لواجهة المسؤول. إذا لم يكن هذا السطر موجودًا في ملف urls.py ، في العمل و هذا يعني أن django اذا كانت الاإعدادت جاهزة لتمكين  ، عند استخدام نموذج الإستبدال django admin interface ، سيتم تكوين واجهة الإدارة لك.

حاول الآن تسجيل الدخول. ستلاحظ أنه لا يمكنك التسجيل وليس لديك حق الوصول إلى واجهة المسؤول. لاستخدام واجهة المسؤول ، تحتاج إلى إنشاء مستخدم مسؤول. للقيام بذلك ، نحتاج إلى التأكد من القيام بما يلي:

1. تم إنشاء الجداول في قاعدة البيانات المطابقة للنماذج في مشروعنا Django. هناك المزيد الذي يفعله Django إلى جانب نموذج المدونة. يدير المصادقة لواجهة المسؤول وسيحتاج إلى إنشاء جداول لتخزين بيانات اعتماد المسؤول المستخدم. في هذه الخطوة ، يجب تشغيل أوامر shell التالية:

```bash
python manage.py makemigrations
python manage.py migrate
```

سيقوم الأمر الأول بإعداد جميع الأوامر SQL لإنشاء جداول قاعدة البيانات لمشروعنا. أمر shell الثاني سينفذه وينشئ الجداول.

2. بمجرد تكوين قاعدة البيانات بشكل صحيح ، يمكننا بعد ذلك إنشاء المستخدم المسؤول باستخدام أمر shell التالي:
. 
```bash
python manage.py createsuperuser

```
سيتم تزويدك بالتعليمات ، اتبعها لإنشاء المستخدم المسؤول واستخدام المعلومات لتسجيل الدخول إلى واجهة المسؤول. ستلاحظ أن المنشورات الخاصة بمدونتنا غير موجودة. لذلك دعنا نخبر واجهة المسؤول بأننا نريد إدارة المنشورات في تطبيق المدونة الخاص بنا باستخدام واجهة المسؤول.

لذلك ، افتح blog / admin.py وقم بتحديثه ليشمل ما يلي:

```python
from django.contrib import admin

from .models import Post

admin.site.register(Post)
```

هنا قمنا باستيراد نموذج Post ، ثم سجلناه في موقع المسؤول. هذا يخبر Django نريد أن تتم إدارة نموذج Post بواسطة واجهة الإدارة. قم الآن بتسجيل الدخول إلى واجهة المسؤول ، وسترى أنه يمكنك إضافة / تحرير / حذف منشورات المدونة من واجهة المسؤول.
يمكنك العثور على المزيد على واجهة الإدارة بالرجوع إلى
 [وثائق Django على واجهة الإدارة](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/)
