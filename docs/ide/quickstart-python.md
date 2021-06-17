---
title: 'Rychlý start: Vytvoření webové aplikace v Pythonu pomocí Visual Studio'
titleSuffix: ''
description: V tomto rychlém startu použijete Visual Studio a rozhraní Flask k vytvoření jednoduché webové aplikace v Pythonu.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom:
- acquisition
- SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 1cefae42025407e0252b5aedc28e979e0d86debc
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113176"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Rychlý start: Vytvoření první webové aplikace v Pythonu pomocí Visual Studio

V tomto 5 až 10minutových úvodu Visual Studio prostředí IDE Pythonu vytvoříte jednoduchou webovou aplikaci v Pythonu založenou na rozhraní Flask. Projekt vytvoříte pomocí samostatných kroků, které vám pomůžou Visual Studio základních funkcích projektu.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma. V instalačním programu nezapomeňte vybrat úlohu **Vývoj v Pythonu.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma. V instalačním programu nezapomeňte vybrat úlohu **Vývoj v Pythonu.**

::: moniker-end

## <a name="create-the-project"></a>Vytvoření projektu

Následující kroky vytvoří prázdný projekt, který slouží jako kontejner pro aplikaci:

::: moniker range="vs-2017"
1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **File (Soubor) > New > Project (Nový projekt).**

3. V dialogovém **okně** Nový projekt zadejte do vyhledávacího pole v pravém  horním rohu "Webový projekt Pythonu", v prostředním seznamu zvolte Webový projekt, zadejte název projektu, například HelloPython, a pak zvolte **OK.**

    ![Dialogové okno Nový projekt s vybraným webovým projektem Pythonu](media/quickstart-python-00-web-project.png)

    Pokud nevidíte šablony projektů Pythonu, spusťte **příkaz Instalační program pro Visual Studio**  , vyberte Další úpravy, vyberte úlohu > Vývoj **v Pythonu** a pak zvolte **Upravit.**

    ![Úloha vývoj pro Python v instalačním Visual Studio souborů](../python/media/installation-python-workload.png)

4. Nový projekt se otevře v **Průzkumník řešení** v pravém podokně. Projekt je v tuto chvíli prázdný, protože neobsahuje žádné další soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Otevřete Visual Studio 2019.
2. Na úvodní obrazovce vyberte **Create a new project (Vytvořit nový projekt).**
3. V **dialogovém okně Vytvořit** nový projekt zadejte do vyhledávacího pole v  horní části "Python web", v prostředním seznamu zvolte Webový projekt a pak vyberte **Další:**

    ![Obrazovka pro vytvoření nového projektu s vybraným webovým projektem v Pythonu](media/quickstart-python-00-web-project-2019a.png)

    Pokud nevidíte šablony projektů Pythonu, spusťte **příkaz Instalační program pro Visual Studio**  , vyberte Další úpravy, vyberte úlohu > Vývoj **v Pythonu** a pak zvolte **Upravit.**

    ![Úloha vývoj pro Python v instalačním Visual Studio souborů](../python/media/installation-python-workload.png)

4. V následujícím dialogovém okně Configure **your new project** (Konfigurace nového projektu) jako Project **name**(Název projektu) zadejte "HelloPython", zadejte umístění a vyberte **Create (Vytvořit).** (Název **řešení se** automaticky nastaví tak, aby odpovídal názvu **projektu**.)

    ![Dialogové okno Konfigurace nového projektu](media/quickstart-python-00-web-project-2019b.png)

