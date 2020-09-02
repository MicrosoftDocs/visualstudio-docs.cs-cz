---
title: Kurz k Přečtěte si kurz v aplikaci Visual Studio Step 2, zobrazení a šablony
titleSuffix: ''
description: Návod základů baněk v kontextu projektů aplikace Visual Studio, konkrétně kroky při vytváření aplikace a používání zobrazení a šablon.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89313741"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace v baňce se zobrazeními a šablonami stránek

**Předchozí krok: [Vytvoření projektu a řešení sady Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

To, co máte z kroku 1 tohoto kurzu, je aplikace v baňce s jednou stránkou a veškerým kódem v jednom souboru. Aby bylo umožněno budoucí vývoj, je vhodné kód Refaktorovat a vytvořit strukturu pro šablony stránky. Konkrétně je vhodné oddělit kód pro zobrazení aplikace z jiných aspektů, jako je kód při spuštění.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Refaktorujte kód aplikace a oddělte zobrazení od spouštěcího kódu (krok 2-1).
> - Vykreslení zobrazení pomocí šablony stránky (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2-1: refaktorace projektu pro podporu dalšího vývoje

V kódu vytvořeném šablonou "prázdný webový projekt" je k dispozici jeden soubor *App.py* , který obsahuje spouštěcí kód vedle jednoho zobrazení. Aby bylo možné další vývoj aplikace s více zobrazeními a šablonami, je vhodné tyto aspekty oddělit.

1. Ve složce projektu vytvořte složku aplikace s názvem (klikněte `HelloFlask` pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **Přidat**  >  **novou složku**.)

2. Ve složce *HelloFlask* vytvořte soubor s názvem * \_ \_ init \_ \_ . py* s následujícím obsahem, který vytvoří `Flask` instanci a načte zobrazení aplikace (vytvořené v dalším kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. Ve složce *HelloFlask* vytvořte soubor s názvem *views.py* s následujícím obsahem. Název *views.py* je důležitý, protože jste použili `import HelloFlask.views` v * \_ \_ init \_ \_ . py*; při běhu se zobrazí chyba, pokud se názvy neshodují.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Kromě přejmenování funkce a směrování na `home` , obsahuje tento kód kód vykreslování stránky z *App.py* a importuje `app` objekt deklarovaný v * \_ \_ init \_ \_ . py*.

4. Vytvoří podsložku v *HelloFlask* s názvem *Templates*, která teď zůstává prázdná.

5. V kořenové složce projektu přejmenujte *App.py* na *runserver.py*a nastavte obsah tak, aby odpovídal následujícímu kódu:

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

6. Struktura projektu by měla vypadat jako na následujícím obrázku:

    ![Struktura projektu po refaktoringu kódu](media/flask/step02-project-structure.png)

7. Vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo použijte tlačítko **webový server** na panelu nástrojů (prohlížeč, který vidíte, se může lišit) a spusťte aplikaci a otevřete prohlížeč. Vyzkoušejte trasy adresy URL/a/Home.

8. Můžete také nastavit zarážky v různých částech kódu a restartovat aplikaci, aby následovala za spouštěcí sekvenci. Například nastavte zarážku na prvních řádcích *runserver.py* a *HelloFlask \_ *init_*. py*a na `return "Hello Flask!"` řádku v *views.py*. Pak aplikaci znovu spusťte (**ladit**  >  **restart**, **CTRL** + **F5**nebo tlačítko panelu nástrojů zobrazené níže) a proveďte krok po (**F10**) kódu nebo spusťte z každé zarážky pomocí klávesy **F5**.

    ![Tlačítko restartovat na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

9. Až skončíte, zastavte aplikaci.

### <a name="commit-to-source-control"></a>Potvrdit do správy zdrojových kódů

Vzhledem k tomu, že jste provedli změny kódu a úspěšně jste je otestovali, nyní je vhodný čas ke kontrole a potvrzení změn ve správě zdrojových kódů. V dalších krocích v tomto kurzu se znovu přihlásíte ke správě zdrojových kódů a vrátíte se zpátky k této části.

1. Vyberte tlačítko změny podél dolní části sady Visual Studio (v kruhu níže), které přechází na **Team Explorer**.

    ![Tlačítko změny správy zdrojového kódu na stavovém řádku sady Visual Studio](media/flask/step02-source-control-changes-button.png)

1. V **Team Explorer**zadejte potvrzovací zprávu, jako je refaktoring Code, a vyberte **potvrdit vše**. Po dokončení potvrzení se zobrazí **potvrzení vytvoření zprávy v \<hash> místním počítači. Synchronizace pro sdílení změn se serverem.** Pokud chcete doručovat změny do vzdáleného úložiště, vyberte **synchronizovat**a potom v části **odchozí potvrzení**vyberte možnost **push** . Před odesláním do vzdáleného úložiště můžete také shromáždit několik místních potvrzení.

    ![Vložení potvrzení do vzdáleného úložiště v Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Otázka: jak často má být jeden potvrzení do správy zdrojového kódu?

Odpověď: potvrzení změn ve správě zdrojového kódu vytvoří záznam v protokolu změn a bod, na který můžete v případě potřeby obnovit úložiště. U každého potvrzení lze také prozkoumat konkrétní změny. Vzhledem k tomu, že potvrzení v Gitu jsou nákladná, je lepší provádět častá potvrzení změn, než je potřeba shromáždit větší počet změn do jediného potvrzení. Jasně není nutné potvrzovat každou malou změnu v jednotlivých souborech. Při přidávání funkce se obvykle provádí potvrzení změn struktury, jako jste provedli v tomto kroku, nebo když jste provedli nějaký refaktoring kódu. Také se poraďte s ostatními členy týmu, aby bylo možné členitost potvrzení, která fungují nejlépe pro každého.

Jak často provádíte potvrzení a jak často se přidávají potvrzení do vzdáleného úložiště, mají dva různé obavy. Před odesláním do vzdáleného úložiště můžete shromáždit několik potvrzení v místním úložišti. Znovu, jak často potvrzujete, závisí na tom, jak váš tým chce spravovat úložiště.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2-2: použití šablony k vykreslení stránky

`home`Funkce, kterou v *views.py* ještě máte, vygeneruje pro stránku nic větší než odpověď HTTP v podobě prostého textu. Většina skutečných webových stránek ale reaguje s bohatou stránkou HTML, která často zahrnuje živá data. Hlavním důvodem pro definování zobrazení pomocí funkce je skutečně generování obsahu dynamicky.

Vzhledem k tomu, že návratová hodnota zobrazení je pouze řetězec, můžete vytvořit libovolný HTML v rámci řetězce pomocí dynamického obsahu. Vzhledem k tomu, že je nejlepší oddělit značky z dat, je mnohem lepší umístit značku do šablony a zachovat data v kódu.

1. U starts upravte *views.py* tak, aby obsahovala následující kód, který používá vloženou HTML pro stránku s nějakým dynamickým obsahem:

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

1. Spusťte aplikaci a několikrát aktualizujte stránku, aby bylo vidět, že se datum a čas aktualizovala. Až skončíte, zastavte aplikaci.

1. Chcete-li převést vykreslování stránky na použití šablony, vytvořte soubor s názvem *index.html* ve složce *Templates* s následujícím obsahem, kde `{{ content }}` je zástupný symbol nebo token pro nahrazení (označovaný také jako *proměnná šablony*), pro který zadáte hodnotu v kódu:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Upravte `home` funkci tak, aby se použila `render_template` k načtení šablony, a zadejte hodnotu pro "obsah", která se provede pomocí pojmenovaného argumentu, který odpovídá názvu zástupného znaku. Baňka automaticky vyhledá šablony ve složce *šablony* , takže cesta k šabloně je relativní vzhledem k této složce:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Spusťte aplikaci, podívejte se na výsledky a sledujte, že vložený kód HTML v `content` hodnotě se nevykresluje *jako* HTML, protože modul šablonování (Jinja) automaticky řídí obsah HTML. Automatické uvozovací znaky zabraňují náhodným útokům prostřednictvím injektáže: vývojáři často shromažďují vstupy z jedné stránky a používají je jako hodnotu v jiné prostřednictvím zástupného symbolu šablony. Řídicí uvozovací znaky také slouží jako připomenutí, že je znovu vhodné zachovat kód HTML z kódu.

    Proto si přečtěte *templates\index.html* a v rámci značek pro každou část dat zajděte o různých zástupných symbolech:

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

    Pak aktualizujte `home` funkci tak, aby poskytovala hodnoty pro všechny zástupné symboly:

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

1. Spusťte aplikaci znovu, abyste viděli správně Vykreslený výstup.

    ![Spuštění aplikace pomocí šablony](media/flask/step02-result.png)

1. Potvrďte změny ve správě zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v části [krok 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Chcete, aby šablony stránky byly v samostatném souboru?

Odpověď: Přestože šablony jsou obvykle udržovány v samostatných souborech HTML, můžete také použít vloženou šablonu. Použití samostatného souboru je však doporučeno pro zachování čistého oddělení mezi značkami a kódem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: je třeba, aby šablony používaly příponu souboru. html?

Odpověď: přípona *. html* pro soubory šablony stránky je zcela volitelná, protože vždy identifikujete přesnou relativní cestu k souboru v prvním argumentu `render_template` funkce. Visual Studio (a další editory) ale obvykle poskytují funkce jako dokončování kódu a zabarvení syntaxe pomocí souborů *. html* , což převažuje na to, že šablony stránek nejsou striktně HTML.

Když pracujete s projektem v baňce, Visual Studio se automaticky detekuje, když soubor HTML, který upravujete, je šablonou baňky, a poskytuje určité automatické dokončování funkcí. Například když začnete psát komentář k šabloně stránky, aplikace `{#` Visual Studio automaticky poskytne ukončovací `#}` znaky. Příkazy pro výběr **Komentáře** a zrušení **Komentáře** (v nabídce **Upravit**  >  **Upřesnit** a na panelu nástrojů) také používají komentáře k šablonám namísto komentářů jazyka HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Otázka: je možné šablony uspořádat do dalších podsložek?

Odpověď: Ano, můžete použít podsložky a pak odkazovat na relativní cestu v části *šablony* v volání `render_template` . Je to skvělý způsob, jak efektivně vytvořit obory názvů pro vaše šablony.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluha statických souborů, přidávání stránek a použití dědičnosti šablon](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Rychlý Start k vygenerování baněk – šablony pro vykreslování](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (Flask.pocoo.org)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask)
