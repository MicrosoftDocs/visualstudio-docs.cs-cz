---
title: 'Úvodní příručka: Vytvoření webové aplikace pythonu pomocí Visual Studia'
description: V tomto rychlém startu použijete Visual Studio a architekturu Flask k vytvoření jednoduché webové aplikace v Pythonu.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: cbb06ac800fd21e2354b04fb2e7e46306da7ed72
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180352"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Úvodní příručka: Vytvoření první webové aplikace Pythonu pomocí Visual Studia

V tomto 5-10 minut úvod do Visual Studia jako Python IDE, můžete vytvořit jednoduchou webovou aplikaci Python unavované na rámci Flask. Projekt můžete vytvořit pomocí diskrétních kroků, které vám pomohou získat informace o základních funkcích sady Visual Studio.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma. V instalačním programu nezapomeňte vybrat vývojové zatížení **Pythonu.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma. V instalačním programu nezapomeňte vybrat vývojové zatížení **Pythonu.**

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Následující kroky vytvoří prázdný projekt, který slouží jako kontejner pro aplikaci:

::: moniker range="vs-2017"
1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor > Nový > Project**.

3. V dialogovém okně **Nový projekt** zadejte do vyhledávacího pole v pravém horním horním poli "Python Web Project", v prostředním seznamu zvolte **Webový projekt,** pojmenujte projekt jako "HelloPython" a pak zvolte **OK**.

    ![Dialogové okno Nový projekt s vybranou možností Webového projektu Pythonu](media/quickstart-python-00-web-project.png)

    Pokud šablony projektu Pythonu nevidíte, spusťte **Instalační službu Visual Studia**, vyberte **Další** > **úpravy**, vyberte **vývojové úlohy Pythonu** a pak zvolte **Změnit**.

    ![Úloha vývoje Pythonu v instalačním programu Visual Studia](../python/media/installation-python-workload.png)

4. Nový projekt se otevře v **Průzkumníku řešení** v pravém podokně. Projekt je prázdný v tomto okamžiku, protože neobsahuje žádné další soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otevřete Visual Studio 2019.
2. Na úvodní obrazovce vyberte **Vytvořit nový projekt**.
3. V **dialogovém** okně Vytvořit nový projekt zadejte do vyhledávacího pole v horní části "Web pythonu", v prostředním seznamu zvolte **Webový projekt** a pak vyberte **Další**:

    ![Vytvoření nové obrazovky projektu s vybranou možností Webového projektu Pythonu](media/quickstart-python-00-web-project-2019a.png)

    Pokud šablony projektu Pythonu nevidíte, spusťte **Instalační službu Visual Studia**, vyberte **Další** > **úpravy**, vyberte **vývojové úlohy Pythonu** a pak zvolte **Změnit**.

    ![Úloha vývoje Pythonu v instalačním programu Visual Studia](../python/media/installation-python-workload.png)

4. V následujícím **dialogovém okně Konfigurovat nový projekt** zadejte "HelloPython" pro název **projektu**, zadejte umístění a vyberte **Vytvořit**. (Název **řešení** je automaticky nastaven tak, aby odpovídal **názvu projektu**.)

    ![Konfigurace dialogového okna nového projektu](media/quickstart-python-00-web-project-2019b.png)

5. Nový projekt se otevře v **Průzkumníku řešení** v pravém podokně. Projekt je prázdný v tomto okamžiku, protože neobsahuje žádné další soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Otázka: Jaká je výhoda vytvoření projektu v sadě Visual Studio pro aplikaci Pythonu?**

**Odpověď**: Aplikace Pythonu jsou obvykle definovány pouze pomocí složek a souborů, ale tato jednoduchá struktura se může stát zatěžující, protože aplikace se zvětšují a možná zahrnují automaticky generované soubory, JavaScript pro webové aplikace a tak dále. Projekt sady Visual Studio pomáhá spravovat tuto složitost. Projekt (soubor *Pyproj)* identifikuje všechny zdrojové a obsahové soubory přidružené k projektu, obsahuje informace o sestavení pro každý soubor, udržuje informace pro integraci se systémy správy zdrojového kódu a pomáhá uspořádat aplikaci do logických součástí.

**Otázka: Jaké je "řešení" zobrazené v Průzkumníku řešení?**

