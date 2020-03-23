---
title: Výuka výuky flask v kroku 1 sady Visual Studio, základy flask
titleSuffix: ''
description: Návod základy Flask v kontextu projektů sady Visual Studio, včetně předpokladů, Git a virtuální prostředí.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302845"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Kurz: Začínáme s webovým rámcem Flask v sadě Visual Studio

[Flask](https://palletsprojects.com/p/flask/) je lehký python framework pro webové aplikace, který poskytuje základy pro směrování adres URL a vykreslování stránek.

Flask se nazývá "mikro" rámec, protože není přímo poskytovat funkce, jako je ověření formuláře, abstrakce databáze, ověřování a tak dále. Tyto funkce jsou místo toho poskytovány speciálními balíčky Pythonu *nazývanými rozšíření*Flask . Rozšíření se hladce integrují s Baňkou tak, aby vypadala, jako by byla součástí samotné baňky. Například Flask sám neposkytuje modul šablony stránky. Templating je poskytována rozšíření, jako je Jinja a Jade, jak je znázorněno v tomto kurzu.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Flask v úložišti Git pomocí šablony "Blank Flask Web Project" (krok 1)
> - Vytvoření aplikace Flask s jednou stránkou a vykreslení této stránky pomocí šablony (krok 2)
> - Obsluhujte statické soubory, přidávejte stránky a používejte dědičnost šablony (krok 3)
> - Vytvoření aplikace s více stránkami a responzivním designem (krok 4) pomocí šablony Flask Web Project
> - Šablona Polls Flask Web Project slouží k vytvoření dotazové aplikace, která používá různé možnosti úložiště (úložiště Azure, MongoDB nebo paměť).

V průběhu těchto kroků vytvoříte jedno řešení sady Visual Studio, které obsahuje tři samostatné projekty. Projekt vytvoříte pomocí různých šablon projektu Flask, které jsou součástí sady Visual Studio. Udržováním projektů ve stejném řešení, můžete snadno přepínat tam a zpět mezi různými soubory pro porovnání.

> [!Note]
> Tento kurz se liší od [flask Rychlý start](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) v tom, že se dozvíte více o Flask, stejně jako o tom, jak používat různé šablony projektu Flask, které poskytují rozsáhlejší výchozí bod pro vaše vlastní projekty. Například šablony projektu automaticky nainstalují balíček Flask při vytváření projektu, místo toho, abyste museli balíček nainstalovat ručně, jak je znázorněno na úvodním panelu.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější v systému Windows s následujícími možnostmi:
  - Úloha **vývoje Pythonu** (karta**Úloha** v instalačním programu). Pokyny naleznete [v tématu Instalace podpory Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **GitHub Extension for Visual Studio** na kartě Jednotlivé **součásti** v části **Nástroje kódu**.

Šablony projektů Flask jsou součástí všech dřívějších verzí pythonových nástrojů pro Visual Studio, i když podrobnosti se mohou lišit od toho, co je popsáno v tomto kurzu.

Vývoj Pythonu není v současné době podporován ve Visual Studiu pro Mac. Na Macu a Linuxu použijte [rozšíření Pythonu v kódu Visual Studia](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Vytvoření projektu a řešení sady Visual Studio

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**, vyhledejte "Flask" a vyberte šablonu **webového projektu Prázdná flask.** (Šablona se také nachází v **pythonu** > **webu** v levém seznamu.)

    ![Dialogové okno Nový projekt v sadě Visual Studio pro webový projekt Prázdná baňka](media/flask/step01-new-blank-project.png)

1. Do polí v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozí grafice) a pak vyberte **OK**:

    - **Název**: nastavte název projektu sady Visual Studio na **basicproject**. Tento název se používá také pro projekt Flask.
    - **Umístění**: zadejte umístění, ve kterém chcete vytvořit řešení a projekt sady Visual Studio.
    - **Název řešení:** nastavte **na LearningFlask**, což je vhodné pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: Ponechat sadu (výchozí).
    - **Vytvořit nové úložiště Git**: Vyberte tuto možnost (která je ve výchozím nastavení jasná), aby Visual Studio při vytváření řešení vytvořilo místní úložiště Git. Pokud tuto možnost nevidíte, spusťte instalační program Visual Studia a přidejte **git pro Windows** a rozšíření **GitHub pro Visual Studio** na kartě Jednotlivé **součásti** v části **Nástroje kódu**.

1. Po chvíli visual studio zobrazí výzvu s dialogem říká **Tento projekt vyžaduje externí balíčky** (viz níže). Toto dialogové okno se zobrazí, protože šablona obsahuje soubor *requirements.txt* odkazující na nejnovější balíček Flask 1.x. (Chcete-li zobrazit přesné závislosti, vyberte možnost **Zobrazit požadované balíčky.)**

    ![Výzva říká, že projekt vyžaduje externí balíčky](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Vyberte **možnost, kterou nainstaluji sám**. Můžete vytvořit virtuální prostředí krátce ujistěte se, že je vyloučenze správy zdrojového kódu. (Prostředí lze vždy vytvořit z *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Zkontrolujte ovládací prvky Git a publikujte ve vzdáleném úložišti

Protože jste v dialogovém okně **Nový projekt** vybrali **možnost Vytvořit nové úložiště Git,** projekt se již po dokončení procesu vytváření pozdochází k místní správě zdrojů. V tomto kroku se seznámíte s ovládacími prvky Git sady Visual Studio a s oknem **Průzkumníka týmu,** ve kterém pracujete se slučovacím programem.

1. Zkontrolujte ovládací prvky Git v dolním rohu hlavního okna sady Visual Studio. Zleva doprava tyto ovládací prvky zobrazují nestisknuté revize, nepotvrzené změny, název úložiště a aktuální větev:

    ![Ovládací prvky Gitu v okně Sady Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Pokud v dialogovém okně **Nový projekt** nevyberete **vytvořit nové úložiště Git,** ovládací prvky Git zobrazí pouze příkaz **Přidat do správy zdrojového kódu,** který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v sadě Visual Studio, pokud jste nevytvořili úložiště](media/tutorials-common/step01-git-add-to-source-control.png)

1. Vyberte tlačítko Změny a Visual Studio otevře okno **Průzkumníka týmu** na stránce **Změny.** Vzhledem k tomu, že nově vytvořený projekt je již potvrzena správy zdrojového kódu automaticky, nevidíte žádné čekající změny.

    ![Okno Průzkumníktýmu na stránce Změny](media/flask/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio vyberte tlačítko nestisknuté potvrzení (šipka nahoru s **2)** a otevřete stránku **Synchronizace** v **Průzkumníkovi týmu**. Vzhledem k tomu, že máte pouze místní úložiště, stránka poskytuje jednoduché možnosti publikování úložiště do různých vzdálených úložišť.

    ![Okno Průzkumníktýmu zobrazující dostupné možnosti úložiště Git pro svoz zdrojového kódu](media/flask/step01-team-explorer.png)

    Můžete si vybrat, kterou službu chcete pro své vlastní projekty. Tento kurz ukazuje použití GitHubu, kde je dokončený ukázkový kód pro kurz udržován v úložišti [Microsoft/python-sample-vs-learning-baňka.](https://github.com/Microsoft/python-sample-vs-learning-flask)

1. Při výběru některého z ovládacích prvků **publikování** vás **Průzkumník týmu** vyzve k zadání dalších informací. Například při publikování ukázky pro tento kurz bylo nejprve vytvořeno samotné úložiště, v takovém případě byla s adresou URL úložiště použita možnost **Push to Remote Repository.**

    ![Okno Průzkumníka týmu pro odesílání do existujícího vzdáleného úložiště](media/flask/step01-push-to-github.png)

    Pokud nemáte existující úložiště, možnosti **Publikovat na GitHubu** a **Nabízení do Azure DevOps** umožňují vytvořit jedno přímo z Visual Studia.

1. Při práci prostřednictvím tohoto kurzu, získat do zvyku pravidelně pomocí ovládacích prvků v sadě Visual Studio potvrdit a nabízený změny. Tento kurz vám připomene na vhodných místech.

> [!Tip]
> Chcete-li rychle přejít v **Průzkumníkovi týmu**, vyberte záhlaví (které čte **Změny** nebo **Push** ve výše uvedených obrázcích) a zobrazí se rozbalovací nabídka dostupných stránek.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: Za prvé, pomocí správy zdrojového kódu od začátku, zejména pokud používáte také vzdálené úložiště, poskytuje pravidelné zálohování mimo pracoviště vašeho projektu. Na rozdíl od udržování projektu pouze v místním systému souborů poskytuje správou zdrojového kódu také úplnou historii změn a snadnou možnost vrátit jeden soubor nebo celý projekt do předchozího stavu. Tato historie změn pomáhá určit příčinu regrese (selhání testu). Kromě toho správy zdrojového kódu je nezbytné, pokud více lidí pracuje na projektu, protože spravuje přepíše a poskytuje řešení konfliktů. Konečně, správa zdrojového kódu, která je v podstatě formou automatizace, nastaví vám dobře pro automatizaci sestavení, testování a správu verzí. Je to opravdu první krok v používání DevOps pro projekt, a protože překážky vstupu jsou tak nízké, je tu opravdu žádný důvod, proč nepoužívat správě zdrojového kódu od začátku.

Další diskusi o správě zdrojového kódu jako automatizace najdete v článku O zdroji dat, který se vztahuje i na webové aplikace, najdete v článku o službě [Zdroj pravdy: Role úložišť v časopise DevOps](https://msdn.microsoft.com/magazine/mt763232).

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Lze zabránit visual studio automaticky pozavazovat nový projekt?

Odpověď: Ano. Chcete-li automatické posunutí zakázat, přejděte na stránku **Nastavení** v **Průzkumníkovi týmu**, vyberte**Globální nastavení** **Gitu** > , zrušte zaškrtnutí políčka **Potvrzení změn po sloučení ve výchozím nastavení**a pak vyberte **Aktualizovat**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Vytvoření virtuálního prostředí a jeho vyloučení ze správy zdrojového kódu

Nyní, když jste nakonfigurovali správě zdrojového kódu pro váš projekt, můžete vytvořit virtuální prostředí potřebné balíčky Flask, které projekt vyžaduje. Potom můžete pomocí **Průzkumníka týmu** vyloučit složku prostředí ze správy zdrojového kódu.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte **přidat virtuální prostředí**.

    ![Příkaz Přidat virtuální prostředí v Průzkumníku řešení](media/flask/step01-add-virtual-environment-command.png)

1. Zobrazí se dialogové okno **Přidat virtuální prostředí** se zprávou, že jsme našli soubor **requirements.txt.** Tato zpráva označuje, že Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Přidání dialogového okna virtuálního prostředí se zprávou requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Vyberte **Vytvořit,** chcete-li přijmout výchozí hodnoty. (Název virtuálního prostředí můžete změnit, pokud chcete, což pouze změní název `env` jeho podsložky, ale je standardní konvence.)

1. Souhlas s oprávněními správce, pokud se zobrazí výzva, pak buďte trpěliví po dobu několika minut, zatímco Visual Studio stahuje a instaluje balíčky, což pro Flask a jeho závislosti znamená rozšíření asi tisíc souborů ve více než 100 podsložkách. Průběh můžete vidět v okně Visual Studio **Output.** Zatímco čekáte, zamyslete se nad následujícími částmi otázek. Můžete také vidět popis závislosti Flask na instalační stránce [Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (flask.pcocoo.org).

1. Na ovládacích prvcích Git u Visual Studia (na stavovém řádku) vyberte indikátor změn (který zobrazuje **99&#42;), **který otevře stránku **Změny** v **Průzkumníkovi týmu**.

    Vytvoření virtuálního prostředí přinesl stovky změn, ale není nutné zahrnout žádné z nich do správy zdrojového kódu, protože vy (nebo kdokoli jiný klonování projektu) můžete vždy znovu vytvořit prostředí z *requirements.txt*.

    Chcete-li virtuální prostředí vyloučit, klepněte pravým tlačítkem myši na složku **env** a vyberte **ignorovat tyto místní položky**.

    ![Ignorování virtuálního prostředí při změnách správy zdrojového kódu](media/flask/step01-ignore-local-items.png)

1. Po vyloučení virtuálního prostředí jsou jedinými zbývajícími změnami soubor projektu a *.gitignore*. Soubor *.gitignore* obsahuje přidanou položku pro složku virtuálního prostředí. Můžete poklepat na soubor a zobrazit rozdíl.

1. Zadejte zprávu o potvrzení a vyberte tlačítko **Potvrdit vše** a pak je stlačte do vzdáleného úložiště, pokud chcete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: Proč chci vytvořit virtuální prostředí?

Odpověď: Virtuální prostředí je skvělý způsob, jak izolovat přesné závislosti aplikace. Tato izolace zabraňuje konfliktům v globálním prostředí Pythonu a pomáhá testování i spolupráci. V průběhu času, jak budete vyvíjet aplikaci, vždy přinést mnoho užitečných balíčků Pythonu. Udržováním balíčků ve virtuálním prostředí specifickém pro projekt můžete snadno aktualizovat soubor *requirements.txt* projektu, který popisuje toto prostředí, které je součástí správy zdrojového kódu. Pokud je projekt zkopírován do jiných počítačů, včetně serverů sestavení, serverů nasazení a dalších vývojových počítačů, je snadné znovu vytvořit prostředí pomocí pouze *requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace naleznete v tématu [Použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Jak lze odebrat virtuální prostředí, které se již zavázalo ke správě zdrojového kódu?

Odpověď: Nejprve upravte soubor *.gitignore,* abyste složku vyloučili: `# Python Tools for Visual Studio (PTVS)` najděte oddíl na konci s komentářem `/BasicProject/env`a přidejte nový řádek pro složku virtuálního prostředí, například . (Vzhledem k tomu, že Visual Studio nezobrazuje soubor v **Průzkumníku řešení**, otevřete jej přímo pomocí **příkazu** > nabídky Soubor**otevřít** > **soubor.** Soubor můžete také otevřít z **Průzkumníka týmu**: na stránce **Nastavení** vyberte **Nastavení úložiště**, přejděte do části Ignorovat **soubory atributů &** a pak vyberte odkaz **Upravit** vedle **.gitignore**.)

Za druhé, otevřete příkazové okno, přejděte do složky, jako je `git rm -r env` *BasicProject,* který obsahuje složku virtuálního prostředí, jako je *env*a spustit . Potom potvrďte tyto změny`git commit -m 'Remove venv'`z příkazového řádku ( ) nebo potvrzení ze stránky **Změny** **průzkumníka týmu**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Zkontrolujte často používaný kód

1. Po dokončení vytváření projektu se zobrazí řešení a projekt v **Průzkumníku řešení**, kde projekt obsahuje pouze dva soubory, *app.py* a *requirements.txt*:

    ![Soubory projektu Prázdné flask v Průzkumníku řešení](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak již bylo uvedeno dříve, soubor *requirements.txt* určuje závislost balíčku Flask. Přítomnost tohoto souboru je to, co vás vyzve k vytvoření virtuálního prostředí při prvním vytvoření projektu.

1. Jediný *soubor app.py* obsahuje tři části. První je `import` příkaz pro Flask, vytvoření `Flask` instance třídy, která `app`je přiřazena `wsgi_app` proměnné a pak přiřazení proměnné (což je užitečné při nasazování do webového hostitele, ale v současné době není použito):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druhá část na konci souboru je trochu volitelný kód, který spustí vývojový server Flask s konkrétními hodnotami hostitele a portu převzatými z proměnných prostředí (výchozí pro localhost:5555):

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

1. Třetí je krátký kousek kódu, který přiřazuje funkci k postupu adresy URL, což znamená, že funkce poskytuje prostředek identifikovaný adresou URL. Můžete definovat trasy pomocí Flask `@app.route` decorator, jehož argumentem je relativní adresa URL z kořenového adresáře webu. Jak můžete vidět v kódu, funkce zde vrátí pouze textový řetězec, který je dost pro prohlížeč k vykreslení. V následujících krocích vykreslíte bohatší stránky s HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Otázka: Jaký je účel argumentu __název__ třídy Flask?

Odpověď: Argument je název modulu nebo balíčku aplikace a říká Flask, kde hledat šablony, statické soubory a další prostředky, které patří do aplikace. Pro aplikace obsažené v jednom `__name__` modulu, je vždy správná hodnota. Je také důležité pro rozšíření, které potřebují ladění informací. Další informace a další argumenty naleznete v [dokumentaci třídy Flask](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Otázka: Může mít funkce více než jeden trasa decorator?

Odpověď: Ano, můžete použít tolik dekorátorů, kolik chcete, pokud stejná funkce slouží více tras. Chcete-li například `hello` použít funkci pro "/" a "/hello", použijte následující kód:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Otázka: Jak funguje Flask s variabilními směry URL a parametry dotazu?

Odpověď: V trase označíte libovolnou proměnnou `<variable_name>`pomocí aplikace a Flask předá proměnnou funkci pomocí pojmenovaného argumentu. Proměnná může být součástí cesty URL nebo v parametru dotazu. Například trasa ve formě `'/hello/<name>` generuje řetězec argument `name` volána do `?message=<msg>` funkce a pomocí v trase analyzuje hodnotu danou parametr dotazu "message=" a předá ji funkci jako `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Chcete-li změnit typ, předpona `int`proměnné s , `float`, `path` (který přijímá lomítka vymezit názvy složek) a `uuid`. Podrobnosti viz [Pravidla proměnných](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) v dokumentaci k flask.

Parametry dotazu jsou `request.args` také k dispozici `request.args.get` prostřednictvím vlastnosti, konkrétně prostřednictvím metody. Další informace naleznete [v tématu Request objekt](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) v dokumentaci flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: Může Visual Studio po instalaci dalších balíčků generovat soubor requirements.txt z virtuálního prostředí?

Odpověď: Ano. Rozbalte uzel **Prostředí Pythonu,** klikněte pravým tlačítkem myši na virtuální prostředí a vyberte příkaz **Generovat soubor requirements.txt.** Je vhodné používat tento příkaz pravidelně při úpravách prostředí a potvrzení změn *souboru requirements.txt* do správy zdrojového kódu spolu s dalšími změnami kódu, které závisí na daném prostředí. Pokud nastavíte průběžnou integraci na serveru sestavení, měli byste vygenerovat soubor a potvrdit změny při každé úpravě prostředí.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: Spuštění projektu

1. V sadě Visual Studio vyberte **možnost Ladění** > **zahájit ladění** **(F5)** nebo použijte tlačítko **Webového serveru** na panelu nástrojů (prohlížeč, který vidíte, se může lišit):

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Buď příkaz přiřadí proměnné prostředí PORT s náhodným číslem portu a poté spustí `python app.py`. Kód spustí aplikaci pomocí tohoto portu v rámci vývojového serveru Flask. Pokud visual studio **říká, že se nepodařilo spustit ladicí program** se zprávou o tom, že nemáte žádný spouštěcí soubor, klepněte pravým tlačítkem myši na **app.py** v **Průzkumníku řešení** a vyberte Nastavit jako **spouštěcí soubor**.

1. Při spuštění serveru se zobrazí okno konzoly, které zobrazuje protokol serveru. Visual Studio pak automaticky `http://localhost:<port>`otevře prohlížeč do , kde byste `hello` měli vidět zprávu vykreslenou funkcí:

    ![Výchozí zobrazení projektu Baňky](media/flask/step01-first-run-success.png)

1. Až budete hotovi, zastavte server zavřením okna konzoly nebo pomocí příkazu **Ladění** > **stop ladění** ladění v sadě Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím příkazů nabídky Ladění a příkazů serveru v podnabídce Pythonu projektu?

Odpověď: Kromě příkazů **nabídky Ladění** a tlačítek panelu nástrojů můžete také spustit server pomocí serveru **Python** > **Run** nebo příkazů serveru pro**ladění** **v** > kontextové nabídce projektu. Oba příkazy otevřou okno konzoly, ve kterém se zobrazí místní adresa URL (localhost:port) pro spuštěný server. Je však nutné ručně otevřít prohlížeč s tímto url a spuštěním ladicího serveru automaticky spustit ladicí program sady Visual Studio. Můžete připojit ladicí program ke spuštěnému procesu později, pokud chcete, pomocí **příkazu Připojit ladění** > **k procesu.**

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základní flask projekt obsahuje kód spuštění a kód stránky ve stejném souboru. Je vhodné oddělit tyto dvě obavy a také oddělit HTML a data pomocí šablon.

> [!div class="nextstepaction"]
> [Vytvoření aplikace Flask se zobrazeními a šablonami stránek](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Rychlý start baňky](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-baňka](https://github.com/Microsoft/python-sample-vs-learning-flask)
