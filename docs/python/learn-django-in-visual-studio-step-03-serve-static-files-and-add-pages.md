---
title: Kurz Django ve Visual Studiu – krok 3, statické soubory a stránky
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, který konkrétně ukazuje, jak zajišťovat statické soubory, přidávání stránek do aplikace a použití dědičnosti šablon
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 748f941d5a8f257b3765b06651ff3244793e0123
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238527"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>Krok 3: obsluha statických souborů, přidávání stránek a použití dědičnosti šablon s aplikací Django

**Předchozí krok: [Vytvoření aplikace Django se zobrazeními a šablonami stránek](learn-django-in-visual-studio-step-02-create-an-app.md)**

V předchozích krocích tohoto kurzu jste se naučili, jak vytvořit aplikaci Minimal Django s jednou stránkou vlastního HTML. Moderní webové aplikace se ale obvykle skládají z mnoha stránek a využívají sdílené prostředky, jako jsou soubory CSS a JavaScript, k zajištění konzistentního stylu a chování.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Pomocí šablon položek sady Visual Studio můžete rychle přidat nové soubory různých typů s praktickým často používaným kódem (krok 3-1).
> - Konfigurace projektu Django pro obsluhu statických souborů (krok 3-2)
> - Přidejte do aplikace další stránky (krok 3-3).
> - Pomocí dědičnosti šablon vytvořte záhlaví a navigační panel, který se používá na stránkách (krok 3-4).

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3-1: Seznámení se šablonami položek

Při vývoji aplikace Django obvykle přidáte mnoho dalších souborů Python, HTML, CSS a JavaScript. Pro každý typ souboru (stejně jako jiné soubory jako *web.config* , které můžete potřebovat pro nasazení), Visual Studio poskytuje praktické [šablony položek](python-item-templates.md) , které vám pomůžou začít.

Dostupné šablony zobrazíte tak, že přejdete na **Průzkumník řešení**, kliknete pravým tlačítkem na složku, ve které chcete položku vytvořit, vyberte **Přidat**  >  **novou položku**:

![Dialogové okno Přidat novou položku v aplikaci Visual Studio](media/django/step03-add-new-item-dialog.png)

Chcete-li použít šablonu, vyberte požadovanou šablonu, zadejte název souboru a vyberte **OK**. Přidáním položky tímto způsobem lze soubor automaticky přidat do projektu aplikace Visual Studio a označit změny pro správu zdrojového kódu.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Otázka: jak Visual Studio ví, které šablony položek nabízí?

Odpověď: soubor projektu sady Visual Studio (*. pyproj*) obsahuje identifikátor typu projektu, který ho označí jako projekt Pythonu. Sada Visual Studio používá tento identifikátor typu k zobrazení pouze těch šablon položek, které jsou vhodné pro typ projektu. Díky tomu může sada Visual Studio poskytovat bohatou sadu šablon položek pro celou řadu typů projektů bez nutnosti pokaždé, když je budete muset seřadit.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: Obsluhujte statické soubory z vaší aplikace

Ve webové aplikaci vytvořené pomocí Pythonu (pomocí libovolného rozhraní) se soubory Pythonu vždycky spouštějí na serveru webového hostitele a nikdy se nepřenáší do počítače uživatele. Jiné soubory, jako jsou například CSS a JavaScript, se používají výhradně v prohlížeči, takže hostitelský server je jednoduše přiřadí tak, jak jsou pokaždé požadovány. Tyto soubory jsou označovány jako "statické" soubory a Django je může doručovat automaticky, aniž byste museli psát kód.

Projekt Django je ve výchozím nastavení nakonfigurovaný tak, aby sloužil statickým souborům ze *statické* složky aplikace. Díky těmto řádkům v *Settings.py*projektu Django:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Můžete uspořádat soubory pomocí libovolné struktury složek v rámci *statických* , které chcete, a pak pomocí relativních cest v rámci této složky odkazovat na soubory. Chcete-li předvést tento proces, následující kroky přidají do aplikace soubor CSS a pak tuto šablonu použijte v šabloně *index.html* :

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **HelloDjangoApp** v projektu sady Visual Studio, vyberte **Přidat**  >  **novou složku**a pojmenujte složku `static` .

