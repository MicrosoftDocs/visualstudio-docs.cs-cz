---
title: Kurz k seznámení s kurzem v nástroji Visual Studio Step 1, základy na baňce
titleSuffix: ''
description: Návod základů v baňce v kontextu projektů aplikace Visual Studio, včetně požadavků, Git a virtuálních prostředí.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 018b9a6707ea46a9b1c46f820faf7bd47dac1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809895"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Kurz: Začínáme s webovým rozhraním v baňce v aplikaci Visual Studio

[Baňka](https://palletsprojects.com/p/flask/) je odlehčená architektura Pythonu pro webové aplikace, která poskytuje základní informace o směrování adres URL a vykreslování stránky.

Baňka se nazývá "mikro" architektura, protože přímo neposkytuje funkce, jako je ověřování formuláře, abstrakce databáze, ověřování atd. Tyto funkce jsou místo toho k dispozici speciálními balíčky Pythonu, které se nazývají *rozšíření*baněk. Rozšíření se hladce integrují s použitím baňky tak, aby se zobrazila jako součást samotné baňky. Například samotná baňka neposkytuje modul šablony stránky. Šablonování je poskytována rozšířeními, jako jsou Jinja a Jade, jak je znázorněno v tomto kurzu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření projektu základní baňky v úložišti Git pomocí šablony "prázdný webový projekt v baňce" (krok 1)
> - Vytvoření aplikace v baňce s jednou stránkou a vykreslení této stránky pomocí šablony (krok 2)
> - Obsluha statických souborů, přidávání stránek a použití dědičnosti šablon (krok 3)
> - Použití šablony webového projektu v baňce k vytvoření aplikace s několika stránkami a návrhem reakce (krok 4)
> - Pomocí šablony webového projektu pro cyklické dotazování můžete vytvořit aplikaci pro cyklické dotazování, která používá celou řadu možností úložiště (úložiště Azure, MongoDB nebo paměť).

V průběhu těchto kroků vytvoříte jedno řešení sady Visual Studio, které obsahuje tři samostatné projekty. Projekt vytvoříte pomocí různých šablon projektů v baňce, které jsou součástí sady Visual Studio. Udržováním projektů ve stejném řešení můžete snadno přepínat mezi různými soubory a jejich porovnáním.

> [!Note]
> Tento kurz se liší od rychlého startu v [baňce](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) , ve kterém se dozvíte více o baňce a také o tom, jak používat různé šablony projektů v baňce, které poskytují rozsáhlejší výchozí bod pro vaše vlastní projekty. Například šablony projektu automaticky instalují balíček baňky při vytváření projektu, ale nevyžadují ruční instalaci balíčku, jak je znázorněno v rychlém startu.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější ve Windows s následujícími možnostmi:
  - Úloha **vývoje Pythonu** (karta**zatížení** v instalačním programu). Pokyny najdete v tématu [Instalace podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **GitHub Extension pro Visual Studio** na kartě **jednotlivé komponenty** v části **nástroje kódu**.

Šablony projektů jsou součástí všech dřívějších verzí Python Tools for Visual Studio, ale podrobnosti se mohou lišit od toho, co je popsáno v tomto kurzu.

Vývoj v jazyce Python není v Visual Studio pro Mac aktuálně podporován. V systému Mac a Linux použijte [rozšíření Python v Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: vytvoření projektu a řešení sady Visual Studio

1. V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**, vyhledejte "baňky" a vyberte šablonu **webového projektu prázdná baňky** . (Šablona se taky nachází v **Pythonu**  >  **Web** v seznamu na levé straně.)

    ![Dialogové okno Nový projekt v aplikaci Visual Studio pro webový projekt prázdné baňky](media/flask/step01-new-blank-project.png)

1. V polích v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozím obrázku) a pak vyberte **OK**:

    - **Název**: Nastavte název projektu sady Visual Studio na **BasicProject**. Tento název se používá také pro projekt baňky.
    - **Umístění**: zadejte umístění, ve kterém chcete vytvořit řešení a projekt sady Visual Studio.
    - **Název řešení**: nastavte na **LearningFlask**, který je vhodný pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: opustit sadu (výchozí).
    - **Vytvořit nové úložiště Git**: tuto možnost vyberte (ve výchozím nastavení není jasné), aby Visual Studio při vytváření řešení vytvořilo místní úložiště Git. Pokud tuto možnost nevidíte, spusťte instalační program sady Visual Studio a přidejte rozšíření **Git pro Windows** a **GitHub pro Visual Studio** na kartu **jednotlivé komponenty** v části **nástroje kódu**.

1. Po chvíli vás Visual Studio vyzve k zadání dialogu, který říká, že **Tento projekt vyžaduje externí balíčky** (viz níže). Toto dialogové okno se zobrazí, protože šablona obsahuje *requirements.txt* soubor s odkazem na nejnovější balíček 1. x v baňce. (Pokud chcete zobrazit přesné závislosti, vyberte **Zobrazit požadované balíčky** .)

    ![Výzva říká, že projekt vyžaduje externí balíčky](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Vyberte možnost, kterou **si nainstalujem sami**. Vytvoříte virtuální prostředí za chvíli, abyste se ujistili, že je vyloučený ze správy zdrojového kódu. (Prostředí lze vždy vytvořit z *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Projděte si ovládací prvky Git a publikujte je na vzdálené úložiště

Vzhledem k tomu, že jste v dialogovém okně **Nový projekt** vybrali možnost **vytvořit nové úložiště Git** , projekt je již po dokončení procesu vytváření svěřen do místního zdrojového kódu. V tomto kroku se seznámení s ovládacími prvky Git sady Visual Studio a **Team Explorerm** oknem, ve kterém pracujete se správou zdrojových kódů.

1. Projděte si ovládací prvky Git v dolním rohu hlavního okna sady Visual Studio. Zleva doprava tyto ovládací prvky zobrazují nenabízená potvrzení, nepotvrzené změny, název úložiště a aktuální větev:

    ![Ovládací prvky Git v okně Visual studia](media/flask/step01-git-controls.png)

    > [!Note]
    > Pokud nevyberete možnost **vytvořit nové úložiště Git** v dialogovém okně **Nový projekt** , ovládací prvky Git zobrazí pouze příkaz **Přidat do zdrojového kódu** , který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v aplikaci Visual Studio, pokud jste úložiště nevytvořili.](media/tutorials-common/step01-git-add-to-source-control.png)

1. Vyberte tlačítko změny a Visual Studio otevře jeho **Team Explorer** okno na stránce **změny** . Vzhledem k tomu, že nově vytvořený projekt je již trvale potvrzen do správy zdrojového kódu, neuvidíte žádné čekající změny.

    ![Team Explorer okno na stránce změny](media/flask/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio vyberte tlačítko nevložená potvrzení (šipka nahoru se **dvěma**) a otevřete tak na **Team Explorer**stránku **synchronizace** . Vzhledem k tomu, že máte pouze místní úložiště, stránka poskytuje snadné možnosti pro publikování úložiště v různých vzdálených úložištích.

    ![Okno Team Explorer zobrazující dostupné možnosti úložiště Git pro správu zdrojového kódu](media/flask/step01-team-explorer.png)

    Můžete zvolit jakoukoli službu, kterou chcete pro své vlastní projekty. V tomto kurzu se dozvíte, jak používat GitHub, kde je dokončený vzorový kód pro kurz v úložišti [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask) .

1. Při výběru kteréhokoli ovládacího prvku pro **publikování** **Team Explorer** zobrazí výzvu k zadání dalších informací. Například při publikování ukázky pro tento kurz musela být nejprve vytvořena úložiště, v takovém případě se jako adresa URL úložiště použila možnost **nabízení vzdálené úložiště** .

    ![Team Explorer okno pro doručování do existujícího vzdáleného úložiště](media/flask/step01-push-to-github.png)

    Pokud nemáte existující úložiště, možnosti **publikovat na GitHubu** a **nabízené oznámení do Azure DevOps** vám umožní vytvořit si ho přímo ze sady Visual Studio.

1. Při práci v tomto kurzu se dostanete k tomu, abyste pravidelně používali ovládací prvky v aplikaci Visual Studio k potvrzení a vložení změn. V tomto kurzu se můžete podívat na vhodné body.

> [!Tip]
> Chcete-li rychle procházet v rámci **Team Explorer**, vyberte záhlaví (které čte **změny** **nebo je nahrajte na obrázku** výše) a zobrazte tak místní nabídku dostupných stránek.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: první ze všech, použití správy zdrojového kódu od začátku, obzvláště pokud používáte také vzdálené úložiště, poskytuje normální zálohu projektu mimo lokalitu. Na rozdíl od udržování projektu pouze v místním systému souborů poskytuje Správa zdrojového kódu také úplnou historii změn a snadnou možnost vrátit jeden soubor nebo celý projekt do předchozího stavu. Tato změna historie pomáhá určit příčinu regresí (selhání testu). Kromě toho Správa zdrojového kódu je zásadní, pokud více lidí pracuje na projektu, protože spravuje přepsání a poskytuje řešení konfliktů. A konečně Správa zdrojového kódu, která je v podstatě formou automatizace, nastavuje správnou automatizaci buildů, testování a správy vydaných verzí. Je to skutečně první krok v použití DevOps pro projekt a protože překážky vstupu jsou tak nízké, neexistuje žádný důvod, proč nepoužívejte správu zdrojového kódu od začátku.

Další diskuzi o správě zdrojového kódu jako Automation najdete v článku [zdroje pravdy: role úložišť v DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), článek na webu MSDN Magazine, který je napsán pro mobilní aplikace, které se vztahují také na webové aplikace.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Mohu aplikaci Visual Studio zabránit v automatickém potvrzování nového projektu?

Odpověď: Ano. Pokud chcete automatické potvrzení zakázat, na stránce **Nastavení** v **Team Explorer**vyberte **Git**  >  **globální nastavení**Gitu, ve výchozím nastavení zrušte zaškrtnutí políčka **po sloučení označit změny**a pak vyberte **aktualizovat**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Vytvoření virtuálního prostředí a jeho vyloučení ze správy zdrojového kódu

Teď, když jste nakonfigurovali správu zdrojového kódu pro svůj projekt, můžete vytvořit virtuální prostředí, které bude vyžadovat, aby byly potřebné balíčky, které projekt vyžaduje. Pak můžete použít **Team Explorer** k vyloučení složky prostředí ze správy zdrojového kódu.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte **Přidat virtuální prostředí**.

    ![Příkaz Přidat virtuální prostředí v Průzkumník řešení](media/flask/step01-add-virtual-environment-command.png)

1. Zobrazí se dialogové okno **Přidat virtuální prostředí** se zprávou, že **jsme našli soubor requirements.txt.** Tato zpráva znamená, že aplikace Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Dialogové okno Přidat virtuální prostředí s requirements.txtovou zprávou](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Výběrem možnosti **vytvořit** přijměte výchozí hodnoty. (Název virtuálního prostředí můžete změnit, pokud chcete, který pouze změní název jeho podsložky, ale `env` je standardní konvence.)

1. Pokud se zobrazí výzva, při stažení a instalaci balíčku, který je součástí sady Visual Studio ke stažení a nainstalují balíčky a jejich závislosti, se rozbalí přibližně tisíce souborů ve více než 100 podsložkách. Průběh můžete zobrazit v okně **výstup** aplikace Visual Studio. Až budete čekat, uvažoval se níže uvedené otázky. Na stránce [instalace baňky](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (Flask.pcocoo.org) můžete také zobrazit popis závislostí ve baňce.

1. V ovládacích prvcích Git sady Visual Studio (na stavovém řádku) vyberte indikátor změn (který zobrazuje **99&#42;**), ve kterém se otevře stránka **změny** v **Team Explorer**.

    Vytvoření virtuálního prostředí ze stovky změn, ale nemusíte ho zahrnovat do správy zdrojových kódů, protože vy (nebo kdokoli jiný klonování projektu) může vždy znovu vytvořit prostředí z *requirements.txt*.

    Virtuální prostředí vyloučíte tak, že kliknete pravým tlačítkem na složku **ENV** a vyberete **ignorovat tyto místní položky**.

    ![Ignoruje se virtuální prostředí při změnách ve správě zdrojového kódu.](media/flask/step01-ignore-local-items.png)

1. Po vyloučení virtuálního prostředí jsou pouze zbývající změny v souboru projektu a *. gitignore*. Soubor *. gitignore* obsahuje přidanou položku pro složku virtuálního prostředí. Poklikáním na soubor můžete zobrazit rozdíl.

1. Zadejte zprávu potvrzení a vyberte tlačítko **potvrdit vše** a pak předejte potvrzení do vzdáleného úložiště, pokud chcete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: proč chci vytvořit virtuální prostředí?

Odpověď: virtuální prostředí představuje skvělý způsob, jak izolovat přesné závislosti vaší aplikace. Tato izolace zabrání konfliktům v globálním prostředí Pythonu a pomáhá při testování i spolupráci. V průběhu času můžete při vývoji aplikace invariably spoustu užitečných balíčků Pythonu. Udržováním balíčků ve virtuálním prostředí specifickém pro projekt můžete snadno aktualizovat soubor *requirements.txt* projektu, který popisuje toto prostředí, které je součástí správy zdrojového kódu. Když je projekt zkopírován do jiných počítačů, včetně serverů sestavení, serverů nasazení a dalších vývojových počítačů, je snadné vytvořit prostředí pouze pomocí *requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace najdete v tématu [použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Návody odebrat virtuální prostředí, které je už zapsané do správy zdrojového kódu?

Odpověď: nejdřív upravte soubor *. gitignore* tak, aby vyloučil složku: Vyhledejte část na konci komentáře `# Python Tools for Visual Studio (PTVS)` a přidejte nový řádek pro složku virtuálního prostředí, například `/BasicProject/env` . (Protože Visual Studio nezobrazuje soubor v **Průzkumník řešení**, otevřete ho přímo pomocí **souboru**  >  **Otevřít**  >  Příkaz nabídky **soubor** . Soubor můžete také otevřít z **Team Explorer**: na stránce **Nastavení** vyberte **Nastavení úložiště**, do části **Ignorovat soubory atributů &** a pak vyberte odkaz **Upravit** vedle **. gitignore**.)

Za druhé Otevřete příkazové okno, přejděte do složky, jako je *BasicProject* , která obsahuje složku virtuálního prostředí, jako je třeba *ENV*, a spusťte příkaz `git rm -r env` . Pak tyto změny potvrďte z příkazového řádku ( `git commit -m 'Remove venv'` ) nebo potvrzení na stránce **změny** **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Projděte si často používaný kód

1. Po dokončení vytváření projektu se zobrazí řešení a projekt v **Průzkumník řešení**, kde projekt obsahuje pouze dva soubory, *App.py* a *requirements.txt*:

    ![Prázdné soubory projektu v baňce v Průzkumník řešení](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak bylo uvedeno dříve, soubor *requirements.txt* určuje závislost balíčku na baňce. Přítomnost tohoto souboru vás zve k vytvoření virtuálního prostředí při prvním vytvoření projektu.

1. Jeden soubor *App.py* obsahuje tři části. První je `import` příkaz pro použití baňky, vytvoření instance `Flask` třídy, která je přiřazena proměnné `app` a následně přiřazení `wsgi_app` proměnné (která je užitečná při nasazení na webového hostitele, ale nepoužívá se v současné době):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druhá část na konci souboru je bitová kopie volitelného kódu, který spouští vývojový server baňky s konkrétními hodnotami hostitelů a portů pořízenými z proměnných prostředí (s výchozí hodnotou localhost: 5555):

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

1. Třetí je krátká bitová kopie, která přiřadí funkci trasy URL, což znamená, že funkce poskytuje prostředek identifikovaný adresou URL. Trasy definujete pomocí dekoratér baňky `@app.route` , jejíž argument je relativní adresa URL z kořene webu. Jak vidíte v kódu, funkce zde vrátí pouze textový řetězec, který je dostatečný pro vykreslení prohlížeče. V krocích, které následují, vykreslíte bohatší stránky pomocí HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Otázka: Jaký je účel argumentu __Name__ pro třídu baněk?

Odpověď: argument je název modulu nebo balíčku aplikace a informuje o baňce, kde hledat šablony, statické soubory a další prostředky, které patří do aplikace. Pro aplikace, které jsou součástí jednoho modulu, `__name__` je vždy správná hodnota. Je také důležité pro rozšíření, která potřebují informace o ladění. Další informace a další argumenty najdete v [dokumentaci třídy s baňkou](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (Flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Otázka: může mít funkce více než jeden dekoratér trasy?

Odpověď: Ano, můžete použít tolik dekoratéry, kolik chcete, pokud stejná funkce obsluhuje více tras. Chcete-li například použít `hello` funkci pro "/" a "/Hello", použijte následující kód:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Otázka: jak má baňka pracovat s proměnnými adresy URL a parametry dotazu?

Odpověď: v trase označíte jakoukoli proměnnou pomocí `<variable_name>` a pomocí pojmenovaného argumentu projdete tuto proměnnou do funkce. Proměnná může být součástí cesty URL nebo v parametru dotazu. Například trasa ve formě `'/hello/<name>` vygeneruje řetězcový argument `name` s názvem funkce a použití `?message=<msg>` v trase analyzuje hodnotu zadanou pro parametr dotazu "Message =" a předá ho funkci jako `msg` :

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Chcete-li změnit typ, předponu proměnné s `int` , `float` , `path` (která přijímá lomítka k vymezení názvů složek) a `uuid` . Podrobnosti najdete v tématu [pravidla proměnných](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) v dokumentaci k baňce.

Parametry dotazu jsou také k dispozici prostřednictvím `request.args` vlastnosti, konkrétně prostřednictvím `request.args.get` metody. Další informace naleznete v dokumentaci k [objektu Request](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) v dokumentaci k baňce.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: může Visual Studio po instalaci dalších balíčků vygenerovat soubor requirements.txt z virtuálního prostředí?

Odpověď: Ano. Rozbalte uzel **prostředí Pythonu** , klikněte pravým tlačítkem na virtuální prostředí a vyberte příkaz pro **vygenerování requirements.txt** . Tento příkaz je vhodné použít pravidelně při úpravách prostředí a potvrdit změny *requirements.txt* do správy zdrojových kódů spolu s dalšími změnami kódu, které jsou závislé na daném prostředí. Pokud nastavíte průběžnou integraci na serveru sestavení, měli byste vygenerovat soubor a potvrdit změny, kdykoli upravíte prostředí.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: spuštění projektu

1. V sadě Visual Studio vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo na panelu nástrojů použijte tlačítko **webový server** (prohlížeč, který vidíte, se může lišit):

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Buď příkaz přiřadí náhodné číslo portu k proměnné prostředí portu a pak spustí `python app.py` . Kód spustí aplikaci pomocí tohoto portu v rámci vývojového serveru ve baňce. Pokud se sadě Visual Studio nepodaří **Spustit ladicí program** se zprávou o tom, že nemá žádný spouštěcí soubor, klikněte pravým tlačítkem na **App.py** v **Průzkumník řešení** a vyberte **nastavit jako spouštěcí soubor**.

1. Po spuštění serveru se zobrazí okno konzoly, ve kterém se zobrazí protokol serveru. Visual Studio pak automaticky otevře prohlížeč na `http://localhost:<port>` , kde by se měla zobrazit zpráva vykreslená `hello` funkcí:

    ![Výchozí zobrazení projektu baňky](media/flask/step01-first-run-success.png)

1. Až skončíte, zastavte Server ukončením okna konzoly nebo pomocí příkazu **ladit**  >  **Zastavit ladění** v aplikaci Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím příkazů nabídky ladění a příkazů serveru v podnabídce Python projektu?

Odpověď: Kromě příkazů nabídky **ladění** a tlačítek na panelu nástrojů můžete také spustit server pomocí příkazů spustit server v **Pythonu**  >  **Run server** nebo **Python**  >  **Spustit ladicí Server** v místní nabídce projektu. Oba příkazy otevřou okno konzoly, ve kterém se zobrazí místní adresa URL (localhost: port) pro spuštěný Server. Je však nutné ručně otevřít prohlížeč s touto adresou URL a spustit ladicí server automaticky nespustí ladicí program sady Visual Studio. Ladicí program můžete ke spuštěnému procesu připojit později, pokud chcete, pomocí příkazu **ladit**  >  **připojit k procesu** .

## <a name="next-steps"></a>Další kroky

V tuto chvíli projekt základní baňky obsahuje spouštěcí kód a kód stránky ve stejném souboru. Je nejvhodnější oddělit tyto dva obavy a také oddělit kód HTML a data pomocí šablon.

> [!div class="nextstepaction"]
> [Vytvoření aplikace v baňce se zobrazeními a šablonami stránek](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Rychlý Start k baňce](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask)