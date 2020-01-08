---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 2, zobrazení a šablony
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, konkrétně postup vytvoření aplikace a používání zobrazení a šablony.
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
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2020
ms.locfileid: "75678958"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Flask pomocí zobrazení a šablony

**Předchozí krok: [vytvářet řešení a projektu sady Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Máte z kroku 1 tohoto kurzu je aplikace Flask pomocí jedné stránce a veškerý kód v jednom souboru. Povolit pro budoucí vývoj, je nejlepší Refaktorovat kód a vytvořit strukturu pro stránku šablony. Zejména budete chtít oddělují kód pro zobrazení aplikace od jiné aspekty spuštění kódu.

V tomto kroku se nyní dozvíte, jak:

> [!div class="checklist"]
> - Refaktorování kódu aplikace k oddělení od spuštění kódu zobrazení (krok 2 - 1)
> - Vykreslení zobrazení pomocí šablony stránky (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2-1: Refaktorovat projektu pro podporu dalšího vývoje aplikací

V kód vytvořený pomocí šablony "Prázdné Flask webového projektu", máte jediný *app.py* soubor, který obsahuje spouštěcí kód společně s jedním zobrazením. Povolit pro další vývoj aplikace s více zobrazení a šablony, je vhodné oddělit tyto problémy.

1. Ve složce projektu, vytvořte složku aplikace s názvem `HelloFlask` (klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **přidat** > **novou složku** .)

2. V *HelloFlask* složce vytvořte soubor s názvem  *\_ \_init\_\_.py* s použitím následujícího obsahu, které vytvoří `Flask` instance a načte zobrazení aplikace (vytvořený v dalším kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. V *HelloFlask* složce vytvořte soubor s názvem *views.py* s následujícím obsahem. Název *views.py* je důležité, protože jste použili `import HelloFlask.views` v rámci  *\_ \_init\_\_.py*; zobrazí se vám Chyba za běhu Pokud názvy se neshodují.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Kromě přejmenování funkce a tras do `home`, tento kód obsahuje kód pro vykreslování stránky z *app.py* a importuje `app` objekt, který je deklarován v  *\_ \_init\_\_.py*.

4. Vytvořte podsložku v *HelloFlask* s názvem *šablony*, které zůstávají prázdné i nyní.

5. V kořenové složce projektu, přejmenujte *app.py* k *runserver.py*a ujistěte se, obsah následujícím kódem:

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

6. Strukturu projektu by měl vypadat jako na následujícím obrázku:

    ![Struktura projektu po refaktorování kódu](media/flask/step02-project-structure.png)

7. Vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů (prohlížeči najdete v květnu Spusťte aplikaci a otevřít prohlížeč lišit). Zkuste oba / a/home tras adresy URL.

8. Můžete také nastavit zarážky na různé části kódu a restartujte aplikaci rozhodování o pořadí spouštění. Například nastavte zarážku na první řádky *runserver.py* a *HelloFlask\_* init_ *.py*a na `return "Hello Flask!"` řádku v *views.py*. Restartujte aplikaci (**ladění** > **restartovat**, **Ctrl**+**F5**, nebo tlačítko panelu nástrojů je uvedeno níže) a Projděte skrze (**F10**) kód nebo spustit z každého zarážky pomocí **F5**.

    ![Restartujte na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

9. Jakmile budete hotovi, zastavte aplikaci.

### <a name="commit-to-source-control"></a>Potvrzení změn do správy zdrojového kódu

Protože jste provedli změny kódu a je otestovali úspěšně, teď je vhodná doba ke kontrole a potvrzení provedených změn do správy zdrojového kódu. Pozdější kroky v tomto kurzu vás upozorní na vhodných chvílích se znovu zapsat do správy zdrojového kódu a vrátit zpět do této části.

1. Vyberte tlačítko změn v dolní části sady Visual Studio (v kruhu níže), která přejde na **Team Exploreru**.

    ![Tlačítka změny správy zdrojového kódu ve stavovém řádku sady Visual Studio](media/flask/step02-source-control-changes-button.png)

1. V **Team Exploreru**, zadejte zprávu potvrzení jako "Refaktorujte kód" a vyberte **Potvrdit vše**. Po dokončení potvrzení se zobrazí **hodnota hash \<potvrzení zprávy > vytvořena místně. Synchronizace pro sdílení změn se serverem.** Pokud chcete zapsat změny do vzdáleného úložiště, vyberte **synchronizace**a pak vyberte **nabízených** pod **odchozí potvrzení změn**. Můžete také shromažďovat více místních potvrzení změn před doručením (push) Vzdálená.

    ![Vložit potvrzení změn do vzdáleného v Průzkumníku týmových projektů](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Otázka: Jak často by měla jedna potvrzení změn do správy zdrojového kódu?

Odpověď: Potvrzení změn do správy zdrojového kódu vytvoří záznam v protokolu změn a bod na které můžete se vrátit úložiště v případě potřeby. Každé potvrzení se dají prozkoumat také jeho konkrétní změny. Vzhledem k tomu potvrzení změn v Gitu cenově dostupné, je lepší časté potvrzení změn, než se shromažďování většího počtu změn do jediného potvrzení změn. Je zřejmé není nutné potvrdit každou malou změnu do jednotlivých souborů. Obvykle provedete potvrzení při přidávání funkcí, změna struktury, jako jste v tomto kroku nebo provést některé refaktoringu kódu. Také zkontrolujte s ostatními ve vašem týmu pro členitost potvrzení změn, která nejlépe vyhovuje všem uživatelům.

Jak často potvrzení a jak často potvrzení změn vložíte do vzdáleného úložiště jsou dvě různé aspekty. Můžete shromažďovat několik potvrzení změn v místním úložišti před nahráním do vzdáleného úložiště. Jak často potvrzení znovu, závisí na jak váš tým chce, aby se pro správu úložiště.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2 – 2: použití šablony k vykreslení stránky

`home` Funkce, která jste dosud v *views.py* generuje nic jiného než prostého textu odpovědi HTTP pro stránky. Většina skutečných webové stránky, ale odpovědět bohaté stránky HTML, které často zahrnují živá data. Primární z důvodu definování zobrazení pomocí funkce je ve skutečnosti dynamicky generovat obsah.

Protože vrácená hodnota pro zobrazení je právě řetězec, můžete také vytvořit veškeré kódování HTML, který chcete v rámci řetězce, pomocí dynamického obsahu. Protože je nejlepší k oddělení od data značek, je však mnohem lepší umístěte kód v šabloně a ponechat data v kódu.

1. Pokud začínáte, upravit *views.py* tak, aby obsahovala následující kód, který používá vložené HTML stránky s některé dynamického obsahu:

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

1. Spusťte aplikaci a aktualizujte stránku několikrát zobrazíte, že se aktualizuje data a času. Jakmile budete hotovi, zastavte aplikaci.

1. Převést vykreslování části stránky chcete použít šablonu, vytvořte soubor s názvem *index.html* v *šablony* složka s následujícím obsahem, kde `{{ content }}` je zástupný symbol nebo nahrazení tokenu (také volá se *proměnnou šablony*) u kterého zadáte hodnotu do kódu:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Upravit `home` použitá funkce `render_template` k načtení šablony a zadat hodnotu "obsah", která se provádí pomocí pojmenovaný argument, který odpovídá názvu zástupný symbol. Flask automaticky vyhledá šablony v *šablony* složku, tak cestu k šabloně je relativní vzhledem k této složce:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Spuštění aplikace se ve výsledcích a zda se zobrazila zpráva vložené HTML v `content` hodnotu nevykreslí *jako* HTML, protože šablonování stroje (šablonovacím systémem) automaticky řídící obsah ve formátu HTML. Automatické uvození zabrání náhodnému ohrožení zabezpečení, útoky prostřednictvím injektáže: vývojáři často shromažďovat vstup z jedné stránky a použít jako hodnotu do jiné prostřednictvím šablony zástupný symbol. Uvozovací znaky slouží taky jako připomenutí, že je znovu nejlepší mít HTML z kódu.

    Odpovídajícím způsobem, zkontrolujte *templates\index.html* tak, aby obsahovala distinct zástupné symboly pro jednotlivá data v rámci značky:

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

    Pak aktualizujte `home` funkce k poskytnutí hodnot pro všechny zástupné symboly:

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

1. Spusťte aplikaci znovu, abyste viděli správně vykresleného výstupu.

    ![Spuštěné aplikace pomocí šablony](media/flask/step02-result.png)

1. Potvrďte změny do správy zdrojového kódu a aktualizovat vaše vzdálené úložiště, v případě potřeby, jak je popsáno v části [krok 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Šablony musí být v samostatném souboru?

Odpověď: I když šablony jsou obvykle spravované do samostatných souborů HTML, můžete také vložené šablony. Použití samostatného souboru se doporučuje, ale udržovat čisté oddělení mezi značek a kódu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: Musíte šablony používají příponu souboru HTML?

Odpověď: *.html* rozšíření pro stránkovací soubory šablony je naprosto volitelné, protože vždy identifikovat přesné relativní cesta k souboru v první argument `render_template` funkce. Ale sady Visual Studio (a ostatní editory) obvykle poskytují funkce, jako je dokončení a syntaxe zabarvení kódu s *.html* soubory, které převažuje skutečnost, že stránka šablony nejsou nezbytně HTML.

Ve skutečnosti když pracujete s projektem Flask, Visual Studio automaticky rozpozná, pokud soubor HTML, který upravujete je ve skutečnosti šablon Flask a poskytuje některé funkce automatického dokončování. Například když začnete psát Flask stránku šablony komentář, `{#`, Visual Studio automaticky poskytuje uzavírací `#}` znaků. **Zakomentovat výběr** a **Odkomentovat výběr** příkazy (na **upravit** > **Upřesnit** nabídky a na panelu nástrojů) komentáře k šabloně používají taky místo komentáře HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Otázka: Je šablony možné uspořádat do podsložky další?

Odpověď: Ano, můžete použít podsložky a potom použijte relativní cesta pod *šablony* ve voláních `render_template`. To je skvělý způsob, jak efektivně vytvořit obory názvů pro šablony.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Rychlý start Flask – vykreslení šablony](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
