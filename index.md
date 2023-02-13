---
layout: home
title: 🏠 Home
nav_exclude: false
nav_order: 1
---

# {{ site.tagline }}
{: .mb-2 }
{{ site.description }}
{: .fs-6 .fw-300 }

<!-- for the old icon: >
 <!-- <img src='favicon.ico' style='vertical-align: text-top' width=37> -->

{{ site.staffersnobio }}

{: .note }
As you start to study for the Midterm Exam, make sure to check out past exams at [practice.dsc80.com](https://practice.dsc80.com) and the other resources linked [here](resources). Check out the logistics post [on Ed](https://edstem.org/us/courses/32057/discussion/2579020).

[Jump to the current week](#week-5-missingness-mechanisms-and-imputation){: .btn }

{% for module in site.modules %}
{{ module }}
{% endfor %}

<!-- <center>
<iframe src="10-80-enrollment.html" scrolling="no" style="border:none;" seamless="seamless" height="480" width="100%">
</center> -->