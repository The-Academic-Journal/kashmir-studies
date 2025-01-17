---
title: "Book Reviews"
layout: default
permalink: "/book-reviews"
---

<div class="container">
    {% assign reviews = site.book-reviews | sort: 'date' | reverse %}
    {% for review in reviews %}
        <div class="row mb-5 align-items-center">
            {% assign is_even = forloop.index | modulo: 2 %}
            
            <!-- Review Text -->
            <div class="col-md-6 {% if is_even == 0 %}order-md-2{% else %}order-md-1{% endif %} order-2">
                <h2>{{ review.title }}</h2>
                {% if review.author %}
                    <h4 class="text-muted">by {{ review.author }}</h4>
                {% endif %}
                {{ review.content }}
            </div>
            
            <!-- Book Image -->
            <div class="col-md-6 {% if is_even == 0 %}order-md-1{% else %}order-md-2{% endif %} order-1 mb-3 mb-md-0">
                {% if review.image %}
                    <img src="{{ review.image | relative_url }}" alt="{{ review.title }} Cover" class="img-fluid rounded">
                {% endif %}
            </div>
        </div>
    {% endfor %}
</div>

