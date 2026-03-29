[index.md](https://github.com/user-attachments/files/26327555/index.md)
---
layout: default
title: Directory
---
<style>
  .directory-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(min(280px,100%), 1fr));
    gap: 1.5rem;
    padding: 2rem 1.5rem;
    max-width: 1100px;
    margin-inline: auto;
  }
  .person-card {
    background: var(--color-surface, #fff);
    border: 1px solid var(--color-border, #d4d1ca);
    border-radius: 0.75rem;
    overflow: hidden;
    box-shadow: 0 1px 2px rgba(0,0,0,0.06);
    transition: box-shadow 180ms ease, transform 180ms ease;
    text-decoration: none;
    display: block;
    color: inherit;
  }
  .person-card:hover {
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    transform: translateY(-2px);
  }
  .card-img { width: 100%; aspect-ratio: 1; object-fit: cover;
              background: #cedcd8; }
  .card-body { padding: 1rem 1.25rem; }
  .card-name { font-family: 'Instrument Serif', serif; font-size: 1.25rem;
               margin-bottom: 0.25rem; }
  .card-role { font-size: 0.85rem; color: #7a7974; }
</style>

<div class="directory-grid">
{% for person in site.people %}
  <a href="{{ person.url }}" class="person-card">
    {% if person.profile_image %}
      <img class="card-img" src="{{ person.profile_image }}"
           alt="{{ person.name }}" loading="lazy" width="280" height="280">
    {% else %}
      <div class="card-img" style="display:flex;align-items:center;justify-content:center;
           font-family:'Instrument Serif',serif;font-size:3rem;color:#01696f;">
        {{ person.name | slice: 0 }}
      </div>
    {% endif %}
    <div class="card-body">
      <h2 class="card-name">{{ person.name }}</h2>
      {% if person.role %}<p class="card-role">{{ person.role }}</p>{% endif %}
    </div>
  </a>
{% endfor %}
</div>
