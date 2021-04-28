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

In the previous step, we created a very simple default admin page. Django allows us to configure how the admin works by defining an ModelAdmin class in blog/admin.py.

في الخطوة السابقة انشأنا صفحة مسؤول افتراضية بسيطة. جانغو يتيح  لنا فهم طريقة العمل المسؤول بالتعريف عن فئة مسؤول النموذج (ModelAdmin) في blog/admin.py.

We started with the following:

بدأنا بالتالي:


```python
from django.contrib import admin

from .models import Post

admin.site.register(Post)
```

Let's modify it to have a configurable admin interface by creating a PostAdmin class that inherits from the ModelAdmin class:

لنعدلها للحصول على واجهة مسؤول عن طريق انشاء فئة PostAdmin المتوارثة من فئة ModelAdmin



```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
  pass

admin.site.register(Post, PostAdmin) # Notice this line changed
```

Notice how we defined `class PostAdmin(admin.ModelAdmin)` which is empty. This means that inherits everything the ModelAdmin has to offer. If you test it you will notice nothing changed about our admin interface and that what we just did is just a longer version of what we did earlier. However, the new version is more flexible and allows as to configure the admin.

لاحظ كيف عرفنا `class PostAdmin(admin.ModelAdmin)` الفارغة, 
هذا يعني ان يرث كل ماهو موجود في ModelAdmin.
 إذا قمت باختباره, لن تلاحظ أي تغيير في واجهة المشرف الخاصة بنا وأن ما فعلناه للتو هو مجرد نسخة أطول مما فعلناه سابقًا. ومع ذلك ، فإن الإصدار الجديد أكثر مرونة ويسمح بفهم المسؤول. 

So let's first modify what is shown in the list view of the Post admin, so modify the code to look like this:

سنعدل اولًا ما يظهر في قائمة Post admin , 
لذا قم بتعديل الكود ليبدو كالتالي:

```python
from django.contrib import admin
from .models import Post



class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on') # This line was added

admin.site.register(Post, PostAdmin)
```

Here we requested that the table displaying the Posts should display a column showing the title, slug, status, and created_on fields. Our list of Post in admin now look like this:

هنا طلبنا ان الجدول الذي يعرض المنشورات يجب ان يعرض عمود يظهر العنوان و رابط الموقع والحالة والحقول المنشأة. قائمة المنشورات الخاصة بنا شتظهر بهذا الشكل:


{{< figure src="courses/350/admin-list.png" caption="Improved Admin Post List" >}}

Next let's add the ability yo filter this list by status:

بعد ذلك ، دعنا نضيف القدرة على تصفية هذه القائمة حسب الحالة:  

```python
from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    list_display = ('title', 'slug', 'status','created_on')
    list_filter = ("status",) # This line was added


admin.site.register(Post, PostAdmin)
```

Now we have the option to list all posts, the draft posts only, or published posts only:

الآن لدينا الخيار بتصنيف (اظهار) كل المنشورات, او المنشورات المحفوظة فقط, او المنشورات المنشرة فقط.

{{< figure src="courses/350/list-filter.png" caption="Admin Post Filter" >}}

As you can see, whenever we want to configure the admin, we add an attribute (a line) that configures the features of the ModelAdmin for our posts and these configurations are reflected on our model admin.

كما ترى ، كلما أردنا تهيئة المسؤول ، نضيف سمة (سطر) تقوم بتهيئة ميزات ModelAdmin لمنشوراتنا وتنعكس هذه التهيئات في نموذج المسؤول لدينا. 

Let's look at two more configurations, first, lets add the ability to search posts. Here we are adding the ability to search posts in the admin interface using their title and content fields:

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

Finally, when creating a post, we would like to pre-populate the slug field with information from the title. A slug is usually constructed by replacing spaces in the title with hyphens (-). Since this is a very common operation in web development, django provides it out of the box for us:

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

There is certainly much more abot the Admin interface that we cannot cover in this course. The way to learn what is available is to keep reading the [Django admin documentation](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/) and experimenting with new features.

هناك بالتأكيد المزيد حول واجهة المسؤول التي لا يمكننا تغطيتها في هذه الدورة التدريبية. الطريقة لمعرفة ما هو متاح هي الاستمرار في قراءة: [Django admin documentation](https://docs.djangoproject.com/en/3.1/ref/contrib/admin/) 
وتجريب الميزات الجديدةز
