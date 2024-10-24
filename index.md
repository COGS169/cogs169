---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title: Home
layout: default
nav_exclude: false
nav_order: 1
---

{% assign variables = site.data[site.data_folder].variables %}
{% assign course_calendar = site.data[site.data_folder].course_calendar %}
<!-- Fall quarter starts in Week 0 while the other quarters start in Week 1 -->
{% assign offset_week = 1 %}

<script>
if (site.data_folder.charAt(0) === 'f') {
    {% assign offset_week = 0 %}
</script>

{: .text-grey-dk-200 .lh-0 .pt-4 }
# Genetic Information for Behavior

{: .text-grey-dk-300 .fw-300 .lh-0 }
## COGS 169 - UC San Diego - Prof. Shannon Ellis

{{ variables.quarter }}
{: .md-badge-purple }

{{ variables.building }}
{: .md-badge-purple }

{{ variables.timings }}
{: .md-badge-purple }


## Welcome <span title="https://jarv.is/" class="wave">👋</span> 

We're really excited to be teaching you all about genetics and what we know about its relation to behavior. All relevant info, e.g. due dates, assignment information, etc. are found on this website. We look forward to teaching and working with all of you and hope to meet you in office hours.
{: .fs-3 }

{: .note .fs-2 }
This course is meant to be a smaller-enrollment upper-division elective where students can get to know one another and can get detailed feedback on their work, so staff will be helping to try to keep enrollment reasonable. As such, unless many students drop the course, there will not be much enrollment off of the waitlist. Also, Prof does not have access to the waitlist or the ability to directly enroll anyone into the class, so please email [{{ variables.cogsadvising }}](mailto:{{ variables.cogsadvising }}) with further questions.

## Course Calendar

{% assign first_date = course_calendar[0].date | date: '%s' %}
{% assign first_day = course_calendar[0].date | date: '%w' %}
{% assign prev_week_no = offset_week %}
<table style="table-layout: fixed; text-align: left; width: 100%;">
    <colspan>
        <col style="width: 15%; border: none">
        <col style="width: 18%; border: none">
        <col style="width: 17%; border: none">
        <col style="width: 12%; border: none">
        <col style="width: 18%; border: none">
        <col style="width: 17%; border: none">
    </colspan>
    <thead>
        <tr class="header">
            <th colspan="6" style="font-size-adjust:0.70"> Week {{ offset_week }} </th>
        </tr>
        <tr class="header">
            <th style="text-align: center; font-size-adjust:0.70"> Date </th>
            <th style="text-align: center; font-size-adjust:0.70"> Lecture </th>
            <th style="text-align: center; font-size-adjust:0.70"> Reading(s) </th>
            <th style="text-align: center; font-size-adjust:0.70"> Main Points </th>
            <th style="text-align: center; font-size-adjust:0.70"> Optional Reading(s)</th>
            <th style="text-align: center; font-size-adjust:0.70"> Due </th>
        </tr>
    </thead>
    <tbody>
{% for row in course_calendar %}
    {% assign week_no = row.date | date: '%s' | minus: first_date | divided_by: 60 | divided_by: 60 | divided_by: 24 | plus: first_day | minus: 1 | divided_by: 7 | plus: offset_week %}
    <!-- Week number is calculated as follows. Take the current row date as epoch and subtract the first date from course calendar.
    Convert it to number of days (How many days ahead is the current row date from first date) and add the day number of the first day of the week.
    Sunday is considered as 0, Monday as 1 and so on (strftime), but to start our week from Monday, we subtract 1 and then divide by 7 to get week no
    Offset week is used since fall quarter starts in Week 0 while other quarters start in Week 1 -->
    {% if week_no != prev_week_no %}
    </tbody>
</table>
<table style="table-layout: fixed; text-align: left; width: 100%;">
    <colspan>
        <col style="width: 15%; border: none">
        <col style="width: 18%; border: none">
        <col style="width: 17%; border: none">
        <col style="width: 12%; border: none">
        <col style="width: 18%; border: none">
        <col style="width: 17%; border: none">
    </colspan>
    <thead>
        <tr class="header">
            <th colspan="6" style="font-size-adjust:0.70"> Week {{ week_no }} </th>
         </tr>
        <tr class="header">
            <th style="text-align: center; font-size-adjust:0.70"> Date </th>
            <th style="text-align: center; font-size-adjust:0.70"> Lecture </th>
            <th style="text-align: center; font-size-adjust:0.70"> Reading(s) </th>
            <th style="text-align: center; font-size-adjust:0.70"> Main Points </th>
            <th style="text-align: center; font-size-adjust:0.70"> Optional Reading(s)</th>
            <th style="text-align: center; font-size-adjust:0.70"> Due </th>
        </tr>
    </thead>
    <tbody>
    {% endif %}
    {% assign prev_week_no = week_no %}
        <tr>
            <td style="text-align: center"> {{ row.date | date: "%a, %b %d" }} </td>
            <td style="padding-left: 4%"> {% if row.slides %} <a href="{{ row.slides }}"> {{ row.title }} </a> {% else %} {{ row.title }} {% endif %} </td>
            <td style="text-align: center"> {{ row.reading }} </td>
            <td style="text-align: center"> <a href="{{ row.mp_link }}"> {{ row.main_points }} </a> </td>
            <td style="text-align: center"> {{ row.opt }} </td>
            <td style="text-align: center"> <a href="{{ row.assign_link }}"> {{ row.assignment }} </a> </td>
        </tr>
{% endfor %}
    </tbody>
</table>
