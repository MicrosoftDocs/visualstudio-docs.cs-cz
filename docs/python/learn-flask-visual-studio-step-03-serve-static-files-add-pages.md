---
title: Výuka flask v kroku 3 sady Visual Studio, statické soubory a stránky
titleSuffix: ''
description: Návod základy Flask v kontextu projektů sady Visual Studio, konkrétně ukazuje, jak sloužit statické soubory, přidat stránky do aplikace a použít dědičnost šablony
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5aa952a00075cdad262803140ab4c0360f0c62a0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72985184"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Krok 3: Obsluhování statických souborů, přidávání stránek a používání dědičnosti šablony

**Předchozí krok: [Vytvoření aplikace Flask se zobrazeními a šablonami stránek](learn-flask-visual-studio-step-02-create-app.md)**

V předchozích krocích tohoto kurzu jste se naučili, jak vytvořit minimální aplikaci Flask s jednou stránkou samostatného HTML. Moderní webové aplikace se však obvykle skládají z mnoha stránek a využívají sdílené prostředky, jako jsou soubory CSS a JavaScript, k zajištění konzistentního stylu a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Pomocí šablon položek sady Visual Studio můžete rychle přidávat nové soubory různých typů pomocí vhodného standardního kódu (krok 3-1)
> - Obsluhovat statické soubory z kódu (krok 3-2, volitelné)
> - Přidání dalších stránek do aplikace (krok 3-3)
> - Vytvoření záhlaví a nav panelu, který se používá na všech stránkách (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznámení se se šablonami položek

Při vývoji aplikace Flask obvykle přidáváte mnoho dalších souborů Pythonu, HTML, CSS a JavaScriptu. Pro každý typ souboru (stejně jako další soubory, jako je *web.config,* které budete potřebovat pro nasazení), Visual Studio poskytuje pohodlné [šablony položek,](python-item-templates.md) které vám pomohou začít.

Dostupné šablony zobrazíte v **Průzkumníku řešení**a klepněte pravým tlačítkem myši na složku, ve které chcete položku vytvořit, a vyberte **přidat** > **novou položku**:

![Dialogové okno Přidat novou položku v sadě Visual Studio](media/flask/step03-add-new-item-dialog.png)

Chcete-li použít šablonu, vyberte požadovanou šablonu, zadejte název souboru a vyberte **OK**. Přidání položky tímto způsobem automaticky přidá soubor do projektu sady Visual Studio a označí změny pro správě zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: Jak Visual Studio vědět, které šablony položek nabídnout?

Odpověď: Soubor projektu Visual Studio (*.pyproj*) obsahuje identifikátor typu projektu, který jej označí jako projekt Pythonu. Visual Studio používá tento identifikátor typu k zobrazení pouze ty šablony položek, které jsou vhodné pro typ projektu. Tímto způsobem visual studio můžete zadat bohatou sadu šablon položek pro mnoho typů projektů, aniž by vás požádat o jejich třídění pokaždé.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Zobrazení statických souborů z aplikace

Ve webové aplikaci vytvořené v Pythonu (pomocí libovolného rozhraní) se soubory Pythonu vždy spouštějí na serveru webového hostitele a nikdy se nepřenášejí do počítače uživatele. Jiné soubory, jako například CSS a JavaScript, jsou však používány výhradně prohlížečem, takže hostitelský server je jednoduše dodává tak, jak jsou požadovány. Tyto soubory jsou označovány jako "statické" soubory a Flask je může automaticky doručit, aniž byste museli psát jakýkoli kód. V souborech HTML můžete například odkazovat pouze na statické soubory pomocí relativní cesty v projektu. První část v tomto kroku přidá soubor CSS do existující šablony stránky.

Když potřebujete doručit statický soubor z kódu, například prostřednictvím implementace koncového bodu rozhraní API, Flask poskytuje pohodlnou metodu, která umožňuje odkazovat na soubory pomocí relativní cesty v rámci složky s názvem *static* (v kořenovém adresáři projektu). Druhá část v tomto kroku ukazuje, že metoda pomocí jednoduchého statického datového souboru.

V obou případech můžete uspořádat soubory pod *statickým,* jak se vám líbí.

### <a name="use-a-static-file-in-a-template"></a>Použití statického souboru v šabloně

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **HelloFlask** v `static`projektu sady Visual Studio, vyberte **přidat** > novou**složku**a pojmenujte složku .

1. Klepněte pravým tlačítkem myši na **statickou** složku a vyberte **přidat** > **novou položku**. V zobrazeném dialogovém okně vyberte šablonu **stylů,** pojmenujte soubor `site.css`a vyberte **OK**. Soubor **site.css** se zobrazí v projektu a je otevřen v editoru. Struktura složek by měla vypadat podobně jako na následujícím obrázku:

    ![Statická struktura souborů, jak je znázorněno v Průzkumníku řešení](media/flask/step03-static-file-structure.png)

1. Nahraďte obsah *webu site.css* následujícím kódem a uložte soubor:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Nahraďte obsah *templates/index.html* souboru aplikace následujícím kódem, `<strong>` který nahradí prvek použitý `<span>` v kroku `message` 2 a, který odkazuje na třídu stylu. Použití třídy stylu tímto způsobem poskytuje mnohem větší flexibilitu při stylingu prvku.

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

1. Spusťte projekt sledovat výsledky. Zastavte aplikaci po dokončení a potvrďte změny do správy zdrojového kódu, pokud se vám líbí (jak je vysvětleno v [kroku 2).](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)

### <a name="serve-a-static-file-from-code"></a>Obsluhovat statický soubor z kódu

Flask poskytuje funkci `serve_static_file` volanou z kódu, která odkazuje na libovolný soubor ve *statické* složce projektu. Následující proces vytvoří jednoduchý koncový bod rozhraní API, který vrací statický datový soubor.

1. Pokud jste tak ještě neučinili, vytvořte *statickou* složku: v **Průzkumníku řešení**klepněte pravým tlačítkem myši na `static`složku **HelloFlask** v projektu sady Visual Studio, vyberte **Přidat** > novou**složku**a pojmenujte složku .

1. Ve *statické* složce vytvořte statický datový soubor JSON s názvem *data.json* s následujícím obsahem (což jsou nesmyslná ukázková data):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. V *views.py*přidejte funkci s route /api/data, která `send_static_file` vrací statický datový soubor pomocí metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Spusťte aplikaci a přejděte do koncového bodu /api/data, abyste zjistili, že je vrácen statický soubor. Až budete hotovi, zastavte aplikaci.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Otázka: Existují nějaké konvence pro uspořádání statických souborů?

Odpověď: Do *statické* složky můžete přidávat další soubory CSS, JavaScript a HTML, jak chcete. Typickým způsobem uspořádání statických souborů je vytvoření podsložek s názvem *písma*, *skripty*a *obsah* (pro šablony stylů a všechny ostatní soubory).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Otázka: Jak zpracovat proměnné adresy URL a parametry dotazu v rozhraní API?

Odpověď: Podívejte se na odpověď v kroku 1-4 pro [otázku: Jak Flask pracuje s variabilními směry URL a parametry dotazu?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky do aplikace

Přidání další stránky do aplikace znamená následující:

- Přidejte funkci Pythonu, která definuje zobrazení.
- Přidejte šablonu pro značku stránky.
- Přidejte potřebné směrování do *urls.py* souboru projektu Flask.

Následující kroky přidají stránku "O" do projektu "HelloFlask" a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **předlohy,** vyberte **Přidat** > **novou položku**, vyberte šablonu **položky stránky HTML,** pojmenujte soubor `about.html`a vyberte **OK**.

    > [!Tip]
    > Pokud se příkaz **Nová položka** nezobrazuje v nabídce **Přidat,** ujistěte se, že jste aplikaci zastavili, aby Visual Studio ukončilo režim ladění.

1. Nahraďte obsah *about.html* následujícími značkami (explicitní odkaz na domovskou stránku nahradíte jednoduchým navigačním panelem v kroku 3-4):

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

1. Otevřete soubor *views.py* aplikace a přidejte funkci s názvem, `about` která šablonu používá:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otevřete *soubor templates/index.html* a okamžitě přidejte následující řádek do elementu, `<body>` který chcete propojit se stránkou Informace (znovu tento odkaz nahradíte nav barem v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí příkazu Nabídka **Uložit** > **vše** soubor nebo stačí stisknout **kombinaci kláves Ctrl**+**Shift**+**S**. (Technicky tento krok není potřeba, protože spuštění projektu v sadě Visual Studio ukládá soubory automaticky. Nicméně, je to dobrý příkaz vědět!)

1. Spusťte projekt sledovat výsledky a zkontrolujte navigaci mezi stránkami. Po dokončení zastavte aplikaci.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Otázka: Záleží na názvu funkce stránky pro Flask?

Odpověď: Ne, protože je `@app.route` decorator, který určuje adresy URL, pro které Flask volá funkci generovat odpověď. Vývojáři obvykle odpovídají názvu funkce k trase, ale takové párování není vyžadováno.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: Vytvoření záhlaví a nav panelu pomocí dědičnosti šablony

Namísto explicitních navigačních odkazů na každé stránce používají moderní webové aplikace obvykle záhlaví značky a navigační panel, který poskytuje nejdůležitější odkazy na stránky, místní nabídky a tak dále. Chcete-li se ujistit, že záhlaví a nav panel jsou stejné na všech stránkách, ale nechcete opakovat stejný kód v každé šabloně stránky. Místo toho chcete definovat společné části všech stránek na jednom místě.

Systém šablon (ve výchozím nastavení Jinja) poskytuje dva způsoby opětovného použití určitých prvků ve více šablonách: zahrnuje a dědičnost.

- *Zahrnuje* další šablony stránek, které vložíte na určité místo v `{% include <template_path> %}`odkazující šabloně pomocí syntaxe . Proměnnou můžete také použít, pokud chcete dynamicky změnit cestu v kódu. Zahrnuty se obvykle používají v těle stránky k vytahování sdílené šablony v určitém umístění na stránce.

- *Dědičnost* `{% extends <template_path> %}` používá na začátku šablony stránky k určení sdílené základní šablony, na které pak odkazuje odkazující šablona. Dědičnost se běžně používá k definování sdíleného rozložení, nav panelu a dalších struktur pro stránky aplikace, takže odkazující šablony stačí přidat nebo upravit určité oblasti základní šablony nazývané *bloky*.

V obou `<template_path>` případech je relativní vzhledem ke`../` složce šablony aplikace (nebo `./` jsou také *povoleny).*

Základní šablona vymezuje *bloky* pomocí `{% block <block_name> %}` a `{% endblock %}` tagy. Pokud odkazující šablona pak používá značky se stejným názvem bloku, její obsah bloku přepíše obsah základní šablony.

Následující kroky ukazují dědičnost:

1. Ve složce *šablony* aplikace vytvořte nový soubor HTML (pomocí kontextové nabídky **Přidat** > **novou položku** nebo **Přidat** > **stránku HTML)** s názvem *layout.html*a nahraďte jeho obsah níže uvedenou značkou. Můžete vidět, že tato šablona obsahuje blok s názvem "obsah", který je vše, co odkazující stránky musí nahradit:

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

1. Upravte *templates/index.html* tak, aby odkazoval na základní šablonu, a přepište blok obsahu. Můžete vidět, že pomocí dědičnosti, tato šablona se stane jednoduché:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Upravte *templates/about.html* tak, aby také odkazoval na základní šablonu a přepsal blok obsahu:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spusťte server sledovat výsledky. Po dokončení zavřete server.

    ![Spuštěná aplikace zobrazující nav panel](media/flask/step03-nav-bar.png)

1. Vzhledem k tomu, že jste v aplikaci provedli podstatné změny, je opět vhodná doba [k potvrzení změn správy zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití úplné šablony webového projektu Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Nasazení webové aplikace do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Další možnosti šablon Jinja, jako je například tok řízení, naleznete [v tématu Jinja Template Designer Documentation](http://jinja.palletsprojects.com/en/2.10.x/templates/) (jinja.pocoo.org)
- Podrobnosti o `url_for`použití naleznete [v url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) v dokumentaci k aplikačním objektům Flask (flask.pocoo.org)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-baňka](https://github.com/Microsoft/python-sample-vs-learning-flask)
