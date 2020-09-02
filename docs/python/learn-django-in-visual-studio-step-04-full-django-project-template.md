---
title: Kurz Django ve Visual Studiu – krok 4, šablona webového projektu
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, konkrétně o funkcích poskytovaných šablonou webového projektu Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c778d830b20797962306700a5af938eb3a3bb142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62961676"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4: použití úplné šablony webového projektu v Django

**Předchozí krok: [poskytování statických souborů, přidávání stránek a použití dědičnosti šablon](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teď, když jste prozkoumali základy Django sestavením aplikace v šabloně "prázdného webového projektu Django" v aplikaci Visual Studio, můžete snadno pochopit úplnou aplikaci vytvořenou šablonou "Django web Project".

V tomto kroku teď:

> [!div class="checklist"]
> - Vytvořte úplnou webovou aplikaci v Django pomocí šablony "Django web Project" a prověřte strukturu projektu (krok 4-1).
> - Seznamte se s zobrazeními a šablonami stránek vytvořenými šablonou projektu, které se skládají ze tří stránek, které dědí ze základní šablony stránky a které využívají statické knihovny JavaScriptu jako jQuery a Bootstrap (krok 4-2).
> - Pochopení směrování adres URL poskytovaného šablonou (krok 4-3)

Šablona také poskytuje základní ověřování, které je popsáno v kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: vytvoření projektu ze šablony

1. V aplikaci Visual Studio přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem na řešení **LearningDjango** vytvořené dříve v tomto kurzu a vyberte **Přidat**  >  **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **soubor**  >  **Nové**  >  Místo toho **projekt** .)

1. V dialogovém okně Nový projekt vyhledejte a vyberte šablonu **webového projektu Django** , zavolejte projekt "DjangoWeb" a vyberte **OK**.

1. Vzhledem k tomu, že šablona znovu obsahuje soubor *requirements.txt* , Visual Studio zobrazí výzvu k instalaci těchto závislostí. Zvolte možnost, **nainstalujte ji do virtuálního prostředí**a v dialogovém okně **Přidat virtuální prostředí** vyberte **vytvořit** a přijměte výchozí hodnoty.

1. Jakmile Visual Studio dokončí nastavení virtuálního prostředí, postupujte podle pokynů v zobrazených *readme.html* a vytvořte uživatele Django superuživatele (tj. správce). Stačí kliknout pravým tlačítkem myši na projekt sady Visual Studio a vybrat příkaz **Python**  >  **Django Create-User** a pak postupovat podle pokynů. Při provádění funkcí ověřování aplikace nezapomeňte zaznamenat své uživatelské jméno a heslo při použití.

1. Nastavte projekt **DjangoWeb** jako výchozí pro řešení sady Visual Studio tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **nastavit jako spouštěný projekt**. Spouštěný projekt, který je zobrazen tučně, je spuštěn při spuštění ladicího programu.

    ![Průzkumník řešení zobrazení projektu DjangoWeb jako spouštěného projektu](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo pomocí tlačítka **webový server** na panelu nástrojů spusťte server:

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, domů, o a kontakt, které můžete procházet pomocí navigačního panelu. Podíváme se na jednu minutu nebo dvě, abyste prozkoumali různé části aplikace. K ověřování pomocí aplikace pomocí příkazu **Přihlásit** použijte přihlašovací údaje uživatele, které jste vytvořili dříve.

    ![Úplné zobrazení prohlížeče aplikace webového projektu Django](media/django/step04-full-app-desktop-view.png)

1. Aplikace vytvořená šablonou Django web Project používá Bootstrap pro reakce na rozložení, které vyhovuje faktorům pro mobilní zařízení. Chcete-li zobrazit tuto odezvu, změňte velikost prohlížeče tak, aby se obsah nakreslovat svisle a navigační panel se změní na ikonu nabídky:

    ![Mobilní (úzké) zobrazení aplikace webového projektu Django](media/django/step04-full-app-mobile-view.png)

1. Aplikaci můžete ponechat spuštěnou v následujících oddílech.

    Pokud chcete zastavit aplikaci a [Potvrdit změny ve správě zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), otevřete nejprve stránku **změny** v **Team Explorer**, klikněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **ENV**) a vyberte možnost **ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Kontrola vytvoření šablony

Na nejširší úrovni vytvoří šablona "webový projekt Django" následující strukturu:

- Soubory v kořenu projektu:
  - *Manage.py*, nástroj pro správu Django.
  - *DB. sqlite3*, výchozí databáze sqlite.
  - *requirements.txt* obsahující závislost na Django 1. x.
  - *readme.html*, soubor, který se zobrazí v aplikaci Visual Studio po vytvoření projektu. Jak je uvedeno v předchozí části, postupujte podle pokynů uvedených tady a vytvořte pro aplikaci účet super uživatel (správce).
