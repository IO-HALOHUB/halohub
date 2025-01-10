---
layout: default
title: Mole Maniacs
permalink: games/mole-maniacs
logo_share: mole-maniacs/logo.png
screenshots:
    - screenshot-8.jpg
    - screenshot-1.jpg
    - screenshot-2.jpg
    - screenshot-3.jpg
    - screenshot-4.jpg
    - screenshot-5.jpg
    - screenshot-6.jpg
    - screenshot-7.jpg
links:
    - name: "Google Play"
      image: "google-play.png"
      url: "https://play.google.com/store/apps/details?id=asia.gamedev.slimes.boompuzzle"
    - name: "itch.io"
      image: "itch-io.png"
      url: "https://murikistudio.itch.io/mole-maniacs"
    - name: "Game Jolt"
      image: "game-jolt.png"
      url: "https://gamejolt.com/games/mole-maniacs/785385"
---

# {{ page.title }}

<div class="swiper my-5" style="max-width: 960px;">
    <div class="swiper-wrapper">
        {% for screenshot in page.screenshots %}
        <div class="swiper-slide">
            <div class="card rounded-5 text-decoration-none d-flex flex-column overflow-hidden">
                <img src="/assets/img/mole-maniacs/{{ screenshot }}" alt="{{ screenshot }}">
            </div>
        </div>
        {% endfor %}
    </div>
    <div class="swiper-pagination"></div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
</div>

**Mole Maniacs** is a *Whack-A-Mole* style game: a game that's not just a hit, but lots of them!

- Complete missions on different levels!
- Submit scores on world leaderboards!
- Hit the moles!
- Get coins by not hitting sheep!
- Collect coins to buy new hammers!
- Don't let your energy bar go down to zero!

<div class="w-100 my-5 d-flex justify-content-center row-or-column align-items-center">
    {% for link in page.links %}
        <a class="m-2 hover" target="_blank" href="{{ link.url }}">
            <img src="/assets/img/get-{{ link.image }}" alt="Get it on {{ link.name }}" style="max-width: 250px">
        </a>
    {% endfor %}
</div>

## Legal Information

- [Terms & Conditions]({{ site.url }}/{{ page.permalink }}/terms-and-conditions)
- [Privacy Policy]({{ site.url }}/{{ page.permalink }}/privacy-policy)

{% include swiper.html %}

<style>
.row-or-column {
    flex-direction: row;
}

@media only screen and (max-width: 860px) {
    .row-or-column {
        flex-direction: column;
    }
}
</style>
