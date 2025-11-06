---
layout: default
title: Home
---

# Software Engineering Faculty Team

## Faculty Members
<div class="grid">
  {% for member in site.data.members %}
  <div class="card">
    {% if member.photo %}<img src="{{ member.photo }}" alt="{{ member.name }}" width="80">{% endif %}
    <strong>{{ member.name }}</strong><br>
    {{ member.title }}<br>
    <a href="mailto:{{ member.email }}">{{ member.email }}</a>
  </div>
  {% endfor %}
</div>

## Upcoming Meetings
<ul>
  {% for issue in site.github.issues | where: "labels", "meeting" | sort: "created_at" | reverse | limit: 5 %}
  <li><strong>{{ issue.title }}</strong> – {{ issue.created_at | date: "%b %d, %Y" }}</li>
  {% endfor %}
</ul>

## Announcements
<ul>
  {% for issue in site.github.issues | where: "labels", "announcement" | sort: "created_at" | reverse | limit: 3 %}
  <li><a href="{{ issue.html_url }}">{{ issue.title }}</a> ({{ issue.created_at | date: "%b %d" }})</li>
  {% endfor %}
</ul>

## Quick Links
- [Syllabus](/docs/syllabus.pdf)
- [Course Files (Google Drive)](https://drive.google.com/drive/folders/YOUR_FOLDER_ID?usp=sharing)
- [Meeting Minutes (Drive)](https://drive.google.com/drive/folders/MINUTES_ID)

## Resources
<ul>
  {% for link in site.data.links %}
  <li><a href="{{ link.url }}">{{ link.title }}</a> – {{ link.description }}</li>
  {% endfor %}
</ul>
