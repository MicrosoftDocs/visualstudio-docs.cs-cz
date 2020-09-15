---
title: 'Rychlý Start: Vytvoření webové aplikace v Pythonu pomocí sady Visual Studio'
titleSuffix: ''
description: V tomto rychlém startu použijete Visual Studio a rozhraní baňce k sestavení jednoduché webové aplikace v Pythonu.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4318cd98de166210a8e8744840967942006b8ea6
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100510"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Rychlý Start: Vytvoření první webové aplikace v Pythonu pomocí sady Visual Studio

V tomto 5-10 minut úvodu do sady Visual Studio jako Python IDE vytvoříte jednoduchou webovou aplikaci v Pythonu na základě architektury baněk. Projekt vytvoříte prostřednictvím diskrétních kroků, které vám pomůžou naučit se základními funkcemi sady Visual Studio.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma. V instalačním programu se ujistěte, že jste vybrali úlohu **vývoje pro Python** .

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma. V instalačním programu se ujistěte, že jste vybrali úlohu **vývoje pro Python** .

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Následující kroky vytvoří prázdný projekt, který slouží jako kontejner pro aplikaci:

::: moniker range="vs-2017"
1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor > nový > projekt**.

3. V dialogovém okně **Nový projekt** zadejte do vyhledávacího pole v pravém horním rohu "webový projekt Python", v rozevíracím seznamu zvolte možnost **webový projekt** , zadejte název projektu jako "HelloPython" a pak zvolte **OK**.

    ![Dialogové okno Nový projekt s vybraným webovým projektem v Pythonu](media/quickstart-python-00-web-project.png)

    Pokud nevidíte šablony projektů Pythonu, spusťte **instalační program pro Visual Studio**, vyberte možnost **Další** > **Úpravy**, vyberte úlohu **vývoje** v jazyce Python a pak zvolte možnost **Upravit**.

    ![Úloha vývoje v Pythonu v instalačním programu sady Visual Studio](../python/media/installation-python-workload.png)

4. Nový projekt se otevře v **Průzkumník řešení** v pravém podokně. Projekt je v tomto okamžiku prázdný, protože neobsahuje žádné jiné soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otevřete Visual Studio 2019.
2. Na úvodní obrazovce vyberte **vytvořit nový projekt**.
3. V dialogovém okně **vytvořit nový projekt** zadejte do pole Hledat v horní části text "Python web", v rozevíracím seznamu zvolte **webový projekt** a potom vyberte **Další**:

    ![Vytvořit novou obrazovku projektu s vybraným webovým projektem v Pythonu](media/quickstart-python-00-web-project-2019a.png)

    Pokud nevidíte šablony projektů Pythonu, spusťte **instalační program pro Visual Studio**, vyberte možnost **Další** > **Úpravy**, vyberte úlohu **vývoje** v jazyce Python a pak zvolte možnost **Upravit**.

    ![Úloha vývoje v Pythonu v instalačním programu sady Visual Studio](../python/media/installation-python-workload.png)

4. V následujícím dialogovém okně **Konfigurace nového projektu** zadejte "HelloPython" pro **název projektu**, zadejte umístění a vyberte **vytvořit**. ( **Název řešení** se automaticky nastaví tak, aby odpovídal **názvu projektu**.)

    ![Dialogové okno Konfigurovat nový projekt](media/quickstart-python-00-web-project-2019b.png)

5. Nový projekt se otevře v **Průzkumník řešení** v pravém podokně. Projekt je v tomto okamžiku prázdný, protože neobsahuje žádné jiné soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Otázka: co je výhodou vytvoření projektu v aplikaci Visual Studio pro aplikaci Python?**

**Odpověď**: aplikace Pythonu se obvykle definují jenom pomocí složek a souborů, ale tato jednoduchá struktura se může zastarat, protože aplikace budou větší a možná budou zahrnovat automaticky generované soubory, JavaScript pro webové aplikace atd. Projekt sady Visual Studio pomáhá spravovat tuto složitost. Projekt (soubor *. pyproj* ) identifikuje všechny zdrojové a obsahové soubory přidružené k vašemu projektu, obsahuje informace o sestavení každého souboru, uchovává informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikace do logických komponent.

**Otázka: co je "řešení" zobrazeno v Průzkumník řešení?**