- Složka *aplikace* obsahuje všechny soubory aplikací, včetně zobrazení, modelů, testů, formulářů, šablon a statických souborů (viz krok 4-2). Obvykle tuto složku přejmenujete, aby používala více různých názvů aplikací.
- Složka *DjangoWeb* (projekt Django) obsahuje typické soubory projektu Django: * \_ \_ init \_ \_ . py*, *Settings.py*, *URLs.py*a *WSGI.py*. Když použijete šablonu projektu, *Settings.py* je už pro aplikaci a databázový soubor nakonfigurovaný a v *URLs.py* je už nakonfigurované směrování na všechny stránky aplikací, včetně přihlašovacího formuláře.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: je možné sdílet virtuální prostředí mezi projekty sady Visual Studio?

Odpověď: Ano, ale udělejte to s vědomím, že různé projekty nejspíš v průběhu času používají různé balíčky, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které ji používají.

Chcete-li však použít stávající virtuální prostředí, postupujte následovně:

1. Až se zobrazí výzva k instalaci závislostí v aplikaci Visual Studio, vyberte možnost **instalovat** vlastní.
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte **Přidat existující virtuální prostředí**.
1. Přejděte na složku obsahující virtuální prostředí a vyberte ji a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: porozumění zobrazením a šablonám stránek vytvořeným šablonou projektu

Při spuštění projektu aplikace obsahuje tři zobrazení: domů, o aplikaci a kontakt. Kód pro tato zobrazení najdete ve složce *app/views* . Každá funkce zobrazení jednoduše volá `django.shortcuts.render` cestu k šabloně a objekt jednoduchého slovníku. Například stránka about je zpracována `about` funkcí:

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

Šablony se nacházejí v *šablonách nebo* složkách aplikace (a obvykle chcete *aplikaci* přejmenovat na název vaší reálné aplikace). Základní šablona, *layout.html*, je nejrozsáhlejší. Odkazuje na všechny nezbytné statické soubory (JavaScript a CSS), definuje blok s názvem "obsah", na který se přepíší jiné stránky, a poskytuje další blok s názvem "skripty". Následující výňatky uvedené v poznámce z *layout.html* znázorňují tyto konkrétní oblasti:

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

Jednotlivé šablony stránky, *about.html*, *contact.html*a *index.html*, každý rozšiřuje základní šablonu *layout.html*. *about.html* je nejjednodušší a ukazuje `{% extends %}` `{% block content %}` značky a:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* a *contact.html* používají stejnou strukturu a poskytují lengthier obsah v bloku Content.

Ve složce *Templates/App* je také Čtvrtá stránka *login.html*spolu s *loginpartial.html* , která se přenesla do *layout.html* pomocí `{% include %}` . Tyto soubory šablon jsou popsány v kroku 5 při ověřování.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Otázka: může být {% Block%} a {% endblock%} odsazený v šabloně stránky Django?

Odpověď: Ano, šablony stránky Django fungují správně, pokud odsadíte značky bloku, třeba je zarovnat v rámci příslušných nadřazených prvků. Nejsou odsazeny v šablonách stránky generovaných šablonou projektu sady Visual Studio, abyste mohli jasně zjistit, kde jsou umístěny.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4-3: pochopení směrování adres URL vytvořeného šablonou

Soubor *URLs.py* projektu Django, jak je vytvořený šablonou Django web Project, obsahuje následující kód:

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

První tři vzory adresy URL se mapují přímo k `home` `contact` `about` zobrazením, a v souboru *views.py* aplikace. Vzorce `^login/$` a `^logout$` na druhé straně využívají integrované zobrazení Django místo zobrazení definovaných aplikací. Volání `url` metody také zahrnují další data pro přizpůsobení zobrazení. Krok 5 prozkoumá tato volání.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Otázka: ve vytvořeném projektu používá vzor adresy URL "o" místo ^ o $, jak je znázorněno zde?

Odpověď: nedostatek koncového znaku $ v regulárním výrazu byl jednoduchým dohledem v mnoha verzích šablony projektu. Vzor adresy URL funguje dokonale dobře pro stránku s názvem "About", ale bez koncového znaku "$" se ve vzorci URL shodují i s adresami URL jako "About = Django", "about09876", "aboutoflaughter" atd. Tady je zobrazen koncový znak $, ve kterém můžete vytvořit vzor adresy URL, který odpovídá *pouze* "About".

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Ověřování uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Nasazení webové aplikace do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Vytvoření první aplikace pro Django, část 4 – formuláře a obecná zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