1. Klikněte pravým tlačítkem na **statickou** složku a vyberte **Přidat**  >  **novou položku**. V dialogovém okně, které se zobrazí, vyberte šablonu šablony **stylů** , pojmenujte soubor `site.css` a vyberte **OK**. Soubor **Web. CSS** se zobrazí v projektu a otevře se v editoru. Vaše struktura složky by měla vypadat podobně jako na následujícím obrázku:

    ![Struktura statického souboru, jak je znázorněno v Průzkumník řešení](media/django/step03-static-file-structure.png)

1. Obsah souboru *site. CSS* nahraďte následujícím kódem a uložte ho:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Nahraďte obsah souboru *Templates/HelloDjangoApp/index.htm* aplikace následujícím kódem, který nahradí `<strong>` prvek použitý v kroku 2 s objektem `<span>` , který odkazuje na `message` třídu Style. Použití třídy stylu tímto způsobem poskytuje mnohem větší flexibilitu při stylování elementu. (Pokud jste nepřesunuli *index.html* do podsložky v *šablonách* při použití vs 2017 15,7 a starší verze, přečtěte si téma [template namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) in Step 2-4.)

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

1. Spusťte projekt a sledujte výsledky. V případě potřeby zastavte Server a potvrďte změny ve správě zdrojového kódu (jak je vysvětleno v [kroku 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Otázka: Jaký je účel značky {% Load staticfiles%}?

Odpověď: `{% load staticfiles %}` řádek je vyžadován před odkazování na statické soubory v prvcích jako `<head>` a `<body>` . V příkladu zobrazeném v této části odkazuje "staticfiles" na vlastní sadu značek šablony Django, což je to, co umožňuje použít `{% static %}` syntaxi pro odkazování na statické soubory.  Bez `{% load staticfiles %}` toho se při spuštění aplikace zobrazí výjimka.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Otázka: existují nějaké konvence pro uspořádávání statických souborů?

Odpověď: v případě potřeby můžete do *statické* složky přidat další soubory CSS, JavaScript a HTML. Typický způsob, jak uspořádat statické soubory, je vytvořit podsložky s názvem *písma*, *skripty*a *obsah* (pro šablony stylů a jiné soubory). V každém případě nezapomeňte zahrnout tyto složky do relativní cesty k souboru v `{% static %}` odkazech.

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>Otázka: je možné dokončit stejnou úlohu bez použití značky {% Load staticfiles%}?

Odpověď: Ano, můžete.

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Přidání stránky do aplikace

Přidání další stránky do aplikace znamená následující:

- Přidejte funkci Pythonu, která definuje zobrazení.
- Přidejte šablonu pro značku stránky.
- Přidejte potřebné směrování do souboru *URLs.py* projektu Django.

Následující postup přidá stránku "o" do projektu "HelloDjangoApp" a odkazy na tuto stránku z domovské stránky:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **Templates/HelloDjangoApp** , vyberte možnost **Přidat**  >  **novou položku**, vyberte šablonu položky **stránky HTML** , zadejte název souboru `about.html` a vyberte **OK**.

    > [!Tip]
    > Pokud se příkaz **Nová položka** v nabídce **Přidat** nezobrazí, ujistěte se, že jste zastavili Server, aby aplikace Visual Studio ukončila režim ladění.

1. Obsah *about.html* nahraďte následujícím kódem (v kroku 3-4 nahraďte explicitní odkaz na domovskou stránku):

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

1. Otevřete soubor *views.py* aplikace a přidejte funkci s názvem `about` , která používá tuto šablonu:

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

1. Otevřete soubor *URLs.py* projektu Django a do pole přidejte následující řádek `urlPatterns` :

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otevřete soubor *Templates/HelloDjangoApp/index.html* a přidejte následující řádek pod `<body>` element, který chcete propojit se stránkou o aplikaci (znovu nahraďte tento odkaz navigačním panelem v kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Uložte všechny soubory pomocí příkazu v nabídce **soubor**  >  **Uložit vše** nebo stačí stisknout klávesy **CTRL** + **SHIFT** + **S**. (Technicky, tento krok není potřebný pro spuštění projektu v aplikaci Visual Studio ukládá soubory automaticky. Je však dobrým příkazem, který vás zajímá.)

1. Spusťte projekt a sledujte výsledky a zkontrolujte navigaci mezi stránkami. Po dokončení Server zavřete.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Otázka: Pokusili jste se použít index pro odkaz na domovskou stránku, ale nepracovali. Proč?

Odpověď: i když je pojmenovaná funkce zobrazení v *views.py* `index` , vzory směrování adres URL v souboru *URLs.py* projektu Django neobsahuje regulární výraz, který odpovídá řetězci "index". Aby se tento řetězec shodoval, je nutné přidat další položku pro vzor `^index$` .

Jak je znázorněno v další části, je mnohem lepší použít `{% url '<pattern_name>' %}` značku v šabloně stránky k odkazování na *název* vzoru. v takovém případě Django vytvoří správnou adresu URL. Například nahraďte `<div><a href="home">Home</a></div>` v *about.html* `<div><a href="{% url 'index' %}">Home</a></div>` . Použití ' index ' zde funguje, protože první vzor adresy URL v *URLs.py* je ve skutečnosti pojmenovaný ' index ' (na základě `name='index'` argumentu). K odkazování na druhý vzor můžete použít taky možnost Home.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3-4: použití dědičnosti šablony k vytvoření záhlaví a navigačního panelu

Namísto explicitních navigačních odkazů na každé stránce obvykle používají moderní webové aplikace hlavičku brandingu a navigační panel, který poskytuje nejdůležitější odkazy na stránky, místní nabídky a tak dále. Chcete-li zajistit, aby záhlaví a navigační panel byly na všech stránkách stejné, nechcete stejný kód opakovat v každé šabloně stránky. Místo toho chcete definovat společné části všech stránek na jednom místě.

Django systém šablonování poskytuje dvě možnosti pro opakované použití určitých prvků v několika šablonách: includes a dědičnost.

- *Zahrnuje* další šablony stránky, které vložíte na konkrétní místo v odkazující šabloně pomocí syntaxe `{% include <template_path> %}` . Proměnnou lze použít také v případě, že chcete změnit cestu dynamicky v kódu. Zahrnutí se obvykle používají v těle stránky pro vyžádání do sdílené šablony v určitém umístění na stránce.

- *Dědičnost* používá na `{% extends <template_path> %}` začátku šablony stránky, aby určovala sdílenou základní šablonu, na které odkazuje šablona. Dědičnost se běžně používá k definování sdíleného rozložení, navigačního panelu a dalších struktur pro stránky aplikace. to znamená, že odkazující šablony potřebují přidat nebo změnit pouze konkrétní oblasti základní šablony s názvem *bloky*.

V obou případech `<template_path>` je relativní vzhledem ke složce *šablon* aplikace ( `../` nebo `./` jsou také povoleny).

Základní šablona vymezují bloky pomocí `{% block <block_name> %}` značek a `{% endblock %}` . Pokud odkazovaná šablona potom používá značky se stejným názvem bloku, její obsah bloku přepíše základní šablonu.

Následující kroky demonstrují dědičnost:

1. Ve složce *Templates/HelloDjangoApp* aplikace vytvořte nový soubor HTML (pomocí místní nabídky **Přidat**  >  **novou položku** nebo **Přidat**  >  **stránku HTML**) s názvem *layout.html*a nahraďte jeho obsah následujícím kódem. Vidíte, že tato šablona obsahuje blok s názvem "content" (obsah), který obsahuje všechny odkazující stránky, které musí nahradit:

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

1. Úpravou *šablon/HelloDjangoApp/index.html* můžete odkazovat na základní šablonu a přepsat blok obsahu. Můžete vidět, že pomocí dědičnosti se tato šablona bude jednoduchá:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Změňte *Templates/HelloDjangoApp/about.html* tak, aby odkazovaly na základní šablonu a přepsali jsme blok obsahu:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Spusťte server a sledujte výsledky. Po dokončení Server zavřete.

    ![Běžící aplikace znázorňující navigační panel](media/django/step03-nav-bar.png)

1. Vzhledem k tomu, že jste provedli podstatné změny v aplikaci, je opět vhodným časem [Potvrdit změny ve správě zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Použití úplné šablony webového projektu Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Nasazení webové aplikace do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Zápis první aplikace v Django, část 3 (zobrazení)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Další možnosti Django šablon, jako je tok řízení, najdete v tématu [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com).
- Podrobné informace o použití `{% url %}` značky najdete v tématu [URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) v rámci [vestavěných značek šablony a filtrů pro Django odkazy na šablony](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com).
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
