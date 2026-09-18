---
layout: page
title: Publications
permalink: /publications/
wide: true
description: Peer-reviewed publications and preprints.
---

{% assign pubs = site.data.publications %}
{% if pubs and pubs.size > 0 %}
{% include publication_list.html publications=pubs %}
{% else %}
<p class="empty">Publication list is being updated.</p>
{% endif %}
