---
layout: default
title: Office Hours
has_children: false
nav_order: 4
permalink: /office-hours/
---

{% assign variables = site.data[site.data_folder].variables %}
{% assign course_calendar = site.data[site.data_folder].course_calendar %}

<!-- ## Contact Info -->

<!-- **Instructor** <br/> {{ variables.instructor.name }} - [{{ variables.instructor.email }}](mailto:{{ variables.instructor.email }})

**Teaching Assistant (TA)**
{% for ta in variables.teaching_assistants %} <br/> {{ ta.name }} - [{{ ta.email }}](mailto:{{ ta.email }}) {% endfor %}
 -->
<!-- **Instructional Assistant (IA)**
{% for ia in variables.instructional_assistants %} <br/> {{ ia.name }} - [{{ ia.email }}](mailto:{{ ia.email }}) {% endfor %} -->
{: .fs-3 }

# Office Hours

Office hours are a great place to personally interact. Beyond projects and course material, we are interested in your goals, career endeavors, and what you want to gain from COGS 169.

<table style="table-layout: fixed; text-align: center; width: 100%;">
    <thead>
        <tr class="header">
            <th style="width: 30%;"> Staff </th>
            <th style="width: 20%;"> E-mail </th>
            <th style="width: 30%;"> Day & Time </th>
            <th style="width: 20%;"> Location </th>
            <!-- <th style="width: 12.5%;"> Link </th> -->
            <!-- <th style="width: 12.5%;"> Pass </th> -->
        </tr>
    </thead>
    <tbody>
        {% for oh in variables.instructor.office_hours %}
        <tr>
            <td> {{ variables.instructor.name }} </td>
            <td> {{ variables.instructor.email }} </td>
            <td> {{ oh.day }} {{ oh.time }} </td>
            <td> {{ oh.location }} </td>
        </tr>
        {% endfor %}
        {% for oh in variables.teaching_assistant.office_hours %}
        <tr>
            <td> {{ variables.teaching_assistant.name }} </td>
            <td> {{ variables.teaching_assistant.email }} </td>
            <td> {{ oh.day }} {{ oh.time }} </td>
            <td> {{ oh.location }} </td>
        </tr>
        {% endfor %}
    </tbody>
</table>

<!-- Zoom Links can be found on Canvas homepage. -->

{: .note .fs-3 }
If you are unable to join or are having other issues, please reach out before or after class!
