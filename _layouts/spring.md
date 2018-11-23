---
layout: default
url: research/
---

<div id="post">
    <h2>{{ page.title }}
    {% if page.type %}
    <span class="tag iconsolata f6 ba b--moon-gray v-top">{{ page.type }}</span>
    {% endif %}</h2>

    <!-- remember tags are people -->
    {% if page.tags %}
        <ul class="people-list">
        {% for person in page.tags %}
            <li class="di">{% if person.name %}<a href="{{ person.url }}">{{ person.name }}</a>{% else %}{{ person }}{% endif %}</li>
        {% endfor %}
        </ul>
    {% endif %}

        <!-- Include GitHub badges if the project has a GitHub repo. -->
        {% if page.github %}
        <ul class="github-badges list">


            <li>

                <a class="github-button"
                    href="https://github.com/{{ page.github }}/subscription"
                    aria-label="Watch {{ page.github }} on GitHub">Watch</a>

                <a class="github-button"
                    href="https://github.com/{{ page.github }}/issues"
                    data-icon="octicon-issue-opened"
                    aria-label="Issue {{ page.github }} on GitHub">Issue</a>

                <a class="github-button"
                    href="https://github.com/{{ page.github }}/fork"
                    data-icon="octicon-repo-forked"
                    aria-label="Fork {{ page.github }} on GitHub">Fork</a>

            <img src="https://img.shields.io/github/languages/top/{{
            page.github }}.svg?style=flat-square"/>

            </li>

        </ul>
        {% endif %}


    <!-- grab image from yaml if there is one -->
        {% if page.image %}
            <div>
                <figure>
                    <a href="/public/images/{{ page.image }}">
                    <img alt="" src="/public/images/{{ page.image }}" class="mw5 fr mb4 ml4 b--solid-ns bw1 b--black-30">
                    </a>
                    {% if page.caption %}
                        <figcaption>{{ page.caption }}</figcaption>
                    {% endif %}
                </figure>
            </div>
        {% endif %}

    <!-- include sparkle if we have one -->
        {% if page.sparkle %}
            <div id="sparkle">{% include {{ page.sparkle }} %}</div>
        {% endif %}
        <!-- include prompt  -->
    {% if page.prompt %}
    <div id="prompt">
        {{ page.prompt }}
    </div>
    {% endif %}

    <!-- include updates if we have them -->
    {% if page.updates%}
        <div class="update-div mb2">
            <h3>Updates</h3>
            {% for update in page.updates %}
                <div class="update-list">
                    <span class="update-date iconsolata">{{ update.date | date: "%m/%y" }}</span>
                    {{ update.text | markdownify | remove: '<p>' | remove: '</p>' }}
                </div>
            {% endfor %}
        </div>
    {% endif %}

    {{ content }}

    <!-- image gallery support -->
        {% if page.images %}
    <div id='gallery-box'>
        {% for image in page.images %}
        <a href="{{ site.url }}/public/images/{{ image }}"><img src="{{ site.url }}/public/images/{{ image }}"></a>
        {% endfor %}
    </div>
        {% endif %}

</div>
