---
title: Kurz k seznámení s kurzem v aplikaci Visual Studio Step 4, šablony webových projektů
titleSuffix: ''
description: Návod základů v baňce v kontextu projektů aplikace Visual Studio, konkrétně o funkcích poskytovaných šablonami webového projektu na baňce a na baňce/Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fa59197e584c6c8062c13354178f883b60b36442
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250567"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4: použití šablony webového projektu na celé baňce

**Předchozí krok: [poskytování statických souborů, přidávání stránek a použití dědičnosti šablon](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teď, když jste prozkoumali základy baňky vytvořením aplikace v šabloně projektu "prázdná aplikace" v aplikaci Visual Studio, můžete snadno pochopit celou aplikaci, která je vytvořená šablonou "webový projekt v baňce".

V tomto kroku teď:

> [!div class="checklist"]
> - Vytvoření webové aplikace s celými baňkami pomocí šablony "webový projekt v baňce" a kontrola struktury projektu (krok 4-1)
> - Seznamte se s zobrazeními a šablonami stránek vytvořenými šablonou projektu, které se skládají ze tří stránek, které dědí ze základní šablony stránky a které využívají statické knihovny JavaScriptu jako jQuery a Bootstrap (krok 4-2).
> - Pochopení směrování adres URL poskytovaného šablonou (krok 4-3)

Tento článek se vztahuje také na šablonu "webový projekt v baňce/Jade", která vytvoří aplikaci, která je shodná s verzí "webový projekt v baňce" pomocí modulu Jade šablonování namísto Jinja. Další podrobnosti jsou uvedeny na konci tohoto článku.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: vytvoření projektu ze šablony

1. V aplikaci Visual Studio přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem na řešení **LearningFlask** vytvořené dříve v tomto kurzu a vyberte **Přidat**  >  **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **soubor**  >  **Nové**  >  Místo toho **projekt** .)

1. V dialogovém okně Nový projekt vyhledejte a vyberte šablonu **webového projektu baňky** , zavolejte projekt "FlaskWeb" a vyberte **OK**.

1. Vzhledem k tomu, že šablona znovu obsahuje soubor *requirements.txt* , Visual Studio zobrazí výzvu k instalaci těchto závislostí. Zvolte možnost, **nainstalujte ji do virtuálního prostředí**a v dialogovém okně **Přidat virtuální prostředí** vyberte **vytvořit** a přijměte výchozí hodnoty.

1. Jakmile sada Visual Studio dokončí nastavení virtuálního prostředí, nastavte projekt **FlaskWeb** jako výchozí pro řešení sady Visual Studio tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **nastavit jako spouštěný projekt**. Spouštěný projekt, který je zobrazen tučně, je spuštěn při spuštění ladicího programu.

    ![Průzkumník řešení zobrazení projektu FlaskWeb jako spouštěného projektu](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo pomocí tlačítka **webový server** na panelu nástrojů spusťte server:

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, domů, o a kontakt, které můžete procházet pomocí navigačního panelu. Podíváme se na jednu minutu nebo dvě, abyste prozkoumali různé části aplikace. K ověřování pomocí aplikace pomocí příkazu **Přihlásit** použijte přihlašovací údaje uživatele, které jste vytvořili dříve.

    ![Úplné zobrazení prohlížeče aplikace webového projektu v baňce](media/flask/step04-full-app-desktop-view.png)

1. Aplikace vytvořená šablonou webového projektu v baňce používá Bootstrap pro reakce na rozložení, které vyhovuje faktorům pro mobilní zařízení. Chcete-li zobrazit tuto odezvu, změňte velikost prohlížeče tak, aby se obsah nakreslovat svisle a navigační panel se změní na ikonu nabídky:

    ![Mobilní (úzké) zobrazení aplikace webového projektu v baňce](media/flask/step04-full-app-mobile-view.png)

1. Aplikaci můžete ponechat spuštěnou v následujících oddílech.

    Pokud chcete zastavit aplikaci a [Potvrdit změny ve správě zdrojového kódu](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), otevřete nejprve stránku **změny** v **Team Explorer**, klikněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **ENV**) a vyberte možnost **ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Kontrola vytvoření šablony

Šablona "webový projekt v baňce" vytvoří strukturu níže. Obsah je velmi podobný tomu, co jste vytvořili v předchozích krocích. Rozdílem je, že šablona "webový projekt v baňce" obsahuje více struktury ve *statické* složce, protože zahrnuje jQuery a Bootstrap pro návrh s odezvou. Šablona také přidá stránku kontaktů. Pokud jste postupovali podle předchozích kroků v tomto kurzu, měli byste si být vědomi všeho ze šablony.

