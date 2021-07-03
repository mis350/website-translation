---
# Page title
title: ISOM 350 - تطوير تطبيقات الأعمال

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: ISOM 350

# Page summary for search engines.
summary: المقرر الثاني ضمن منهج تخصص نظم المعلومات الدري والذي يعني باستخدام لغة البايثون لتطوير تطبيقات الأعمال

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 1

draft: False

# Featured image
# To use, place an image named `featured.jpg/png` in your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
# Set `preview_only` to `true` to just use the image for thumbnails.
image:
  placement: 1
  caption: "Python logo"
  focal_point: "smart"
  preview_only: false
  alt_text: Python logo

---

## المتطلبات

سنستخدك موقع replit.com كأداة التطوير الأساسية لهذا المقرر، والمطلوب من جميع الطلبة اتمام الآتي استعداداً للمقرر:

- قراءة  [الخطة التعليمية للمقرر](https://bit.ly/mis350_syl)
- التسجيل [في فريق replit للمقرر](https://replit.com/teams/join/slpharshbwpedtcbfdfsnrkqjlkjpabh-miscba)
- التسجيل في خدمة [{{< icon name="github" pack="fab" >}}github.com](https://github.com/join)
  - ثم المشاركة [ بفريق المقرر على {{< icon name="github" pack="fab" >}}GitHub](https://classroom.github.com/classrooms/17110202-mis350-spring21)
- اتمام مقرر مبادئ في البمجة (لا يشترط أن يكون بلغة البايثون)
- التعود على قراءة [دليل استخدام {{< icon name="python" pack="fab" >}}Django](https://docs.djangoproject.com/en/3.1/)

## المصادر المطلوبة

- {{< icon name="book-open" pack="fas" >}} هذا الموقع ابتداءً [بالمقدمة]({{< ref "courses/350/intro" >}})
- [{{< icon name="file-powerpoint" pack="fas" >}}شرائح العرض لهذا المقرر]({{< ref "courses/350/slides" >}})
- [{{< icon name="python" pack="fab" >}}دليل استخدام Django](https://docs.djangoproject.com/en/3.1/)



## متطلبات اختيارية

- الكتاب لمقرر مبادئ البرمجة سكون مفيد كمرجع للغة وننصح باقتنائه وهو:


  Tony Gaddis, [Starting Out with Python](
https://www.pearson.com/uk/educators/higher-education-educators/program/Gaddis-Starting-Out-with-Python-Global-Edition-4th-Edition/PGM1963337.html), Global Edition, 4th Edition
  Haywood Community College, 2019 [{{< icon name="file-pdf" pack="fas" >}} شراؤه على الانترنت](https://collegestudenttextbook.org/product/starting-out-with-python-global-4th-edition-ebook/)

{{< spoiler text="متطلبات اخرى.." >}}
While this is not required, should you choose to run a Django development server locally on your machine to avoid using the internet while development, you will need to install the following packages:

- Install [anacoda python](https://www.anaconda.com/products/individual#Downloads)
- Install [Visual Studio Code](https://code.visualstudio.com/download)
- Install Django using terminal on mac, or CMD on windows, by typing:
```bash
pip install django
```

**Note:** It will be your responsibility to read the Django documentation on how to setup the development environment on your computer.
{{< /spoiler >}}

## خطة الدراسة

| Week  | Topic  | Slides | Assignment  |
|---|---|---|---|
| 1 | [المقدمة]({{< ref "courses/350/intro" >}})  |  [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/intro" >}}) | [أكمل متطلبات المقرر]({{< ref "courses/350/#requirements">}})  |
| 2 |  [مراجعة لغة البايثون]({{< ref "courses/350/intro/python" >}})  | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/python" >}})  |  [إنشاء فريق على GitHub](https://classroom.github.com/g/kxc1jQKA) |
| 3 |  [التعاون و التطوير الجماعي]({{< ref "courses/350/intro/collab" >}})  | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "slides/350/collab" >}})  | [تمرين على التطوير الجماعي](https://classroom.github.com/g/7iv9aOyv)  |
| 3 |  [إدارة المشروع]({{< ref "courses/350/intro/proj-mgt" >}}) | | [شارك في ترجمة هذا الموقع](https://github.com/mis350/website-translation) |
| 3 |  [تطبيقات الويب]({{< ref "courses/350/intro/webapplications.md" >}}) | [{{< icon name="file-powerpoint" pack="fas" >}}]({{< ref "/slides/350/webapps" >}})  |  |
| 4 |  [مقدمة لاستخدام Django]({{< ref "courses/350/intro/dev-process.md" >}}) | | |
| 4 |  [إعداد المشروع]({{< ref "courses/350/blog-project/setup.md" >}}) | | |
| 4 |  [نماذج البيانات]({{< ref "courses/350/blog-project/models.md" >}}) | | |
