---
title: Naučte se django kurz v Sadě Visual Studio krok 4, šablona webového projektu
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, konkrétně funkce poskytované šablonou webového projektu Django.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62961676"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Krok 4: Použití úplné šablony webového projektu Django

**Předchozí krok: [Obsluha statických souborů, přidávání stránek a používání dědičnosti šablony](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teď, když jste prozkoumali základy Django vytvořením aplikace na šabloně "Blank Django Web Project" v sadě Visual Studio, můžete snadno pochopit plnější aplikaci, která je vytvořena šablonou "Django Web Project".

V tomto kroku nyní:

> [!div class="checklist"]
> - Vytvořte si plnější webovou aplikaci Django pomocí šablony "Django Web Project" a prozkoumejte strukturu projektu (krok 4-1)
> - Porozumět zobrazením a šablonám stránek vytvořeným šablonou projektu, které se skládají ze tří stránek, které dědí ze základní šablony stránky a které využívají statické knihovny JavaScriptu, jako je jQuery a Bootstrap (krok 4-2)
> - Principy směrování adres URL poskytovaného šablonou (krok 4-3)

Šablona také poskytuje základní ověřování, které je zahrnuto v kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Vytvoření projektu ze šablony

1. V sadě Visual Studio přejděte do **Průzkumníka řešení**, klikněte pravým tlačítkem myši na řešení **LearningDjango** vytvořené dříve v tomto kurzu a vyberte **přidat** > **nový projekt**. (Pokud chcete použít nové řešení, vyberte místo toho **možnost Soubor** > **nového** > **projektu.)**

1. V novém dialogovém okně projektu vyhledejte a vyberte šablonu **webového projektu Django,** zavolejte projekt "DjangoWeb" a vyberte **OK**.

1. Vzhledem k tomu, že šablona opět obsahuje soubor *requirements.txt,* Visual Studio se zeptá, kam nainstalovat tyto závislosti. Zvolte možnost Instalovat **do virtuálního prostředí**a v dialogovém okně Přidat virtuální **prostředí** vyberte **Vytvořit,** abyste přijali výchozí hodnoty.

1. Po dokončení nastavení virtuálního prostředí visual studio, postupujte podle pokynů v *zobrazenéreadme.html* vytvořit Django super uživatele (to znamená správce). Stačí kliknout pravým tlačítkem myši na projekt sady Visual Studio a vybrat příkaz **Python** > **Django Vytvořit superuser** a potom postupujte podle pokynů. Nezapomeňte si při provádění ověřovacích funkcí aplikace zaznamenat své uživatelské jméno a heslo.

1. Nastavte projekt **DjangoWeb** jako výchozí pro řešení sady Visual Studio klepnutím pravým tlačítkem myši na tento projekt v **Průzkumníku řešení** a výběrem **možnosti Nastavit jako projekt po spuštění**. Projekt spuštění, který je zobrazen tučně, je to, co je spuštěno při spuštění ladicího programu.

    ![Průzkumník řešení zobrazující projekt DjangoWeb jako projekt spuštění](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **Možnost Ladění** > **spouštět ladění** **(F5)** nebo pomocí tlačítka Webový **server** na panelu nástrojů spusťte server:

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, Domovská stránka, Informace a Kontakt, mezi nimiž procházíte pomocí nav panelu. Udělejte si minutu nebo dvě, abyste prozkoumali různé části aplikace. Chcete-li se s aplikací ověřit pomocí příkazu **Přihlásit,** použijte dříve vytvořená pověření superuživatele.

    ![Zobrazení celého prohlížeče aplikace Django Web Project](media/django/step04-full-app-desktop-view.png)

1. Aplikace vytvořená šablonou "Django Web Project" používá Bootstrap pro responzivní rozložení, které vyhovuje mobilním tvarovým faktorům. Chcete-li zobrazit tuto odezvu, změňte velikost prohlížeče do úzkého zobrazení tak, aby se obsah vykresloval svisle a nav panel se změní na ikonu nabídky:

    ![Mobilní (úzký) pohled na aplikaci Django Web Project](media/django/step04-full-app-mobile-view.png)

1. Aplikaci můžete nechat spuštěnou pro následující oddíly.

    Pokud chcete aplikaci zastavit a [potvrdit změny správy zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), otevřete **nejprve** stránku Změny v **Průzkumníkovi týmu**, klepněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **env)** a vyberte **Ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Zkontrolujte, co šablona vytváří

Na nejširší úrovni šablona "Django Web Project" vytvoří následující strukturu:

- Soubory v kořenovém adresáři projektu:
  - *manage.py*, administrativní nástroj Django.
  - *db.sqlite3*, výchozí databáze SQLite.
  - *requirements.txt* obsahující závislost na souboru Django 1.x.
  - *readme.html*, soubor, který se zobrazí v sadě Visual Studio po vytvoření projektu. Jak je uvedeno v předchozí části, postupujte podle pokynů zde vytvořit super uživatel (správce) účet pro aplikaci.
- Složka *aplikace* obsahuje všechny soubory aplikace, včetně zobrazení, modelů, testů, formulářů, šablon a statických souborů (viz krok 4-2). Tuto složku obvykle přejmenujete tak, aby používala výraznější název aplikace.
- Složka *DjangoWeb* (projekt Django) obsahuje typické soubory projektu Django: * \_ \_\_\_init .py*, *settings.py*, *urls.py*a *wsgi.py*. Pomocí šablony projektu *je settings.py* již nakonfigurovánpro aplikaci a databázový soubor a *urls.py* je již nakonfigurován o trasách na všechny stránky aplikace, včetně přihlašovacího formuláře.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: Je možné sdílet virtuální prostředí mezi projekty sady Visual Studio?

Odpověď: Ano, ale s vědomím, že různé projekty pravděpodobně používají různé balíčky v průběhu času, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které jej používají.

Chcete-li však použít existující virtuální prostředí, postupujte takto:

1. Po zobrazení výzvy k instalaci závislostí v sadě Visual Studio vyberte **možnost Nainstalovat je sám.**
1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte **přidat existující virtuální prostředí**.
1. Přejděte do složky obsahující virtuální prostředí a vyberte ji a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: Pochopení zobrazení a šablon stránek vytvořených šablonou projektu

Jak zjistíte při spuštění projektu, aplikace obsahuje tři zobrazení: Domů, O a Kontakt. Kód pro tato zobrazení se nachází ve složce *aplikace/zobrazení.* Každá funkce zobrazení `django.shortcuts.render` jednoduše volá s cestou k šabloně a jednoduchým objektem slovníku. Například stránka O aplikaci `about` je zpracována funkcí:

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

Šablony jsou umístěny ve složce *šablony/aplikace* aplikace (a obvykle chcete *aplikaci* přejmenovat na název skutečné aplikace). Základní *šablona, layout.html*, je nejrozsáhlejší. Odkazuje na všechny potřebné statické soubory (JavaScript a CSS), definuje blok s názvem "obsah", který ostatní stránky přepsat, a poskytuje další blok s názvem "skripty". Následující poznámky z *layout.html* ukazují tyto specifické oblasti:

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

Jednotlivé šablony *stránek, about.html*, *contact.html*a *index.html*, každá rozšířit základní šablony *layout.html*. *about.html* je nejjednodušší a `{% extends %}` zobrazuje `{% block content %}` a tagy:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* a *contact.html* používají stejnou strukturu a poskytují delší obsah v bloku "obsah".

Ve složce *templates /app* je také čtvrtá stránka *login.html*, spolu s *loginpartial.html,* který je uveden do *layout.html* pomocí `{% include %}`. Tyto soubory šablon jsou popsány v kroku 5 o ověřování.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Otázka: Lze v šabloně stránky Django odsazet {% bloku %} a {% koncového bloku %}?

Odpověď: Ano, šablony stránek Django fungují dobře, pokud odsavíte značky bloků, možná je zarovnáte v příslušných nadřazených prvcích. Nejsou odsazené v šablonách stránek generovaných šablonou projektu Sady Visual Studio, takže můžete jasně vidět, kde jsou umístěny.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4-3: Principy směrování adres URL vytvořeného šablonou

Soubor *urls.py* projektu Django vytvořený šablonou "Django Web Project" obsahuje následující kód:

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

První tři vzory adres URL `home`se `contact`mapují přímo na soubor , a `about` zobrazení v *souboru views.py* aplikace. Vzory `^login/$` a `^logout$`na druhé straně používají předdefinované zobrazení Django namísto zobrazení definovaných aplikací. Volání `url` metody také obsahují další data pro přizpůsobení zobrazení. Krok 5 zkoumá tyto hovory.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Otázka: V projektu jsem vytvořil, proč "o" URL vzor používá '^o' místo '^ o $', jak je znázorněno zde?

Odpověď: Nedostatek koncové '$' v regulárním výrazu byl jednoduchý dohled v mnoha verzích šablony projektu. Url vzor funguje perfektně pro stránku s názvem "o", ale bez koncové '$' URL vzor také odpovídá URL jako "about = django", "about09876", "aboutoflaughter"a tak dále. Koncové '$' je zde zobrazen o vytvoření url vzor, který odpovídá *pouze* "o".

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Ověření uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Psaní první aplikace Django, část 4 - formuláře a obecná zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