- Soubory v kořenu projektu:
  - *runserver.py*, skript pro spuštění aplikace na vývojovém serveru.
  - *requirements.txt* , který obsahuje závislost na baňce 0. x.
- Složka *FlaskWeb* obsahuje všechny soubory aplikace:
  - init.py označí kód aplikace jako modul Pythonu, vytvoří objekt v baňce a naimportuje zobrazení aplikace. * \_ \_ \_ \_ *
  - *views.py* obsahuje kód pro vykreslení stránek.
  - *Statická* složka obsahuje podsložky s názvem *Content* (soubory CSS), *písma* (soubory písem) a *skripty* (soubory JavaScriptu).
  - Složka *šablony* obsahuje základní šablonu *layout.html* spolu s *about.html*, *contact.html*a *index.html* pro konkrétní stránky, které každá rozšiřuje *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: je možné sdílet virtuální prostředí mezi projekty sady Visual Studio?

Odpověď: Ano, ale udělejte to s vědomím, že různé projekty nejspíš v průběhu času používají různé balíčky, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které ji používají.

Chcete-li však použít stávající virtuální prostředí, postupujte následovně:

1. Až se zobrazí výzva k instalaci závislostí v aplikaci Visual Studio, vyberte možnost **instalovat** vlastní.
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte **Přidat existující virtuální prostředí**.
1. Přejděte na složku obsahující virtuální prostředí a vyberte ji a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: porozumění zobrazením a šablonám stránek vytvořeným šablonou projektu

Při spuštění projektu aplikace obsahuje tři zobrazení: domů, o aplikaci a kontakt. Kód pro tato zobrazení najdete v *FlaskWeb/views. py*. Každá funkce zobrazení jednoduše volá `flask.render_template` cestu k šabloně a seznam argumentů proměnných pro hodnoty, které mají být do šablony zadány. Například stránka about je zpracována `about` funkcí (jejíž dekoratér poskytuje směrování adres URL):

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

`home`Funkce a `contact` jsou téměř identické, s podobným dekoratéry a mírně odlišnými argumenty.

Šablony se nacházejí ve složce *šablony* aplikace. Základní šablona, *layout.html*, je nejrozsáhlejší. Odkazuje na všechny nezbytné statické soubory (JavaScript a CSS), definuje blok s názvem "obsah", na který se přepíší jiné stránky, a poskytuje další blok s názvem "skripty". Následující výňatky uvedené v poznámce z *layout.html* znázorňují tyto konkrétní oblasti:

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

## <a name="the-flaskjade-web-project-template"></a>Šablona webového projektu pro baňky nebo Jade

Jak je uvedeno na začátku tohoto článku, Visual Studio poskytuje šablonu pro webový projekt ve formátu "baněk/Jade", která vytvoří aplikaci, která je vizuálně shodná s tím, co je vytvořeno pomocí "webové projekty v baňce". Hlavním rozdílem je to, že používá modul Jade šablonování, což je rozšíření Jinja, které implementuje stejné koncepty s pokročilejším jazykem. Konkrétně Jade používá klíčová slova namísto značek uzavřených do {%%} oddělovačů, například a umožňuje odkazování stylů CSS a prvků HTML pomocí klíčových slov.

Aby bylo možné povolit Jade, šablona projektu nejprve zahrnuje balíček pyjade v *requirements.txt*.

Soubor * \_ \_ init \_ \_ . py* aplikace obsahuje řádek pro

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

Ve složce *šablony* se zobrazí soubory *. Jade* namísto šablon *. html* a zobrazení v *views.py* odkazují na tyto soubory v volání `flask.render_template` . V opačném případě je kód zobrazení stejný.

Otevřením jednoho ze souborů *. Jade* můžete zobrazit výstižnější výraz šablony. Tady je například obsah *šablony/layout. Jade* , jak je vytvořený šablonou webového projektu "baňka/Jade":

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

A tady je obsah *šablon/About. Jade*, který ukazuje použití `#{ <name>}` zástupných symbolů:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Nebojte se experimentovat s Jinja a Jade syntaxemi, abyste viděli, které z nich nejlépe vyhovuje.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Šablona webového projektu v baňce k dotazům](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Vytvoření první aplikace v baňce, část 4 – formuláře a obecná zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHubu (dokumentace)](https://github.com/liuliqiang/pyjade) (GitHub.com)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask)