5. Nový projekt se otevře v **Průzkumník řešení** v pravém podokně. Projekt je v tuto chvíli prázdný, protože neobsahuje žádné další soubory.

    ![Průzkumník řešení zobrazující nově vytvořený prázdný projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Otázka: Jaká je výhoda vytvoření projektu v Visual Studio pro aplikaci v Pythonu?**

**Odpověď:** Aplikace Pythonu se obvykle definují jenom pomocí složek a souborů, ale tato jednoduchá struktura může být zatěžující, když se aplikace zvětšují a mohou zahrnovat automaticky generované soubory, JavaScript pro webové aplikace atd. Tuto Visual Studio spravuje projekt projektu. Projekt (soubor *.pyproj)* identifikuje všechny zdrojové soubory a soubory obsahu přidružené k projektu, obsahuje informace o sestavení pro každý soubor, udržuje informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikaci do logických komponent.

**Otázka: Jaké řešení se v Průzkumník řešení?**

**Odpověď:** Visual Studio řešení je kontejner, který pomáhá spravovat jeden nebo více souvisejících projektů jako skupinu a ukládá nastavení konfigurace, která nejsou specifická pro projekt. Projekty v řešení se také mohou navzájem odkazovat, takže spuštění jednoho projektu (aplikace v Pythonu) automaticky sestaví druhý projekt (například rozšíření C++, které se používá v aplikaci v Pythonu).

## <a name="install-the-flask-library"></a>Instalace knihovny Flask

Webové aplikace v Pythonu téměř vždy používají jednu z mnoha dostupných knihoven Pythonu ke zpracování podrobností nízké úrovně, jako je směrování webových požadavků a formování odpovědí. Pro tento účel Visual Studio celou řadu šablon pro webové aplikace, z nichž jednu použijete později v tomto rychlém startu.

Tady pomocí následujících kroků nainstalujete knihovnu Flask do výchozího globálního prostředí, které Visual Studio tento projekt používá.

::: moniker range="vs-2017"
1. Rozbalte **uzel Prostředí Pythonu** v projektu a zobrazte výchozí prostředí projektu.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment.png)

2. Klikněte pravým tlačítkem na prostředí a vyberte **Install Python Package (Nainstalovat balíček Pythonu).** Tento příkaz otevře okno **Prostředí Pythonu** na kartě **Balíčky.**