**Odpověď**: řešení sady Visual Studio je kontejner, který vám pomůže spravovat jeden nebo více souvisejících projektů jako skupinu a ukládá nastavení konfigurace, která nejsou specifická pro projekt. Projekty v řešení mohou také odkazovat na sebe, například při spuštění jednoho projektu (aplikace Python) automaticky vytvoří druhý projekt (například rozšíření C++ používané v aplikaci v Pythonu).

## <a name="install-the-flask-library"></a>Instalace knihovny baněk

Webové aplikace v Pythonu téměř vždy používají jednu z mnoha dostupných knihoven Python ke zpracování podrobností nízké úrovně, jako je směrování webových požadavků a reakce na tvarování. Pro účely tohoto účelu nabízí Visual Studio celou řadu šablon pro webové aplikace, z nichž jeden použijete později v tomto rychlém startu.

Tady použijete následující postup k instalaci knihovny baněk do výchozího "globálního prostředí", které Visual Studio používá pro tento projekt.

::: moniker range="vs-2017"
1. Rozbalením uzlu **prostředí Pythonu** v projektu zobrazíte výchozí prostředí pro projekt.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment.png)

2. Klikněte pravým tlačítkem na prostředí a vyberte **instalovat balíček python**. Tento příkaz otevře okno **prostředí Pythonu** na kartě **balíčky** .

3. Do vyhledávacího pole zadejte "baněk" a vyberte **PIP Install baněk z PyPI**. Přijměte všechny výzvy pro oprávnění správce a Prohlédněte si okno **výstup** v aplikaci Visual Studio a sledujte jeho průběh. (Výzva ke zvýšení oprávnění nastane, pokud se složka balíčků pro globální prostředí nachází v chráněné oblasti, jako je *C:\Program Files*.)

    ![Instalace knihovny baněk pomocí instalace PIP](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozbalením uzlu **prostředí Pythonu** v projektu zobrazíte výchozí prostředí pro projekt.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment-2019.png)

2. Klikněte pravým tlačítkem na prostředí a vyberte **Spravovat balíčky Pythonu...**. Tento příkaz otevře okno **prostředí Pythonu** na kartě **Packages (PyPi)** .

