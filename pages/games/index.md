---
layout: default
title: Games
permalink: games
---

# Games

<div class="swiper mt-4" style="max-width: 640px;">
    <div class="swiper-wrapper">
        {% for game in site.data.games %}
        <div class="swiper-slide">
            <a class="card hover rounded-5 text-decoration-none d-flex flex-column overflow-hidden" style="background: {{ game.background }}" href="{{ site.url }}/{{ game.url }}">
                <img src="/assets/img/{{ game.icon }}" alt="{{ game.title }}">
            </a>
        </div>
        {% endfor %}
    </div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
</div>

{% include swiper.html %}
