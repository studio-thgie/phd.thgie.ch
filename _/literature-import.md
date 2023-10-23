---
title: "{{title}}"
authors: "{{authors}}"
year: {{date | format("YYYY")}}
tags: [{% for tag in tags %}{{tag.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]
---
# {{title}}

- [Bibliography](#bibliography)
- [Abstract](#abstract)
- [Notes](#notes)
- [Annotations](#annotations)

{% persist "notes" %}
{% endpersist %}
## Bibliography
{{bibliography}}
{% if abstractNote %}
## Abstract
{{abstractNote}}{% endif %}

## Notes
{% if markdownNotes %}{{markdownNotes}}{% endif %}

## Annotations
{% for annotation in annotations %}{% if annotation.annotatedText %}> {{annotation.annotatedText}} (p. {{annotation.page}}){% endif %}
{% if annotation.comment %}> – {{annotation.comment}}{% endif %}
{% endfor %}