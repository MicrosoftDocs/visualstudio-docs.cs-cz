---
title: Přečtěte si kurz Django v sadě Visual Studio, kroku 5, ověřování
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně funkce ověřování podle šablony webového projektu Django.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 77cc7816a1a05e3b6a883416225717679dd5661b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064070"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5: Ověření uživatelů v Django

**Předchozí krok: [použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Vzhledem k tomu, že ověřování je běžné potřeby pro webové aplikace, šablona "Webového projektu Django" zahrnuje flow základní ověřování. ("Dotazuje webového projektu Django" Šablona popsané v kroku 6 v rámci tohoto kurzu také obsahuje stejný tok.) Pokud používáte některý z šablony projektu Django, Visual Studio obsahuje všechny moduly, které jsou nezbytné pro ověřování v projektu Django *settings.py*.

V tomto kroku se dozvíte:

> [!div class="checklist"]
> - Jak používat tok ověřování, které jsou součástí šablony sady Visual Studio (krok 5 - 1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: použití toku ověřování

Následující kroky postupu tok ověřování a popisují součástí projektu, které jsou zahrnuty:

1. Pokud ještě není jste postupovali podle pokynů *readme.html* soubor v kořenové složce projektu k vytvoření účtu superuživatele (správce), proveďte to nyní.

1. Spusťte aplikaci pomocí sady Visual Studio **ladění** > **spustit ladění** (**F5**). Když se aplikace zobrazí v prohlížeči, zda se zobrazila zpráva **přihlášení** se zobrazí v pravém horním rohu navigačního panelu.

    ![Přihlašovací ovládací prvek na stránce aplikace webového projektu Django](media/django/step05-login-control.png)

1. Otevřít *templates/app/layout.html* a zda se zobrazila zpráva `<div class="navbar ...>` prvek obsahuje značku `{% include app/loginpartial.html %}`. `{% include %}` Značky nastaví systém šablon Django aby se načetla obsah souboru v tomto okamžiku v šabloně obsahuje.

1. Otevřít *templates/app/loginpartial.html* a sledujte, jak používá podmíněný značky `{% if user.is_authenticated %}` spolu s `{% else %}` značky k vykreslení různé prvky uživatelského rozhraní v závislosti na tom, jestli má uživatel ověřen:

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

1. Vzhledem k tomu, že žádný uživatel je ověřen při prvním spuštění aplikace, tento kód šablony vykreslí pouze "Odstranit" odkaz na relativní cestou "login". Jak je uvedeno v *urls.py* (jak ukazuje předchozí části), tohoto postupu je namapován na `django.contrib.auth.views.login` zobrazení. Toto zobrazení přijímá následující data:

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

    Tady `template_name` identifikuje šablony, která pro přihlašovací stránku, v tomto případě *templates/app/login.html*. `extra_context` Vlastnost se přidá do výchozí kontext data k šabloně. Nakonec `authentication_form` Určuje třídu s formuláři pomocí přihlášení; v šabloně zobrazí jako `form` objektu. Výchozí hodnota je `AuthenticationForm` (z `django.contrib.auth.views`); místo toho používá formuláře definované v aplikace šablony projektů sady Visual Studio *forms.py* souboru:

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

    Jak je vidět tento formulář třída odvozena z `AuthenticationForm` a konkrétně přepíše pole uživatelské jméno a heslo pro přidání zástupný text. Šablony sady Visual Studio zahrnuje toto explicitní kód na za předpokladu, že budete pravděpodobně chtít přizpůsobit formulář, jako je například přidávání ověření síly hesla.

1. Když přejdete na přihlašovací stránku, potom, vykresluje aplikace *login.html* šablony. Proměnné `{{ form.username }}` a `{{ form.password }}` vykreslení `CharField` forms z `BootstrapAuthenticationForm`. Vyhnete se taky o vestavěný oddíl zobrazit chyby ověření a prvek předem připravená pro přihlašování přes sociální sítě, pokud budete chtít přidat tyto služby.

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

1. Při odeslání formuláře Django se pokusí ověřit vaše přihlašovací údaje (třeba super uživatelské přihlašovací údaje). Pokud se ověření nezdaří, zůstanete na aktuální stránce ale `form.errors` nastavenou na hodnotu true. Pokud je ověření úspěšné, Django přejde na relativní adresu URL do pole "next" `<input type="hidden" name="next" value="/" />`, který v tomto případě je domovská stránka (`/`).

1. Teď, když na domovské stránce se vykreslí znovu, `user.is_authenticated` vlastnost má hodnotu true, pokud *loginpartial.html* vykreslován šabloně. V důsledku toho se zobrazí **Hello (uživatelské jméno)** zprávu a **Odhlásit**. Můžete použít `user.is_authenticated` v ostatních částech aplikace ke kontrole ověřování.

    ![Hello na zprávu a odhlášení prvek na stránce aplikace webového projektu Django](media/django/step05-logoff-control.png)

1. Pokud chcete zkontrolovat, zda je ověřený uživatel oprávnění pro přístup k určitým prostředkům, potřebujete získat uživatelská oprávnění z databáze. Další informace najdete v tématu [pomocí ověřování systému Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django docs).

1. Super uživatel nebo správce, zejména je oprávnění pro přístup k vestavěné rozhraní správce Django pomocí relativní adresy URL "/admin/" a "/ admin/doc /". Chcete-li tato rozhraní, postupujte takto:

    1. Instalovat balíček Pythonu docutils do vašeho prostředí. Je skvělý způsob, jak to provést pro přidání "docutils" vaší *souboru requirements.txt* soubor, pak v **Průzkumníka řešení**, rozbalte projekt, rozbalte **prostředí Pythonu** uzlu, pak Klikněte pravým tlačítkem na prostředí, které používáte vyberte **instalovat z requirements.txt**.

    1. Otevření projektu Django *urls.py* a odeberte výchozí komentářů z následující položky:

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

    1. V projektu Django *settings.py* souboru, přejděte `INSTALLED_APPS` kolekce a přidejte `'django.contrib.admindocs'`.

    1. Po restartování aplikace, můžete přejít na "/admin/" a "/ admin/doc /" a provádět úkoly, jako je vytvoření dalších uživatelských účtů.

        ![Rozhraní správce Django](media/django/step05-administrator-interface.png)

1. Poslední část pro tok ověřování odhlášení. Jak je vidět v *loginpartial.html*, **Odhlásit** odkaz jednoduše se příspěvek na relativní adresu URL "/ přihlášení", který zařizuje služba předdefinovaných zobrazení `django.contrib.auth.views.logout`. Toto zobrazení nezobrazuje žádné uživatelské rozhraní a právě přejde na domovské stránce (jak je znázorněno v *urls.py* pro "^ odhlášení$" vzor). Pokud chcete zobrazit stránka odhlášení, nejprve změňte vzor adresy URL pro přidání vlastnosti "template_name" a odeberte vlastnost "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Pak vytvořte *templates/app/loggedoff.html* s použitím následujícího obsahu (minimální):

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Výsledek se zobrazí takto:

    ![Přidat stránku odhlášen](media/django/step05-logged-off-page.png)

1. Když jste hotovi, server zastavit a znovu potvrďte změny do správy zdrojového kódu.

### <a name="question-what-is-the-purpose-of-the--csrftoken--tag-that-appears-in-the-form-elements"></a>Otázka: Co je účelem {% csrf_token %} značek, které se zobrazí v \<formuláře\> elementy?

Odpověď: `{% csrf_token %}` značka zahrnuje integrované v Django [webů ochranu proti padělání (csrf) žádost o](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django docs). Obvykle přidáte tuto značku na libovolný element, který zahrnuje POST, PUT nebo DELETE požadavek metody, jako je například formulář. Funkce šablony vykreslování (`render`) pak vloží nezbytné ochrany.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití šablony Polls – webový projekt Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Ověřování uživatelů v Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
