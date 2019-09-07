# Global Templates

## 'base.html'

The global ```base.html``` template includes the html head and body markup to render a responsive, styled website page. Template fragments ```_nav.html``` and ```_messages.html``` are included. The optional template fragment ```_account_bar.html``` can be used in apps that include Django User Accounts.

Pinax starter projects each include a project-level ```site_base.html``` template that extends ```base.html``` and is taylored to the project.

```block``` sections in a project's ```site_base.html``` template will be inserted into the corresponding ```block``` sections in the ```base.html``` template.

Additional app-level templates will often extend a project's ```site_base.html```.

```html
{% load staticfiles %}
<!DOCTYPE html>
<html lang="{{ LANGUAGE_CODE }}">
    <head>
        <meta charset="utf-8" />
        <title>{% block head_title_base %}{% if SITE_NAME %}{{ SITE_NAME }} | {% endif %}{% block head_title %}{% endblock %}{% endblock %}</title>
        {% block viewport %}
            <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no">
        {% endblock %}

        {% block styles %}{% endblock %}

        {% block html5shim %}
            <!-- HTML5 shim, for IE6-8 support of HTML elements -->
            <!--[if lt IE 9]>
                <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.2/html5shiv.min.js"></script>
            <![endif]-->
        {% endblock %}

        {% block extra_head_base %}
            <script defer src="https://use.fontawesome.com/releases/v5.0.4/js/all.js"></script>
            {% block extra_head %}{% endblock %}
        {% endblock %}
    </head>
    <body class="{% block body_class_base %}{% block body_class %}{% endblock %}{% endblock %}" id="{% block body_id %}{% endblock %}" {% block body_extra_attributes %}{% endblock %}>
        {% block topbar_base %}
            <header>
                <nav>
                    <div class="topbar-container">
                    {% block topbar %}
                        {% block site_brand %}<a href="{% url "home" %}">{{ SITE_NAME }}</a>{% endblock %}
                        <button class="expand" type="button" data-toggle="collapse" data-target=".nav-container" aria-controls="navbar" aria-expanded="false" aria-label="Toggle navigation">
                            <i class="fas fa-bars"></i>
                        </button>

                        <div class="nav-container" id="navbar">
                            {% block nav %}{% include "_nav.html" %}{% endblock %}
                            {% block account_bar %}{% include "_account_bar.html" %}{% endblock %}
                        </div>
                    {% endblock %}
                    </div>
                </nav>
            </header>
        {% endblock %}

        {% block body_base %}
        <main>
            {% block content_left %}{% endblock %}
            <section id="content-section">
                <div id="content-body">
                    {% block messages %}{% include "_messages.html" %}{% endblock %}
                    {% block body %}{% endblock %}
                </div>
            </section>
            {% block content_right %}{% endblock %}
        </main>
        {% endblock %}

        {% block footer_base %}
            <footer>
                <div>
                    {% block footer %}{% endblock %}
                </div>
            </footer>
        {% endblock %}

        {% block scripts %}{% endblock %}

        {% block extra_body_base %}
            {% block extra_body %}{% endblock %}
        {% endblock %}
    </body>
</html>
```