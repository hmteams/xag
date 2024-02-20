---
layout: default
title: Patterns
---

<h1>Overview</h1>

<h1>Patterns</h1>

<p>This repository contains design patterns for explainable agents as advocated in the ...(link blue sky paper). These patterns are a community-driven effort to share knowledge and practices for designing explainable agent systems.</p>

<ul>
  {% for pattern in site.patterns %}
    <li>
      <a href="/xag{{ pattern.url }}">{{ pattern.title }}</a>
    </li>
  {% endfor %}
</ul>

<h1>Explainable events</h1>
...

<h1>How to Contribute</h1>
<p>We welcome contributions from the community! If you have a design pattern that you'd like to share, please follow these steps:</p>

<ol>
  <li><strong>Fork the repository:</strong> Begin by forking the <a href="https://github.com/hmteams/xag" target="_blank">XAG repository</a> on GitHub.</li>
  <li><strong>Create your pattern:</strong> Use our <a href="https://github.com/hmteams/xag/TEMPLATE.md" target="_blank">template</a> as a starting point to create your pattern. Add your pattern to the <code>_patterns</code> directory in your fork.</li>
  <li><strong>Submit a pull request:</strong> Once you're happy with your submission, submit a pull request to the main repository for review.</li>
</ol>

<p>Our team will review your submission and merge it into the collection if it meets our guidelines.</p>
