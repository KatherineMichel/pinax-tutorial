# Basic Project-Level URLs and Templates

Pinax starter project ```urls.py``` file ```urlpatterns``` will include the URLs of the Pinax apps included in the Pinax starter project. Also included will be admin URLs, and possibly Django User Account app URLs, if Django User Account app is used in the project. 

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

## 'homepage.html'

At the project-level, all Pinax starter projects at a minimum render a homepage, usually using a generic view called ```TemplateView``` and a template named ```homepage.html``` found in the project templates folder. ```homepage.html``` extends ```site_base.html```.

A ```TemplateView```  is a shortcut that enables a template to be rendered directly, not through a view in the views.py file, unless the TemplateView is subclassed. 

Note, ```homepage.html``` is named ```home``` in the project-level ```urls.py``` so that ```homepage.html``` can be more conveniently referred to as ```home``` in other parts of the code, such as the navbar.

## Admin Templates

If used, Django admin templates should also be included in the project templates directory.

