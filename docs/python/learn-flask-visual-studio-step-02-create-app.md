---
title: Výuka flask v kroku 2, zobrazení a šablony visual ateliového studia
titleSuffix: ''
description: Návod základy Flask v kontextu projektů sady Visual Studio, konkrétně kroky vytváření aplikace a pomocí zobrazení a šablony.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 03a0eb6808b2298e0727492978d9beb7cfaf2216
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302838"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Flask se zobrazeními a šablonami stránek

**Předchozí krok: [Vytvoření projektu a řešení sady Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Co máte z kroku 1 tohoto kurzu je flask aplikace s jednou stránkou a veškerý kód v jednom souboru. Chcete-li povolit budoucí vývoj, je nejlepší refaktorovat kód a vytvořit strukturu pro šablony stránek. Zejména chcete oddělit kód pro zobrazení aplikace od jiných aspektů, jako je spouštěcí kód.

V tomto kroku se nyní dozvíte, jak:

> [!div class="checklist"]
> - Refaktorovat kód aplikace tak, aby se oddělila zobrazení od spouštěcího kódu (krok 2-1)
> - Vykreslení zobrazení pomocí šablony stránky (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2-1: Refaktorovat projekt na podporu dalšího rozvoje

V kódu vytvořeném šablonou "Blank Flask Web Project" máte jeden *soubor app.py,* který obsahuje spouštěcí kód vedle jednoho zobrazení. Chcete-li umožnit další vývoj aplikace s více zobrazeními a šablonami, je nejlepší tyto obavy oddělit.

1. Ve složce projektu vytvořte `HelloFlask` složku aplikace s názvem (klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **Přidat** > **novou složku**.)

2. Ve složce *HelloFlask* vytvořte soubor s názvem * \_ \_init\_\_.py* s následujícím obsahem, který vytvoří `Flask` instanci a načte zobrazení aplikace (vytvořená v dalším kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. Ve složce *HelloFlask* vytvořte soubor s názvem *views.py* s následujícím obsahem. Název *views.py* je důležitý, `import HelloFlask.views` protože jste použili v rámci * \_ \_init\_\_.py*; pokud se názvy neshodují, zobrazí se chyba za běhu.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Kromě přejmenování funkce a trasy `home`do aplikace obsahuje tento kód kód vykreslování stránky z *app.py* a `app` importuje objekt, který je deklarován v * \_ \_init\_\_.py*.

4. Vytvořte podsložku v *HelloFlask* s názvem *šablony*, která zůstává prázdná pro tuto chvíli.

5. V kořenové složce projektu přejmenujte *app.py* na *runserver.py*a změřte obsah na následující kód:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. Struktura projektu by měla vypadat takto:

    ![Struktura projektu po refaktoringu kódu](media/flask/step02-project-structure.png)

7. Vyberte **Možnost Ladění** > **zahájit ladění** **(F5)** nebo pomocí tlačítka **Webovéserver** na panelu nástrojů (prohlížeč, který se může lišit) spustit aplikaci a otevřít prohlížeč. Vyzkoušejte trasy adres URL / a /home.

8. Můžete také nastavit zarážky v různých částech kódu a restartujte aplikaci postupujte podle pořadí spuštění. Například nastavte zarážku na prvních řádcích *runserver.py* a *HelloFlask\_* `return "Hello Flask!"` init_*.py*a na řádku v *views.py*. Pak restartujte aplikaci (**Ladění** > **Restart**, **Ctrl**+**F5**, nebo toolbar tlačítko je uvedeno níže) a krok ování **(F10)** kód, nebo spustit z každé zarážky pomocí **F5**.

    ![Tlačítko Restartovat na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

9. Až budete hotovi, zastavte aplikaci.

### <a name="commit-to-source-control"></a>Potvrzení správy zdrojového kódu

Vzhledem k tomu, že jste provedli změny v kódu a úspěšně jste je otestovali, je nyní skvělý čas zkontrolovat a potvrdit změny správy zdrojového kódu. Pozdější kroky v tomto kurzu připomenout vhodné časy potvrdit řízení zdrojového kódu znovu a odkazovat se zpět do této části.

1. Vyberte tlačítko změny v dolní části sady Visual Studio (zakroužkované níže), které přejde do **Průzkumníka týmu**.

    ![Tlačítko Změny správy zdrojového kódu na stavovém řádku sady Visual Studio](media/flask/step02-source-control-changes-button.png)

1. V **Průzkumníkovi týmu**zadejte zprávu o potvrzení, například Refaktorovat kód, a vyberte **Potvrdit vše**. Po dokončení revize se zobrazí **zpráva, že \<> hash potvrzení vytvořena místně. Synchronizujte a sdílejte změny se serverem.** Pokud chcete změny do vzdáleného úložiště vysunout, vyberte **Synchronizovat**a pak v části **Odchozí potvrzení**vyberte **Nabízená** . Před odesláním na vzdálenou poštu můžete také akumulovat více místních potvrzení.

    ![Nabízené revize do vzdáleného prostoru v Průzkumníkovi týmu](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Otázka: Jak často by se měl člověk zavázat ke směřovat zdrojové zdroje?

Odpověď: Potvrzení změn do správy zdrojového kódu vytvoří záznam v protokolu změn a bod, ke kterému můžete v případě potřeby vrátit úložiště. Každý závazek lze také prozkoumat pro své konkrétní změny. Vzhledem k tomu, že revize v Gitu jsou levné, je lepší provést časté revize, než hromadit větší počet změn do jednoho potvrzení. Je zřejmé, že není nutné pověřit každou malou změnu jednotlivých souborů. Obvykle provedete revizi při přidávání funkce, změně struktury, jako jste to udělali v tomto kroku, nebo provedete refaktoring kódu. Také se poraďte s ostatními ve vašem týmu o rozlišovací schopnost revizí, které fungují nejlépe pro každého.

Jak často se odevzdáváte a jak často odevzdání do vzdáleného úložiště vysunete, jsou dvě různé obavy. Můžete akumulovat více revizí v místním úložišti před jejich odesláním do vzdáleného úložiště. Opět platí, jak často potvrdíte závisí na tom, jak váš tým chce spravovat úložiště.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2-2: Vykreslení stránky pomocí šablony

Funkce, `home` kterou dosud máte v *views.py* generuje nic víc než odpověď HTTP ve formátu prostého textu pro stránku. Nicméně, většina reálných webových stránek, reagovat s bohatými HTML stránky, které často obsahují živá data. Ve skutečnosti primárnídůvod pro definování zobrazení pomocí funkce je generovat obsah dynamicky.

Vzhledem k tomu, že vrácená hodnota pro zobrazení je pouze řetězec, můžete vytvořit libovolný kód HTML, který se vám líbí v řetězci, pomocí dynamického obsahu. Protože je však nejlepší oddělit značky od dat, je mnohem lepší umístit značky do šablony a zachovat data v kódu.

1. Pro začátek upravte *views.py* tak, aby obsahovala následující kód, který používá pro stránku vsazený kód HTML s určitým dynamickým obsahem:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Spusťte aplikaci a několikrát aktualizujte stránku, abyste viděli, že se aktualizuje datum a čas. Až budete hotovi, zastavte aplikaci.

1. Chcete-li převést vykreslování stránky na *templates* použití šablony, vytvořte soubor `{{ content }}` s názvem *index.html* ve složce šablon s následujícím obsahem, kde je zástupný symbol nebo náhradní token (nazývaný také *proměnná šablony),* pro který zadáte hodnotu v kódu:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Upravte `home` funkci, `render_template` která se má použít k načtení šablony, a zajistěte hodnotu pro "obsah", která se provádí pomocí pojmenovaného argumentu odpovídajícího názvu zástupného symbolu. Flask automaticky vyhledá šablony ve složce *šablony,* takže cesta k šabloně je relativní k této složce:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Spusťte aplikaci zobrazit výsledky a pozoruji, `content` že vsazené HTML v hodnotě není vykreslen *jako* HTML, protože šablonovací modul (Jinja) automaticky unikne html obsahu. Automatické úniky zabraňují náhodným chybám při injektážním útokům: vývojáři často shromažďují vstupy z jedné stránky a používají jej jako hodnotu v jiné prostředcích prostřednictvím zástupného symbolu šablony. Escapování také slouží jako připomínka, že je opět nejlepší, aby HTML z kódu.

    Proto zkontrolujte *šablony\index.html* tak, aby obsahovaly odlišné zástupné symboly pro každou část dat v rámci značky:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Poté aktualizujte funkci a `home` zadejte hodnoty pro všechny zástupné symboly:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Spusťte aplikaci znovu, abyste viděli správně vykreslený výstup.

    ![Spuštění aplikace pomocí šablony](media/flask/step02-result.png)

1. Potvrďte změny do správy zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v [kroku 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Musí být šablony stránek v samostatném souboru?

Odpověď: Ačkoli jsou šablony obvykle udržovány v samostatných souborech HTML, můžete také použít vložkou šablonu. Použití samostatného souboru se však doporučuje zachovat čisté oddělení mezi značky a kód.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: Musí šablony používat příponu .html?

Odpověď: Přípona *HTML* pro soubory šablon stránky je zcela volitelná, protože v prvním argumentu k `render_template` funkci vždy identifikujete přesnou relativní cestu k souboru. Visual Studio (a další editory) však obvykle poskytují funkce, jako je dokončení kódu a zbarvení syntaxe se soubory *.html,* což převažuje nad skutečností, že šablony stránek nejsou striktně HTML.

Ve skutečnosti při práci s projektem Flask Visual Studio automaticky detekuje, kdy soubor HTML, který upravujete, je ve skutečnosti šablona Flask a poskytuje určité funkce automatického dokončování. Když například začnete psát komentář šablony stránky `{#`Flask , visual `#}` studio vám automaticky poskytne závěrečné znaky. Příkazy **Výběr poznámek** a **Odkomentovat výběr** (v nabídce **Upravit** > **upřesnit** a na panelu nástrojů) také používají komentáře šablony místo komentářů HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Otázka: Mohou být šablony uspořádány do dalších podsložek?

Odpověď: Ano, můžete použít podsložky a potom odkazovat na `render_template`relativní cestu pod *šablonami* v volání . To je skvělý způsob, jak efektivně vytvořit jmenné prostory pro šablony.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluhování statických souborů, přidávání stránek a používání dědičnosti šablony](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Úvodní příručka flak - vykreslovací šablony](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-baňka](https://github.com/Microsoft/python-sample-vs-learning-flask)
