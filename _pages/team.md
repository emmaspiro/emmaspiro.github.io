---
layout: page
permalink: /team
title: team
description: I am honored to work with many students, researchers, postdoctoral scholars, and collaborators.
nav: true
nav_order: 6
---

**Prospective students:** I typically recruit 1-2 new PhD students each year. I have a general policy not to speak to candidates in advance of the admissions process. This allows me to treat candidates equitably. I will reach out to candidates who apply to the UW Information Science PhD program and make our shortlist to discuss your research ideas and share more about our current research projects. 

In the meantime, you are in the right place to review recent publications and projects to help inform your research statement and other application materials. If you are interested in information integrity and manipulation, please also browse our work at the <a href="https://www.cip.uw.edu/">Center for an Informed Public</a>, which I co-founded in 2019. I currently serve as the CIP Director. 


{% assign groups = site.members | sort: "group_rank" | map: "group" | uniq %}
{% for group in groups %}
### {{ group }}

    {% assign members = site.members | sort: "lastname" | where: "group", group %}
    {% for member in members %}
<p>
    <div class="card {% if member.inline == false %}hoverable{% endif %}">
        <div class="row no-gutters">
            <div class="col-sm-4 col-md-3">
                <img src="{{ '/assets/img/' | append: member.profile.image | relative_url }}" class="card-img img-fluid" alt="{{ member.profile.name }}" />
            </div>
            <div class="team col-sm-8 col-md-9">
                <div class="card-body">
                    {% if member.inline == false %}<a href="{{ member.url | relative_url }}">{% endif %}
                    <h5 class="card-title">{{ member.profile.name }}</h5>
                    {% if member.profile.position %}<h6 class="card-subtitle mb-2 text-muted">{{ member.profile.position }}</h6>{% endif %}
                    <p class="card-text">
                        {{ member.teaser }}
                    </p>
                    {% if member.inline == false %}</a>{% endif %}
                    {% if member.profile.email %}
                        <a href="mailto:{{ member.profile.email }}" class="card-link"><i class="fas fa-envelope"></i></a>
                    {% endif %}
                    {% if member.profile.linkedin %}
                        <a href="https://linkedin.com/in/{{ member.profile.linkedin }}/" class="card-link" target="_blank"><i class="fab fa-linkedin"></i></a>
                    {% endif %}
                    {% if member.profile.website %}
                        <a href="{{ member.profile.website }}" class="card-link" target="_blank"><i class="fas fa-globe"></i></a>
                    {% endif %}
                    <p class="card-text">
                        <small class="test-muted"><i class="fas fa-thumbtack"></i> {{ member.profile.address | replace: '<br />', ', ' }}</small>
                    </p>
                </div>
            </div>
        </div>
    </div>
</p>
    {% endfor %}
{% endfor %}