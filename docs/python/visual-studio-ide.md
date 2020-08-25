---
title: Přehled sady Visual Studio pro vývojáře v Pythonu
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 943c0567e3726d014f7dae01915916864e09ed9b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801643"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Vítejte v integrovaném vývojovém prostředí sady Visual Studio | Python

*Integrované vývojové prostředí* sady Visual Studio je Creative Starting panel pro Python (a další jazyky), který můžete použít k úpravám, ladění a testování kódu a pak k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatou funkcí, který se dá použít pro mnoho aspektů vývoje softwaru. Před a nad standardním editorem a ladicím programem, který nejvíce nabízí, Visual Studio zahrnuje nástroje pro dokončování kódu, interaktivní prostředí REPL a další funkce, které usnadňují proces vývoje softwaru.

[![Visual Studio s projektem Pythonu](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Tento obrázek ukazuje Visual Studio s otevřeným projektem v Pythonu a několik oken s klíčovými okny, které budete pravděpodobně používat:

- [**Průzkumník řešení**](../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, navigovat a spravovat soubory kódu. **Průzkumník řešení** může přispět k uspořádání kódu seskupením souborů do [řešení a projektů](../get-started/tutorial-projects-solutions.md).
  - Vedle **Průzkumník řešení** jsou [**prostředí Pythonu**](managing-python-environments-in-visual-studio.md), kde můžete spravovat různé interprety Pythonu, které jsou nainstalované v počítači.

  ::: moniker range=">=vs-2019"
  - Můžete také otevřít a spustit kód Pythonu ve složce bez vytváření projektů a souborů řešení sady Visual Studio. Další informace najdete v tématu [rychlý Start: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- [Okno editoru](../ide/writing-code-in-the-code-and-text-editor.md) (Center), kde se pravděpodobně bude strávit většinou času, zobrazuje obsah souboru. Tady můžete [Upravit kód Pythonu](editing-python-code-in-visual-studio.md), přejít v rámci struktury kódu a nastavovat zarážky během ladění relace. Pomocí Pythonu můžete také vybrat kód a stisknutím kombinace kláves CTRL + ENTER spustit tento kód v [interaktivním okně REPL](python-interactive-repl-in-visual-studio.md).

- [Okno výstup](../ide/reference/output-window.md) (dole na střed) je místo, kde aplikace Visual Studio odesílá oznámení, jako jsou například ladění a chybové zprávy, upozornění, stavové zprávy publikování a další. Každý zdroj zprávy má svou vlastní kartu.
  - [Okno pro interaktivní REPL v Pythonu](python-interactive-repl-in-visual-studio.md) se zobrazí ve stejné oblasti jako okno výstup.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (vpravo dole) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) a [Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edice

Visual Studio je k dispozici pro Windows a Mac; Podpora Pythonu je však k dispozici pouze v aplikaci Visual Studio pro systém Windows.

Existují tři edice sady Visual Studio ve Windows: Community, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v tématu [porovnání sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Oblíbené funkce pro produktivitu

Některé z oblíbených funkcí v aplikaci Visual Studio, které vám pomůžou zvýšit produktivitu při vývoji softwaru, zahrnují:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech zapisují malé bity kódu za vás. Vypadá to, že je v editoru vložená základní dokumentace, která vám ušetří informace o typu jinde. Funkce IntelliSense se liší podle jazyka a v článku [Úprava kódu Pythonu](editing-python-code-in-visual-studio.md#intellisense) jsou podrobnosti pro Python. Následující obrázek ukazuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ![Dokončení členů pomocí Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refactoring](refactoring-python-code.md)

   Po kliknutí pravým tlačítkem na část kódu a výběru **rychlých akcí a refaktoringu**vám Visual Studio poskytne operace, jako je například inteligentní přejmenování proměnných, extrakce jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Analyzování kódu](refactoring-python-code.md)

   Linting kontroluje chyby a běžné problémy v kódu Pythonu a podporuje vám dobré vzory psaní kódu v Pythonu.

   ![Příkaz PyLint v kontextové nabídce pro projekty v Pythonu](media/code-pylint-command.png)

- Vyhledávací pole

   Visual Studio se může zdát při velkém množství nabídek, možností a vlastností. Vyhledávací pole je skvělým způsobem, jak rychle najít, co potřebujete v aplikaci Visual Studio. Když začnete psát název hledaného textu, Visual Studio zobrazí seznam výsledků, které vám přesně přejdou, kde potřebujete. Pokud potřebujete přidat funkci do sady Visual Studio, například chcete-li přidat podporu pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační program pro Visual Studio k instalaci úlohy nebo jednotlivé součásti.

   ![Vyhledávací pole v aplikaci Visual Studio](media/tour-ide-quick-launch.png)

- Vlnovky a [rychlé akce](../ide/quick-actions.md)

   Vlnovky jsou podtržení vlnovkou, které upozorňují na chyby nebo potenciální problémy ve vašem kódu při psaní. Tato vizuální podoby vám umožní opravit problémy hned bez čekání na zjištění chyby během sestavení nebo při spuštění programu. Pokud najedete myší na vlnovku, zobrazí se další informace o chybě. Žárovka se může zobrazit také na levém okraji s akcemi, které jsou známé jako rychlé akce, a opravit tak chybu.

   ![Vlnovky v aplikaci Visual Studio](media/tour-ide-squiggles.png)

- [Přejít na a prohlížet definici](../ide/go-to-and-peek-definition.md)

   Funkce **Přejít k definici** přejde přímo do umístění, kde je definována funkce nebo typ. Příkaz **prohlížet definice** zobrazí definici v okně bez otevření samostatného souboru. Příkaz **Najít všechny odkazy** poskytuje také užitečný způsob, jak zjistit, kde je daný identifikátor definován a použit.

   ![Příkazy navigace v kódu](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Výkonné funkce pro Python

::: moniker range=">=vs-2019"
- [Spustit kód bez projektu](quickstart-05-python-visual-studio-open-folder.md)

    Počínaje verzí sady Visual Studio 2019 můžete otevřít složku obsahující kód Pythonu, abyste mohli využívat funkce, jako je IntelliSense a ladění, aniž byste museli vytvořit projekt sady Visual Studio pro kód.
::: moniker-end

- [Spolupráce v sadě Visual Studio](/visualstudio/liveshare/)

    Visual Studio Live Share umožňuje spolupracovat s ostatními uživateli v reálném čase, a to bez ohledu na to, jaký programovací jazyk používáte, nebo typy aplikací, které vytváříte.

- [Interaktivní REPL Pythonu](python-interactive-repl-in-visual-studio.md)

    Visual Studio poskytuje interaktivní okno pro čtení a vyhodnocení-tisk smyčky (REPL) pro každé prostředí Pythonu, které se zlepšuje na REPL, které získáte pomocí *python.exe* na příkazovém řádku. V **interaktivním** okně můžete zadat libovolný kód Pythonu a zobrazit okamžité výsledky.

    ![Interaktivní okno Pythonu](media/interactive-window.png)

- [Ladění](debugging-python-in-visual-studio.md)

    Sada Visual Studio poskytuje komplexní ladicí prostředí pro Python, včetně připojení ke spuštěným procesům, vyhodnocování výrazů v okně **kukátko** a **bezprostředních** oknech, kontrolu místních proměnných, zarážek, krokování/převzetí/převzetí příkazů, **nastavení dalšího příkazu**a další. Můžete také ladit vzdálený kód Pythonu běžící na počítačích se systémem Linux.

    ![Ladění Pythonu v aplikaci Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interakce s C++](working-with-c-cpp-python-in-visual-studio.md)

    Mnoho knihoven vytvořených pro Python je napsáno v jazyce C++ za účelem optimálního výkonu. Visual Studio poskytuje rozsáhlá zařízení pro vývoj rozšíření C++, včetně [ladění ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Ladění v Pythonu a C++ společně s kombinovaným režimem](media/mixed-mode-debugging.png)

- [Profilace](profiling-python-code-in-visual-studio.md)

    Při použití překladače založeného na CPython můžete vyhodnotit výkon kódu Pythonu v sadě Visual Studio.

    ![Sestava o výkonu profilace](media/profiling-results.png)

- [Testování částí](unit-testing-python-in-visual-studio.md)

    Visual Studio poskytuje integrovanou podporu pro zjišťování, spouštění a ladění testů jednotek, a to vše v kontextu integrovaného vývojového prostředí (IDE).

    ![Testování částí znázorňující neúspěšný stav testu](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Další kroky

Prozkoumejte Python v aplikaci Visual Studio dále pomocí jednoho z následujících rychlých startů nebo kurzů:

> [!div class="nextstepaction"]
> [Rychlý Start: Vytvoření webové aplikace s použitím baňky](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Začínáme s webovým rozhraním Django v aplikaci Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Začínáme s webovým rozhraním v baňce v aplikaci Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Viz také

- Objevte [Další funkce sady Visual Studio](../ide/advanced-feature-overview.md)
- Navštívit [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/)
- Přečtěte si [blog sady Visual Studio](https://devblogs.microsoft.com/visualstudio/) .