3. Do vyhledávacího pole zadejte flask a z **PyPI vyberte pip install flask.** Přijměte všechny výzvy k oprávněním správce a sledujte **průběh** Visual Studio okně Výstup. (Výzva ke zvýšení oprávnění nastane, když se složka balíčků pro globální prostředí nachází v chráněné oblasti, jako *je C:\Program Files.)*

    ![Instalace knihovny Flask pomocí instalace pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Rozbalte **uzel Prostředí Pythonu** v projektu a zobrazte výchozí prostředí projektu.

    ![Průzkumník řešení zobrazující výchozí prostředí](media/quickstart-python-02-default-environment-2019.png)

2. Klikněte pravým tlačítkem na prostředí a vyberte **Spravovat balíčky Pythonu...**. Tento příkaz otevře okno **Prostředí Pythonu** na kartě **Balíčky (PyPI).**

3. Do vyhledávacího pole zadejte "flask". Pokud **se Flask** zobrazí pod vyhledávacím polem, můžete tento krok přeskočit. Jinak vyberte **Spustit příkaz: pip install flask**. Přijměte všechny výzvy k oprávněním správce a sledujte **průběh** Visual Studio okně Výstup. (Výzva ke zvýšení oprávnění nastane, když se složka balíčků pro globální prostředí nachází v chráněné oblasti, jako *je C:\Program Files.)*

    ![Instalace knihovny Flask pomocí instalace pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Po instalaci se knihovna zobrazí v prostředí Průzkumník řešení **,** což znamená, že ji můžete využít v kódu Pythonu.

    ::: moniker range="vs-2017"
    ![Nainstalovaná knihovna Flask, která se zobrazuje Průzkumník řešení](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Nainstalovaná knihovna Flask, která se zobrazuje Průzkumník řešení](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Místo instalace knihoven v globálním prostředí vývojáři obvykle vytvoří "virtuální prostředí", ve kterém instaluje knihovny pro konkrétní projekt. Visual Studio šablony obvykle nabízejí tuto možnost, jak je popsáno v tématu Rychlý start – Vytvoření projektu [Pythonu pomocí šablony](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Otázka: Kde se dozvím další informace o dalších dostupných balíčcích Pythonu?**

**Odpověď:** Navštivte index [balíčků Pythonu.](https://pypi.org/)

## <a name="add-a-code-file"></a>Přidání souboru kódu

Teď jste připraveni přidat kód Pythonu, který implementuje minimální webovou aplikaci.

1. Klikněte pravým tlačítkem na projekt **v Průzkumník řešení** a vyberte Add > New Item (Přidat **novou položku).**

1. V dialogovém okně, které se zobrazí, vyberte Prázdný soubor **Pythonu,** pojmete *ho app.py* a vyberte **Přidat.** Visual Studio automaticky otevře soubor v okně editoru.

1. Zkopírujte následující kód a vložte ho *do app.py*:

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

1. Možná jste si všimli, že **dialogové okno** Přidat novou položku > zobrazuje mnoho dalších typů souborů, které můžete přidat do projektu Pythonu, včetně třídy Pythonu, balíčku Pythonu, testu jednotek Pythonu, *souborůweb.config* a dalších. Obecně platí, že tyto šablony položek, jak se nazývají, jsou skvělým způsobem, jak rychle vytvářet soubory s užitečným často používaným kódem.

**Otázka: Kde se o Flasku dozvím více?**

**Odpověď:** Projděte si dokumentaci ke Flasku a začněte rychlým startem [pro Flask.](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte pravým *tlačítkem na app.py* v **Průzkumník řešení** a vyberte Nastavit jako **spouštěcí soubor**. Tento příkaz identifikuje soubor kódu, který se má spustit v Pythonu při spuštění aplikace.

    ::: moniker range="vs-2017"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumník řešení](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Nastavení spouštěcího souboru pro projekt v Průzkumník řešení](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Klikněte pravým tlačítkem na projekt **v Průzkumník řešení** a vyberte **Vlastnosti**. Pak vyberte **kartu Debug (Ladění)** a vlastnost Port **Number (Číslo portu) nastavte** na `4449` . Tento krok zajistí, Visual Studio spustí prohlížeč s , aby odpovídal `localhost:4449` `app.run` argumentům v kódu.

3. Vyberte **Ladit > Spustit bez ladění** (**Ctrl** + **F5**), který uloží změny souborů a spustí aplikaci.

4. Zobrazí se příkazové okno se zprávou Spuštěno v **https: \/ /localhost:4449** a mělo by se otevřít okno prohlížeče, kde se zobrazí zpráva `localhost:4449` "Hello, Python!" Požadavek GET se zobrazí také v příkazovém okně se stavem 200.

    Pokud se prohlížeč neotevře automaticky, spusťte prohlížeč podle svého výběru a přejděte na `localhost:4449` .

    Pokud se v příkazovém okně zobrazí pouze interaktivní prostředí Pythonu nebo pokud toto okno  krátce bliká na obrazovce, ujistěte se, že jste v kroku 1 výše nastavili app.py jako spouštěcí soubor.

5. Přejděte na `localhost:4449/hello` a otestujte, že dekorátor `/hello` pro prostředek funguje také. Požadavek GET se znovu zobrazí v příkazovém okně se stavem 200. Nebojte se vyzkoušet i jinou adresu URL, abyste viděli, že se v příkazovém okně zobrazí stavové kódy 404.

6. Zavřete příkazové okno, aby se aplikace zastavila, a pak zavřete okno prohlížeče.

**Otázka: Jaký je rozdíl mezi příkazem Spustit bez ladění a Spustit ladění?**

**Odpověď:** Ke  spuštění aplikace v kontextu ladicího programu Visual Studio použijete možnost Spustit [ladění,](../python/debugging-python-in-visual-studio.md)která umožňuje nastavit zarážky, zkoumat proměnné a krokovat kód řádek po řádku. Aplikace mohou v ladicím programu běžet pomaleji kvůli různým hookům, které umožňuje ladění. **Funkce** Spustit bez ladění naopak spustí aplikaci přímo, jako kdybyste ji spustili z příkazového řádku bez kontextu ladění, automaticky také spustí prohlížeč a přejde na adresu URL zadanou na kartě Ladění vlastností **projektu.**

## <a name="next-steps"></a>Další kroky

Blahopřejeme ke spuštění první aplikace v Pythonu Visual Studio, ve které jste se trochu naučili používat Visual Studio prostředí IDE Pythonu!

> [!div class="nextstepaction"]
> [Nasazení aplikace do Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Vzhledem k tomu, že kroky, které jste v tomto rychlém startu postupli, jsou poměrně obecné, pravděpodobně jste odhadli, že je možné a měli byste je automatizovat. Taková automatizace je role Visual Studio projektů. Projít rychlý start – Vytvoření projektu [Pythonu](../python/quickstart-02-python-in-visual-studio-project-from-template.md) pomocí šablony pro ukázku, která vytvoří webovou aplikaci podobnou té, kterou jste vytvořili v tomto článku, ale s menším počtem kroků.

Pokud chcete pokračovat v plnohodnotnějším kurzu o Pythonu v Visual Studio, včetně použití interaktivního okna, ladění, vizualizace dat a práce s Gitem, projděte si [Kurz: Začínáme](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)s Pythonem v Visual Studio .

Pokud chcete prozkoumat další Visual Studio, které nabízí, vyberte následující odkazy.

- Další informace o [šablonách webových aplikací v Pythonu Visual Studio](../python/python-web-application-project-templates.md).
- Další informace o [ladění Pythonu](../python/debugging-python-in-visual-studio.md)
- Přečtěte si další informace [o Visual Studio IDE](../get-started/visual-studio-ide.md) obecně.
