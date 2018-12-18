---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 3, statické soubory a stránky
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, konkrétně představením toho, jak doručování statických souborů, přidání stránky do aplikace a používat šablonu dědičnosti
ms.date: 09/04/2018
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
ms.openlocfilehash: 906c44ca3b1d0771202e78910870d38f9d4fb995
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065022"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Doručování statických souborů, přidejte stránky a použijte šablonu dědičnosti

**Předchozí krok: [vytvoření aplikace Flask pomocí zobrazení a stránky šablony](learn-flask-visual-studio-step-02-create-app.md)**

V předchozích krocích v tomto kurzu jste zjistili, jak k vytvoření minimální aplikace Flask pomocí jediné stránce samostatná HTML. Moderních webových aplikací, ale jsou obvykle skládá z mnoha stránkách a používání sdílených prostředků, jako jsou soubory CSS a JavaScript, k poskytování konzistentního stylů a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Použití šablon položek aplikace Visual Studio můžete rychle přidat nové soubory různé typy s pohodlný často používaný kód (krok 3 - 1)
> - Doručování statických souborů z kódu (krok 3-2, nepovinné)
> - Přidání další stránky do aplikace (krok 3 – 3)
> - Vytvořit záhlaví a navigační panel, který se používá na stránkách (krok 3-4) pomocí šablony dědičnosti

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznamte se s šablon položek

Při vývoji aplikace Flask, obvykle přidáte mnoho souborů další Python, HTML, CSS a JavaScript. Pro každý typ souboru (také další soubory, jako jsou *web.config* , které můžete potřebovat k nasazení), Visual Studio poskytuje pohodlné [šablon položek](python-item-templates.md) vám pomůžou začít.

Pokud chcete zobrazit dostupné šablony, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem na složku, ve kterém chcete vytvořit položku, vyberte **přidat** > **nová položka**:

![Přidání nové položky dialogového okna v sadě Visual Studio](media/flask/step03-add-new-item-dialog.png)

Použití šablony, vyberte požadovanou šablonu, zadejte název pro soubor a vyberte **OK**. Přidání položky tímto způsobem automaticky přidá soubor do projektu sady Visual Studio a označí změny pro správu zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: Jak Visual Studio vědět, které položky šablony, které nabízí?

Odpověď: Souboru projektu Visual Studio (*.pyproj*) obsahuje identifikátor typ projektu, který označuje jako projekt Python. Visual Studio používá tento identifikátor typu k zobrazení pouze tyto šablony položek, které jsou vhodné pro typ projektu. Tímto způsobem, Visual Studio může poskytovat bohatou sadu šablon položek, pro mnoho typů projektů bez zobrazení výzvy k řazení projde pokaždé, když.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3 – 2: doručování statických souborů z vaší aplikace

Ve webové aplikaci vytvořené s využitím Pythonu (pomocí libovolné architektury) soubory Pythonu vždy spustit na serveru webového hostitele a se nikdy nepřenáší na počítači uživatele. Další soubory, ale například šablony stylů CSS a JavaScript používá jediná prohlížeče, tak server hostitele jednoduše poskytnout, je jako – je vždy, když jste žádali. Tyto soubory jsou označovány jako "statických" soubory a Flask může doručit automaticky aniž byste museli psát jakýkoli kód. V rámci soubory HTML například právě najdete statické soubory pomocí relativní cesty v projektu. První část v tomto kroku přidá soubor CSS do stávající šablony stránky.

Když budete potřebovat k doručování statických souborů z kódu, jako například prostřednictvím implementace koncový bod rozhraní API Flask představuje pohodlný způsob, který umožňuje odkazovat na soubory pomocí relativní cesty ve složce s názvem *statické* (v kořenové složce projektu). Druhá část v tomto kroku ukazuje metody pomocí jednoduchého statický datový soubor.

V obou případech můžete uspořádat soubory podle *statické* libovolně.

### <a name="use-a-static-file-in-a-template"></a>Použijte statického souboru do šablony

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **HelloFlask** složky v projektu sady Visual Studio, vyberte **přidat** > **novou složku**a pojmenujte složku `static`.

