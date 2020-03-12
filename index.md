---
layout: default
---
{% include var.md %}

# Welcome to Luos documentation

## Introduction 

We started designing Luos with the conviction that building electronic systems should be made easier than it is today. Most of the time should be spent on designing the applications and behaviors instead of on complex and time-and-money-eating technicalities. To give a simple example, adding a new sensor &mdash;for instance a lidar&mdash; to an electronic device in conception should not take more than a few minutes. So you can try, test and iterate fast on a project to truly design what users want.

**Today, Luos is exactly like a [<span class="tooltip">microservices<span class="tooltiptext">{{ microservices_def }}</span></span> architecture](https://en.wikipedia.org/wiki/Microservices){:target="_blank"}: it encapsulates any software or hardware function to make it communicate and work with any other encapsulated module, however it was developed.**

We have imagined Luos around three key concepts:
 * **Luos Core:** a tiny library that can be added to the MCU of an embedded board to make it seamlessly communicate with other boards. When conceiving electronic devices, you should be able to compose it from multiple functional parts and not think about communication issues between these parts.
 * **Luos Driver:** a hardware abstraction to make the integration of a sensor, an effector or a software function as easy at it should be &mdash;that is, with one line of code! Drivers must use standardized APIs to let you switch from one type of sensors to another without breaking anything. For example, all types of distance sensors should return a distance in meters using a same function `get_distance()`.
 * **Robus:** A communication bus dedicated to embedded system communication, to make all the above natural and simple. 

<hr class="hr_top">

<span style="font-size: 20px;">Discover how Luos works and how to use it:</span>

{% assign cat_order = site.categories | sort: categories %}
{%- for cat in cat_order -%}
{%- assign category = cat | first -%}
{% if category contains "modules_list" or category contains "boards_list" %}{% continue %}{% endif %}
## {{ cat | first | slice: 2, 30 | replace:"_", " " | capitalize }}
{% if category == "3_prototyping_boards" %}
Luos provides [prototyping boards](https://www.generationrobots.com/fr/256_luos){:target="_blank"} to start understanding and using the technology.
{% endif %}
<ul>
{% assign sorted = cat.last | sort: "order" %}
{% for post in sorted %}
<li><a class="{% if post.wip == 1 %}wip_txt{% endif %}" href="{{ post.url }}">{{ post.title }}</a> – {{ post.desc }}</li>
{% endfor %}
{%- assign test_cat = cat | first -%}
{%- if test_cat contains 'modules' -%}
	<li class="ul_tree"><span class="branch_closed">Modules list</span>
		<ul class="closed">
			{%- assign sorted_post = site.posts | sort: 'title' -%}
			{%- for post in sorted_post -%}
			{%- if post.url contains 'modules_list' -%}
			<li class="branch_single"><a href="{{ post.url }}">{{ post.title }}</a></li>
			{%- endif -%}
			{%- endfor -%}
		</ul>
	</li>
{%- endif -%}
{%- if test_cat contains 'prototyping_boards' -%}
	<li class="ul_tree"><span class="branch_closed">Boards list</span>
		<ul class="closed">
			{%- assign sorted_post = site.posts | sort: 'title' -%}
			{%- for post in sorted_post -%}
			{%- if post.url contains 'boards_list' -%}
			<li class="branch_single"><a href="{{ post.url }}">{{ post.title }}</a></li>
			{%- endif -%}
			{%- endfor -%}
		</ul>
	</li>
{%- endif -%}
</ul>
{%- endfor -%}

{% for cat in site.categories %}
{% assign category = cat | first %}
{% if category == "others" %}
## {{ cat | first | replace:"_", " " | capitalize }}
<ul>
{% assign sorted = cat.last | sort: "order" %}
{% for post in sorted %}
<li><a class="{% if post.wip == 1 %}wip_txt{% endif %}" href="{{ post.url }}">{{ post.title }}</a> – {{ post.desc }}</li>
{% endfor %}
{% endif %}
{% endfor %}
