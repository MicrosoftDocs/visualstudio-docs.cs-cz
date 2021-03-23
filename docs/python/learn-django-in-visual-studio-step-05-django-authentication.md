---
title: Seznámení s Django v aplikaci Visual Studio, krok 5, ověřování
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, konkrétně o funkcích ověřování poskytovaných šablonami webových projektů Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f589aed953a852cb57570988d914f77b2fa10b2
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806014"
---
# <a name="step-5-authenticate-users-in-django"></a>Krok 5: ověření uživatelů v Django

**Předchozí krok: [použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
Vzhledem k tomu, že ověřování je běžnou potřebou pro webové aplikace, zahrnuje šablona "webový projekt Django" tok základního ověřování. (Šablona "cyklické Djangos web Project" popsaná v kroku 6 tohoto kurzu obsahuje také stejný tok.) Při použití některé z šablon projektů Django zahrnuje Visual Studio všechny nezbytné moduly pro ověřování v *Settings.py* projektu Django.
::: moniker-end

::: moniker range=">=vs-2019"
Vzhledem k tomu, že ověřování je běžnou potřebou pro webové aplikace, zahrnuje šablona "webový projekt Django" tok základního ověřování. Při použití některé z šablon projektů Django zahrnuje Visual Studio všechny nezbytné moduly pro ověřování v *Settings.py* projektu Django.
::: moniker-end

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

    1. Nainstalujte do svého prostředí balíček python Docutils. Skvělým způsobem, jak to provést, je přidat do souboru *requirements.txt* "Docutils", pak v **Průzkumník řešení** rozbalíte projekt, rozbalíte uzel **prostředí Pythonu** a potom kliknete pravým tlačítkem na prostředí, ve kterém jste vybrali **instalovat z requirements.txt**.

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

::: moniker range="vs-2017"
- [Použití šablony webového projektu Django pro cyklické dotazování](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Pokud jste řešení sady Visual Studio potvrdili pro správu zdrojového kódu v průběhu tohoto kurzu, je teď dobrý čas udělat další potvrzení změn. Vaše řešení by mělo odpovídat zdrojovému kódu kurzu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django).

Nyní jste prozkoumali celou šablonu "prázdný webový projekt v Django" a "webový projekt Django" v aplikaci Visual Studio. Seznámili jste se se základy Django, jako je používání zobrazení a šablon, a máte prozkoumání směrování, ověřování a používání databázových modelů. Nyní byste měli být schopni vytvořit vlastní webovou aplikaci s libovolnými zobrazeními a modely, které potřebujete.

Spuštění webové aplikace ve vývojovém počítači je pouze jedním krokem v tom, že je aplikace k dispozici pro vaše zákazníky. Další kroky můžou zahrnovat následující úlohy:

- Nasaďte webovou aplikaci na provozní server, například Azure App Service. Viz [publikovat do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Stránku 404 upravte vytvořením šablony s názvem *Templates/404.html*. Pokud je přítomna, Django použije tuto šablonu namísto jejího výchozího typu. Další informace najdete v tématu [zobrazení chyb](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) v dokumentaci k Django.

- Zápis testů jednotek v *Tests.py*; šablony projektů sady Visual Studio poskytují počáteční body pro tyto a další informace najdete na stránce s [psaním první aplikace v Django, v části 5 – testování](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) a [testování v Django](https://docs.djangoproject.com/en/2.0/topics/testing/) v dokumentaci Django.

- Změňte aplikaci z SQLite na úložiště dat na úrovni produkčního prostředí, jako je PostgreSQL, MySQL a SQL Server (všechny můžou být hostované v Azure). Jak je popsáno v tématu [kdy použít SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), je podrobná práce pro weby s nízkým až středním provozem s menším počtem přístupů 100 tisíc za den, ale nedoporučuje se pro vyšší svazky. Je také omezen na jeden počítač, a proto jej nelze použít v jakémkoli scénáři s více servery, jako je vyrovnávání zatížení a geografická replikace. Informace o podpoře Django pro jiné databáze najdete v tématu [nastavení databáze](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Můžete také použít [sadu Azure SDK pro Python](/azure/python/) pro práci se službami Azure Storage, jako jsou tabulky a objekty blob.

- Nastavte kanál průběžné integrace nebo průběžného nasazování na službu, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (prostřednictvím Azure Repos nebo GitHubu nebo jinde) můžete nakonfigurovat projekt Azure DevOps tak, aby automaticky spouštěl testy jednotek jako předpoklad pro vydání, a také nakonfigurovat kanál pro nasazení na přípravný Server pro další testy před nasazením do produkčního prostředí. Azure DevOps navíc integruje s monitorovacími řešeními, jako je App Insights, a uzavírá celý cyklus pomocí nástrojů pro agilní plánování. Další informace najdete v tématu [vytvoření kanálu CI/CD pro Python s projektem Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) a také v [dokumentaci k Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
::: moniker-end
## <a name="go-deeper"></a>Přejít hlouběji

- [Ověřování uživatelů v Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
