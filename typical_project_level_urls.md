# Typical Project-Level URLs and Homepage

Pinax starter project ```urls.py``` file ```urlpatterns``` will include the URLs of the Pinax apps included in the Pinax starter project. Also included will be admin URLs, and possibly Django User Account app URLs, if Django User Account app is used in the project. 

Note, ```homepage.html``` is named ```home``` so that ```homepage.html``` can be more conveniently referred to as ```home``` in other parts of the code, such as the navbar.

```html
{% block site_brand %}<a href="{% url "home" %}">{{ SITE_NAME }}</a>{% endblock %}
```

```python
urlpatterns = [{% if django_version >= "2" %}
    path("", TemplateView.as_view(template_name="homepage.html"), name="home"),
    path("admin/", admin.site.urls),
    path("account/", include("account.urls")),
{% else %}
    url(r"^$", TemplateView.as_view(template_name="homepage.html"), name="home"),
    url(r"^admin/", admin.site.urls),
    url(r"^account/", include("account.urls")),
{% endif %}]
```
