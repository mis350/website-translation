---
# Page title
title: ISOM 350 - Business Application Development

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Improved Admin

# Page summary for search engines.
summary: Second programming course for MIS majors utilizing Python to build data-driven business applications.

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 4

draft: False


---

{{% callout note %}}
Switch to branch **4-improved admin** from **malmarz/isom350-blog** github repo to see this step's implementation
{{% /callout %}}

في الخطوة السابقة انشأنا صفحة مسؤول افتراضية بسيطة. جانغو يتيح  لنا فهم طريقة العمل المسؤول بالتعريف عن فئة مسؤول النموذج (ModelAdmin) في blog/admin.py.


بدأنا بالتالي


```python
from django.contrib import admin

from .models import Post

admin.site.register(Post)
```

لنعدلها للحصول على واجهة مسؤول عن طريق انشاء فئة PostAdmin المتوارثة من فئة ModelAdmin

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
  pass

admin.site.register(Post, PostAdmin) # Notice this line changed
```

لاحظ كيف عرفنا `class PostAdmin(admin.ModelAdmin)` الفارغة, 
هذا يعني ان يرث كل ماهو موجود في ModelAdmin.
 إذا قمت باختباره, لن تلاحظ أي تغيير في واجهة المشرف الخاصة بنا وأن ما فعلناه للتو هو مجرد نسخة أطول مما فعلناه سابقًا. ومع ذلك ، فإن الإصدار الجديد أكثر مرونة ويسمح بفهم المسؤول. 

سنعدل اولًا ما يظهر في قائمة Post admin , 
لذا قم بتعديل الكود ليبدو كالتالي:



```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on') # This line was added

admin.site.register(Post, PostAdmin)
```

هنا طلبنا ان الجدول الذي يعرض المنشورات يجب ان يعرض عمود يظهر العنوان و رابط الموقع والحالة والحقول المنشأة. قائمة المنشورات الخاصة بنا شتظهر بهذا الشكل:

{{< figure src="courses/350/admin-list.png" caption="Improved Admin Post List" >}}

بعد ذلك ، دعنا نضيف القدرة على تصفية هذه القائمة حسب الحالة:  

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added


admin.site.register(Post, PostAdmin)
```

الآن لدينا الخيار بتصنيف (اظهار) كل المنشورات, او المنشورات المحفوظة فقط, او المنشورات المنشرة فقط.

{{< figure src="courses/350/list-filter.png" caption="Admin Post Filter" >}}

كما ترى ، كلما أردنا تهيئة المسؤول ، نضيف سمة (سطر) تقوم بتهيئة ميزات ModelAdmin لمنشوراتنا وتنعكس هذه التهيئات في نموذج المسؤول لدينا. 

لننظر إلى تهيئتين اخريين, أولًا, لنضيف امكانية البحث عن المنشورات, هنا نحن اضفنا امكانية البحث عن المنشورات في واجهة المسؤول بإستخدام حقول العنوان والمحتوى.



```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added
    search_fields = ['title', 'content']

admin.site.register(Post, PostAdmin)
```

اخيرًا, عند انشاء منشور, نود ملء حفل رابط الموقع بمعلومات من العنوان الرئيسي.
عادة ما يتم انشاء رابط الموقع (Slug) عن طريق استبدال المسافات في العنوان ب (-)
نظرَا لكونها عملية شائعة في تطوير الويب فإن جانغو يوفرها لنا


```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added
    search_fields = ['title', 'content']
    prepopulated_fields = {'slug': ('title',)}
admin.site.register(Post, PostAdmin)
```

هناك بالتأكيد المزيد حول واجهة المسؤول التي لا يمكننا تغطيتها في هذه الدورة التدريبية. الطريقة لمعرفة ما هو متاح هي الاستمرار في قراءة: [Django admin documentation](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/) 
وتجريب الميزات الجديدة.


