---
title: "{{title}}"
authors: "{{authors}}"
year: {{date | format("YYYY")}}
tags: [{% for tag in tags %}{{tag.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]
---
# {{title}}

- [Bibliography](#bibliography)
- [Notes](#notes)
- [Abstract](#abstract)
- [Reading Notes](#reading-notes)

## Bibliography
{{bibliography}}

{% if abstractNote %}## Abstract
{{abstractNote}}{% endif %}

## Notes
{% persist "notes" %}{% endpersist %}
{% if markdownNotes %}{{markdownNotes}}{% endif %}

## Related
{% persist "related" %}{% endpersist %}