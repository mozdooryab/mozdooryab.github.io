---
layout: default
title: "خانه"
---

<h1 style="margin-bottom:24px;">فهرست افراد</h1>

<div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:20px;">
  {% for person in site.australia %}
    <a href="{{ person.url | relative_url }}" style="display:block;background:var(--surface);border:1px solid var(--border);border-radius:20px;overflow:hidden;">
      {% if person.featured_image %}
        <img src="{{ person.featured_image }}" alt="{{ person.name_fa }}" style="width:100%;height:220px;object-fit:cover;border-radius:0;">
      {% endif %}
      <div style="padding:16px 18px;">
        <div style="font-weight:800;font-size:1.1rem;margin-bottom:6px;">{{ person.name_fa }}</div>
        <div style="color:var(--muted);font-size:.95rem;">{{ person.city }}</div>
      </div>
    </a>
  {% endfor %}
</div>
