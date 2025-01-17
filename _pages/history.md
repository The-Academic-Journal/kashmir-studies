---
title: "History"
permalink: "/history"
---

<div class="container">
    {% assign categories = site.posts | map: "categories" | flatten | uniq | sort %}
    
    {% for category in categories %}
        <div class="mb-5">
            <h2 class="border-bottom pb-2">{{ category | replace: '-', ' ' | capitalize }}</h2>
            
            <div class="row">
                {% for post in site.posts %}
                    {% if post.categories contains category %}
                        <div class="col-md-12 mb-4">
                            <div class="card h-100">
                                <div class="card-body">
                                    <h3 class="card-title">
                                        <a href="{{ post.url | relative_url }}" class="text-dark">{{ post.title }}</a>
                                    </h3>
                                    {% if post.author %}
                                        <small class="text-muted">
                                            By {% for author in post.author %}{{ author }}{% unless forloop.last %}, {% endunless %}{% endfor %}
                                        </small>
                                    {% endif %}
                                    {% if post.abstract %}
                                        <p class="card-text mt-3">{{ post.abstract | truncatewords: 50 }}</p>
                                    {% endif %}
                                    <a href="{{ post.url | relative_url }}" class="btn btn-primary">Read More</a>
                                </div>
                            </div>
                        </div>
                    {% endif %}
                {% endfor %}
            </div>
        </div>
    {% endfor %}
</div>