1. Klikněte pravým tlačítkem myši **statické** a pak zvolte položku **přidat** > **nová položka**. V dialogovém okně, které se zobrazí, vyberte **šablony stylů** šablony, názvem souboru `site.css`a vyberte **OK**. **Site.css** souboru se zobrazí v projektu a je otevřen v editoru. Vaše struktura složky by měl vypadat podobně jako na následujícím obrázku:

    ![Struktura statického souboru, jak je znázorněno v Průzkumníku řešení](media/flask/step03-static-file-structure.png)

1. Nahraďte obsah *site.css* následujícím kódem a soubor uložte:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Nahraďte obsah aplikace *templates/index.html* souboru následujícím kódem, který nahrazuje `<strong>` prvku použitého při kroku 2 `<span>` , která odkazuje na `message` styl třídy. Použití třídy stylu tímto způsobem nabízí mnohem větší flexibilitu v používání stylů pro element.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Spusťte projekt tak, aby sledujte výsledky. Zastavit aplikaci, až budete hotovi a potvrďte změny do správy zdrojového kódu Pokud chcete (jak je vysvětleno v [kroku 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Poskytování statických souborů z kódu

Flask poskytuje funkci s názvem `serve_static_file` , můžete volat z kódu k odkazování na jakýkoli soubor v rámci projektu *statické* složky. Následující postup vytvoří jednoduchou koncový bod rozhraní API, která vrací statický datový soubor.

1. Pokud jste tak ještě neučinili, vytvořte *statické* složky: v **Průzkumníka řešení**, klikněte pravým tlačítkem na **HelloFlask** složky v projektu sady Visual Studio, vyberte **Přidat** > **novou složku**a pojmenujte složku `static`.

1. V *statické* složku, vytvořte statickou datový soubor JSON s názvem *data.json* s použitím následujícího obsahu (které jsou bezvýznamné ukázkových dat):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. V *views.py*, přidat funkci s/api/data trasy, která vrací statický datový soubor pomocí `send_static_file` metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Spusťte aplikaci a přejděte do/api/koncový bod datové zobrazíte, že se vrátí ke statickému souboru. Jakmile budete hotovi, zastavte aplikaci.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Dotaz: Existují jakékoli konvence pro uspořádání statické soubory?

Odpověď: Můžete přidat další soubory šablon stylů CSS, JavaScript a HTML v vaše *statické* složky libovolně. Typické způsob uspořádání statických souborů je vytvořit podsložky s názvem *písma*, *skripty*, a *obsah* (pro šablony stylů a všechny další soubory).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Otázka: Jak mám postupovat při URL proměnné a parametry dotazu v rozhraní API?

Odpověď: Viz odpovědí v kroku 1 – 4 pro [Otázka: jak Flask pracovat s proměnnou cesty adresy URL a parametrů dotazu?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky aplikace

Přidání další stránky do aplikace znamená, že následující:

- Přidání funkce Pythonu, který definuje zobrazení.
- Přidejte šablonu pro na stránce značek.
- Přidat nezbytné směrování do projektu Flask *urls.py* souboru.

Následující postup přidání stránky "O" do "HelloFlask" projekt a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **šablony** složky, vyberte **přidat** > **nová položka**, vyberte **Stránku HTML** šablony položky, zadejte název souboru `about.html`a vyberte **OK**.

    > [!Tip]
    > Pokud **nová položka** nezobrazí příkaz na **přidat** nabídky, ujistěte se, že jste zastavení aplikace tak, aby Visual Studio se ukončí režim ladění.

1. Nahraďte obsah *about.html* následujícím kódem (nahradíte explicitní odkaz na domovskou stránku jednoduché navigační panel v kroku 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otevřete aplikaci prvku *views.py* a přidejte funkce s názvem `about` , který používá šablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otevřít *templates/index.html* soubor a přidejte následující řádek bezprostředně v rámci `<body>` elementu na stránku o (znovu, nahradíte tento odkaz navigačního panelu v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí **souboru** > **Uložit vše** příkaz nabídky nebo stejně press **Ctrl**+**Shift** + **S**. (Technicky, tento krok není potřeba, protože spuštění projektu v sadě Visual Studio automaticky ukládá soubory. Nicméně je dobré příkaz vědět o!)

1. Spusťte projekt sledujte výsledky a zkontrolovat navigace mezi stránkami. Zastavte aplikaci, až budete hotovi.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Otázka: Název funkce stránky důležité Flask?

Odpověď: Ne, protože je `@app.route` dekoratér, který určuje adresy URL, pro které Flask volá funkci pro generování odpovědi. Vývojáři obvykle shodovat s názvem funkce trasy, ale takové párování není povinné.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: použití dědičnosti šablony k vytvoření záhlaví a navigační panel

Namísto toho, aby explicitní navigačních odkazů na každé stránce, moderních webových aplikací obvykle používají značky záhlaví a navigační panel, který poskytuje nejdůležitější odkazů na stránky, kontextových nabídkách a tak dále. Pokud chcete mít jistotu, že záhlaví a navigačního panelu jsou stejné ve všech stránek, ale nechcete opakujte stejný kód v každé šabloně stránky. Chcete místo toho definujte společné části všech stránek na jednom místě.

Flask na šablonování systému (šablonovacím systémem ve výchozím nastavení) poskytuje dva prostředky pro opětovné použití konkrétní prvky napříč více šablon: zahrnuje a dědičnosti.

- *Zahrnuje* se další stránka šablony, které můžete vložit na určitém místě v šabloně odkazující pomocí syntaxe `{% include <template_path> %}`. Můžete také použít proměnné Pokud chcete změnit cestu dynamicky v kódu. Zahrnuje se obvykle používají v těle stránky, aby se načetla sdílené šablony v konkrétním umístění na stránce.

- *Dědičnost* používá `{% extends <template_path> %}` na začátku stránky šablonu k zadání sdíleného základní šablonu, která pak staví šablony odkazující na. Dědičnost se běžně používá k definování sdíleného rozložení, navigačního panelu a jiných struktur stránek vaší aplikace, tak, aby odkazující šablony potřebujete pouze přidat nebo změnit určité oblasti základní šablonu s názvem *bloky*.

V obou případech `<template_path>` je relativní vzhledem k aplikaci prvku *šablony* složky (`../` nebo `./` jsou také povoleny).

Základní šablona kolem *bloky* pomocí `{% block <block_name> %}` a `{% endblock %}` značky. Pokud šablonu odkazující pak používá značky se stejným názvem bloku, obsah bloku přepisuje základní šablonu.

Následující kroky ukazují dědičnosti:

1. V aplikaci prvku *šablony* složku, vytvořte nový soubor HTML (pomocí **přidat** > **nová položka** místní nabídky nebo **přidat**  >  **Stránku HTML**) volá *layout.html*a jeho obsah nahraďte následující značky. Uvidíte, že tato šablona obsahuje blok s názvem "obsah", který je všechno, odkazující stránky potřeba nahradit:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
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

1. Upravit *templates/index.html* do základní šablony a přepsat blok s obsahem. Uvidíte, že s použitím dědičnosti, tato šablona stane jednoduché:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Upravit *templates/about.html* také odkazovat na základní šablonu a přepsat blok s obsahem:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spuštění serveru a sledujte výsledky. Zavřete serverem, až budete hotovi.

    ![Spuštěné aplikaci zobrazující navigačního panelu](media/flask/step03-nav-bar.png)

1. Vzhledem k tomu, že jste provedli významné změny aplikace, znovu je vhodná doba [potvrďte změny do správy zdrojových kódů](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití úplné šablony webového projektu Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Další možnosti šablon šablonovacím systémem, jako je například tok řízení, najdete v části [šablonovacím systémem šablona návrháře dokumentaci](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Podrobnosti o použití `url_for`, naleznete v tématu [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) v dokumentaci k objektu aplikace Flask (flask.pocoo.org)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
