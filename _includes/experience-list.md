<hr style="border: 0.5px solid grey;">
{% for group in site.data.experience %}
{%- for job in group.entries %}

{% if job.hidden %}<!---
{% endif %}* <span style="float: left;">**{{ job.role }}**</span><span style="float: right;">**{{ job.dates }}**</span><br />
<span style="float: left;">{% for org in job.orgs %}[{{ org.name }}]({{ org.url }}){% unless forloop.last %} & {% endunless %}{% endfor %}</span><span style="float: right;">{{ job.place }}</span><br />
{%- for area in job.areas %}
<ins>*Research Area:*</ins> {{ area }}<br />
{%- endfor %}
{%- if job.hidden %}
-->{% endif %}
{%- endfor %}

<hr style="border: 0.5px solid grey;">
{%- endfor %}
