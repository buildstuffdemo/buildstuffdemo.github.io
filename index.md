# Welcome to BuildStuff Demos

<img width="288" alt="image" src="https://github.com/buildstuffdemo/buildstuffdemo.github.io/assets/10250297/2cd5c25f-d4e1-4884-be06-4880d7d2721e">

> > > ### Demos

<style>
  
@keyframes colorChange {
  0% { background-color: #f9f9f9; }
  50% { background-color: #e0e0e0; }
  100% { background-color: #f9f9f9; }
}

.odd {
  animation: colorChange 15s infinite;
}

@keyframes colorChangeEven {
  0% { background-color: #e0e0e0; }
  50% { background-color: #f9f9f9; }
  100% { background-color: #e0e0e0; }
}

.even {
  animation: colorChangeEven 15s infinite;
}
</style>

{% assign counter = 0 %}

<ul>
{% assign sorted_repositories = site.github.public_repositories | sort: "name" %}
{% for repo in sorted_repositories %}
  {% if repo.owner.login == 'buildstuffdemo' and repo.name contains 'demo' %}
    {% unless repo.name contains 'github.io' or repo.fork %}
      {% assign row_class = counter | modulo: 2 | times: 1 | plus: 1 %}
      <li>
        <a class="{% if row_class == 1 %}odd{% else %}even{% endif %}" href="https://buildstuffdemo.github.io/{{ repo.name }}">{{ repo.name  | replace: '-', ' ' }}</a>
          <p class="repo-description">{{ repo.description | default: "" }}</p>
        <p class="repo-updated">Last updated: {{ repo.updated_at | date: "%B %d, %Y" }}</p>
      </li>
      {% assign counter = counter | plus: 1 %}
    {% endunless %}
  {% endif %}
{% endfor %}
</ul>
{% if counter == 0 %}
  <p>No demos found.</p>
{% endif %}
