---
title: Naučte se Django kurz v sadě Visual Studio, krok 5, ověřování
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, konkrétně funkce ověřování, jak je k dispozici šablony webového projektu Django.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957846"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5: Ověření uživatelů v Django

**Předchozí krok: [Použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Vzhledem k tomu, že ověřování je běžnou potřebou webových aplikací, šablona "Django Web Project" obsahuje základní tok ověřování. (Šablona "Ankety Django Web Project" popsané v kroku 6 tohoto kurzu také zahrnuje stejný tok.) Při použití některé šablony projektu Django Visual Studio obsahuje všechny potřebné moduly pro ověřování v *settings.py*projektu Django .

V tomto kroku se dozvíte:

> [!div class="checklist"]
> - Použití toku ověřování poskytovaného v šablonách sady Visual Studio (krok 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Krok 5-1: Použití toku ověřování

Následující kroky provedou tok ověřování a popíší části projektu, které jsou zapojeny:

1. Pokud jste ještě nepostupovali podle pokynů v souboru *readme.html* v kořenovém adresáři projektu a vytvořili účet super uživatele (správce), učiňte tak nyní.

1. Spusťte aplikaci z Visual Studia pomocí **ladění** > **start ladění** **(F5**). Když se aplikace zobrazí v prohlížeči, všimněte si, že **Přihlásit** se zobrazí v pravém horním části panelu nav.

    ![Ovládání přihlášení na stránce aplikace Django Web Project](media/django/step05-login-control.png)

1. Otevřete *templates/app/layout.html* a `<div class="navbar ...>` dbejte `{% include app/loginpartial.html %}`na to, aby prvek obsahoval značku . Značka `{% include %}` instruuje Django je šablonovací systém vytáhnout obsah zahrnutého souboru v tomto bodě v obsahující šablony.

1. Otevřete *templates/app/loginpartial.html* a sledujte, `{% if user.is_authenticated %}` jak `{% else %}` používá podmíněnou značku spolu se značkou k vykreslení různých prvků uživatelského rozhraní v závislosti na tom, zda se uživatel ověřil:

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

1. Vzhledem k tomu, že žádný uživatel je ověřen při prvním spuštění aplikace, tento kód šablony vykreslí pouze odkaz "Přihlásit" relativní cestu "přihlášení". Jak je uvedeno v *urls.py* (jak je znázorněno v `django.contrib.auth.views.login` předchozím úseku), je tato trasa mapována na pohled. Toto zobrazení obdrží následující údaje:

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

    Zde `template_name` identifikuje šablonu pro přihlašovací stránku, v tomto případě *templates/app/login.html*. Vlastnost `extra_context` je přidána do výchozíkontextová data uvedená do šablony. Nakonec `authentication_form` určuje třídu formuláře, která se má použít s přihlášením; v šabloně se `form` zobrazí jako objekt. Výchozí hodnota `AuthenticationForm` je `django.contrib.auth.views`(od ); Šablona projektu Visual Studia místo toho používá formulář definovaný v *souboru forms.py* aplikace:

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

    Jak můžete vidět, tato třída `AuthenticationForm` formuláře je odvozena od polí uživatelského jména a hesla a konkrétně přepíše je a přidá zástupný text. Šablona sady Visual Studio obsahuje tento explicitní kód za předpokladu, že pravděpodobně budete chtít přizpůsobit formulář, jako je například přidání ověření síly hesla.

1. Když přejdete na přihlašovací stránku, pak aplikace vykreslí šablonu *login.html.* Proměnné `{{ form.username }}` a `{{ form.password }}` vykreslení `CharField` formulářů z `BootstrapAuthenticationForm`. K dispozici je také předdefinovaná část, která zobrazuje chyby ověření, a připravený prvek pro přihlášení do sociálních sítí, pokud se rozhodnete přidat tyto služby.

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

1. Při odeslání formuláře se django pokusí ověřit vaše přihlašovací údaje (například pověření super uživatele). Pokud se ověření nezdaří, zůstanete na aktuální stránce, ale `form.errors` na je nastavena na hodnotu true. Pokud je ověření úspěšné, Django přejde na relativní adresu `<input type="hidden" name="next" value="/" />`URL v poli "další", což je v tomto případě domovská stránka (`/`).

1. Nyní, když je domovská stránka `user.is_authenticated` vykreslena znovu, vlastnost je true při *loginpartial.html* šablona je vykreslen. V důsledku toho se zobrazí zpráva **Hello (uživatelské jméno)** a **Odhlásit .** Můžete použít `user.is_authenticated` v jiných částech aplikace ke kontrole ověřování.

    ![Ovládací prvek zprávy Hello a odhlášení na stránce aplikace Aplikace Webového projektu Django](media/django/step05-logoff-control.png)

1. Chcete-li zkontrolovat, zda je ověřený uživatel oprávněn k přístupu k určitým prostředkům, je třeba z databáze načíst oprávnění specifická pro uživatele. Další informace naleznete [v tématu Použití systému ověřování Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django docs).

1. Super uživatel nebo správce, zejména, je oprávněn k přístupu k vestavěným django administrátorské rozhraní pomocí relativní adresy URL "/admin/" a "/admin/doc/". Chcete-li tato rozhraní povolit, postupujte takto:

    1. Nainstalujte balíček docutils Python do vašeho prostředí. Skvělý způsob, jak to udělat, je přidat "docutils" do souboru *requirements.txt,* pak v **Průzkumníkovi řešení**rozbalte projekt, rozbalte uzel **Prostředí Pythonu** a klikněte pravým tlačítkem myši na prostředí, které používáte, **a vyberte možnost Instalovat z requirements.txt**.

    1. Otevřete *urls.py* projektu Django a odeberte výchozí komentáře z následujících položek:

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

    1. V souboru *settings.py* projektu Django přejděte do `INSTALLED_APPS` kolekce a přidejte `'django.contrib.admindocs'`.

    1. Po restartování aplikace můžete přejít na "/admin/" a "/admin/doc/" a provádět úkoly, jako je vytváření dalších uživatelských účtů.

        ![Administrátorské rozhraní Django](media/django/step05-administrator-interface.png)

1. Poslední část toku ověřování je odhlášení. Jak můžete vidět v *loginpartial.html*, **odhlásit** odkaz prostě dělá POST na relativní URL "/login", který je zpracován vestavěný pohled `django.contrib.auth.views.logout`. Toto zobrazení nezobrazuje žádné ui a pouze přejde na domovskou stránku (jak je znázorněno v *urls.py* pro vzor ^odhlášení$"). Pokud chcete zobrazit odhlašovací stránku, nejprve změňte vzorek adresy URL takto, abyste přidali vlastnost "template_name" a odebrali vlastnost "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Poté vytvořte *templates/app/loggedoff.html* s následujícím (minimálním) obsahem:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Výsledek se zobrazí takto:

    ![Přidána odhlášená stránka](media/django/step05-logged-off-page.png)

1. Až budete hotovi, zastavte server a znovu potvrdíte změny správy zdrojového kódu.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Otázka: Jaký je účel značky {% csrf_token %}, která se zobrazí v prvcích \<formuláře?\>

Odpověď: `{% csrf_token %}` Značka obsahuje Django je vestavěný [cross-site žádost o padělání (csrf) ochrana](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django docs). Tuto značku obvykle přidáte do libovolného prvku, který zahrnuje metody požadavku POST, PUT nebo DELETE, například formulář. Funkce vykreslování šablony (`render`) pak vloží potřebnou ochranu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití šablony Webového projektu Ankety Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Ověření uživatele v Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
