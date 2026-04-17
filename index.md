---
title: Home
---

{% assign profile = site.data.profile %}

<section class="hero">
  <div class="hero-copy">
    <p class="eyebrow">{{ profile.title }}</p>
    <h1>{{ profile.name }}</h1>
    <p class="hero-meta">{{ profile.institution }} · {{ profile.location }}</p>
    <p class="hero-tagline">{{ profile.tagline }}</p>
    <p class="hero-submeta">{{ profile.address }}</p>
    <div class="button-row">
      {% for link in profile.links limit:3 %}
        {% assign href = link.url %}
        {% if href contains '://' or href contains 'mailto:' %}
          <a class="button" href="{{ href }}">{{ link.label }}</a>
        {% else %}
          <a class="button" href="{{ href | relative_url }}">{{ link.label }}</a>
        {% endif %}
      {% endfor %}
    </div>
  </div>
  <div class="hero-card">
    {% if profile.avatar and profile.avatar != "" %}
      <img src="{{ profile.avatar | relative_url }}" alt="{{ profile.name }}">
    {% else %}
      <div class="avatar-fallback">{{ profile.name | slice: 0 }}</div>
    {% endif %}
  </div>
</section>

<section id="about" class="content-section">
  <div class="section-heading">
    <p>About</p>
    <h2>Research profile</h2>
  </div>
  <div class="section-grid">
    <div class="card">
      <p>{{ profile.bio }}</p>
    </div>
    <div class="card">
      <h3>Affiliation</h3>
      <p>{{ profile.affiliation }}</p>
      <p class="muted">Advised by {{ profile.advisor }}</p>
    </div>
    <div class="card">
      <h3>Interests</h3>
      <ul class="tag-list">
        {% for item in profile.interests %}
          <li>{{ item }}</li>
        {% endfor %}
      </ul>
    </div>
  </div>
</section>

<section class="content-section">
  <div class="section-heading">
    <p>Highlights</p>
    <h2>Recent news</h2>
  </div>
  <div class="timeline">
    {% for item in profile.news %}
      <article class="timeline-item">
        <span>{{ item.date }}</span>
        <p>{{ item.text }}</p>
      </article>
    {% endfor %}
  </div>
</section>

<section id="publications" class="content-section">
  <div class="section-heading">
    <p>Output</p>
    <h2>Selected publications</h2>
  </div>
  <div class="stack">
    {% for paper in site.data.publications %}
      <article class="publication-card">
        <div class="publication-layout">
          {% if paper.image and paper.image != "" %}
            <div class="publication-image-wrap">
              <img class="publication-image" src="{{ paper.image | relative_url }}" alt="{{ paper.title }}">
            </div>
          {% endif %}
          <div class="publication-copy">
            <div class="publication-topline">
              <span>{{ paper.year }}</span>
              <span>{{ paper.venue }}</span>
            </div>
            <h3>{{ paper.title }}</h3>
            <p class="authors">{{ paper.authors }}</p>
            {% assign paper_text = paper.description | default: paper.summary %}
            <div class="publication-description">{{ paper_text | markdownify }}</div>
            <div class="link-row">
              {% for link in paper.links %}
                {% assign href = link.url %}
                {% assign link_text = link.label | default: link.name %}
                {% if href contains '://' or href contains 'mailto:' %}
                  <a href="{{ href }}">{{ link_text }}</a>
                {% else %}
                  <a href="{{ href | relative_url }}">{{ link_text }}</a>
                {% endif %}
              {% endfor %}
            </div>
          </div>
        </div>
      </article>
    {% endfor %}
  </div>
</section>

<section id="experience" class="content-section">
  <div class="section-heading">
    <p>Background</p>
    <h2>Education and experience</h2>
  </div>
  <div class="section-grid">
    <div class="card">
      <h3>Education</h3>
      <div class="stack compact">
        {% for item in profile.education %}
          <article class="entry">
            <div class="entry-topline">
              <strong>{{ item.degree }}</strong>
              <span>{{ item.period }}</span>
            </div>
            <p>{{ item.institution }}</p>
            <p class="muted">{{ item.detail }}</p>
          </article>
        {% endfor %}
      </div>
    </div>
    <div class="card">
      <h3>Experience</h3>
      <div class="stack compact">
        {% for item in profile.experience %}
          <article class="entry">
            <div class="entry-topline">
              <strong>{{ item.role }}</strong>
              <span>{{ item.period }}</span>
            </div>
            <p>{{ item.organization }}</p>
            <p class="muted">{{ item.detail }}</p>
          </article>
        {% endfor %}
      </div>
    </div>
  </div>
</section>

{% if profile.honors and profile.honors.size > 0 %}
  <section class="content-section">
    <div class="section-heading">
      <p>Recognition</p>
      <h2>Honors</h2>
    </div>
    <div class="section-grid">
      {% for honor in profile.honors %}
        <article class="card project-card">
          <h3>{{ honor.title }}</h3>
          <p>{{ honor.year }}</p>
        </article>
      {% endfor %}
    </div>
  </section>
{% endif %}

{% if profile.projects and profile.projects.size > 0 %}
  <section class="content-section">
    <div class="section-heading">
      <p>Build</p>
      <h2>Projects</h2>
    </div>
    <div class="section-grid">
      {% for project in profile.projects %}
        <article class="card project-card">
          <h3>{{ project.name }}</h3>
          <p>{{ project.summary }}</p>
          {% assign href = project.url %}
          {% if href contains '://' or href contains 'mailto:' %}
            <a href="{{ href }}">View project</a>
          {% else %}
            <a href="{{ href | relative_url }}">View project</a>
          {% endif %}
        </article>
      {% endfor %}
    </div>
  </section>
{% endif %}

<section id="contact" class="content-section contact-card">
  <div>
    <p class="eyebrow">Contact</p>
    <h2>Open to research collaboration, talks, and student mentoring.</h2>
  </div>
  <div class="contact-links">
    <a class="button" href="mailto:{{ profile.email }}">Email me</a>
    {% for link in profile.links %}
      {% unless link.label == "Email" %}
        {% assign href = link.url %}
        {% if href contains '://' or href contains 'mailto:' %}
          <a href="{{ href }}">{{ link.label }}</a>
        {% else %}
          <a href="{{ href | relative_url }}">{{ link.label }}</a>
        {% endif %}
      {% endunless %}
    {% endfor %}
  </div>
</section>
