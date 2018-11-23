---
layout: index
title: workshops
---

{% include mission.md %}

<div class="">Select your workshop: </div>

<ul class="list pl4">

{% for workshop in site.workshops %}

    <li class="small-caps">
        <a href="{{site.baseurl}}/workshops/{{workshop.tag}}">
            {{workshop.title}}
        </a>
    </li>

{% endfor %}

</ul>
