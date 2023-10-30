# buildstuffdemo.github.io


{% for repo in site.github.public_repositories %}
  {% if repo.owner.login == 'orgname' %}
- {{ repo.name }}
  {% endif %}
{% endfor %}
