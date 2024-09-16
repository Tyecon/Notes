---
tags:
  - Reference
  - {% for t in tags %}- {{t.tag}}\n{% if not loop.last %}, {% endif %}{% endfor %}
---
# {{title}}
## Formatted Bibliography
{{bibliography}}
{% if abstractNote %}
## Abstract
{{abstractNote}}
{% endif %}
## Annotations
{% for annotation in annotations %}
{% if annotation.annotatedText %}
	{{annotation.annotatedText}}
	{% endif %}
	{% if annotation.comment %}
	{{annotation.comment}}
{% endif %}
{% endfor %}