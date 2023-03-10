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

[Jump to the current week](#week-8-modeling-and-feature-engineering){: .btn }

<!-- {: .note }
**Some office hours on Wednesday 3/8, Thursday 3/9, and Tuesday 3/21 are being held in the SDSC Auditorium instead of the 2nd floor – look closely at the [calendar](calendar) for details.** Treat these office hours as study sessions – come to them to work on projects or study for the final exam! -->

{% for module in site.modules %}
{{ module }}
{% endfor %}

<!-- <center>
<iframe src="10-80-enrollment.html" scrolling="no" style="border:none;" seamless="seamless" height="480" width="100%">
</center> -->