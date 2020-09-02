---
title: Seznámení s Django v aplikaci Visual Studio, krok 5, ověřování
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, konkrétně o funkcích ověřování poskytovaných šablonami webových projektů Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bdc76b0a7b9d3f74da77b317faf31dae83706f04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62957846"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5: ověření uživatelů v Django

**Předchozí krok: [použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Vzhledem k tomu, že ověřování je běžnou potřebou pro webové aplikace, zahrnuje šablona "webový projekt Django" tok základního ověřování. (Šablona "cyklické Djangos web Project" popsaná v kroku 6 tohoto kurzu obsahuje také stejný tok.) Při použití některé z šablon projektů Django zahrnuje Visual Studio všechny nezbytné moduly pro ověřování v *Settings.py*projektu Django.

V tomto kroku se naučíte:

> [!div class="checklist"]
> - Jak používat tok ověřování, který je k dispozici v šablonách sady Visual Studio (krok 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: použití toku ověřování

Následující kroky uplatňují tok ověřování a popisují části projektu, které jsou součástí:

1. Pokud jste už nepoužili pokyny v souboru *readme.html* v kořenovém adresáři projektu k vytvoření účtu Super uživatele (správce), udělejte to teď.

1. Spusťte aplikaci ze sady Visual **Studio pomocí ladění**  >  **Spustit ladění** (**F5**). Když se aplikace objeví v prohlížeči, sledujte, že se **přihlásíte** v pravém horním rohu navigačního panelu.

    ![Řízení přihlášení na stránce aplikace webového projektu Django](media/django/step05-login-control.png)

1. Otevřete *Templates/App/layout.html* a sledujte, že `<div class="navbar ...>` element obsahuje značku `{% include app/loginpartial.html %}` . `{% include %}`Značka instruuje systém šablonování, aby Django do obsahu zahrnutého souboru v tomto okamžiku v nadřazené šabloně.

1. Otevřete *šablony/aplikace/loginpartial.html* a sledujte, jak používá podmíněný tag `{% if user.is_authenticated %}` spolu se `{% else %}` značkou pro vykreslení různých prvků uživatelského rozhraní v závislosti na tom, jestli uživatel ověřil:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Vzhledem k tomu, že při prvním spuštění aplikace není ověřený žádný uživatel, tento kód šablony vykresluje pouze odkaz Přihlásit se k relativní cestě "přihlášení". Jak je uvedeno v *URLs.py* (jak je znázorněno v předchozí části), je tato trasa namapována na `django.contrib.auth.views.login` zobrazení. Toto zobrazení obdrží následující data:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Tady se `template_name` určí šablona pro přihlašovací stránku, v tomto případě *šablony/aplikace/login.html*. `extra_context`Vlastnost je přidána do výchozích kontextových dat uvedených v šabloně. Nakonec `authentication_form` Určuje třídu formuláře, která se má použít s přihlášením. v šabloně se zobrazí jako `form` objekt. Výchozí hodnota je `AuthenticationForm` (od `django.contrib.auth.views` ); šablona projektu sady Visual Studio místo toho používá formulář definovaný v souboru *Forms.py* aplikace:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Jak vidíte, tato třída formuláře je odvozena z `AuthenticationForm` a konkrétně Přepisuje pole uživatelské jméno a heslo, aby bylo možné přidat zástupný text. Šablona sady Visual Studio zahrnuje tento explicitní kód na předpokladu, že pravděpodobně chcete přizpůsobit formulář, jako je například přidání ověření síly silného hesla.

1. Když přejdete na přihlašovací stránku, vykreslí aplikace šablonu *login.html* . Proměnné `{{ form.username }}` a `{{ form.password }}` Vykreslí `CharField` formuláře z `BootstrapAuthenticationForm` . K dispozici je také integrovaný oddíl k zobrazení chyb ověřování a předem připravený prvek pro sociální přihlášení, pokud se rozhodnete tyto služby přidat.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Při odeslání formuláře se Django pokusí ověřit vaše přihlašovací údaje (například přihlašovací údaje uživatele Super). Pokud se ověření nepovede, zůstanete na aktuální stránce, ale `form.errors` nastavíte na hodnotu true (pravda). Pokud je ověření úspěšné, Django přejde na relativní adresu URL v poli Next, `<input type="hidden" name="next" value="/" />` které v tomto případě je Domovská stránka ( `/` ).

1. Když teď znovu vykreslíte domovskou stránku, `user.is_authenticated` vlastnost má hodnotu true, když se vykreslí šablona *loginpartial.html* . V důsledku toho se zobrazí zpráva **Hello (Username)** a **odhlášení**. Můžete použít `user.is_authenticated` v jiných částech aplikace ke kontrole ověřování.

    ![Zpráva a ovládací prvek odhlášení Hello na stránce aplikace webového projektu Django](media/django/step05-logoff-control.png)

1. Pokud chcete ověřit, jestli má ověřený uživatel autorizaci pro přístup ke konkrétním prostředkům, musíte z vaší databáze načíst oprávnění specifická pro uživatele. Další informace najdete v tématu [použití ověřovacího systému Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (dokumentace Django).

1. Uživatel super nebo správce, konkrétně má oprávnění pro přístup k vestavěným Djangom rozhraním správce pomocí relativních adres URL "/admin/" a "/admin/doc/". Pokud chcete tato rozhraní povolit, udělejte toto:

    1. Nainstalujte do svého prostředí balíček python Docutils. Skvělým způsobem, jak to provést, je přidat do souboru *requirements.txt* "Docutils", pak v **Průzkumník řešení**rozbalíte projekt, rozbalíte uzel **prostředí Pythonu** a potom kliknete pravým tlačítkem na prostředí, ve kterém jste vybrali **instalovat z requirements.txt**.

    1. Otevřete *URLs.py* projektu Django a odeberte výchozí komentáře z následujících položek:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. V souboru *Settings.py* projektu Django přejděte do `INSTALLED_APPS` kolekce a přidejte `'django.contrib.admindocs'` .

    1. Po restartování aplikace můžete přejít na "/admin/" a "/admin/doc/" a provádět úlohy, jako je vytváření dalších uživatelských účtů.

        ![Rozhraní správce Django](media/django/step05-administrator-interface.png)

1. Poslední část toku ověřování se odhlásí. Jak vidíte v *loginpartial.html* **, odkaz pro odhlášení jednoduše** provede příspěvek na relativní adresu URL "/login", která je zpracovávána integrovaným zobrazením `django.contrib.auth.views.logout` . Toto zobrazení nezobrazuje žádné uživatelské rozhraní a pouze naviguje na domovskou stránku (jak je znázorněno v *URLs.py* pro vzor "^ odhlášení $"). Pokud chcete zobrazit stránku pro odhlášení, nejprve změňte vzor adresy URL tak, aby se přidala vlastnost "template_name" a odebrala vlastnost "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Pak vytvořte *Templates/App/loggedoff.html* s následujícím (minimálním) obsahem:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Výsledek se zobrazí takto:

    ![Přidání odhlášené stránky](media/django/step05-logged-off-page.png)

1. Až skončíte, zastavte Server a potom znovu potvrďte změny ve správě zdrojového kódu.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Otázka: Jaký je účel značky {% csrf_token%}, který se zobrazí v \<form\> elementech?

Odpověď: Tato `{% csrf_token %}` značka zahrnuje integrovanou ochranu CSRF (Django docs) [mezi lokalitami](https://docs.djangoproject.com/en/2.0/ref/csrf/) Django. Tuto značku obvykle přidáte do libovolného prvku, který zahrnuje metody žádosti POST, PUT nebo DELETE, jako je například formulář. Funkce vykreslení šablony ( `render` ) pak vloží potřebnou ochranu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití šablony webového projektu Django pro cyklické dotazování](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Ověřování uživatelů v Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
