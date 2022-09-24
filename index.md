---
title: Instructions hébergées en ligne
permalink: index.html
layout: home
---

# <a name="content-directory"></a>Répertoire de contenu

Hyperlinks to each of the walkthroughs. Instructors may choose to use the walkthrough as a demonstration or a student lab. 

## <a name="walkthroughs"></a>Procédures pas à pas

{% assign wts = site.pages | where_exp:"page", "page.url contains ’/Instructions/Walkthroughs’" %}
| Module | Procédure pas à pas |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

