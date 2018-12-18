---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 4, šablony webových projektů
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, konkrétně funkcí poskytovaných službou webový projekt Flask a webový projekt Flask/Jade šablony.
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
ms.openlocfilehash: c072d1187abf463cc2f185946f7e238bb091a534
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051698"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4: Použití úplné šablony webového projektu Flask

**Předchozí krok: [doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teď, když jste prozkoumali základní informace o Flask vytvořením aplikace na šabloně "Prázdný projekt Flask aplikace" v sadě Visual Studio, je možné snadno zjistit plnější aplikace, který je vytvořen pomocí šablony "Webový projekt Flask".

V tomto kroku můžete nyní:

> [!div class="checklist"]
> - Vytvoření plnější webové aplikace Flask pomocí šablony "Webový projekt Flask" a zkontrolujte strukturu projektu (krok 4 - 1)
> - Rady pro pochopení zobrazení a stránky šablony vytvořené šablony projektu, které tvoří tři stránky, které dědí ze základní stránky šablony a, který využívá statické knihovny JavaScriptu, jako je jQuery a Bootstrap (krok 4-2)
> - Vysvětlení směrování adres URL poskytovanou šablonou (krok 4-3)

Tento článek se týká také do šablony "Webový projekt Flask/Jade", který vytváří aplikaci, která je stejná jako "Flask webového projektu" místo šablonovacím systémem Jade šablonování modul. Další podrobnosti jsou zahrnuty na konci tohoto článku.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: vytvoření projektu ze šablony

1. V sadě Visual Studio, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem myši **LearningFlask** řešení vytvořené dříve v tomto kurzu a vyberte **přidat**  >   **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **souboru** > **nový** > **projektu** místo.)

1. V dialogovém okně Nový projekt, vyhledejte a vyberte **webový projekt Flask** šablony, volání "FlaskWeb" projekt a vyberte **OK**.

1. Vzhledem k tomu šablonu znovu zahrnuje *souboru requirements.txt* souboru, Visual Studio vyzve vhodného místa pro instalaci těchto závislostí. Zvolte si možnost **nainstalovat do virtuálního prostředí**a **přidat virtuální prostředí** dialogové okno Vybrat **vytvořit** přijměte výchozí hodnoty.

