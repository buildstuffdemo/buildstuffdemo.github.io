Welcome to BuildStuff Demos

## Demos

{% for repo in site.github.public_repositories %}
{% if repo.owner.login == 'buildstuffdemo' and repo.name contains 'demo' %}
{% unless repo.name contains 'github.io' %}

- [{{ repo.name }}](https://buildstuffdemo.github.io/{{ repo.name }})
  {% endunless %}
  {% endif %}
  {% endfor %}