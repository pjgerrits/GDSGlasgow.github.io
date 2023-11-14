---
layout: page
permalink: /profiles/
title: people
description: members of our team
nav: true
nav_order: 2
---

{% assign groups = site.team | sort: "group_rank" | map: "group" | uniq %}
{% for group in groups %}
## {{ group }}

    {% assign members = site.team | sort: "weight" | where: "group", group %}
    {% for member in members %}
<p>
    <div class="card {% if member.inline == false %}hoverable{% endif %}">
        <div class="row no-gutters">
            <div class="col-sm-4 col-md-3">
                <img src="{{ '/assets/img/team_profiles/' | append: member.profile.image | relative_url }}" class="card-img" alt="{{ member.profile.name }}"/>
            </div>
            <div class="team col-sm-8 col-md-9">
                <div class="card-body">
                    {% if member.inline == false %}<a href="{{ member.url | relative_url }}">{% endif %}
                    <h5 class="card-title">{{ member.profile.name }}</h5>
                    {% if member.profile.position %}<h6 class="card-subtitle mb-3 text-muted">{{ member.profile.position }}</h6>{% endif %}
                    <p class="card-text">
                        {{ member.teaser }}
                    </p>
                    <br>
                    {% if member.inline == false %}</a>{% endif %}
                    {% if member.profile.email %}
                        <a href="mailto:{{ member.profile.email }}" class="card-link"><i class="fas fa-envelope"></i></a>
                    {% endif %}
                    {% if member.profile.phone %}
                        <a href="tel:{{ member.profile.phone }}" class="card-link"><i class="fas fa-phone"></i></a>
                    {% endif %}
                    {% if member.profile.linkedin %}
                        <a href="https://linkedin.com/in/{{ member.profile.linkedin }}/" class="card-link" target="_blank"><i class="fab fa-linkedin"></i></a>
                    {% endif %}
                    {% if member.profile.orcid %}
                        <a href="https://orcid.org/{{ member.profile.orcid }}" class="card-link" target="_blank"><i class="fab fa-orcid"></i></a>
                    {% endif %}
                    {% if member.profile.twitter %}
                        <a href="https://twitter.com/{{ member.profile.twitter }}" class="card-link" target="_blank"><i class="fab fa-twitter"></i></a>
                    {% endif %}
                    {% if member.profile.github %}
                        <a href="https://github.com/{{ member.profile.github }}" class="card-link" target="_blank"><i class="fab fa-github"></i></a>
                    {% endif %}
                    {% if member.profile.gitlab %}
                        <a href="https://gitlab.com/{{ member.profile.gitlab }}" class="card-link" target="_blank"><i class="fab fa-gitlab"></i></a>
                    {% endif %}
                    {% if member.profile.mastodon %}
                        <a href="https://mastodon.social/{{ member.profile.mastodon }}" class="card-link" target="_blank"><i class="fab fa-mastodon"></i></a>
                    {% endif %}
                    {% if member.profile.researchgate %}
                        <a href="https://www.researchgate.net/profile/{{ member.profile.researchgate }}" class="card-link" target="_blank"><i class="fab fa-researchgate"></i></a>
                    {% endif %}
                    {% if member.profile.researchgate_noprofile %}
                        <a href="https://www.researchgate.net/scientific-contributions/{{ member.profile.researchgate_noprofile }}" class="card-link" target="_blank"><i class="fab fa-researchgate"></i></a>
                    {% endif %}
                    {% if member.profile.website %}
                        <a href="{{ member.profile.website }}" class="card-link" target="_blank"><i class="fas fa-globe"></i></a>
                    {% endif %}
                    {% if member.profile.uofg %}
                        <a href="https://www.gla.ac.uk/{{ member.profile.uofg }}" class="card-link" target="_blank"><i class="fas fa-university"></i></a>
                    {% endif %}
                </div>
            </div>
        </div>
    </div>
</p>
<br>
    {% endfor %}
{% endfor %}