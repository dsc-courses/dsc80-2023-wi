---
layout: page
title: 👩‍🏫 Staff
description: A listing of all the course staff members.
nav_order: 6
---

# 👩‍🏫 Staff

## Instructor

{% assign instructors = site.staffers | where: 'role', 'Instructor' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

## Tutors

{% assign staff = site.staffers | where: 'role', 'Staff' %}
<div class="role">
  {% for staffer in staff %}
  {{ staffer }}
  {% endfor %}
</div>