**Odpověď**: Řešení sady Visual Studio je kontejner, který vám pomůže spravovat jeden nebo více souvisejících projektů jako skupinu a ukládá nastavení konfigurace, která nejsou specifická pro projekt. Projekty v řešení mohou také odkazovat jeden na druhého, tak, že spuštění jednoho projektu (aplikace Python) automaticky vytvoří druhý projekt (například rozšíření C++ používané v aplikaci Python).

## <a name="install-the-flask-library"></a>Instalace knihovny Flask

Webové aplikace v Pythonu téměř vždy používají jednu z mnoha dostupných knihoven Pythonu ke zpracování podrobností nízké úrovně, jako je směrování webových požadavků a tvarování odpovědí. Pro tento účel Visual Studio poskytuje různé šablony pro webové aplikace, z nichž jeden, který použijete později v tomto rychlém startu.

Zde použijete následující kroky k instalaci knihovny Flask do výchozího "globálního prostředí", které visual studio používá pro tento projekt.

::: moniker range="vs-2017"
1. Rozbalte uzel **Prostředí Pythonu** v projektu a zobceme výchozí prostředí projektu.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment.png)

2. Klepněte pravým tlačítkem myši na prostředí a vyberte **nainstalovat balíček Pythonu**. Tento příkaz otevře okno **Prostředí Pythonu** na kartě **Balíčky.**

3. Do vyhledávacího pole se zadejte "baňka" a z PyPI se vybere **pip instalovaná baňka**. Přijímejte všechny výzvy k zadání oprávnění správce a sledujte, jak se v sadě Visual Studio postupuje v okně **Výstup** v sadě Visual Studio. (Výzva ke zvýšení oprávnění se stane, když je složka balíčků pro globální prostředí umístěna v chráněné oblasti, jako je *C:\Program Files*.)

    ![Instalace knihovny Flask pomocí pip install](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozbalte uzel **Prostředí Pythonu** v projektu a zobceme výchozí prostředí projektu.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment-2019.png)

2. Klikněte pravým tlačítkem myši na prostředí a vyberte **Spravovat balíčky Pythonu...**. Tento příkaz otevře okno **Prostředí Pythonu** na kartě **Balíčky (PyPI).**

