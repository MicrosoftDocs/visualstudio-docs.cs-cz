---
title: Výuka flask v kroku 4 sady Visual Studio, šablony webových projektů
titleSuffix: ''
description: Návod základy Flask v kontextu projektů sady Visual Studio, konkrétně funkce poskytované flask webový projekt a flask/ Jade web project šablony.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9f4c165f3e882cea71ee4aaff9f2358c27ce6a2b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957233"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Krok 4: Použití úplné šablony webového projektu Flask

**Předchozí krok: [Obsluha statických souborů, přidávání stránek a používání dědičnosti šablony](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teď, když jste prozkoumali základy Flask vytvořením aplikace na šabloně "Blank Flask App Project" v sadě Visual Studio, můžete snadno pochopit plnější aplikaci, která je vytvořena šablonou "Flask Web Project".

V tomto kroku nyní:

> [!div class="checklist"]
> - Vytvořte plnější webovou aplikaci Flask pomocí šablony "Flask Web Project" a prohlédněte si strukturu projektu (krok 4-1)
> - Porozumět zobrazením a šablonám stránek vytvořeným šablonou projektu, které se skládají ze tří stránek, které dědí ze základní šablony stránky a které využívají statické knihovny JavaScriptu, jako je jQuery a Bootstrap (krok 4-2)
> - Principy směrování adres URL poskytovaného šablonou (krok 4-3)

Tento článek se vztahuje také na šablonu "Flask/Jade Web Project", která vytváří aplikaci, která je shodná s aplikací "Flask Web Project" pomocí modulu Jade templating místo Jinja. Další podrobnosti jsou uvedeny na konci tohoto článku.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4-1: Vytvoření projektu ze šablony

1. V sadě Visual Studio přejděte do **Průzkumníka řešení**, klepněte pravým tlačítkem myši na řešení **LearningFlask** vytvořené dříve v tomto kurzu a vyberte **přidat** > **nový projekt**. (Pokud chcete použít nové řešení, vyberte místo toho **možnost Soubor** > **nového** > **projektu.)**

1. V novém dialogovém okně projektu vyhledejte a vyberte šablonu **webového projektu Flask,** zavolejte projekt "FlaskWeb" a vyberte **OK**.

1. Vzhledem k tomu, že šablona opět obsahuje soubor *requirements.txt,* Visual Studio se zeptá, kam nainstalovat tyto závislosti. Zvolte možnost Instalovat **do virtuálního prostředí**a v dialogovém okně Přidat virtuální **prostředí** vyberte **Vytvořit,** abyste přijali výchozí hodnoty.

1. Po dokončení nastavení virtuálního prostředí nastavte projekt **FlaskWeb** jako výchozí pro řešení sady Visual Studio klepnutím pravým tlačítkem myši na tento projekt v **Průzkumníkovi řešení** a výběrem **možnosti Nastavit jako projekt po spuštění**. Projekt spuštění, který je zobrazen tučně, je to, co je spuštěno při spuštění ladicího programu.

    ![Průzkumník řešení zobrazující projekt FlaskWeb jako spouštěcí projekt](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Vyberte **Možnost Ladění** > **spouštět ladění** **(F5)** nebo pomocí tlačítka Webový **server** na panelu nástrojů spusťte server:

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, Domovská stránka, Informace a Kontakt, mezi nimiž procházíte pomocí nav panelu. Udělejte si minutu nebo dvě, abyste prozkoumali různé části aplikace. Chcete-li se s aplikací ověřit pomocí příkazu **Přihlásit,** použijte dříve vytvořená pověření superuživatele.

    ![Zobrazení celého prohlížeče aplikace Flask Web Project](media/flask/step04-full-app-desktop-view.png)

1. Aplikace vytvořená šablonou "Flask Web Project" používá Bootstrap pro responzivní rozložení, které vyhovuje mobilním tvarovým faktorům. Chcete-li zobrazit tuto odezvu, změňte velikost prohlížeče do úzkého zobrazení tak, aby se obsah vykresloval svisle a nav panel se změní na ikonu nabídky:

    ![Mobilní (úzký) pohled na aplikaci Flask Web Project](media/flask/step04-full-app-mobile-view.png)

1. Aplikaci můžete nechat spuštěnou pro následující oddíly.

    Pokud chcete aplikaci zastavit a [potvrdit změny správy zdrojového kódu](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), otevřete **nejprve** stránku Změny v **Průzkumníkovi týmu**, klepněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **env)** a vyberte **Ignorovat tyto místní položky**.

### <a name="examine-what-the-template-creates"></a>Zkontrolujte, co šablona vytváří

Šablona "Flask Web Project" vytvoří níže uvedenou strukturu. Obsah je velmi podobný tomu, co jste vytvořili v předchozích krocích. Rozdíl je v tom, že šablona "Flask Web Project" obsahuje více struktury ve *statické* složce, protože obsahuje jQuery a Bootstrap pro responzivní návrh. Šablona také přidá stránku Kontakt. Celkově pokud jste postupovali podle předchozích kroků v tomto kurzu, vše ze šablony by mělo být známé.

- Soubory v kořenovém adresáři projektu:
  - *runserver.py*, skript pro spuštění aplikace na vývojovém serveru.
  - *requirements.txt* obsahující závislost na Flask 0.x.
- Složka *FlaskWeb* obsahuje všechny soubory aplikace:
  - init.py označí kód aplikace jako modul Pythonu, vytvoří objekt Flask a importuje zobrazení aplikace. * \_ \_\_ *
  - *views.py* obsahuje kód pro vykreslení stránek.
  - *Statická* složka obsahuje podsložky s názvem *obsah* (soubory CSS), *písma* (soubory písem) a *skripty* (soubory JavaScriptu).
  - Složka *šablony* obsahuje základní šablonu *layout.html* spolu s *about.html*, *contact.html*a *index.html* pro konkrétní stránky, které rozšiřují *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Otázka: Je možné sdílet virtuální prostředí mezi projekty sady Visual Studio?

Odpověď: Ano, ale s vědomím, že různé projekty pravděpodobně používají různé balíčky v průběhu času, a proto sdílené virtuální prostředí musí obsahovat všechny balíčky pro všechny projekty, které jej používají.

Chcete-li však použít existující virtuální prostředí, postupujte takto:

1. Po zobrazení výzvy k instalaci závislostí v sadě Visual Studio vyberte **možnost Nainstalovat je sám.**
1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte **přidat existující virtuální prostředí**.
1. Přejděte do složky obsahující virtuální prostředí a vyberte ji a pak vyberte **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: Pochopení zobrazení a šablon stránek vytvořených šablonou projektu

Jak zjistíte při spuštění projektu, aplikace obsahuje tři zobrazení: Domů, O a Kontakt. Kód pro tato zobrazení se nachází v *FlaskWeb/views.py*. Každá funkce zobrazení `flask.render_template` jednoduše volá s cestou k šabloně a seznamem proměnných pro hodnoty, které mají být šabloně uvedeny. Například O stránce je zpracována `about` funkce (jehož decorator poskytuje směrování URL):

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

Funkce `home` `contact` a jsou téměř identické, s podobnými dekoratéry a mírně odlišnými argumenty.

Šablony jsou *umístěny* ve složce šablony aplikace. Základní *šablona, layout.html*, je nejrozsáhlejší. Odkazuje na všechny potřebné statické soubory (JavaScript a CSS), definuje blok s názvem "obsah", který ostatní stránky přepsat, a poskytuje další blok s názvem "skripty". Následující poznámky z *layout.html* ukazují tyto specifické oblasti:

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

## <a name="the-flaskjade-web-project-template"></a>Šablona webového projektu Flask/Jade

Jak je uvedeno na začátku tohoto článku, Visual Studio poskytují šablonu "Flask/Jade Web Project", která vytvoří aplikaci, která je vizuálně identická s tím, co je produkován "Flask Web Project". Hlavním rozdílem je, že používá motor Jade templating, což je rozšíření jinja, které implementuje stejné koncepty s stručnějším jazykem. Jade konkrétně používá klíčová slova namísto značek uzavřených například v oddělovačích {% %} a umožňuje odkazovat na styly CSS a prvky HTML pomocí klíčových slov.

Chcete-li povolit Jade, šablona projektu nejprve obsahuje balíček pyjade v *requirements.txt*.

Soubor * \_ \_init\_\_.py* aplikace obsahuje řádek

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

Ve složce *šablony* se místo šablon *HTML* zobrazují soubory *.jade* a zobrazení v *views.py* odkazují `flask.render_template`na tyto soubory v jejich volání . V opačném případě je kód zobrazení stejný.

Otevření jednoho ze souborů *.jade,* můžete vidět stručnější výraz šablony. Například zde je obsah *šablon/layout.jade,* jak je vytvořen šablonou "Flask/Jade Web Project":

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

A tady je obsah *šablon / about.jade*, `#{ <name>}` ukazující použití pro zástupné symboly:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Neváhejte a experimentujte se syndaněmi Jinja i Jade a zjistěte, který z nich vám nejlépe vyhovuje.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Šablona webového projektu Polls Flask](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Psaní první flask app, část 4 - formuláře a obecná zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHib (dokumentace)](https://github.com/liuliqiang/pyjade) (github.com)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-baňka](https://github.com/Microsoft/python-sample-vs-learning-flask)
