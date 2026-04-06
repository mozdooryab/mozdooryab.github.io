---
layout: default
title: "خانه"
---

<div style="display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:16px;margin-bottom:24px;">
  <h1 style="margin:0;">فهرست افراد</h1>
  <div style="position:relative;width:min(340px,100%);">
    <input
      id="searchInput"
      type="search"
      placeholder="جستجو... نام، شهر، سمت"
      autocomplete="off"
      style="width:100%;padding:10px 44px 10px 16px;border:1px solid var(--border);border-radius:999px;background:var(--surface);color:var(--text);font-family:inherit;font-size:1rem;outline:none;"
    >
    <svg style="position:absolute;left:14px;top:50%;transform:translateY(-50%);opacity:.4;pointer-events:none;" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
  </div>
</div>

<div id="noResults" style="display:none;text-align:center;padding:48px 0;color:var(--muted);font-size:1.1rem;">
  نتیجه‌ای پیدا نشد
</div>

<div id="grid" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:20px;">
  {% assign shuffled = site.australia | sort: "name_en" %}
  {% for person in shuffled %}
    <a class="person-card" href="{{ person.url | relative_url }}"
       data-name="{{ person.name_fa }} {{ person.name_en }}"
       data-city="{{ person.city }}"
       data-role="{{ person.role }}"
       style="display:block;background:var(--surface);border:1px solid var(--border);border-radius:20px;overflow:hidden;transition:transform .2s,box-shadow .2s;">
      {% if person.featured_image %}
        <img src="{{ person.featured_image }}" alt="{{ person.name_fa }}" style="width:100%;height:220px;object-fit:cover;border-radius:0;">
      {% else %}
        <div style="width:100%;height:220px;background:var(--border);"></div>
      {% endif %}
      <div style="padding:16px 18px;">
        <div style="font-weight:800;font-size:1.1rem;margin-bottom:6px;">{{ person.name_fa }}</div>
        <div style="color:var(--muted);font-size:.95rem;">{{ person.city }}</div>
      </div>
    </a>
  {% endfor %}
</div>

<script>
(function(){
  // Shuffle cards randomly on each page load
  const grid = document.getElementById('grid');
  const cards = Array.from(grid.children);
  for (let i = cards.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    grid.appendChild(cards[j]);
    cards.splice(j, 1);
  }

  // Live search
  const input = document.getElementById('searchInput');
  const noResults = document.getElementById('noResults');

  input.addEventListener('input', function(){
    const q = this.value.trim().toLowerCase();
    let visible = 0;
    document.querySelectorAll('.person-card').forEach(card => {
      const text = (
        card.dataset.name + ' ' +
        card.dataset.city + ' ' +
        card.dataset.role
      ).toLowerCase();
      const show = !q || text.includes(q);
      card.style.display = show ? 'block' : 'none';
      if (show) visible++;
    });
    noResults.style.display = visible === 0 ? 'block' : 'none';
  });
})();
</script>