3. Do vyhledávacího pole zadejte "baňku". Pokud se pod vyhledávacím polem zobrazí **Flask,** můžete tento krok přeskočit. V opačném případě zvolte **Spustit, příkaz: pip nainstalovat baňku**. Přijímejte všechny výzvy k zadání oprávnění správce a sledujte, jak se v sadě Visual Studio postupuje v okně **Výstup** v sadě Visual Studio. (Výzva ke zvýšení oprávnění se stane, když je složka balíčků pro globální prostředí umístěna v chráněné oblasti, jako je *C:\Program Files*.)

    ![Instalace knihovny Flask pomocí pip install](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po instalaci se knihovna zobrazí v prostředí v **Průzkumníku řešení**, což znamená, že ji můžete využít v kódu Pythonu.

    ::: moniker range="vs-2017"
    ![Knihovna baňek nainstalovaná a zobrazená v Průzkumníku řešení](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Knihovna baňek nainstalovaná a zobrazená v Průzkumníku řešení](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Namísto instalace knihoven v globálním prostředí vývojáři obvykle vytvářejí "virtuální prostředí", ve kterém mají instalovat knihovny pro konkrétní projekt. Šablony sady Visual Studio obvykle nabízejí tuto možnost, jak je popsáno v [úvodním panelu – vytvoření projektu Pythonu pomocí šablony](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Otázka: Kde se dozvím více o dalších dostupných balíčcích Pythonu?**

**Odpověď**: Navštivte [index balíčků pythonu](https://pypi.org/).

## <a name="add-a-code-file"></a>Přidání souboru kódu

Nyní jste připraveni přidat trochu kódu Pythonu k implementaci minimální webové aplikace.

1. Klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **přidat > novou položku**.

1. V zobrazeném dialogovém okně vyberte **Vyprázdnit soubor pythonu**, pojmenujte ho *app.py*a vyberte **Přidat**. Visual Studio automaticky otevře soubor v okně editoru.

1. Zkopírujte následující kód a vložte jej do *app.py*:

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

1. Možná jste si všimli, že dialogové okno **Přidat > novou položku** zobrazuje mnoho dalších typů souborů, které můžete přidat do projektu Pythonu, včetně třídy Python, balíčku Pythonu, testu částí Pythonu, souborů *web.config* a dalších. Obecně platí, že tyto šablony položek, jak se nazývají, jsou skvělý majek lze rychle vytvářet soubory s užitečným často používaným kódem.

**Otázka: Kde se mohu dozvědět více o Flask?**

**Odpověď**: Viz dokumentace k baňce, počínaje [rychlým startem baňky](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Spuštění aplikace

1. Klepněte *app.py* pravým tlačítkem myši app.py v **Průzkumníku řešení** a vyberte nastavit jako **spouštěcí soubor**. Tento příkaz identifikuje soubor kódu, který se má spustit v Pythonu při spuštění aplikace.

    ::: moniker range="vs-2017"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumníku řešení](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumníku řešení](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**. Potom vyberte kartu **Ladění** a nastavte `4449`vlastnost **Číslo portu** na . Tento krok zajišťuje, že Visual Studio `localhost:4449` spustí `app.run` prohlížeč s tak, aby odpovídaly argumenty v kódu.

3. Vyberte **možnost Ladění > Spustit bez ladění** (**Ctrl**+**F5**), která ukládá změny souborů a spouští aplikaci.

4. Zobrazí se příkazové okno se <https://localhost:4449/>zprávou *Spuštěno v `localhost:4449` "a okno prohlížeče by se mělo otevřít tam, kde se zobrazí zpráva "Hello, Python!" Požadavek GET se také zobrazí v příkazovém okně se stavem 200.

    Pokud se prohlížeč neotevře automaticky, spusťte prohlížeč `localhost:4449`podle vašeho výběru a přejděte na .

    Pokud se v příkazovém okně zobrazí pouze interaktivní prostředí Pythonu nebo pokud toto okno krátce bliká na obrazovce, ujistěte se, že jste *nastavili app.py* jako spouštěcí soubor v kroku 1 výše.

5. Přejděte `localhost:4449/hello` na test, který `/hello` decorator pro prostředek také funguje. Požadavek GET se opět zobrazí v příkazovém okně se stavem 200. Nebojte se vyzkoušet nějaké jiné URL, stejně vidět, že ukazují 404 stavové kódy v příkazovém okně.

6. Zavřete příkazové okno, chcete-li aplikaci zastavit, a pak zavřete okno prohlížeče.

**Otázka: Jaký je rozdíl mezi příkazem Start Without Debugging a Start Debugging?**

**Odpověď**: Pomocí **spuštění ladění** spustit aplikaci v kontextu [ladicího programu Sady Visual Studio](../python/debugging-python-in-visual-studio.md), což umožňuje nastavit zarážky, zkoumat proměnné a krokovat kód řádek po řádku. Aplikace může běžet pomaleji v ladicím programu z důvodu různých háčků, které umožňují ladění. **Spustit bez ladění**, naopak spustí aplikaci přímo, jako kdybyste ji spustili z příkazového řádku bez kontextu ladění, a také automaticky spustí prohlížeč a přejde na adresu URL zadanou na kartě **Ladění** vlastností projektu.

## <a name="next-steps"></a>Další kroky

Blahopřejeme vám ke spuštění první aplikace Pythonu z Visual Studia, ve které jste se naučili něco málo o použití Visual Studia jako IDE pythonu!

> [!div class="nextstepaction"]
> [Nasazení aplikace do služby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Vzhledem k tomu, že kroky, které jste postupovali v tomto rychlém startu, jsou poměrně obecné, pravděpodobně jste uhodli, že mohou a měly by být automatizovány. Tato automatizace je role šablon projektů sady Visual Studio. Projděte [si úvodní příručku – vytvořte projekt Pythonu pomocí šablony](../python/quickstart-02-python-in-visual-studio-project-from-template.md) pro ukázku, která vytvoří webovou aplikaci podobnou té, kterou jste vytvořili v tomto článku, ale s menším počtem kroků.

Chcete-li pokračovat s plnější kurz o Pythonu v sadě Visual Studio, včetně použití interaktivního okna, ladění, vizualizace dat a práce s Gitem, projděte [si kurz: Začínáme s Pythonem v sadě Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Chcete-li prozkoumat další, které Visual Studio nabízí, vyberte níže uvedené odkazy.

- Další informace o [šablonách webových aplikací pythonu ve Visual Studiu](../python/python-web-application-project-templates.md).
- Další informace o [ladění Pythonu](../python/debugging-python-in-visual-studio.md)
- Další informace o [ide Visual Studio](../get-started/visual-studio-ide.md) obecně.
