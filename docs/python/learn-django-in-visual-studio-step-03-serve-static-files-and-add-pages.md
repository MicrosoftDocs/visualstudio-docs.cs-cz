---
title: Naučte se Django kurz v sadě Visual Studio krok 3, statické soubory a stránky
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, konkrétně ukazuje, jak sloužit statické soubory, přidat stránky do aplikace a použít dědičnost šablony
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 54a80ef606a553846ef5be7a86ed4183f3ffde57
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957985"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsluhování statických souborů, přidávání stránek a používání dědičnosti šablony

**Předchozí krok: [Vytvoření aplikace Django se zobrazeními a šablonami stránek](learn-django-in-visual-studio-step-02-create-an-app.md)**

V předchozích krocích tohoto kurzu jste se naučili, jak vytvořit minimální aplikaci Django s jednou stránkou samostatného HTML. Moderní webové aplikace se však obvykle skládají z mnoha stránek a využívají sdílené prostředky, jako jsou soubory CSS a JavaScript, k zajištění konzistentního stylu a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Pomocí šablon položek sady Visual Studio můžete rychle přidávat nové soubory různých typů pomocí vhodného standardního kódu (krok 3-1)
> - Konfigurace projektu Django tak, aby sloužil statickým souborům (krok 3-2)
> - Přidání dalších stránek do aplikace (krok 3-3)
> - Vytvoření záhlaví a nav panelu, který se používá na všech stránkách (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznámení se se šablonami položek

Při vývoji aplikace Django obvykle přidáváte mnoho dalších souborů Pythonu, HTML, CSS a JavaScriptu. Pro každý typ souboru (stejně jako další soubory, jako je *web.config,* které budete potřebovat pro nasazení), Visual Studio poskytuje pohodlné [šablony položek,](python-item-templates.md) které vám pomohou začít.

Dostupné šablony zobrazíte v **Průzkumníku řešení**a klepněte pravým tlačítkem myši na složku, ve které chcete položku vytvořit, a vyberte **přidat** > **novou položku**:

![Dialogové okno Přidat novou položku v sadě Visual Studio](media/django/step03-add-new-item-dialog.png)

Chcete-li použít šablonu, vyberte požadovanou šablonu, zadejte název souboru a vyberte **OK**. Přidání položky tímto způsobem automaticky přidá soubor do projektu sady Visual Studio a označí změny pro správě zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: Jak Visual Studio vědět, které šablony položek nabídnout?

Odpověď: Soubor projektu Visual Studio (*.pyproj*) obsahuje identifikátor typu projektu, který jej označí jako projekt Pythonu. Visual Studio používá tento identifikátor typu k zobrazení pouze ty šablony položek, které jsou vhodné pro typ projektu. Tímto způsobem visual studio můžete zadat bohatou sadu šablon položek pro mnoho typů projektů, aniž by vás požádat o jejich třídění pokaždé.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Zobrazení statických souborů z aplikace

Ve webové aplikaci vytvořené v Pythonu (pomocí libovolného rozhraní) se soubory Pythonu vždy spouštějí na serveru webového hostitele a nikdy se nepřenášejí do počítače uživatele. Jiné soubory, jako například CSS a JavaScript, jsou však používány výhradně prohlížečem, takže hostitelský server je jednoduše dodává tak, jak jsou požadovány. Tyto soubory jsou označovány jako "statické" soubory a Django je může automaticky doručit, aniž byste museli psát jakýkoli kód.

Projekt Django je ve výchozím nastavení nakonfigurován tak, aby sloužil statickým souborům ze *statické* složky aplikace, a to díky těmto řádkům v *settings.py*projektu Django :

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Soubory můžete uspořádat pomocí libovolné struktury složek v rámci *statické,* která se vám líbí, a potom použít relativní cesty v rámci této složky odkazovat na soubory. Chcete-li tento proces demonstrovat, přidejte do aplikace soubor CSS a použijte tuto šablonu stylů v šabloně *index.html:*

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **HelloDjangoApp** v `static`projektu sady Visual Studio, vyberte **přidat** > novou**složku**a pojmenujte složku .

1. Klepněte pravým tlačítkem myši na **statickou** složku a vyberte **přidat** > **novou položku**. V zobrazeném dialogovém okně vyberte šablonu **stylů,** pojmenujte soubor `site.css`a vyberte **OK**. Soubor **site.css** se zobrazí v projektu a je otevřen v editoru. Struktura složek by měla vypadat podobně jako na následujícím obrázku:

    ![Statická struktura souborů, jak je znázorněno v Průzkumníku řešení](media/django/step03-static-file-structure.png)

1. Nahraďte obsah *webu site.css* následujícím kódem a uložte soubor:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Nahraďte obsah *templates/HelloDjangoApp/index.html* souboru aplikace následujícím kódem, `<strong>` který nahradí prvek použitý `<span>` v kroku `message` 2 a, který odkazuje na třídu stylu. Použití třídy stylu tímto způsobem poskytuje mnohem větší flexibilitu při stylingu prvku. (Pokud jste nepřesunuli *index.html* do podsložky v *šablonách* při použití VS 2017 15.7 a starší, podívejte se na [názvy šablon](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) v kroku 2-4.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Spusťte projekt sledovat výsledky. Zastavte server po dokončení a potvrďte změny do správy zdrojového kódu, pokud se vám líbí (jak je vysvětleno v [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Otázka: Jaký je účel značky {% load staticfiles %}?

Odpověď: `{% load staticfiles %}` Řádek je vyžadován před odkazem na `<head>` `<body>`statické soubory v prvcích, jako je a . V příkladu uvedeném v této části "staticfiles" odkazuje na vlastní sadu značek šablony Django, což je to, co umožňuje použít `{% static %}` syntaxi k odkazu na statické soubory.  Bez `{% load staticfiles %}`, uvidíte výjimku při spuštění aplikace.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Otázka: Existují nějaké konvence pro uspořádání statických souborů?

Odpověď: Do *statické* složky můžete přidávat další soubory CSS, JavaScript a HTML, jak chcete. Typickým způsobem uspořádání statických souborů je vytvoření podsložek s názvem *písma*, *skripty*a *obsah* (pro šablony stylů a všechny ostatní soubory). V každém případě nezapomeňte zahrnout tyto složky v `{% static %}` relativní cestě k souboru v odkazech.

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky do aplikace

Přidání další stránky do aplikace znamená následující:

- Přidejte funkci Pythonu, která definuje zobrazení.
- Přidejte šablonu pro značku stránky.
- Přidejte potřebné směrování do *souboru urls.py* projektu Django.

Následující kroky přidají stránku "O aplikaci" do projektu "HelloDjangoApp" a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **složku šablony/HelloDjangoApp,** vyberte `about.html` **přidat** > **novou položku**, vyberte šablonu **položky stránky HTML,** pojmenujte soubor a vyberte **OK**.

    > [!Tip]
    > Pokud se příkaz **Nová položka** v nabídce **Přidat** nezobrazí, ujistěte se, že jste server zastavili, aby visual studio ukončilo režim ladění.

1. Nahraďte obsah *about.html* následujícími značkami (explicitní odkaz na domovskou stránku nahradíte jednoduchým navigačním panelem v kroku 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otevřete soubor *views.py* aplikace a přidejte funkci s názvem, `about` která šablonu používá:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Otevřete soubor *urls.py* projektu Django a do `urlPatterns` pole přidejte následující řádek:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otevřete *soubor templates/HelloDjangoApp/index.html* a pod `<body>` element, který chcete propojit s odkazem na stránku Informace, přidáte následující řádek (tento odkaz opět nahradíte nav barem v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí příkazu Nabídka **Uložit** > **vše** soubor nebo stačí stisknout **kombinaci kláves Ctrl**+**Shift**+**S**. (Technicky tento krok není potřeba, protože spuštění projektu v sadě Visual Studio ukládá soubory automaticky. Nicméně, je to dobrý příkaz vědět!)

1. Spusťte projekt sledovat výsledky a zkontrolujte navigaci mezi stránkami. Po dokončení zavřete server.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Otázka: Snažil jsem se pomocí "index" pro odkaz na domovskou stránku, ale nefungovalo to. Proč?

Odpověď: I když je *views.py* funkce `index`zobrazení v views.py pojmenována , vzory směrování adres URL v *souboru urls.py* projektu Django neobsahují regulární výraz, který odpovídá řetězci "index". Chcete-li tento řetězec porovnat, musíte přidat `^index$`další položku pro vzorek .

Jak je znázorněno v další části, je `{% url '<pattern_name>' %}` mnohem lepší použít značku v šabloně stránky, abyste odkazovali na *název* vzoru, v takovém případě Django vytvoří správnou adresu URL pro vás. Například nahradit `<div><a href="home">Home</a></div>` v *about.html* s `<div><a href="{% url 'index' %}">Home</a></div>`. Použití 'index' funguje zde, protože první URL vzor v *urls.py* je ve skutečnosti `name='index'` s názvem 'index' (na základě argumentu). Můžete také použít 'home' odkazovat na druhý vzor.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Vytvoření záhlaví a nav panelu pomocí dědičnosti šablony

Namísto explicitních navigačních odkazů na každé stránce používají moderní webové aplikace obvykle záhlaví značky a navigační panel, který poskytuje nejdůležitější odkazy na stránky, místní nabídky a tak dále. Chcete-li se ujistit, že záhlaví a nav panel jsou stejné na všech stránkách, ale nechcete opakovat stejný kód v každé šabloně stránky. Místo toho chcete definovat společné části všech stránek na jednom místě.

Systém templating u django poskytuje dva způsoby opětovného použití konkrétních prvků ve více šablonách: zahrnuje a dědičnost.

- *Zahrnuje* další šablony stránek, které vložíte na určité místo v `{% include <template_path> %}`odkazující šabloně pomocí syntaxe . Proměnnou můžete také použít, pokud chcete dynamicky změnit cestu v kódu. Zahrnuty se obvykle používají v těle stránky k vytahování sdílené šablony v určitém umístění na stránce.

- *Dědičnost* `{% extends <template_path> %}` používá na začátku šablony stránky k určení sdílené základní šablony, na které pak odkazuje odkazující šablona. Dědičnost se běžně používá k definování sdíleného rozložení, nav panelu a dalších struktur pro stránky aplikace, takže odkazující šablony stačí přidat nebo upravit určité oblasti základní šablony nazývané *bloky*.

V obou `<template_path>` případech je relativní vzhledem ke`../` složce šablony aplikace (nebo `./` jsou také *povoleny).*

Základní šablona vymezuje bloky pomocí `{% block <block_name> %}` a `{% endblock %}` tagy. Pokud odkazující šablona pak používá značky se stejným názvem bloku, její obsah bloku přepíše obsah základní šablony.

Následující kroky ukazují dědičnost:

1. Ve složce *šablony aplikace/HelloDjangoApp* vytvořte nový soubor HTML (pomocí kontextové nabídky **Přidat** > **novou položku** nebo **Přidat** > **stránku HTML**) nazvaný *layout.html*a nahraďte jeho obsah níže uvedenou značkou. Můžete vidět, že tato šablona obsahuje blok s názvem "obsah", který je vše, co odkazující stránky musí nahradit:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Přidejte následující styly do statického souboru *aplikace/site.css* (tento návod se zde nepokouší demonstrovat responzivní návrh; tyto styly jednoduše generují zajímavý výsledek):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Upravte *templates/HelloDjangoApp/index.html* tak, aby odkazoval na základní šablonu, a přepište blok obsahu. Můžete vidět, že pomocí dědičnosti, tato šablona se stane jednoduché:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Upravte *templates/HelloDjangoApp/about.html* tak, aby také odkazovalna základní šablonu a přepsalblok obsahu:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spusťte server sledovat výsledky. Po dokončení zavřete server.

    ![Spuštěná aplikace zobrazující nav panel](media/django/step03-nav-bar.png)

1. Vzhledem k tomu, že jste provedli podstatné změny v aplikaci, je opět vhodná doba [k potvrzení změn správy zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Psaní první aplikace Django, část 3 (zobrazení)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Další možnosti šablon Django, jako je například tok řízení, naleznete [v tématu Jazyk šablony Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Podrobné informace o `{% url %}` používání značky najdete v [adrese URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) v rámci [vestavěné šablony značek a filtrů pro django šablony odkaz](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
