---
title: Přehled Visual Studia pro vývojáře Pythonu
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b8b656aaefe4440e811378da2b84d1b944d4fb1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73661935"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Vítá vás ide sady Visual Studio | Python

*Integrované vývojové prostředí* visual studia je kreativní spouštěcí panel pro Python (a další jazyky), který můžete použít k úpravám, ladění a testování kódu a následnému publikování aplikace. Integrované vývojové prostředí (IDE) je program bohatý na funkce, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardního editoru a ladicího programu, které poskytuje většina IDE, sada Visual Studio obsahuje nástroje pro dokončení kódu, interaktivní prostředí REPL a další funkce pro usnadnění procesu vývoje softwaru.

[![Visual Studio s projektem Pythonu](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Tento obrázek znázorňuje Visual Studio s otevřeným projektem Pythonu a několika klíčovými okny nástrojů, která budete pravděpodobně používat:

- [**Průzkumník řešení**](../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, procházet a spravovat soubory kódu. **Průzkumník řešení** může pomoci uspořádat kód seskupením souborů do [řešení a projektů](../get-started/tutorial-projects-solutions.md).
  - Vedle **Průzkumníka řešení** je [**Python Environments**](managing-python-environments-in-visual-studio.md), kde spravujete různé interprety Pythonu, které jsou nainstalovány ve vašem počítači.

  ::: moniker range=">=vs-2019"
  - Můžete také otevřít a spustit kód Pythonu ve složce bez vytváření souborů projektu a řešení sady Visual Studio. Další informace naleznete v [tématu Úvodní příručka: Otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- [Okno editoru](../ide/writing-code-in-the-code-and-text-editor.md) (uprostřed), kde pravděpodobně strávíte většinu svého času, zobrazuje obsah souboru. Toto je místo, kde [můžete upravovat kód Pythonu](editing-python-code-in-visual-studio.md), procházet v rámci struktury kódu a nastavit zarážky během ladění relací. V Pythonu můžete také vybrat kód a stisknutím kombinace kláves Ctrl+Enter spustit tento kód v [interaktivním okně REPL](python-interactive-repl-in-visual-studio.md).

- [Okno Výstup](../ide/reference/output-window.md) (dolní centrum) je místo, kde Visual Studio odesílá oznámení, jako je ladění a chybové zprávy, upozornění, zprávy o stavu publikování a další. Každý zdroj zprávy má vlastní kartu.
  - [Okno Interaktivní REPL pythonu](python-interactive-repl-in-visual-studio.md) se zobrazí ve stejné oblasti jako okno Výstup.

- [Průzkumník týmu](/azure/devops/user-guide/work-team-explorer?view=vsts) (vpravo dole) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií správy verzí, jako je [Git](https://git-scm.com/) a Team Foundation Version [Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edice

Visual Studio je k dispozici pro Windows a Mac; Podpora Pythonu je však k dispozici pouze v sadě Visual Studio pro Windows.

Existují tři edice sady Visual Studio v systému Windows: Komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v [tématu Porovnání idů sady Visual Studio.](https://visualstudio.microsoft.com/vs/compare/)

## <a name="popular-productivity-features"></a>Oblíbené funkce produktivity

Některé z oblíbených funkcí v sadě Visual Studio, které vám pomohou být produktivnější při vývoji softwaru, zahrnují:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech za vás píší malé kousky kódu. Je to jako mít základní dokumentaci veditoru v editoru, který vám ušetří od nutnosti hledat informace o typu jinde. Funkce IntelliSense se liší podle jazyka a článek [o úpravách kódu Pythonu](editing-python-code-in-visual-studio.md#intellisense) obsahuje podrobnosti pro Python. Následující obrázek znázorňuje, jak technologie IntelliSense zobrazuje seznam členů pro daný typ:

   ![Dokončení členství pomocí technologie Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refactoring](refactoring-python-code.md)

   Kliknutím pravým tlačítkem myši na část kódu a výběrem **rychlých akcí a refaktoringů**poskytuje sada Visual Studio operace, jako je inteligentní přejmenování proměnných, extrahování jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Analyzování kódu](refactoring-python-code.md)

   Linting kontroluje chyby a běžné problémy v kódu Pythonu, což vás povzbuzuje s dobrými vzory kódování Pythonu.

   ![Příkaz PyLint v kontextové nabídce pro projekty Pythonu](media/code-pylint-command.png)

- Vyhledávací pole

   Visual Studio může zdát ohromující občas s tolika nabídky, možnosti a vlastnosti. Vyhledávací pole je skvělý způsob, jak rychle najít to, co potřebujete v sadě Visual Studio. Když začnete psát název něčeho, co hledáte, Visual Studio zobrazí seznam výsledků, které vás přesně přemístí tam, kam potřebujete. Pokud potřebujete přidat funkce do sady Visual Studio, například pro přidání podpory pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační služba sady Visual Studio pro instalaci pracovního vytížení nebo jednotlivé součásti.

   ![Vyhledávací pole ve Visual Studiu](media/tour-ide-quick-launch.png)

- Klikyháky a [rychlé akce](../ide/quick-actions.md)

   Vlnité vlnovky jsou podtržení vlnovkou, která vás při psaní upozorní na chyby nebo potenciální problémy v kódu. Tyto vizuální vodítka umožňují okamžitě opravit problémy bez čekání na chybu, která má být zjištěna během sestavení nebo při spuštění programu. Pokud najedete na vlnovku, zobrazí se další informace o chybě. Na levém okraji se může zobrazit také žárovka s akcemi, které se označují jako rychlé akce, které chybu opraví.

   ![Vlnité v sadě Visual Studio](media/tour-ide-squiggles.png)

- [Přejít na definici náhledu](../ide/go-to-and-peek-definition.md)

   Funkce **Přejít na definici** vás přenese přímo do umístění, kde je definována funkce nebo typ. Příkaz **Definice náhledu** zobrazí definici v okně bez otevření samostatného souboru. Příkaz **Najít všechny odkazy** také poskytuje užitečný způsob, jak zjistit, kde je daný identifikátor definován i používán.

   ![Navigační příkazy kódu](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Výkonné funkce pro Python

::: moniker range=">=vs-2019"
- [Spuštění kódu bez projektu](quickstart-05-python-visual-studio-open-folder.md)

    Počínaje Visual Studio 2019, můžete otevřít složku obsahující kód Pythonu využívat funkce, jako je IntelliSense a ladění bez nutnosti vytvářet projekt Visual Studio pro kód.
::: moniker-end

- [Spolupráce v sadě Visual Studio](/visualstudio/liveshare/)
  
    Visual Studio Live Share umožňuje společně upravovat a ladit s ostatními v reálném čase, bez ohledu na to, jaký programovací jazyk používáte nebo typy aplikací, které vytváříte. 

- [Python Interaktivní REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio poskytuje interaktivní okno smyčky repl (read-evaluate-print) pro každé prostředí Pythonu, které vylepšuje funkci REPL, kterou získáte pomocí *souboru python.exe* na příkazovém řádku. V **interaktivním** okně můžete zadat libovolný kód Pythonu a zobrazit okamžité výsledky.

    ![Interaktivní okno Pythonu](media/interactive-window.png)

- [ladění](debugging-python-in-visual-studio.md)

    Visual Studio poskytuje komplexní ladění prostředí pro Python, včetně připojení k běžící procesy, vyhodnocení výrazy v **watch** a **okamžité** okna, kontrola místníproměnné, zarážky, krok dovnitř/ven/přes příkazy, **Set Next Statement**a další. Můžete také ladit vzdálený kód Pythonu spuštěný na počítačích s Linuxem.

    ![Ladění Pythonu v sadě Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interakce s C++](working-with-c-cpp-python-in-visual-studio.md)

    Mnoho knihoven vytvořených pro Python je napsáno v jazyce C++ pro optimální výkon. Visual Studio poskytuje bohaté vybavení pro vývoj rozšíření C++, včetně [ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Ladění Pythonu a C++ ve smíšeném režimu společně](media/mixed-mode-debugging.png)

- [Profilování](profiling-python-code-in-visual-studio.md)

    Při použití překladač založené na CPython, můžete vyhodnotit výkon kódu Pythonu v rámci Sady Visual Studio.

    ![Sestava výkonu profilování](media/profiling-results.png)

- [Testování částí](unit-testing-python-in-visual-studio.md)

    Visual Studio poskytuje integrovanou podporu pro zjišťování, spouštění a ladění testování částí vše v kontextu integrovaného vývojového prostředí.

    ![Testování částí zobrazující stav neúspěšného testu](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Další kroky

Prozkoumejte Python v Sadě Visual Studio dále podle následujících rychlých startů nebo kurzů:

> [!div class="nextstepaction"]
> [Úvodní příručka: Vytvoření webové aplikace pomocí funkce Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Práce s Pythonem v Sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Začínáme s webovým frameworkem Django v sadě Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Začínáme s webovým rámcem Flask v sadě Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Viz také

- Objevte [další funkce sady Visual Studio](../ide/advanced-feature-overview.md)
- Navštivte [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Přečtěte si [blog visual ateliéru](https://devblogs.microsoft.com/visualstudio/)