3. Do vyhledávacího pole zadejte "baněk". Pokud se objeví **baňka** pod vyhledávacím polem, můžete tento krok přeskočit. V opačném případě vyberte **Spustit příkaz: Instalační baňka PIP**. Přijměte všechny výzvy pro oprávnění správce a Prohlédněte si okno **výstup** v aplikaci Visual Studio a sledujte jeho průběh. (Výzva ke zvýšení oprávnění nastane, pokud se složka balíčků pro globální prostředí nachází v chráněné oblasti, jako je *C:\Program Files*.)

    ![Instalace knihovny baněk pomocí instalace PIP](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po nainstalování se knihovna zobrazí v prostředí v **Průzkumník řešení**, což znamená, že ji můžete využít v kódu Pythonu.

    ::: moniker range="vs-2017"
    ![Nainstalovaná a zobrazená knihovna baněk v Průzkumník řešení](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Nainstalovaná a zobrazená knihovna baněk v Průzkumník řešení](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Místo instalace knihoven v globálním prostředí vývojáři většinou vytvoří "virtuální prostředí", ve kterém se budou instalovat knihovny pro konkrétní projekt. Šablony sady Visual Studio obvykle nabízejí tuto možnost, jak je popsáno v tématu [rychlý Start – vytvoření projektu v Pythonu pomocí šablony](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Otázka: kde se dozvím Další informace o dalších dostupných balíčcích Pythonu?**

**Odpověď**: přejděte na [Rejstřík balíčku Pythonu](https://pypi.org/).

## <a name="add-a-code-file"></a>Přidat soubor kódu

Nyní jste připraveni přidat bitovou kopii kódu Pythonu pro implementaci minimální webové aplikace.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **Přidat > nová položka**.

1. V dialogovém okně, které se zobrazí, vyberte **prázdný soubor Pythonu**, pojmenujte ho *App.py*a vyberte **Přidat**. Visual Studio automaticky otevře soubor v okně editoru.

1. Zkopírujte následující kód a vložte ho do *App.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Možná jste si všimli, že dialogové okno **přidat > novou položku** zobrazí mnoho dalších typů souborů, které můžete přidat do projektu Pythonu, včetně třídy Python, balíčku Pythonu, testu jednotek Pythonu, *web.config* souborů a dalších. Obecně platí, že tyto šablony položek, jak jsou volány, představují skvělý způsob, jak rychle vytvořit soubory s užitečným často používaným kódem.

**Otázka: kde se mohu dozvědět více o baňce?**

**Odpověď**: Přečtěte si dokumentaci k baňce počínaje [rychlým startem baňky](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Spuštění aplikace

1. V **Průzkumník řešení** klikněte pravým tlačítkem na *App.py* a vyberte **nastavit jako spouštěcí soubor**. Tento příkaz identifikuje soubor kódu, který se spustí v Pythonu při spuštění aplikace.

    ::: moniker range="vs-2017"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumník řešení](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumník řešení](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **vlastnosti**. Pak vyberte kartu **ladit** a nastavte vlastnost **číslo portu** na `4449` . Tento krok zajistí, že Visual Studio spustí prohlížeč s `localhost:4449` , aby odpovídal `app.run` argumentům v kódu.

3. Vyberte **ladit > spustit bez ladění** (**CTRL** + **F5**), které uloží změny souborů a spustí aplikaci.

4. Zobrazí se okno příkazového řádku se zprávou, která **běží v protokolu https: \/ /localhost: 4449**, a otevře se okno prohlížeče, `localhost:4449` kde se zobrazí zpráva "Hello, Python!". Požadavek GET se také zobrazí v příkazovém okně se stavem 200.

    Pokud se prohlížeč neotevře automaticky, spusťte prohlížeč podle svého výběru a přejděte na `localhost:4449` .

    Pokud se v příkazovém okně zobrazí jenom interaktivní prostředí Pythonu nebo se toto okno na obrazovce krátce zabliká, ujistěte se, že jste v kroku 1 výše nastavili *App.py* jako spouštěcí soubor.

5. Přejděte na, `localhost:4449/hello` abyste otestovali, že dekoratér `/hello` prostředku taky funguje. Znovu se v příkazovém okně zobrazí požadavek GET se stavem 200. Nebojte se vyzkoušet jinou adresu URL a také zjistit, že v příkazovém okně zobrazují stavové kódy 404.

6. Zavřete okno příkaz a zastavte aplikaci a zavřete okno prohlížeče.

**Otázka: Jaký je rozdíl mezi příkazem spustit bez ladění a spustit ladění?**

**Odpověď**: pomocí možnosti **Spustit ladění** spustíte aplikaci v kontextu [ladicího programu sady Visual Studio](../python/debugging-python-in-visual-studio.md), což vám umožní nastavovat zarážky, prozkoumávat proměnné a krokovat kód podle řádku. Aplikace můžou běžet pomaleji v ladicím programu kvůli různým zavěšením, který umožňuje ladění. **Spusťte bez ladění**, na rozdíl od toho aplikace spouští přímo jako při spuštění z příkazového řádku bez kontextu ladění a také automaticky spustí prohlížeč a přejde na adresu URL zadanou na kartě **ladění** vlastností projektu.

## <a name="next-steps"></a>Další kroky

Blahopřejeme ke spuštění první aplikace v Pythonu ze sady Visual Studio, ve které jste se seznámili s používáním sady Visual Studio jako Python IDE!

> [!div class="nextstepaction"]
> [Nasazení aplikace do Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Vzhledem k tomu, že kroky, které jste provedli v tomto rychlém startu, jsou poměrně obecné, pravděpodobně jste se seznámili s tím, že by mohly být a Tato automatizace je role šablon projektů sady Visual Studio. Projděte si [rychlý Start – vytvoření projektu v Pythonu pomocí šablony](../python/quickstart-02-python-in-visual-studio-project-from-template.md) pro ukázku, která vytvoří webovou aplikaci podobnou té, kterou jste vytvořili v tomto článku, ale s menším počtem kroků.

Pokud chcete pokračovat v úplném kurzu na Pythonu v aplikaci Visual Studio, včetně použití interaktivního okna, ladění, vizualizace dat a práce s Git, Projděte si [kurz: Začínáme s Pythonem v aplikaci Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Pokud chcete prozkoumat další možnosti, které Visual Studio nabízí, vyberte odkazy níže.

- Seznamte [se se šablonami webových aplikací v Pythonu v aplikaci Visual Studio](../python/python-web-application-project-templates.md).
- Další informace o [ladění Pythonu](../python/debugging-python-in-visual-studio.md)
- Další informace o [integrovaném vývojovém prostředí sady Visual Studio](../get-started/visual-studio-ide.md) najdete v části Obecné.