1. Po dokončení nastavení virtuálního prostředí sady Visual Studio nastavte **FlaskWeb** projekt jako výchozí pro řešení sady Visual Studio kliknutím pravým tlačítkem myši v projektu **Průzkumníka řešení** a Výběr **nastavit jako spouštěný projekt**. Projekt při spuštění, která je znázorněna v tučné písmo, se co je spuštěn při spuštění ladicího programu.

    ![Průzkumník řešení zobrazující FlaskWeb projekt jako spouštěný projekt](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů můžete spustit na serveru:

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikace vytvořené pomocí šablony má tři stránky, Home, o programu a kontaktovat, který můžete procházet pomocí navigačního panelu. Trvat minutu nebo dvě prozkoumat různé části aplikace. K ověření aplikace prostřednictvím **přihlášení** příkazu, použijte přihlašovací údaje superuživatele vytvořili dříve.

    ![Úplné prohlížeči aplikace Flask webového projektu](media/flask/step04-full-app-desktop-view.png)

1. Aplikace vytvořené pomocí šablony "Webový projekt Flask" využívá Bootstrap responzivním rozložením, které se přizpůsobuje mobilních zařízení. Pokud chcete zobrazit tento rychlost odezvy, změna velikosti prohlížeči v úzkém zobrazení tak, aby obsah vykreslí svisle a na navigačním panelu se změní ikona nabídky:

    ![Mobilní zařízení (úzké) zobrazení aplikace webový projekt Flask](media/flask/step04-full-app-mobile-view.png)

1. Můžete nechat aplikaci spuštěnou pro následující části.

    Pokud budete chtít aplikaci zastavit a [potvrzení změn do správy zdrojových kódů](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), nejdřív otevřete **změny** stránku **Průzkumník týmových projektů**, klikněte pravým tlačítkem na složku pro virtuální prostředí ( pravděpodobně **env**) a vyberte **ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Zkontrolujte, co šablona vytvoří

"Webový projekt Flask" šablona vytvoří následující strukturu. Obsah je velmi podobný co jste vytvořili v předchozích krocích. Rozdíl je, že šablona "Webový projekt Flask" obsahuje další struktury *statické* složky, protože obsahuje jQuery a Bootstrap responzivní návrh. Šablona přidá také stránka kontaktu. Celkově Pokud jste postupovali podle předchozích kroků v tomto kurzu, všechno v šabloně měli seznámit.

- Soubory v kořenové složce projektu:
  - *runserver.PY*, skript ke spuštění aplikace v vývojový server.
  - *soubor Requirements.txt* obsahuje závislost na Flask 0.x.
- *FlaskWeb* složka obsahuje všechny soubory aplikace:
  - *\_\_Init.PY\_ \_*  označí kód aplikace jako modul Pythonu, vytvoří objekt Flask a importuje zobrazení aplikace.
  - *Views.PY* obsahuje kód pro vykreslení stránky.
  - *Statické* složka obsahuje podsložky s názvem *obsah* (soubory šablon stylů CSS), *písma* (soubory písem), a *skripty* (soubory JavaScriptu).
  - *Šablony* obsahuje složku *layout.html* základní šablona spolu s *about.html*, *contact.html*, a  *index.HTML* pro konkrétní stránky, které každý rozšířit *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: Je možné sdílet mezi projekty aplikace Visual Studio do virtuálního prostředí?

Odpověď: Ano, ale Uděláte to tak povědomí, že různé projekty, které mohou použít jiné balíčky v čase, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které ji používají.

Nicméně pokud chcete použít existující virtuální prostředí, postupujte takto:

1. Po zobrazení výzvy k instalaci závislostí v sadě Visual Studio, vyberte **nainstaluji je sám** možnost.
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prostředí Pythonu** uzel a vyberte možnost **přidat existující virtuální prostředí**.
1. Vyhledejte a vyberte složku, která obsahuje virtuální prostředí a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4 – 2: pochopení zobrazení a stránky šablony vytvořené šablony projektu

Jak zjistíte, když spustíte projekt, aplikace obsahuje tři zobrazení: Home, o programu a kontaktujte. Kód pro tato zobrazení je součástí *FlaskWeb/views.py*. Každá funkce zobrazení jednoduše volá `flask.render_template` cestou k šabloně a proměnné seznam argumentů pro hodnoty poskytnout do šablony. Například se postará o stránku `about` – funkce (jehož dekoratér poskytuje směrování adres URL):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` a `contact` jsou téměř identické, s dekoratéry podobné a mírně odlišná argumenty funkce.

Šablony jsou umístěny v aplikaci prvku *šablony* složky. Základní šablona *layout.html*, je nejvíc rozsáhlý. Odkazuje na všechny potřebné statické soubory (jazyk JavaScript a CSS), definuje blok s názvem "obsah" jiných stránek přepsání a poskytuje další blok s názvem "skripty". Následující anotována výňatky ze *layout.html* zobrazit tyto konkrétní oblasti:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Šablona webový projekt Flask/Jade

Jak je uvedeno na začátku tohoto článku, Visual Studio poskytují šablonu "Webový projekt Flask/Jade", která vytvoří aplikaci, která je vizuálně shodná s co vytvořil "Webový projekt Flask". Hlavní rozdíl je, že používá modul Jade šablon, což je rozšíření šablonovacím systémem, která implementuje stejné koncepty stručnější jazyk. Konkrétně Jade používá klíčová slova namísto značky, které jsou uzavřeny v {% oddělovače, například a umožňuje odkazovat na prvky HTML pomocí klíčových slov a stylů CSS.

Umožňující Jade zahrnuje šablony projektu nejprve pyjade balíčku v *souboru requirements.txt*. 

Aplikace  *\_ \_init\_\_.py* souboru obsahuje řádek do

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```
V *šablony* složky, uvidíte *.jade* soubory místo *.html* šablony a zobrazení v *views.py* najdete v těchto souborů v jejich volání `flask.render_template`. Zobrazení kódu jinak je stejný.

Otevření jedné ze *.jade* soubory, můžete zobrazit stručnější výraz šablony. Například tady je obsah *templates/layout.jade* jako autor šablony "Webový projekt Flask/Jade":

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

A tady je obsah *templates/about.jade*, znázorňujícího používání `#{ <name>}` pro zástupné symboly:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Bez obav experimentovat s šablonovacím systémem i Jade syntaxí zobrazíte, která z nich se vám nejvíce vyhovuje.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Polls – webový projekt Flask šablony](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Zápis svoji první aplikaci Flask, část 4 – formulářů a obecného zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHib (dokumentace)](https://github.com/liuliqiang/pyjade) (webu github.com)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
