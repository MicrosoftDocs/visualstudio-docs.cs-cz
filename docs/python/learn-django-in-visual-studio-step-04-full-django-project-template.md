---
title: Přečtěte si kurz Django v sadě Visual Studio kroku 4, Šablona webového projektu
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně funkcím, které poskytuje šablony webového projektu Django.
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
ms.openlocfilehash: 865a0368933fa0a66728afaead6677cbeca84834
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065458"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4: Použití úplné šablony webového projektu Django

**Předchozí krok: [doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teď, když jste prozkoumali základní informace o Django vytvořením aplikace na šablony "Prázdné Django webového projektu" v sadě Visual Studio, je možné snadno zjistit plnější aplikace, který je vytvořen pomocí šablony "Webového projektu Django".

V tomto kroku můžete nyní:

> [!div class="checklist"]
> - Vytvoření pomocí šablony "Webového projektu Django" plnější webové aplikace Django a zkontrolujte strukturu projektu (krok 4 - 1)
> - Rady pro pochopení zobrazení a stránky šablony vytvořené šablony projektu, které tvoří tři stránky, které dědí ze základní stránky šablony a, který využívá statické knihovny JavaScriptu, jako je jQuery a Bootstrap (krok 4-2)
> - Vysvětlení směrování adres URL poskytovanou šablonou (krok 4-3)

Šablona také nabízí základní ověřování, který je popsaný v kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: vytvoření projektu ze šablony

1. V sadě Visual Studio, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem myši **LearningDjango** řešení vytvořené dříve v tomto kurzu a vyberte **přidat**  >   **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **souboru** > **nový** > **projektu** místo.)

1. V dialogovém okně Nový projekt, vyhledejte a vyberte **webového projektu Django** šablony, volání "DjangoWeb" projekt a vyberte **OK**.

1. Vzhledem k tomu šablonu znovu zahrnuje *souboru requirements.txt* souboru, Visual Studio vyzve vhodného místa pro instalaci těchto závislostí. Zvolte si možnost **nainstalovat do virtuálního prostředí**a **přidat virtuální prostředí** dialogové okno Vybrat **vytvořit** přijměte výchozí hodnoty.

1. Po dokončení nastavení virtuálního prostředí sady Visual Studio, postupujte podle pokynů zobrazených *readme.html* vytvořit Django superuživatel (to znamená, že správce). Stačí pravým tlačítkem myši na projekt aplikace Visual Studio a vybrat **Python** > **vytvořit Superživatele Django** příkaz a pak postupujte podle zobrazených výzev. Ujistěte se, že záznam uživatelského jména a hesla použijte při výkonu funkce ověřování aplikace.

