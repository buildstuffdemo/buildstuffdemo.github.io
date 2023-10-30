# Welcome to BuildStuff Demos

>>>>>>> # Demos

<style>
.odd {
  background-color: #f9f9f9;
}

.even {
  background-color: #e0e0e0;
}
</style>


{% assign counter = 0 %}

<ul>
{% for repo in site.github.public_repositories %}
  {% if repo.owner.login == 'buildstuffdemo' and repo.name contains 'demo' %}
    {% unless repo.name contains 'github.io' or repo.fork %}
      {% assign row_class = cycle 'odd', 'even' %}
      <li class="{{ row_class }}">
        <a href="https://buildstuffdemo.github.io/{{ repo.name }}">{{ repo.name }}</a>
        <p class="repo-description">{{ repo.description }}</p>
      </li>
      {% assign counter = counter | plus: 1 %}
    {% endunless %}
  {% endif %}
{% endfor %}
</ul>
{% if counter == 0 %}
  <p>No demos found.</p>
{% endif %}
