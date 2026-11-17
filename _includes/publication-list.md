<hr style="border: 0.5px solid grey;">
{% for group in site.data.publications %}
{%- for pub in group.entries %}

{% if pub.hidden %}<!---
{% endif %}**{{ pub.title }}**<br />
{{ pub.authors }}<br />
{{ pub.venue }}<br />
📄 [[Paper]]({{ pub.paper }}){% if pub.code %} | 💻 [[Code]]({{ pub.code }}){% endif %}
{%- if pub.hidden %}
-->{% endif %}
{%- endfor %}

<hr style="border: 0.5px solid grey;">
{%- endfor %}
