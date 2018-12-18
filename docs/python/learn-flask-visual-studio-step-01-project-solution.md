---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 1, Flask základy
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, včetně požadavků, Git a virtuální prostředí.
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
ms.openlocfilehash: 0603c1b8dcabc37631c7a52e11cfa964331010d8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066636"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Kurz: Začínáme s architektury Flask webů v sadě Visual Studio

[Flask](http://flask.pocoo.org/) je zjednodušené architektura Python pro webové aplikace, která poskytuje základy pro směrování adres URL a vykreslování části stránky.

Flask se nazývá "micro" framework, protože ho přímo neposkytuje funkce, jako je ověřování formuláře, abstrakce databáze, ověřování a tak dále. Tyto funkce jsou k dispozici místo toho speciální balíčky Python Flask volá *rozšíření*. Rozšíření bez problémů integrovat Flask tak, aby se zobrazují, jakoby jsou součástí Flask, samotného. Například Flask sám neposkytuje modulu šablon stránky. Ukázka poskytuje rozšíření jako šablonovacím systémem a Jade, jak je ukázáno v tomto kurzu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Flask v úložišti Git pomocí šablony "Prázdné Flask webového projektu" (krok 1)
> - Vytvoření aplikace Flask pomocí jedné stránce a vykreslit tuto stránku pomocí šablony (krok 2)
> - Doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti (krok 3)
> - Použití šablony webového projektu Flask k vytvoření aplikace s více stránkami a responzivní návrh (krok 4)
> - Šablona Polls – webový projekt Flask slouží k vytvoření cyklického dotazování aplikaci, která bude celá řada možností úložišť (úložiště Azure, MongoDB nebo paměť).

V průběhu těchto kroků vytvořte jedno řešení sady Visual Studio, který obsahuje tři samostatné projekty. Vytvoření projektu pomocí jiné šablony projektu Flask, které jsou součástí sady Visual Studio. Udržováním projekty ve stejném řešení, lze snadno přepínat vpřed a zpět mezi různé soubory pro porovnání.

> [!Note]
> V tomto kurzu se liší od [rychlý start Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) v tom, že další informace o Flask i jak používat různé Flask šablony projektů, které poskytují rozsáhlejší počáteční bod pro svoje vlastní projekty. Například šablony projektu automaticky instalovat balíček Flask při vytváření projektu, ale můžete balíček nainstalovat ručně, jak je znázorněno v tomto rychlém startu.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 na Windows s následujícími možnostmi:
  - **Vývoj v jazyce Python** pracovního vytížení (**úlohy** kartu v instalačním programu). Pokyny najdete v tématu [podpora instalace Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **rozšíření GitHub pro Visual Studio** na **jednotlivé komponenty** kartu **kódu nástroje**.

Šablony projektu Flask jsou součástí všech předchozích verzích nástroje Python Tools for Visual Studio, i když podrobnosti se mohou lišit co je popsáno v tomto kurzu.

Vývoj v jazyce Python se nepodporuje v současné době v sadě Visual Studio pro Mac. Na Mac a Linux, použijte [rozšíření Pythonu ve Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: vytvoření projektu sady Visual Studio a řešení

1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**, vyhledejte "Flask" a vyberte **prázdný webový projekt Flask**  šablony. (Šablona také najdete v části **Python** > **webové** v seznamu vlevo.)

    ![Dialogové okno nového projektu v sadě Visual Studio pro prázdný webový projekt Flask](media/flask/step01-new-blank-project.png)

1. V polích v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozím obrázku) a pak vyberte **OK**:

    - **Název**: nastavení názvu projektu Visual Studia pro **BasicProject**. Tento název se také používá pro projekt Flask.
    - **Umístění**: určení umístění, ve kterém chcete vytvořit řešení sady Visual Studio a projekt.
    - **Název řešení**: nastavte na **LearningFlask**, která je vhodná pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: ponechejte nastavenou (výchozí).
    - **Vytvoření nového úložiště Git**: tuto možnost použijte (což je vymazat ve výchozím nastavení) tak, aby Visual Studio vytvoří místní úložiště Git, při vytváření řešení. Pokud nevidíte tuto možnost, spusťte instalační program sady Visual Studio 2017 a přidejte **Git pro Windows** a **rozšíření GitHub pro Visual Studio** na **jednotlivé komponenty** kartu v části **kódu nástroje**.

1. Za okamžik, Visual Studio zobrazí dialogové okno o tom, že **tento projekt vyžaduje externí balíčky** (viz dole). Tento dialog se zobrazuje, protože obsahuje šablony *souboru requirements.txt* souboru odkazující na nejnovější balíček 1.x Flask. (Vyberte **zobrazit požadované balíčky** zobrazíte přesné závislosti.)

    ![Příkazový řádek o tom, že, že projekt vyžaduje externí balíčky.](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Vyberte možnost **nainstaluji je sám**. Můžete vytvořit virtuální prostředí krátce a ujistěte se, že je vyloučena ze správy zdrojového kódu. (Prostředí vždy možné vytvářet z *souboru requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Zkontrolujte ovládací prvky Git a publikujte do vzdáleného úložiště

Protože jste vybrali **vytvořit nové úložiště Git** v **nový projekt** dialogového okna, projekt již byla potvrzena do místní správy zdrojového kódu ihned poté, co byl dokončen proces vytváření. V tomto kroku měli seznámit s ovládacími prvky Git sady Visual Studio a **Team Exploreru** okno, ve kterém pracujete se správou zdrojového kódu.

1. Prozkoumejte Git ovládacích prvků v pravém dolním rohu sady Visual Studio hlavního okna. Zleva doprava tyto ovládací prvky zobrazují nevložená potvrzení, nepotvrzené změny, názvu úložiště a aktuální větve:

    ![Git ovládacích prvků v okně aplikace Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Pokud nevyberete **vytvořit nové úložiště Git** v **nový projekt** dialogového okna, ovládací prvky Git se zobrazují pouze **přidat do správy zdrojových kódů** příkaz, který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v sadě Visual Studio, pokud není vytvořené úložiště](media/tutorials-common/step01-git-add-to-source-control.png)

1. Vyberte tlačítko změn a sady Visual Studio otevře jeho **Team Exploreru** na okno **změny** stránky. Vzhledem k tomu, že nově vytvořený projekt je už potvrzená do správy zdrojového kódu automaticky, se nezobrazí všechny čekající změny.

    ![Okno Průzkumníka týmu na stránce změny](media/flask/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio, klikněte na tlačítko nevložená potvrzení (na šipku nahoru s **2**) otevřete **synchronizace** stránku **Team Exploreru**. Protože máte místní úložiště, na stránce poskytuje jednoduché možnosti publikovat úložiště na jiné vzdálené úložiště.

    ![Team Explorer zobrazující k dispozici Git úložiště možnosti okna pro správu zdrojového kódu](media/flask/step01-team-explorer.png)

    Můžete zvolit služby, podle toho, která chcete pro svoje vlastní projekty. Používání Githubu, kde je hotová ukázka kódu pro tento kurz udržována v tomto kurzu se dozvíte [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) úložiště.

1. Při výběru některého **publikovat** ovládací prvky, **Team Exploreru** vás vyzve k zadání další informace. Například při publikování vzorku pro účely tohoto kurzu je název samotného úložiště musel vytvořit při první, v takovém případě **vložit do vzdáleného úložiště** byla použita možnost s adresou URL v úložišti.

    ![Okno Průzkumníka týmu při vkládání do existující vzdáleného úložiště](media/flask/step01-push-to-github.png)

    Pokud nemáte existující úložiště, **publikování ve službě GitHub** a **odeslat do Azure DevOps** možnosti umožňují vytvořit přímo z Visual Studia.

1. Při práci kroky v tomto kurzu si zvyknout pravidelně používání ovládacích prvků v sadě Visual Studio k potvrzení a nasdílení změn změny. V tomto kurzu upozorňuje na vhodných míst.

> [!Tip]
> Rychle přejít v rámci **Team Exploreru**, vyberte záhlaví (, který čte **změny** nebo **Push** na obrázcích výše) Chcete-li zobrazit místní nabídku stránky k dispozici.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: Za prvé, od samého začátku pomocí správy zdrojového kódu, zejména pokud používáte vzdálené úložiště, poskytuje zálohování mimo pracoviště regulární vašeho projektu. Na rozdíl od jenom na údržbu projektu místního systému souborů, správy zdrojového kódu také poskytuje kompletní změnu historie a snadno možnost obnovit jeden soubor nebo celého projektu do předchozího stavu. Který historii změn pomáhá určit, proč regrese (neúspěšné testy). Kromě toho je nezbytné, najde víc lidí práci na projektu, jak spravuje přepíše a poskytuje řešení konfliktů správy zdrojového kódu. A konečně správy zdrojového kódu, který je v podstatě formu automatizace, nastaví je dobře pro automatizaci sestavení, testování a produktu release management. Ve skutečnosti je prvním krokem při používání DevOps pro projekt, a protože překážky položky jsou tak nízké, ve skutečnosti neexistuje žádný důvod není použití správy zdrojového kódu od začátku.

Další informace o správy zdrojového kódu jako automatizaci, naleznete v tématu [zdroj pravdy: z úložišť Role v DevOps](https://msdn.microsoft.com/magazine/mt763232), článek v MSDN Magazine napsané pro mobilní aplikace, které platí také pro webové aplikace.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Můžu zabránit v sadě Visual Studio automaticky potvrzení nového projektu?

Odpověď: Ano. Chcete-li zakázat režim automatického potvrzení, přejděte na **nastavení** stránku **Průzkumník týmových projektů**vyberte **Git** > **globální nastavení**, zrušte zaškrtnutí políčka možnost s názvem **potvrzení změn po sloučení standardně**a pak vyberte **aktualizace**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1 – 3: vytvoření virtuálního prostředí a vyloučit ze správy zdrojového kódu

Teď, když nakonfigurujete pro svůj projekt správy zdrojového kódu, můžete vytvořit virtuální prostředí potřebné balíčky Flask, které projekt vyžaduje. Pak můžete použít **Team Exploreru** vyloučit složku prostředí ze správy zdrojového kódu.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prostředí Pythonu** uzel a vyberte možnost **přidat virtuální prostředí**.

    ![Přidat virtuální prostředí příkaz v okně Průzkumník řešení](media/flask/step01-add-virtual-environment-command.png)

1. **Přidat virtuální prostředí** dialogového okna se zobrazí se zpráva s oznámením **našli jsme soubor requirements.txt.** Tato zpráva znamená, že Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Přidat virtuální prostředí dialogu se zprávou, soubor requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Vyberte **vytvořit** přijměte výchozí hodnoty. (Můžete změnit název virtuálního prostředí, pokud chcete, která právě změní název jejích podsložkách ale `env` je standardní konvence.)

1. Souhlas s oprávněními správce, pokud se zobrazí výzva, pak buďte prosím trpěliví. za pár minut, zatímco Visual Studio stáhne a nainstaluje balíčky, které pro Flask a jeho závislosti znamená, že rozšíření o tisíc souborů ve více než 100 podsložky. Zobrazí se průběh v sadě Visual Studio **výstup** okna. Zatímco čekáte, uvažoval následující části otázku. Můžete také zobrazit popis Flask v závislosti na [Flask instalace](http://flask.pocoo.org/docs/1.0/installation/#installation) stránky (flask.pcocoo.org).

1. V ovládacích prvcích Gitu služby Visual Studio (na stavový řádek), vyberte indikátor změn (, která zobrazuje **99&#42;**) otevře **změny** stránku **Team Exploreru**.

    Vytváří se virtuální prostředí převést do režimu na stovkách změny, ale není nutné zahrnout některý z nich ve správě zdrojového kódu, protože jste (nebo každý jinde klonování projektu) můžete vždy znovu vytvořit prostředí z *souboru requirements.txt*.

    Vyloučit virtuální prostředí, klikněte pravým tlačítkem myši **env** a pak zvolte položku **ignorovat tyto místní položky**.

    ![Ignoruje se do virtuálního prostředí v změny správy zdrojového kódu](media/flask/step01-ignore-local-items.png)

1. Po vyloučení virtuální prostředí, jsou jenom zbývající změny do souboru projektu a *.gitignore*. *.Gitignore* soubor obsahuje neplatnou položku přidání ke složce virtuálního prostředí. Dvakrát kliknete na soubor zobrazíte rozdíl

1. Zadejte zprávu potvrzení a vyberte **Potvrdit vše** tlačítko a potom nasdílejte potvrzení změn do vzdáleného úložiště, pokud chcete, můžete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: Proč mám chcete vytvořit virtuální prostředí?

Odpověď: Virtuální prostředí je skvělý způsob, jak izolovat přesné závislostí aplikace. Tato izolace zabrání konfliktům v rámci globálního prostředí Pythonu a pomáhá testování a spolupráci. V průběhu času při vývoji aplikace, je vždy přenést v mnoha užitečné balíčky Pythonu. Udržováním balíčků ve virtuálním prostředí specifické pro projekt, můžete snadno aktualizovat projektu *souboru requirements.txt* soubor, který popisuje prostředí, který je zahrnut ve správě zdrojového kódu. Když projekt je zkopírován do jakékoli jiné počítače, včetně serverů sestavení, nasazení serverů a jiných vývojových počítačích je snadné vytvořit znovu prostředí pouze pomocí *souboru requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace najdete v tématu [použít virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Jak odebrat virtuální prostředí, které už je potvrzená do správy zdrojových kódů?

Odpověď: Především upravte vaše *.gitignore* souborů k vyloučení složky: najít oddíl obsahující komentáře `# Python Tools for Visual Studio (PTVS)` a přidejte nový řádek ke složce virtuálního prostředí, jako `/BasicProject/env`. (Vzhledem k tomu, že sada Visual Studio nezobrazuje souboru v **Průzkumníka řešení**, otevřete ho pomocí přímo **souboru** > **otevřete**  >   **Soubor** příkazu nabídky. Můžete také otevřít soubor z **Team Exploreru**: na **nastavení** stránce **nastavení úložiště**, přejděte na stránku **ignorovat soubory atributůanástroje** a potom vyberte **upravit** odkaz **.gitignore**.)

Za druhé, otevřete okno příkazového řádku, přejděte do složky, jako je *BasicProject* , která obsahuje složky virtuální prostředí jako *env*a spusťte `git rm -r env`. Tyto změny potvrdit z příkazového řádku (`git commit -m 'Remove venv'`), případně z **změny** stránce **Team Exploreru**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1 – 4: prozkoumání často používaný kód

1. Po vytvoření projektu dokončí, najdete v článku řešení a projekt **Průzkumníka řešení**, pokud projekt obsahuje pouze dva soubory *app.py* a *souboru requirements.txt*:

    ![V Průzkumníku řešení prázdné soubory projektu Flask](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak bylo uvedeno dříve, *souboru requirements.txt* soubor určuje závislost balíčku Flask. Přítomnost tento soubor je, co vás zve k vytvoření virtuálního prostředí, při prvním vytvoření projektu.

1. Jedné *app.py* soubor obsahuje tři části. Nejprve je `import` příkaz pro Flask, vytvoření instance `Flask` třídu, která je přiřazená k proměnné `app`a poté přiřazováním `wsgi_app` proměnné (což je užitečné při nasazování webového hostitele, ale nepoužívá se v současné době):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druhá část, na konci souboru, je hodně nepovinné kód, který se spustí vývojový server Flask konkrétního hostitele a port hodnotami z proměnné prostředí (jako výchozí se použije localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Je třetí krátký bitového kódu, který se přiřadí adresu URL funkce směrování, to znamená, že funkce poskytuje zdroje podle adresy URL. Definování tras pomocí Flask společnosti `@app.route` dekoratér, jehož argumentem je relativní adresa URL z kořenového adresáře webu. Jak je vidět v kódu, vrátí funkce tady jenom textový řetězec, který je dostatečná pro prohlížeče k vykreslení. V následujících kroků vykreslování bohatší stránek HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-name-argument-to-the-flask-class"></a>Otázka: Co je účelem __název__ argument třídy Flask?

Odpověď: Argument je název modulu nebo balíček aplikace a zjistí Flask, kde má hledat šablony, statické soubory a další prostředky, které patří k aplikaci. Pro aplikace, které jsou obsaženy v jednom modulu `__name__` je vždy správnou hodnotu. Je také důležité pro rozšíření, která vyžadují informace o ladění. Další informace, a další argumenty, najdete v článku [dokumentace třídy Flask](http://flask.pocoo.org/docs/1.0/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Otázka: Je funkce mít více než jeden dekoratér trasy?

Odpověď: Ano, můžete použít tolik dekoratéry, pokud má stejnou funkci slouží několik tras. Chcete-li například použít `hello` funkce pro obě "/" a "/ hello", použijte následující kód:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Otázka: Jak Flask funguje s proměnnou cesty adresy URL a parametry dotazu?

Odpověď: V trase, můžete označit všechny proměnné s `<variable_name>`, a Flask předá proměnná do funkce pomocí pojmenovaného argumentu. Proměnná může být část cesty adresy URL nebo v parametru dotazu. Například trasy ve formě `'/hello/<name>` generuje řetězcový argument volá `name` funkce a pomocí `?message=<msg>` v trase analyzuje zadaná hodnota pro "zpráva =" parametr dotazu a předává je do funkce v podobě `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Chcete-li změnit typ předpony proměnnou `int`, `float`, `path` (která přijímá lomítka od sebe odděluje názvy složek), a `uuid`. Podrobnosti najdete v tématu [pravidla proměnných](http://flask.pocoo.org/docs/1.0/quickstart/#variable-rules) v dokumentaci k Flask.

Parametry dotazu jsou také k dispozici prostřednictvím `request.args` vlastnost, konkrétně prostřednictvím `request.args.get` metody. Další informace najdete v tématu [žádost objekt](http://flask.pocoo.org/docs/1.0/quickstart/#the-request-object) v dokumentaci k Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: Může Visual Studio generovat soubor requirements.txt z virtuálního prostředí po instalaci dalších balíčků?

Odpověď: Ano. Rozbalte **prostředí Pythonu** uzel, klikněte pravým tlačítkem na virtuální prostředí a vyberte **generovat soubor requirements.txt** příkazu. Dobré jeho použití tohoto příkazu pravidelně jako můžete upravit prostředí a potvrzení se změní na *souboru requirements.txt* do správy zdrojového kódu společně s další změny kódu, které jsou závislé na příslušné prostředí. Pokud nastavení nepřetržité integrace na serveru sestavení byste měli vždy, když změníte prostředí generovat soubor a změn.

## <a name="step-1-5-run-the-project"></a>Krok 1 – 5: spuštění projektu

1. V sadě Visual Studio, vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů () prohlížeče, který se může lišit):

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Buď příkaz přiřadí náhodný port číslo portu proměnné prostředí a pak spustí `python app.py`. Kód spustí aplikaci pomocí tohoto portu v rámci vývojový server Flask společnosti. Pokud je zobrazeno v sadě Visual Studio **se nepovedlo spustit ladicí program** a zobrazí se zpráva o nutnosti žádný spouštěcí soubor, klikněte pravým tlačítkem na **app.py** v **Průzkumníka řešení** a vyberte  **Nastavit jako spouštěcí soubor**.

1. Při spuštění serveru, najdete v okně konzoly otevřete tuto zobrazí protokolu serveru. Visual Studio pak automaticky otevře v prohlížeči `http://localhost:<port>`, ve kterém by se zobrazit zpráva vykreslený `hello` funkce:

    ![Výchozí zobrazení projektu Flask](media/flask/step01-first-run-success.png)

1. Až budete hotovi, server zastavit ukončením okna konzoly nebo s použitím **ladění** > **Zastavit ladění** příkaz v sadě Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím nástrojů ladění příkazů nabídky a příkazy serveru v podnabídce projektu Pythonu?

Odpověď: navíc k **ladění** příkazů nabídky a tlačítka panelu nástrojů můžete spustit na serveru pomocí **Python** > **spuštění serveru** nebo **Python** > **server pro spuštění ladění** příkazy v místní nabídce projektu. Oba příkazy otevřete okno konzoly, ve kterém se zobrazí místní adresa URL (localhost:port) pro spuštěný server. Nicméně je nutné ručně otevřít prohlížeč s touto adresou URL a serverem ladění nespustí automaticky ladicího programu sady Visual Studio. Můžete připojit ladicí program ke spuštěnému procesu později, pokud chcete, pomocí **ladění** > **připojit k procesu** příkazu.

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základního projektu Flask obsahuje spuštění kódu a kódu stránky ve stejném souboru. Je vhodné oddělit tyto dva problémy a také oddělení kódu HTML a data pomocí šablon.

> [!div class="nextstepaction"]
> [Vytvoření aplikace Flask pomocí zobrazení a šablony](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Rychlý start Flask](http://flask.pocoo.org/docs/1.0/quickstart/) (flask.pocoo.org)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
