---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 1, Flask základy
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, včetně požadavků, Git a virtuální prostředí.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7707d993ac5fb6f73060d0f862c828e67c833872
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409835"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Kurz: Začínáme s architektury Flask webů v sadě Visual Studio

[Baňka](https://palletsprojects.com/p/flask/) je odlehčená architektura Pythonu pro webové aplikace, která poskytuje základní informace o směrování adres URL a vykreslování stránky.

Flask se nazývá "micro" framework, protože ho přímo neposkytuje funkce, jako je ověřování formuláře, abstrakce databáze, ověřování a tak dále. Tyto funkce jsou místo toho k dispozici speciálními balíčky Pythonu, které se nazývají *rozšíření*baněk. Rozšíření bez problémů integrovat Flask tak, aby se zobrazují, jakoby jsou součástí Flask, samotného. Například Flask sám neposkytuje modulu šablon stránky. Ukázka poskytuje rozšíření jako šablonovacím systémem a Jade, jak je ukázáno v tomto kurzu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Flask v úložišti Git pomocí šablony "Prázdné Flask webového projektu" (krok 1)
> - Vytvoření aplikace Flask pomocí jedné stránce a vykreslit tuto stránku pomocí šablony (krok 2)
> - Doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti (krok 3)
> - Použití šablony webového projektu Flask k vytvoření aplikace s více stránkami a responzivní návrh (krok 4)
> - Šablona Polls – webový projekt Flask slouží k vytvoření cyklického dotazování aplikaci, která bude celá řada možností úložišť (úložiště Azure, MongoDB nebo paměť).

V průběhu těchto kroků vytvořte jedno řešení sady Visual Studio, který obsahuje tři samostatné projekty. Vytvoření projektu pomocí jiné šablony projektu Flask, které jsou součástí sady Visual Studio. Udržováním projekty ve stejném řešení, lze snadno přepínat vpřed a zpět mezi různé soubory pro porovnání.

> [!Note]
> Tento kurz se liší od rychlého startu v [baňce](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) , ve kterém se dozvíte více o baňce a také o tom, jak používat různé šablony projektů v baňce, které poskytují rozsáhlejší výchozí bod pro vaše vlastní projekty. Například šablony projektu automaticky instalovat balíček Flask při vytváření projektu, ale můžete balíček nainstalovat ručně, jak je znázorněno v tomto rychlém startu.

## <a name="prerequisites"></a>Předpoklady

- Visual Studio 2017 nebo novější ve Windows s následujícími možnostmi:
  - Úloha **vývoje Pythonu** (karta**zatížení** v instalačním programu). Pokyny najdete v tématu [Instalace podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **GitHub Extension pro Visual Studio** na kartě **jednotlivé komponenty** v části **nástroje kódu**.

Šablony projektu Flask jsou součástí všech předchozích verzích nástroje Python Tools for Visual Studio, i když podrobnosti se mohou lišit co je popsáno v tomto kurzu.

Vývoj v jazyce Python se nepodporuje v současné době v sadě Visual Studio pro Mac. V systému Mac a Linux použijte [rozšíření Python v Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: vytvoření projektu sady Visual Studio a řešení

1. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**, vyhledejte "baňky" a vyberte šablonu **webového projektu prázdná baňky** . (Šablona se nachází také v části **Python** > **Web** v levém seznamu.)

    ![Dialogové okno nového projektu v sadě Visual Studio pro prázdný webový projekt Flask](media/flask/step01-new-blank-project.png)

1. V polích v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozím obrázku) a pak vyberte **OK**:

    - **Název**: Nastavte název projektu sady Visual Studio na **BasicProject**. Tento název se také používá pro projekt Flask.
    - **Umístění**: zadejte umístění, ve kterém chcete vytvořit řešení a projekt sady Visual Studio.
    - **Název řešení**: nastavte na **LearningFlask**, který je vhodný pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: opustit sadu (výchozí).
    - **Vytvořit nové úložiště Git**: tuto možnost vyberte (ve výchozím nastavení není jasné), aby Visual Studio při vytváření řešení vytvořilo místní úložiště Git. Pokud tuto možnost nevidíte, spusťte instalační program sady Visual Studio a přidejte rozšíření **Git pro Windows** a **GitHub pro Visual Studio** na kartu **jednotlivé komponenty** v části **nástroje kódu**.

1. Po chvíli vás Visual Studio vyzve k zadání dialogu, který říká, že **Tento projekt vyžaduje externí balíčky** (viz níže). Toto dialogové okno se zobrazí, protože šablona obsahuje soubor s *požadavky. txt* odkazující na nejnovější balíček. x, který je v baňce. (Pokud chcete zobrazit přesné závislosti, vyberte **Zobrazit požadované balíčky** .)

    ![Příkazový řádek o tom, že, že projekt vyžaduje externí balíčky.](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Vyberte možnost, kterou **si nainstalujem sami**. Můžete vytvořit virtuální prostředí krátce a ujistěte se, že je vyloučena ze správy zdrojového kódu. (Prostředí je možné vždy vytvořit z *požadavků. txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Zkontrolujte ovládací prvky Git a publikujte do vzdáleného úložiště

Vzhledem k tomu, že jste v dialogovém okně **Nový projekt** vybrali možnost **vytvořit nové úložiště Git** , projekt je již po dokončení procesu vytváření svěřen do místního zdrojového kódu. V tomto kroku se seznámení s ovládacími prvky Git sady Visual Studio a **Team Explorerm** oknem, ve kterém pracujete se správou zdrojových kódů.

1. Prozkoumejte Git ovládacích prvků v pravém dolním rohu sady Visual Studio hlavního okna. Zleva doprava tyto ovládací prvky zobrazují nevložená potvrzení, nepotvrzené změny, názvu úložiště a aktuální větve:

    ![Git ovládacích prvků v okně aplikace Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Pokud nevyberete možnost **vytvořit nové úložiště Git** v dialogovém okně **Nový projekt** , ovládací prvky Git zobrazí pouze příkaz **Přidat do zdrojového kódu** , který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v sadě Visual Studio, pokud není vytvořené úložiště](media/tutorials-common/step01-git-add-to-source-control.png)

1. Vyberte tlačítko změny a Visual Studio otevře jeho **Team Explorer** okno na stránce **změny** . Vzhledem k tomu, že nově vytvořený projekt je už potvrzená do správy zdrojového kódu automaticky, se nezobrazí všechny čekající změny.

    ![Okno Průzkumníka týmu na stránce změny](media/flask/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio vyberte tlačítko nevložená potvrzení (šipka nahoru se **dvěma**) a otevřete tak na **Team Explorer**stránku **synchronizace** . Protože máte místní úložiště, na stránce poskytuje jednoduché možnosti publikovat úložiště na jiné vzdálené úložiště.

    ![Team Explorer zobrazující k dispozici Git úložiště možnosti okna pro správu zdrojového kódu](media/flask/step01-team-explorer.png)

    Můžete zvolit služby, podle toho, která chcete pro svoje vlastní projekty. V tomto kurzu se dozvíte, jak používat GitHub, kde je dokončený vzorový kód pro kurz v úložišti [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask) .

1. Při výběru kteréhokoli ovládacího prvku pro **publikování** **Team Explorer** zobrazí výzvu k zadání dalších informací. Například při publikování ukázky pro tento kurz musela být nejprve vytvořena úložiště, v takovém případě se jako adresa URL úložiště použila možnost **nabízení vzdálené úložiště** .

    ![Okno Průzkumníka týmu při vkládání do existující vzdáleného úložiště](media/flask/step01-push-to-github.png)

    Pokud nemáte existující úložiště, možnosti **publikovat na GitHubu** a **nabízené oznámení do Azure DevOps** vám umožní vytvořit si ho přímo ze sady Visual Studio.

1. Při práci kroky v tomto kurzu si zvyknout pravidelně používání ovládacích prvků v sadě Visual Studio k potvrzení a nasdílení změn změny. V tomto kurzu upozorňuje na vhodných míst.

> [!Tip]
> Chcete-li rychle procházet v rámci **Team Explorer**, vyberte záhlaví (které čte **změny** **nebo je nahrajte na obrázku** výše) a zobrazte tak místní nabídku dostupných stránek.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: Za prvé, od samého začátku pomocí správy zdrojového kódu, zejména pokud používáte vzdálené úložiště, poskytuje zálohování mimo pracoviště regulární vašeho projektu. Na rozdíl od jenom na údržbu projektu místního systému souborů, správy zdrojového kódu také poskytuje kompletní změnu historie a snadno možnost obnovit jeden soubor nebo celého projektu do předchozího stavu. Který historii změn pomáhá určit, proč regrese (neúspěšné testy). Kromě toho je nezbytné, najde víc lidí práci na projektu, jak spravuje přepíše a poskytuje řešení konfliktů správy zdrojového kódu. A konečně správy zdrojového kódu, který je v podstatě formu automatizace, nastaví je dobře pro automatizaci sestavení, testování a produktu release management. Ve skutečnosti je prvním krokem při používání DevOps pro projekt, a protože překážky položky jsou tak nízké, ve skutečnosti neexistuje žádný důvod není použití správy zdrojového kódu od začátku.

Další diskuzi o správě zdrojového kódu jako Automation najdete v článku [zdroje pravdy: role úložišť v DevOps](https://msdn.microsoft.com/magazine/mt763232), článek na webu MSDN Magazine, který je napsán pro mobilní aplikace, které se vztahují také na webové aplikace.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Můžu zabránit v sadě Visual Studio automaticky potvrzení nového projektu?

Odpověď: Ano. Chcete-li zakázat automatické potvrzování, na stránce **Nastavení** v **Team Explorer**vyberte možnost **Git** > **globální nastavení**, zrušte zaškrtnutí políčka s názvem **změny po sloučení ve výchozím**nastavení a pak vyberte **aktualizovat**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1 – 3: vytvoření virtuálního prostředí a vyloučit ze správy zdrojového kódu

Teď, když nakonfigurujete pro svůj projekt správy zdrojového kódu, můžete vytvořit virtuální prostředí potřebné balíčky Flask, které projekt vyžaduje. Pak můžete použít **Team Explorer** k vyloučení složky prostředí ze správy zdrojového kódu.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte **Přidat virtuální prostředí**.

    ![Přidat virtuální prostředí příkaz v okně Průzkumník řešení](media/flask/step01-add-virtual-environment-command.png)

1. Zobrazí se dialogové okno **Přidat virtuální prostředí** se zprávou, že **jsme našli soubor požadavky. txt.** Tato zpráva znamená, že Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Přidat virtuální prostředí dialogu se zprávou, soubor requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Výběrem možnosti **vytvořit** přijměte výchozí hodnoty. (Název virtuálního prostředí můžete změnit, pokud chcete, který pouze změní název jeho podsložky, ale `env` je standardní konvence.)

1. Souhlas s oprávněními správce, pokud se zobrazí výzva, pak buďte prosím trpěliví. za pár minut, zatímco Visual Studio stáhne a nainstaluje balíčky, které pro Flask a jeho závislosti znamená, že rozšíření o tisíc souborů ve více než 100 podsložky. Průběh můžete zobrazit v okně **výstup** aplikace Visual Studio. Zatímco čekáte, uvažoval následující části otázku. Na stránce [instalace baňky](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (Flask.pcocoo.org) můžete také zobrazit popis závislostí ve baňce.

1. V ovládacích prvcích Git sady Visual Studio (na stavovém řádku) vyberte indikátor změn (který zobrazuje **&#42;99**), který otevře stránku **změny** v **Team Explorer**.

    Vytvoření virtuálního prostředí do stovek změn, ale nemusíte do správy zdrojových kódů zahrnout žádné z nich, protože vy (nebo kdokoli jiný klonování projektu) může vždy znovu vytvořit prostředí z *požadavků. txt*.

    Virtuální prostředí vyloučíte tak, že kliknete pravým tlačítkem na složku **ENV** a vyberete **ignorovat tyto místní položky**.

    ![Ignoruje se do virtuálního prostředí v změny správy zdrojového kódu](media/flask/step01-ignore-local-items.png)

1. Po vyloučení virtuálního prostředí jsou pouze zbývající změny v souboru projektu a *. gitignore*. Soubor *. gitignore* obsahuje přidanou položku pro složku virtuálního prostředí. Dvakrát kliknete na soubor zobrazíte rozdíl

1. Zadejte zprávu potvrzení a vyberte tlačítko **potvrdit vše** a pak předejte potvrzení do vzdáleného úložiště, pokud chcete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: Proč mám chcete vytvořit virtuální prostředí?

Odpověď: Virtuální prostředí je skvělý způsob, jak izolovat přesné závislostí aplikace. Tato izolace zabrání konfliktům v rámci globálního prostředí Pythonu a pomáhá testování a spolupráci. V průběhu času při vývoji aplikace, je vždy přenést v mnoha užitečné balíčky Pythonu. Udržováním balíčků ve virtuálním prostředí specifickém pro projekt, můžete snadno aktualizovat soubor *. txt požadavky* projektu, který popisuje toto prostředí, které je součástí správy zdrojového kódu. Když je projekt zkopírován do jiných počítačů, včetně serverů sestavení, serverů nasazení a dalších vývojových počítačů, je snadné vytvořit prostředí pouze pomocí pouze *požadavků. txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace najdete v tématu [použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Jak odebrat virtuální prostředí, které už je potvrzená do správy zdrojových kódů?

Odpověď: nejdřív upravte soubor *. gitignore* tak, aby vyloučí složku: Najděte oddíl na konci s komentářem `# Python Tools for Visual Studio (PTVS)` a přidejte nový řádek pro složku virtuálního prostředí, jako je třeba `/BasicProject/env`. (Vzhledem k tomu, že Visual Studio nezobrazuje soubor v **Průzkumník řešení**, otevřete ho přímo pomocí příkazu > **otevřete** **soubor nabídky** ** > .** Soubor můžete také otevřít z **Team Explorer**: na stránce **Nastavení** vyberte **Nastavení úložiště**, do části **Ignorovat soubory atributů &** a pak vyberte odkaz **Upravit** vedle **. gitignore**.)

Za druhé Otevřete příkazové okno, přejděte do složky, jako je *BasicProject* , která obsahuje složku virtuálního prostředí, jako je třeba *ENV*, a spusťte `git rm -r env`. Pak tyto změny potvrďte z příkazového řádku (`git commit -m 'Remove venv'`) nebo je potvrďte na stránce **změny** v **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1 – 4: prozkoumání často používaný kód

1. Po dokončení vytváření projektu uvidíte řešení a projekt v **Průzkumník řešení**, kde projekt obsahuje jenom dva soubory, *App.py* a *požadavky. txt*:

    ![V Průzkumníku řešení prázdné soubory projektu Flask](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak bylo uvedeno dříve, soubor *požadavky. txt* určuje závislost balíčku na baňce. Přítomnost tento soubor je, co vás zve k vytvoření virtuálního prostředí, při prvním vytvoření projektu.

1. Jeden soubor *App.py* obsahuje tři části. Prvním je příkaz `import` pro baňky, vytvoření instance `Flask` třídy, která je přiřazena proměnné `app`a následně přiřazení `wsgi_app` proměnné (což je užitečné při nasazování na webový hostitel, ale v současné době se nepoužívá):

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

1. Je třetí krátký bitového kódu, který se přiřadí adresu URL funkce směrování, to znamená, že funkce poskytuje zdroje podle adresy URL. Trasy definujete `@app.route` dekoratér v baňce, jejíž argument je relativní adresa URL z kořene webu. Jak je vidět v kódu, vrátí funkce tady jenom textový řetězec, který je dostatečná pro prohlížeče k vykreslení. V následujících kroků vykreslování bohatší stránek HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Otázka: Jaký je účel argumentu __Name__ pro třídu baněk?

Odpověď: Argument je název modulu nebo balíček aplikace a zjistí Flask, kde má hledat šablony, statické soubory a další prostředky, které patří k aplikaci. U aplikací obsažených v jednom modulu je `__name__` vždy správná hodnota. Je také důležité pro rozšíření, která vyžadují informace o ladění. Další informace a další argumenty najdete v [dokumentaci třídy s baňkou](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (Flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Otázka: Je funkce mít více než jeden dekoratér trasy?

Odpověď: Ano, můžete použít tolik dekoratéry, pokud má stejnou funkci slouží několik tras. Například chcete-li použít funkci `hello` pro "/" a "/Hello", použijte následující kód:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Otázka: Jak Flask funguje s proměnnou cesty adresy URL a parametry dotazu?

Odpověď: v trase označíte jakoukoli proměnnou pomocí `<variable_name>`a pomocí pojmenovaného argumentu projdete tuto proměnnou do funkce. Proměnná může být část cesty adresy URL nebo v parametru dotazu. Například trasa ve formě `'/hello/<name>` generuje řetězcový argument s názvem `name` do funkce a použití `?message=<msg>` v trase analyzuje hodnotu zadanou pro parametr dotazu "Message =" a předá ho funkci jako `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Chcete-li změnit typ, předponu proměnné s `int`, `float`, `path` (která přijímá lomítka k vymezení názvů složek) a `uuid`. Podrobnosti najdete v tématu [pravidla proměnných](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) v dokumentaci k baňce.

Parametry dotazu jsou také k dispozici prostřednictvím vlastnosti `request.args`, konkrétně prostřednictvím metody `request.args.get`. Další informace naleznete v dokumentaci k [objektu Request](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) v dokumentaci k baňce.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: Může Visual Studio generovat soubor requirements.txt z virtuálního prostředí po instalaci dalších balíčků?

Odpověď: Ano. Rozbalte uzel **prostředí Pythonu** , klikněte pravým tlačítkem na virtuální prostředí a vyberte příkaz **generovat požadavky. txt** . Tento příkaz je vhodné použít pravidelně při úpravách prostředí a potvrdit změny *požadavků. txt* do správy zdrojových kódů spolu s dalšími změnami kódu, které jsou závislé na daném prostředí. Pokud nastavení nepřetržité integrace na serveru sestavení byste měli vždy, když změníte prostředí generovat soubor a změn.

## <a name="step-1-5-run-the-project"></a>Krok 1 – 5: spuštění projektu

1. V sadě Visual Studio vyberte **ladit** > **Spustit ladění** (**F5**) nebo použít tlačítko **webový server** na panelu nástrojů (prohlížeč, který vidíte, se může lišit):

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Buď příkaz přiřadí náhodné číslo portu k proměnné prostředí portu a potom spustí `python app.py`. Kód spustí aplikaci pomocí tohoto portu v rámci vývojový server Flask společnosti. Pokud se sadě Visual Studio nepodaří **Spustit ladicí program** se zprávou o tom, že nemá žádný spouštěcí soubor, klikněte pravým tlačítkem na **App.py** v **Průzkumník řešení** a vyberte **nastavit jako spouštěcí soubor**.

1. Při spuštění serveru, najdete v okně konzoly otevřete tuto zobrazí protokolu serveru. Visual Studio pak automaticky otevře prohlížeč pro `http://localhost:<port>`, kde by se měla zobrazit zpráva vykreslená funkcí `hello`:

    ![Výchozí zobrazení projektu Flask](media/flask/step01-first-run-success.png)

1. Až skončíte, zastavte Server ukončením okna konzoly nebo pomocí příkazu **ladění** > **Zastavit ladění** v aplikaci Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím nástrojů ladění příkazů nabídky a příkazy serveru v podnabídce projektu Pythonu?

Odpověď: Kromě příkazů nabídky **ladění** a tlačítek na panelu nástrojů můžete také spustit server pomocí příkazu **Python** > **spustit server** nebo **Python** > **spustit příkazy ladění serveru** v místní nabídce projektu. Oba příkazy otevřete okno konzoly, ve kterém se zobrazí místní adresa URL (localhost:port) pro spuštěný server. Nicméně je nutné ručně otevřít prohlížeč s touto adresou URL a serverem ladění nespustí automaticky ladicího programu sady Visual Studio. Ladicí program můžete ke spuštěnému procesu připojit později, pokud chcete, pomocí příkazu **ladit** > **připojit k procesu** .

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základního projektu Flask obsahuje spuštění kódu a kódu stránky ve stejném souboru. Je vhodné oddělit tyto dva problémy a také oddělení kódu HTML a data pomocí šablon.

> [!div class="nextstepaction"]
> [Vytvoření aplikace v baňce se zobrazeními a šablonami stránek](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Rychlý Start k baňce](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask)