1. Nastavte **DjangoWeb** projekt jako výchozí pro řešení sady Visual Studio kliknutím pravým tlačítkem myši v projektu **Průzkumníka řešení** a vyberete **nastavit jako spouštěný projekt** . Projekt při spuštění, která je znázorněna v tučné písmo, se co je spuštěn při spuštění ladicího programu.

    ![Průzkumník řešení zobrazující DjangoWeb projekt jako spouštěný projekt](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů můžete spustit na serveru:

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořené pomocí šablony má tři stránky, Home, o programu a kontaktovat, který můžete procházet pomocí navigačního panelu. Trvat minutu nebo dvě prozkoumat různé části aplikace. K ověření aplikace prostřednictvím **přihlášení** příkazu, použijte přihlašovací údaje superuživatele vytvořili dříve.

    ![Zobrazit v prohlížeči úplné aplikace webového projektu Django](media/django/step04-full-app-desktop-view.png)

1. Aplikace vytvořené pomocí šablony "Webového projektu Django" využívá Bootstrap responzivním rozložením, které se přizpůsobuje mobilních zařízení. Pokud chcete zobrazit tento rychlost odezvy, změna velikosti prohlížeči v úzkém zobrazení tak, aby obsah vykreslí svisle a na navigačním panelu se změní ikona nabídky:

    ![Zobrazení Mobile (úzké) s aplikací webového projektu Django](media/django/step04-full-app-mobile-view.png)

1. Můžete nechat aplikaci spuštěnou pro následující části.

    Pokud budete chtít aplikaci zastavit a [potvrzení změn do správy zdrojových kódů](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), nejdřív otevřete **změny** stránku **Průzkumník týmových projektů**, klikněte pravým tlačítkem na složku pro virtuální prostředí ( pravděpodobně **env**) a vyberte **ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Zkontrolujte, co šablona vytvoří

Na úrovni nejširší "Webového projektu Django" šablona vytvoří následující strukturu:

- Soubory v kořenové složce projektu:
  - *souboru Manage.PY*, nástroj pro správu Django.
  - *DB.sqlite3*, vytvoří i výchozí databáze SQLite.
  - *soubor Requirements.txt* obsahuje závislost na Django 1.x.
  - *Readme.HTML*, soubor, který se zobrazí v sadě Visual Studio po vytvoření projektu. Jak je uvedeno v předchozí části, postupujte podle zde uvedených pokynů k vytvoření účtu superuživatele (správce) pro aplikaci.
- *Aplikace* složka obsahuje všechny soubory aplikace, včetně zobrazení, modely, testy, formulářů, šablon a statické soubory (viz krok 4-2). Obvykle přejmenovat tuto složku používat více odlišný název aplikace.
- *DjangoWeb* složky (projektu Django) obsahuje typické soubory projektu Django:  *\_ \_init\_\_.py*,  *Settings.PY*, *urls.py*, a *wsgi.py*. Pomocí šablony projektu *settings.py* už je nakonfigurovaný pro aplikace a soubor databáze a *urls.py* už má nakonfigurovanou trasy pro všechny aplikace stránky, včetně přihlašovací formulář.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: Je možné sdílet mezi projekty aplikace Visual Studio do virtuálního prostředí?

Odpověď: Ano, ale Uděláte to tak povědomí, že různé projekty, které mohou použít jiné balíčky v čase, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které ji používají.

Nicméně pokud chcete použít existující virtuální prostředí, postupujte takto:

1. Po zobrazení výzvy k instalaci závislostí v sadě Visual Studio, vyberte **nainstaluji je sám** možnost.
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prostředí Pythonu** uzel a vyberte možnost **přidat existující virtuální prostředí**.
1. Vyhledejte a vyberte složku, která obsahuje virtuální prostředí a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4 – 2: pochopení zobrazení a stránky šablony vytvořené šablony projektu

Jak zjistíte, když spustíte projekt, aplikace obsahuje tři zobrazení: Home, o programu a kontaktujte. Kód pro tato zobrazení je součástí *aplikace a zobrazení* složky. Každá funkce zobrazení jednoduše volá `django.shortcuts.render` cestou k šablonu a objekt jednoduchý slovník. Například se postará o stránku `about` funkce:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Šablony jsou umístěny v aplikaci prvku *šablony nebo aplikaci* složku (a obvykle budete chtít přejmenovat *aplikace* na název vaší aplikace skutečný). Základní šablona *layout.html*, je nejvíc rozsáhlý. Odkazuje na všechny potřebné statické soubory (jazyk JavaScript a CSS), definuje blok s názvem "obsah" jiných stránek přepsání a poskytuje další blok s názvem "skripty". Následující anotována výňatky ze *layout.html* zobrazit tyto konkrétní oblasti:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Šablony jednotlivou stránku *about.html*, *contact.html*, a *index.html*, každé rozšiřte základní šablonu *layout.html*. *About.HTML* je nejjednodušší a ukazuje, `{% extends %}` a `{% block content %}` značky:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.HTML* a *contact.html* použít stejnou strukturu a poskytovat delší obsah v bloku "obsah".

V *šablony nebo aplikaci* složku je také čtvrtá stránka *login.html*, spolu s *loginpartial.html* přenese do *layout.html*pomocí `{% include %}`. Tyto soubory šablon jsou popsané v kroku 5 v ověřování.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Otázka: Můžou {% blokovat %} a {% endblock %} odsazeny v šabloně Django stránky?

Odpověď: Ano, šablony Django fungovat správně Pokud odsazení bloku značky, třeba tak, aby zarovnání v rámci jejich odpovídající nadřazené prvky. Nejsou určeny v šablonách stránky vygenerovaná šablona projektu sady Visual Studio tak, aby jasně vidíte, kde jsou umístěny.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4-3: vysvětlení směrování adres URL, které se vytvoří pomocí šablony

V projektu Django *urls.py* soubor při vytváření šablony "Webového projektu Django" obsahuje následující kód:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

První tři vzory adres URL mapují přímo `home`, `contact`, a `about` zobrazení v aplikaci prvku *views.py* souboru. Tyto vzory se dají `^login/$` a `^logout$`, na druhé straně, místo zobrazení definované aplikací použít předdefinovaná zobrazení Django. Volání `url` metoda obsahovat také další data, čímž přizpůsobíte zobrazení. Krok 5 zkoumá těchto volání.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Otázka: V projektu jsem vytvořil, proč "about" vzor adresy URL používá "^ o ' místo ' ^ o$" jak je znázorněno zde?

Odpověď: Chybějící koncové "$" v regulárním výrazu byl jednoduchý dohledu v mnoha verze šablony projektu. Vzor adresy URL dokonale dobře funguje pro stránku s názvem "about", ale bez koncové "$" vzor adresy URL také odpovídající adresy URL jako "přibližně = django", "about09876", "aboutoflaughter" a proto na. Koncové "$" je znázorněna zde vytvořit vzor adresy URL, která odpovídá *pouze* "o".

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Ověřování uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Zápis svoji první aplikaci Django, část 4 – formulářů a obecného zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
