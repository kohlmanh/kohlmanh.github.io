---
layout: work
title: Work
permalink: /work/
---

{% assign works = site.data.artindex %}
{% if works %}
  {% assign years = works | group_by: "Year" | sort: "name" | reverse %}

  <div class="art-grid" id="art-grid">
    {% for year in years %}
      {% for work in year.items %}
        <div class="art-item" data-year="{{ year.name }}" onclick="openModal('{{ work.ImageFilename | escape }}', '{{ work.Title | escape }}', '{{ work.Material | escape }}', '{{ work.Dimensions | escape }}', '{{ work.Description | escape }}')">
          <div class="carousel">
            {% assign imageFiles = work.ImageFilename | split: ',' %}
            {% for imageFile in imageFiles %}
              <div class="carousel-item {% if forloop.first %}active{% endif %}">
                <img src="assets/images/work images/{{ imageFile | strip }}" alt="{{ work.Title | strip }}" class="art-image" loading="lazy">
              </div>
            {% endfor %}
            {% if imageFiles.size > 1 %}
              <button class="carousel-arrow prev" onclick="moveCarousel(this, -1); event.stopPropagation();">&#10094;</button>
              <button class="carousel-arrow next" onclick="moveCarousel(this, 1); event.stopPropagation();">&#10095;</button>
            {% endif %}
          </div>
          <p class="art-title">{{ work.Title | strip }}</p>
        </div>
      {% endfor %}
    {% endfor %}
  </div>
{% else %}
  <p>No artwork data found.</p>
{% endif %}

<style>
  .home-button {
    font-size: 22px;
    font-weight: bold;
  }
</style>

<script>
  function updateYearOnScroll() {
    const items = document.querySelectorAll('.art-item');
    let currentYear = '';
    let scrollPosition = window.scrollY + window.innerHeight / 2;

    items.forEach(item => {
      const rect = item.getBoundingClientRect();
      const itemTop = rect.top + window.scrollY;
      const itemBottom = itemTop + rect.height;
      if (scrollPosition >= itemTop && scrollPosition <= itemBottom) {
        currentYear = item.getAttribute('data-year');
      }
    });

    const ticker = document.getElementById('year-ticker');
    if (ticker && currentYear) {
      ticker.textContent = currentYear;
      ticker.style.fontSize = '32px';
      ticker.style.fontWeight = 'bold';
    }
  }

  window.addEventListener('scroll', updateYearOnScroll);
  document.addEventListener('DOMContentLoaded', updateYearOnScroll);
</script>
