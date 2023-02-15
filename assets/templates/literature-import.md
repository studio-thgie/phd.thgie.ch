---
title: "{{title}}"
authors: "{{authors}}"
year: {{date | format("YYYY")}}
tags: [{% for tag in tags %}{{tag.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]
priority:
status:
---
# {{title}}

- [Bibliography](#bibliography)
- [Notes](#notes)
- [Abstract](#abstract)
- [Reading Notes](#reading-notes)

## Bibliography
{{bibliography}}
## Notes
{% persist "notes" %}
{% endpersist %}
{% if abstractNote %}
## Abstract
{{abstractNote}}
{% endif %}{% if markdownNotes %}
## Reading Notes
{{markdownNotes}}
{% endif %}
## Related
{% persist "related" %}
{% endpersist %}