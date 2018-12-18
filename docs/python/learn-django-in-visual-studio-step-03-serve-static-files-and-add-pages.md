---
title: Přečtěte si kurz Django v sadě Visual Studio kroku 3, statické soubory a stránky
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně představením toho, jak doručování statických souborů, přidání stránky do aplikace a používat šablonu dědičnosti
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
ms.openlocfilehash: cfde21f356e35366cfb80b029f918eed0364a7b5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066077"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Doručování statických souborů, přidejte stránky a použijte šablonu dědičnosti

**Předchozí krok: [vytvoření aplikace Django s zobrazení a stránky šablony](learn-django-in-visual-studio-step-02-create-an-app.md)**

V předchozích krocích v tomto kurzu jste zjistili, jak vytvoření minimální aplikace Django s jednostránkové samostatná HTML. Moderních webových aplikací, ale jsou obvykle skládá z mnoha stránkách a používání sdílených prostředků, jako jsou soubory CSS a JavaScript, k poskytování konzistentního stylů a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Použití šablon položek aplikace Visual Studio můžete rychle přidat nové soubory různé typy s pohodlný často používaný kód (krok 3 - 1)
> - Konfigurace projektu Django pro obsluhu statických souborů (krok 3-2)
> - Přidání další stránky do aplikace (krok 3 – 3)
> - Vytvořit záhlaví a navigační panel, který se používá na stránkách (krok 3-4) pomocí šablony dědičnosti

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznamte se s šablon položek

Při vývoji aplikace Django, obvykle přidáte mnoho souborů další Python, HTML, CSS a JavaScript. Pro každý typ souboru (také další soubory, jako jsou *web.config* , které můžete potřebovat k nasazení), Visual Studio poskytuje pohodlné [šablon položek](python-item-templates.md) vám pomůžou začít.

Pokud chcete zobrazit dostupné šablony, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem na složku, ve kterém chcete vytvořit položku, vyberte **přidat** > **nová položka**:

![Přidání nové položky dialogového okna v sadě Visual Studio](media/django/step03-add-new-item-dialog.png)

Použití šablony, vyberte požadovanou šablonu, zadejte název pro soubor a vyberte **OK**. Přidání položky tímto způsobem automaticky přidá soubor do projektu sady Visual Studio a označí změny pro správu zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: Jak Visual Studio vědět, které položky šablony, které nabízí?

Odpověď: Souboru projektu Visual Studio (*.pyproj*) obsahuje identifikátor typ projektu, který označuje jako projekt Python. Visual Studio používá tento identifikátor typu k zobrazení pouze tyto šablony položek, které jsou vhodné pro typ projektu. Tímto způsobem, Visual Studio může poskytovat bohatou sadu šablon položek, pro mnoho typů projektů bez zobrazení výzvy k řazení projde pokaždé, když.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3 – 2: doručování statických souborů z vaší aplikace

Ve webové aplikaci vytvořené s využitím Pythonu (pomocí libovolné architektury) soubory Pythonu vždy spustit na serveru webového hostitele a se nikdy nepřenáší na počítači uživatele. Další soubory, ale například šablony stylů CSS a JavaScript používá jediná prohlížeče, tak server hostitele jednoduše poskytnout, je jako – je vždy, když jste žádali. Tyto soubory jsou označovány jako "statických" soubory a Django může doručit automaticky aniž byste museli psát jakýkoli kód.

Ve výchozím nastavení k doručování statických souborů z aplikace je nakonfigurované projektu Django *statické* složky díky tyto řádky v projektu Django *settings.py*:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Můžete uspořádat soubory pomocí libovolné struktury složek v rámci *statické* a pak použít relativní cesty k odkazování na soubory v této složce. Abychom si předvedli tento proces, přidejte soubor CSS do aplikace následující kroky a pak pomocí této šablony stylů v *index.html* šablony:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **HelloDjangoApp** složky v projektu sady Visual Studio, vyberte **přidat** > **novou složku**a pojmenujte složku `static`.

