---
title: Kurz k seznámení s kurzem v aplikaci Visual Studio Step 3, statické soubory a stránky
titleSuffix: ''
description: Návod základů v baňce v kontextu projektů aplikace Visual Studio, konkrétně demonstrace, jak sloužit ke zpracování statických souborů, přidávání stránek do aplikace a použití dědičnosti šablon
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 69fd704976ee941cb053d75040a3d3ec7871a380
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238739"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>Krok 3: obsluha statických souborů, přidávání stránek a použití dědičnosti šablon s aplikací v baňce

**Předchozí krok: [Vytvoření aplikace v baňce se zobrazeními a šablonami stránek](learn-flask-visual-studio-step-02-create-app.md)**

V předchozích krocích tohoto kurzu jste se naučili, jak vytvořit aplikaci minimálních baněk s jednou stránkou HTML, která je samostatně obsažená. Moderní webové aplikace se ale obvykle skládají z mnoha stránek a využívají sdílené prostředky, jako jsou soubory CSS a JavaScript, k zajištění konzistentního stylu a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Pomocí šablon položek sady Visual Studio můžete rychle přidat nové soubory různých typů s praktickým často používaným kódem (krok 3-1).
> - Obsluhovat statické soubory z kódu (krok 3-2, volitelné)
> - Přidejte do aplikace další stránky (krok 3-3).
> - Pomocí dědičnosti šablon vytvořte záhlaví a navigační panel, který se používá na stránkách (krok 3-4).

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznámení se šablonami položek

Při vývoji aplikace v baňce obvykle přidáte mnoho dalších souborů Python, HTML, CSS a JavaScript. Pro každý typ souboru (stejně jako jiné soubory jako *web.config* , které můžete potřebovat pro nasazení), Visual Studio poskytuje praktické [šablony položek](python-item-templates.md) , které vám pomůžou začít.

Dostupné šablony zobrazíte tak, že přejdete na **Průzkumník řešení**, kliknete pravým tlačítkem na složku, ve které chcete položku vytvořit, vyberte **Přidat**  >  **novou položku**:

![Dialogové okno Přidat novou položku v aplikaci Visual Studio](media/flask/step03-add-new-item-dialog.png)

Chcete-li použít šablonu, vyberte požadovanou šablonu, zadejte název souboru a vyberte **OK**. Přidáním položky tímto způsobem lze soubor automaticky přidat do projektu aplikace Visual Studio a označit změny pro správu zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: jak Visual Studio ví, které šablony položek nabízí?

Odpověď: soubor projektu sady Visual Studio (*. pyproj*) obsahuje identifikátor typu projektu, který ho označí jako projekt Pythonu. Sada Visual Studio používá tento identifikátor typu k zobrazení pouze těch šablon položek, které jsou vhodné pro typ projektu. Díky tomu může sada Visual Studio poskytovat bohatou sadu šablon položek pro celou řadu typů projektů bez nutnosti pokaždé, když je budete muset seřadit.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Obsluhujte statické soubory z vaší aplikace

Ve webové aplikaci vytvořené pomocí Pythonu (pomocí libovolného rozhraní) se soubory Pythonu vždycky spouštějí na serveru webového hostitele a nikdy se nepřenáší do počítače uživatele. Jiné soubory, jako jsou například CSS a JavaScript, se používají výhradně v prohlížeči, takže hostitelský server je jednoduše přiřadí tak, jak jsou pokaždé požadovány. Tyto soubory jsou označovány jako "statické" soubory a v baňce je lze doručovat automaticky, aniž byste museli psát kód. V souborech HTML můžete například pouze odkazovat na statické soubory pomocí relativní cesty v projektu. První část tohoto kroku přidá soubor CSS do vaší existující šablony stránky.

Pokud potřebujete doručovat statický soubor z kódu, jako je například prostřednictvím implementace koncového bodu rozhraní API, vytvoří baňka pohodlný způsob, jak odkazovat na soubory pomocí relativních cest v rámci složky s názvem *static* (v kořenu projektu). Druhá část tohoto kroku ukazuje tuto metodu pomocí jednoduchého statického datového souboru.

V obou případech můžete soubory uspořádat *staticky* , ale chcete je.

