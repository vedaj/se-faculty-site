---
layout: default
title: Home
---

<div class="row">
  <div class="col-lg-8">

    <!-- Faculty Members -->
    <section id="members" class="mb-5">
      <h2 class="section-title"><i class="fas fa-users me-2"></i>Faculty Team</h2>
      <div class="row g-4">
        {% for member in site.data.members %}
        <div class="col-md-6 col-lg-4">
          <div class="card h-100">
            {% if member.photo %}
            <img src="{{ member.photo | relative_url }}" class="faculty-img card-img-top" alt="{{ member.name }}">
            {% endif %}
            <div class="card-body text-center">
              <h5 class="card-title">{{ member.name }}</h5>
              <p class="text-muted">{{ member.title }}</p>
              <a href="mailto:{{ member.email }}" class="btn btn-primary btn-sm">
                <i class="fas fa-envelope"></i> Contact
              </a>
            </div>
          </div>
        </div>
        {% endfor %}
      </div>
    </section>

    <!-- Schedule -->
    <section id="schedule" class="mb-5">
      <h2 class="section-title"><i class="fas fa-calendar-alt me-2"></i>Upcoming Meetings</h2>
      <div class="list-group">
        {% for issue in site.github.issues | where_exp: "item", "item.labels contains 'meeting'" | sort: "created_at" | reverse | limit: 5 %}
        <a href="{{ issue.html_url }}" class="list-group-item list-group-item-action">
          <div class="d-flex w-100 justify-content-between">
            <h6 class="mb-1">{{ issue.title }}</h6>
            <small>{{ issue.created_at | date: "%b %d" }}</small>
          </div>
          <p class="mb-1 text-muted">Click to view details</p>
        </a>
        {% else %}
        <p class="text-muted">No upcoming meetings.</p>
        {% endfor %}
      </div>
    </section>

    <!-- Announcements -->
    <section id="announcements" class="mb-5">
      <h2 class="section-title"><i class="fas fa-bullhorn me-2"></i>Announcements</h2>
      <div class="row g-3">
        {% for issue in site.github.issues | where_exp: "item", "item.labels contains 'announcement'" | sort: "created_at" | reverse | limit: 3 %}
        <div class="col-md-6">
          <div class="card">
            <div class="card-body">
              <h6 class="card-title"><a href="{{ issue.html_url }}">{{ issue.title }}</a></h6>
              <p class="card-text text-muted small">{{ issue.created_at | date: "%b %d, %Y" }}</p>
            </div>
          </div>
        </div>
        {% else %}
        <p class="text-muted">No announcements yet.</p>
        {% endfor %}
      </div>
    </section>

  </div>

  <!-- Sidebar -->
  <div class="col-lg-4">
    <div class="card sticky-top" style="top: 6rem;">
      <div class="card-header bg-primary text-white">
        <i class="fas fa-link me-2"></i>Quick Access
      </div>
      <div class="list-group list-group-flush">
        <a href="{{ '/docs/syllabus.pdf' | relative_url }}" class="list-group-item list-group-item-action">
          <i class="fas fa-file-pdf text-danger"></i> Syllabus
        </a>
        <a href="https://amritavishwavidyapeetham.sharepoint.com/sites/23CSE311SoftwareEngineering/Shared%20Documents" 
           class="list-group-item list-group-item-action" target="_blank">
          <i class="fas fa-folder-open text-warning"></i> Course Files (SharePoint)
        </a>
        <a href="https://drive.google.com/drive/folders/MINUTES_ID" class="list-group-item list-group-item-action">
          <i class="fas fa-clipboard-list text-success"></i> Meeting Minutes
        </a>
      </div>
    </div>

    <!-- Embedded Course Files Directory -->
    <section id="course-files" class="mt-4">
      <h5 class="section-title"><i class="fas fa-folder-open me-2"></i>Course Files Directory</h5>
      <div class="border rounded overflow-hidden" style="height: 420px;">
        <iframe 
          src="https://amritavishwavidyapeetham.sharepoint.com/sites/23CSE311SoftwareEngineering/Shared%20Documents/embed" 
          width="100%" 
          height="100%" 
          frameborder="0" 
          allowfullscreen 
          loading="lazy">
        </iframe>
      </div>
      <small class="text-muted d-block mt-2">
        Files are hosted on SharePoint. Use the link above to open in full view.
      </small>
    </section>

    <!-- Resources -->
    <section id="resources" class="mt-4">
      <h5 class="section-title"><i class="fas fa-external-link-alt me-2"></i>Resources</h5>
      <ul class="list-group">
        {% for link in site.data.links %}
        <li class="list-group-item">
          <a href="{{ link.url }}" target="_blank">{{ link.title }}</a>
          <small class="text-muted d-block">{{ link.description }}</small>
        </li>
        {% endfor %}
      </ul>
    </section>
  </div>
</div>