1. Klikněte pravým tlačítkem myši **statické** a pak zvolte položku **přidat** > **nová položka**. V dialogovém okně, které se zobrazí, vyberte **šablony stylů** šablony, názvem souboru `site.css`a vyberte **OK**. **Site.css** souboru se zobrazí v projektu a je otevřen v editoru. Vaše struktura složky by měl vypadat podobně jako na následujícím obrázku:

    ![Struktura statického souboru, jak je znázorněno v Průzkumníku řešení](media/django/step03-static-file-structure.png)

1. Nahraďte obsah *site.css* následujícím kódem a soubor uložte:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Nahraďte obsah aplikace *templates/HelloDjangoApp/index.html* souboru následujícím kódem, který nahrazuje `<strong>` prvku použitého při kroku 2 `<span>` , která odkazuje na `message` styl třídy. Použití třídy stylu tímto způsobem nabízí mnohem větší flexibilitu v používání stylů pro element. (Pokud jste ještě přesunuli *index.html* do podsložky v *šablony* při použití VS 2017 15.7 a odkazovat dříve, [šablony namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) v kroku 2 – 4.)

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

1. Spusťte projekt tak, aby sledujte výsledky. Zastavit server, až budete hotovi a potvrďte změny do správy zdrojového kódu Pokud chcete (jak je vysvětleno v [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Otázka: Co je účelem {% zatížení, které staticfiles %} značku?

Odpověď: `{% load staticfiles %}` řádku je vyžadována před odkazující na statické soubory v elementech jako `<head>` a `<body>`. V příkladu v této části "staticfiles" odkazuje na vlastní Django šablony značky sadu, což je, co vám umožňuje používat `{% static %}` syntaxe pro odkazování na statické soubory.  Bez `{% load staticfiles %}`, zobrazí se vám výjimku při spuštění aplikace.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Dotaz: Existují jakékoli konvence pro uspořádání statické soubory?

Odpověď: Můžete přidat další soubory šablon stylů CSS, JavaScript a HTML v vaše *statické* složky libovolně. Typické způsob uspořádání statických souborů je vytvořit podsložky s názvem *písma*, *skripty*, a *obsah* (pro šablony stylů a všechny další soubory). V obou případech musíte zahrnout tyto složky v relativní cesta k souboru v `{% static %}` odkazy.

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky aplikace

Přidání další stránky do aplikace znamená, že následující:

- Přidání funkce Pythonu, který definuje zobrazení.
- Přidejte šablonu pro na stránce značek.
- Přidat nezbytné směrování do projektu Django *urls.py* souboru.

Následující postup přidání stránky "O" do "HelloDjangoApp" projekt a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem **šablony/HelloDjangoApp** složky, vyberte **přidat** > **nová položka**vyberte **stránku HTML** šablony položky, zadejte název souboru `about.html`a vyberte **OK**.

    > [!Tip]
    > Pokud **nová položka** nezobrazí příkaz na **přidat** nabídky, ujistěte se, že jste zastavení serveru tak, aby Visual Studio se ukončí režim ladění.

1. Nahraďte obsah *about.html* následujícím kódem (nahradíte explicitní odkaz na domovskou stránku jednoduché navigační panel v kroku 3-4):

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

1. Otevřete aplikaci prvku *views.py* a přidejte funkce s názvem `about` , který používá šablonu:

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

1. Otevření projektu Django *urls.py* a přidejte následující řádek, který `urlPatterns` pole:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otevřít *templates/HelloDjangoApp/index.html* a přidejte následující řádek pod ním `<body>` elementu na stránku o (znovu, nahradíte tento odkaz navigačního panelu v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí **souboru** > **Uložit vše** příkaz nabídky nebo stejně press **Ctrl**+**Shift** + **S**. (Technicky, tento krok není potřeba, protože spuštění projektu v sadě Visual Studio automaticky ukládá soubory. Nicméně je dobré příkaz vědět o!)

1. Spusťte projekt sledujte výsledky a zkontrolovat navigace mezi stránkami. Zavřete serverem, až budete hotovi.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Otázka: Mohu pokusili pomocí odkazu na domovskou stránku "index", ale akce nebyla úspěšná. Proč?

Odpověď: I když zobrazení fungovat v *views.py* názvem `index`, adresy URL směrování vzory v projektu Django *urls.py* soubor neobsahuje regulární výraz, který se shoduje s řetězcem " index". Tak, aby odpovídaly tento řetězec budete muset přidat další položku pro vzor `^index$`.

Jak je znázorněno v další části, je mnohem vhodnější použít `{% url '<pattern_name>' %}` značky v šabloně stránky k odkazování *název* vzoru, ve kterém případu Django pro vás vytvoří správnou adresu URL. Nahraďte třeba `<div><a href="home">Home</a></div>` v *about.html* s `<div><a href="{% url 'index' %}">Home</a></div>`. Použití "index" funguje tady, protože první adresa URL vzorku v *urls.py* , ve skutečnosti jmenuje "index" (základě `name='index'` argument). "Domovskou" můžete použít také k odkazování na druhý vzor.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: použití dědičnosti šablony k vytvoření záhlaví a navigační panel

Namísto toho, aby explicitní navigačních odkazů na každé stránce, moderních webových aplikací obvykle používají značky záhlaví a navigační panel, který poskytuje nejdůležitější odkazů na stránky, kontextových nabídkách a tak dále. Pokud chcete mít jistotu, že záhlaví a navigačního panelu jsou stejné ve všech stránek, ale nechcete opakujte stejný kód v každé šabloně stránky. Chcete místo toho definujte společné části všech stránek na jednom místě.

Django na šablonování systém poskytuje dva prostředky pro opětovné použití konkrétní prvky napříč více šablon: zahrnuje a dědičnosti.

- *Zahrnuje* se další stránka šablony, které můžete vložit na určitém místě v šabloně odkazující pomocí syntaxe `{% include <template_path> %}`. Můžete také použít proměnné Pokud chcete změnit cestu dynamicky v kódu. Zahrnuje se obvykle používají v těle stránky, aby se načetla sdílené šablony v konkrétním umístění na stránce.

- *Dědičnost* používá `{% extends <template_path> %}` na začátku stránky šablonu k zadání sdíleného základní šablonu, která pak staví šablony odkazující na. Dědičnost se běžně používá k definování sdíleného rozložení, navigačního panelu a jiných struktur stránek vaší aplikace, tak, aby odkazující šablony potřebujete pouze přidat nebo změnit určité oblasti základní šablonu s názvem *bloky*.

V obou případech `<template_path>` je relativní vzhledem k aplikaci prvku *šablony* složky (`../` nebo `./` jsou také povoleny).

Základní šablona kolem blocích pomocí `{% block <block_name> %}` a `{% endblock %}` značky. Pokud odkazující šablona pak pomocí značky se stejným názvem bloku, přednost před jeho blokovat obsah, který základní šablony.

Následující kroky ukazují dědičnosti:

1. V aplikaci prvku *šablony/HelloDjangoApp* složku, vytvořte nový soubor HTML (pomocí **přidat** > **nová položka** místní nabídky nebo **přidat**  >  **Stránku HTML**) volá *layout.html*a jeho obsah nahraďte následující značky. Uvidíte, že tato šablona obsahuje blok s názvem "obsah", který je všechno, odkazující stránky potřeba nahradit:

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

1. Přidat do aplikace následující styly *static/site.css* souboru (Tento návod nepokouší k předvedení přizpůsobivý návrh zde; tyto styly jsou jednoduše generovat zajímavé výsledky):

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

1. Upravit *templates/HelloDjangoApp/index.html* do základní šablony a přepsat blok s obsahem. Uvidíte, že s použitím dědičnosti, tato šablona stane jednoduché:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Upravit *templates/HelloDjangoApp/about.html* také odkazovat na základní šablonu a přepsat blok s obsahem:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spuštění serveru a sledujte výsledky. Zavřete serverem, až budete hotovi.

    ![Spuštěné aplikaci zobrazující navigačního panelu](media/django/step03-nav-bar.png)

1. Vzhledem k tomu došlo k zásadnějším změnám do aplikace, znovu je vhodná doba [potvrďte změny do správy zdrojových kódů](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Zápis svoji první aplikaci Django, část 3 (zobrazení)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Další možnosti šablon Django, jako je například tok řízení, najdete v části [jazyk šablony Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Úplné podrobnosti o použití `{% url %}` značku, přečtěte si téma [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) v rámci [značky integrované šablony a filtry pro referenční dokumentace k šablonám Django](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