### <a name="use-a-static-file-in-a-template"></a>Použití statického souboru v šabloně

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **HelloFlask** v projektu sady Visual Studio, vyberte **Přidat**  >  **novou složku**a pojmenujte složku `static` .

1. Klikněte pravým tlačítkem na **statickou** složku a vyberte **Přidat**  >  **novou položku**. V dialogovém okně, které se zobrazí, vyberte šablonu šablony **stylů** , pojmenujte soubor `site.css` a vyberte **OK**. Soubor **Web. CSS** se zobrazí v projektu a otevře se v editoru. Vaše struktura složky by měla vypadat podobně jako na následujícím obrázku:

    ![Struktura statického souboru, jak je znázorněno v Průzkumník řešení](media/flask/step03-static-file-structure.png)

1. Obsah souboru *site. CSS* nahraďte následujícím kódem a uložte ho:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Obsah souboru *Templates/index.html* aplikace nahraďte následujícím kódem, který nahradí `<strong>` prvek použitý v kroku 2 s objektem `<span>` , který odkazuje na `message` třídu Style. Použití třídy stylu tímto způsobem poskytuje mnohem větší flexibilitu při stylování elementu.

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

1. Spusťte projekt a sledujte výsledky. Pokud chcete, zastavte aplikaci po dokončení a potvrďte změny ve správě zdrojového kódu (jak je vysvětleno v [kroku 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Obsluha statického souboru z kódu

Baňka poskytuje funkci nazvanou `serve_static_file` , která může být volána z kódu pro odkazování na libovolný soubor v rámci *statické* složky projektu. Následující proces vytvoří jednoduchý koncový bod rozhraní API, který vrací statický datový soubor.

1. Pokud jste to ještě neudělali, vytvořte *statickou* složku: v **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **HelloFlask** v projektu sady Visual Studio, vyberte **Přidat**  >  **novou složku**a pojmenujte složku `static` .

1. Ve složce *static* vytvořte statický datový soubor JSON s názvem *data.js* s následujícím obsahem (což jsou nesmyslově vzorová data):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. V *views.py*Přidejte funkci s/API/data trasy, která vrací statický datový soubor pomocí `send_static_file` metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Spusťte aplikaci a přejděte do koncového bodu/API/data a podívejte se, že se vrátí statický soubor. Až skončíte, zastavte aplikaci.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Otázka: existují nějaké konvence pro uspořádávání statických souborů?

Odpověď: v případě potřeby můžete do *statické* složky přidat další soubory CSS, JavaScript a HTML. Typický způsob, jak uspořádat statické soubory, je vytvořit podsložky s názvem *písma*, *skripty*a *obsah* (pro šablony stylů a jiné soubory).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Otázka: Návody zpracovat proměnné adresy URL a parametry dotazu v rozhraní API?

Odpověď: Podívejte se na odpověď v kroku 1-4 pro [otázku: Jak funguje baňka s proměnnými adresy URL a parametry dotazu?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky do aplikace

Přidání další stránky do aplikace znamená následující:

- Přidejte funkci Pythonu, která definuje zobrazení.
- Přidejte šablonu pro značku stránky.
- Přidejte potřebné směrování do souboru *URLs.py* projektu baňky.

Následující postup přidá stránku "o" do projektu "HelloFlask" a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **šablony** , vyberte možnost **Přidat**  >  **novou položku**, vyberte šablonu položky **stránky HTML** , zadejte název souboru `about.html` a vyberte možnost **OK**.

    > [!Tip]
    > Pokud se příkaz **Nová položka** v nabídce **Přidat** nezobrazí, ujistěte se, že jste aplikaci zastavili, aby aplikace Visual Studio ukončila režim ladění.

1. Obsah *about.html* nahraďte následujícím kódem (v kroku 3-4 nahraďte explicitní odkaz na domovskou stránku):

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

1. Otevřete soubor *views.py* aplikace a přidejte funkci s názvem `about` , která používá tuto šablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otevřete soubor *Templates/index.html* a v rámci elementu přidejte následující řádek, `<body>` který bude odkazovat na stránku o aplikaci (znovu nahraďte tento odkaz navigačním panelem v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí příkazu v nabídce **soubor**  >  **Uložit vše** nebo stačí stisknout klávesy **CTRL** + **SHIFT** + **S**. (Technicky, tento krok není potřebný pro spuštění projektu v aplikaci Visual Studio ukládá soubory automaticky. Je však dobrým příkazem, který vás zajímá.)

1. Spusťte projekt a sledujte výsledky a zkontrolujte navigaci mezi stránkami. Po dokončení aplikaci zastavte.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Otázka: je název funkce stránky v baňce?

Odpověď: Ne, protože se jedná o `@app.route` dekoratér, který určuje adresy URL, na které se zavolá funkce pro vygenerování odpovědi. Vývojáři obvykle odpovídají názvu funkce trase, ale toto porovnávání není vyžadováno.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: použití dědičnosti šablony k vytvoření záhlaví a navigačního panelu

Namísto explicitních navigačních odkazů na každé stránce obvykle používají moderní webové aplikace hlavičku brandingu a navigační panel, který poskytuje nejdůležitější odkazy na stránky, místní nabídky a tak dále. Chcete-li zajistit, aby záhlaví a navigační panel byly na všech stránkách stejné, nechcete stejný kód opakovat v každé šabloně stránky. Místo toho chcete definovat společné části všech stránek na jednom místě.

Systém šablonování baňky (Jinja ve výchozím nastavení) poskytuje dva způsoby opakovaného použití určitých prvků v rámci více šablon: includes a dědičnost.

- *Zahrnuje* další šablony stránky, které vložíte na konkrétní místo v odkazující šabloně pomocí syntaxe `{% include <template_path> %}` . Proměnnou lze použít také v případě, že chcete změnit cestu dynamicky v kódu. Zahrnutí se obvykle používají v těle stránky pro vyžádání do sdílené šablony v určitém umístění na stránce.

- *Dědičnost* používá na `{% extends <template_path> %}` začátku šablony stránky, aby určovala sdílenou základní šablonu, na které odkazuje šablona. Dědičnost se běžně používá k definování sdíleného rozložení, navigačního panelu a dalších struktur pro stránky aplikace. to znamená, že odkazující šablony potřebují přidat nebo změnit pouze konkrétní oblasti základní šablony s názvem *bloky*.

V obou případech `<template_path>` je relativní vzhledem ke složce *šablon* aplikace ( `../` nebo `./` jsou také povoleny).

Základní šablona vymezují *bloky* pomocí `{% block <block_name> %}` značek a `{% endblock %}` . Pokud odkazovaná šablona potom používá značky se stejným názvem bloku, její obsah bloku přepíše základní šablonu.

Následující kroky demonstrují dědičnost:

1. Ve složce *šablony* aplikace vytvořte nový soubor HTML (pomocí místní nabídky **Přidat**  >  **novou položku** nebo **Přidat**  >  **stránku HTML**) s názvem *layout.html*a nahraďte jeho obsah následujícím kódem. Vidíte, že tato šablona obsahuje blok s názvem "content" (obsah), který obsahuje všechny odkazující stránky, které musí nahradit:

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

1. Do souboru *static/site. CSS* aplikace přidejte následující styly (Tento názorný postup se nepokusí dopředný návrh; tyto styly jsou jednoduše vygenerovat zajímavý výsledek):

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

1. Úpravou *šablon/index.html* můžete odkazovat na základní šablonu a přepsat blok obsahu. Můžete vidět, že pomocí dědičnosti se tato šablona bude jednoduchá:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Změňte *šablony/about.html* tak, aby odkazovaly na základní šablonu a přepsali jsme blok obsahu:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spusťte server a sledujte výsledky. Po dokončení Server zavřete.

    ![Běžící aplikace znázorňující navigační panel](media/flask/step03-nav-bar.png)

1. Vzhledem k tomu, že jste provedli podstatné změny v aplikaci, je opět vhodným časem [Potvrdit změny ve správě zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití šablony webového projektu na celé baňce](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Nasazení webové aplikace do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Další možnosti Jinja šablon, jako je například tok řízení, najdete v [dokumentaci k Jinja Template Designer](http://jinja.palletsprojects.com/en/2.10.x/templates/) (Jinja.pocoo.org).
- Podrobnosti o použití naleznete v `url_for` tématu [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) v dokumentaci k aplikačnímu objektu baňky (Flask.pocoo.org).
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask)
