---
tags:
  - Reference
citekey: "{{citekey}}"
---
{% set unwantedTags = ["SKIM", "SKIMMED", "TODO", "DONE", "LitNote"] -%}
Topics: {% for tag in tags -%}
		{%- if not unwantedTags.includes(tag.tag) -%}
		[[{{tag.tag}}]]{{ ", " if not loop.last }}
		{%- endif -%}
	{%- endfor %}
	
{%- if url %}
{{url}}  
{%- endif -%}

{% if abstractNote %}
## Abstract  
{{abstractNote}}  
{%- endif -%}

{% if markdownNotes %}
## Notes
{{markdownNotes}}
{%- endif -%}

{#-{% if attachment.length!=0 %}
## Attachments
{%- for attachment in attachments %}
{{attachment.title}}
{%- endfor -%}
{%- endif -%}-#}

{% if annotations.length!=0 %}
## Annotations  
{%- for annotation in annotations %}
{% if annotation.annotatedText -%}
	> {{annotation.annotatedText}}
	{% endif %}
	{% if annotation.comment %}
	{{annotation.comment}}
{%- endif -%}
{%- endfor -%}
{%- endif -%}
