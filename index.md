---
layout: default
title: Patterns
---

# Overview

This repository contains design patterns for explainable agents as advocated in the [_Explainable Agents (XAg) by Design_ AAMAS'24 Blue Sky](https://www.aamas2024-conference.auckland.ac.nz/accepted/blue-sky-ideas/){:target="_blank"}.

These patterns are a community-driven effort to share knowledge and practices for explainable-by-design agents.

Cite this work:
>  Rodriguez, S. and Thangarajah, J. (2024) ‘Explainable Agents (XAg) by Design’, in Proceedings of the 2024 International Conference on Autonomous Agents and Multiagent Systems (Blue Sky). Auckland, New Zeland (AAMAS ’24), p. [to appear].


# Patterns

<ul>
  {% for pattern in site.patterns %}
    <li>
       <a href="{{ site.baseurl }}{{ pattern.url }}">{{ pattern.title }}</a>
    </li>
  {% endfor %}
</ul>

# Explainable events

The following contain sample streams for the named design patterns.

<ul>
  {% for stream in site.streams %}
    <li>
       <a href="{{ site.baseurl }}{{ stream.url }}">{{ stream.title }}</a>
    </li>
  {% endfor %}
</ul>

# How to Contribute

We welcome contributions from the community! If you have a design pattern that you'd like to share, please follow these steps:

<ol>
  <li><strong>Fork the repository:</strong> Begin by forking the <a href="https://github.com/hmteams/xag" target="_blank">XAG repository</a> on GitHub.</li>
  <li><strong>Create your pattern:</strong> Use our <a href="https://github.com/hmteams/xag/TEMPLATE.md" target="_blank">template</a> as a starting point to create your pattern. Add your pattern to the <code>_patterns</code> directory in your fork.</li>
  <li><strong>Submit a pull request:</strong> Once you're happy with your submission, submit a pull request to the main repository for review.</li>
</ol>

<p>Our team will review your submission and merge it into the collection if it meets our guidelines.</p>
