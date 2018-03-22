---
layout: page
title: Concepts
permalink: /concepts/
---

## {{ site.data.start_builder.title }}

{% for item in site.data.start_builder.sections %}
  {{ item.title }} - {{ item.url }}
{% endfor %}

## {{ site.data.start_nlp.title }}

{% for item in site.data.start_nlp.sections %}
  {{ item.title }} - {{ item.url }}
{% endfor %}

## {{ site.data.nlp_lexic.title }}

{% for item in site.data.nlp_lexic.sections %}
  {{ item.title }} - {{ item.url }}
{% endfor %}

## {{ site.data.bot_builder.title }}

{% for item in site.data.bot_builder.sections %}
  {{ item.title }} - {{ item.url }}
{% endfor %}

## {{ site.data.bot_connector.title }}

{% for item in site.data.bot_connector.sections %}
  {{ item.title }} - {{ item.url }}
{% endfor %}
