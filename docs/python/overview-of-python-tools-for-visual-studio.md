---
title: Podpora Pythonu v aplikaci Visual Studio ve Windows
titleSuffix: ''
description: Souhrn funkcí Pythonu v aplikaci Visual Studio, což je nejlepší prostředí Python IDE ve Windows (známé také jako Python Tools for Visual Studio, PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a913fa6abdcf59a64d8514f17656b8f8531d476d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315262"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Práce s Pythonem v aplikaci Visual Studio ve Windows

Python je oblíbený programovací jazyk, který je spolehlivý, flexibilní a snadný, snadno se naučíte používat na všech operačních systémech a který podporuje jak silnou komunitu vývojářů, tak i mnoho bezplatných knihoven. Python podporuje všechny způsoby vývoje, včetně webových aplikací, webových služeb, aplikací klasické pracovní plochy, skriptování a vědeckého zpracování a používá ho spousta vysokých škol, vědců, příležitostného vývojáře a profesionálních vývojářů. Další informace o jazyce v [Python.org](https://www.python.org) a [Pythonu](https://www.python.org/about/gettingstarted/)najdete v části začátečník.

Visual Studio je výkonné prostředí Python IDE ve Windows. Visual Studio poskytuje podporu [Open Source](https://github.com/Microsoft/ptvs) pro jazyk Pythonu prostřednictvím úloh **vývoje v Pythonu** a **datových vědy** (Visual Studio 2017 a novější) a bezplatného rozšíření Python Tools for Visual Studio (Visual Studio 2015 a starší).

Python není v Visual Studio pro Mac v současnosti podporován, ale je k dispozici v systémech Mac a Linux prostřednictvím Visual Studio Code (viz [otázky a odpovědi](#questions-and-answers)).

Jak začít:

- Postupujte podle [pokynů k instalaci](installing-python-support-in-visual-studio.md) a nastavte úlohu Pythonu.
- Seznamte se s možnostmi Pythonu sady Visual Studio v částech v tomto článku.
::: moniker range="vs-2017"
- Projděte jednu nebo více rychlých startů a vytvořte projekt. Pokud si nejste jistí, začněte s [vytvořením webové aplikace s použitím baňky](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Projděte jednu nebo více rychlých startů a vytvořte projekt. Pokud si nejste jistí, začněte s [rychlým startem: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md) nebo [Vytvoření webové aplikace s použitím baňky](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- V kurzu [práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) najdete kompletní ucelené prostředí.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio podporuje Python verze 2,7 a také verze 3,5 až 3,7. I když je možné použít sadu Visual Studio k úpravám kódu napsaného v jiných verzích Pythonu, tyto verze se oficiálně nepodporují a funkce, jako je například IntelliSense a ladění, nemusí fungovat. Podpora Pythonu verze 3,8 je stále ve vývoji, konkrétní podrobnosti o podpoře se dají zobrazit v tomto [problému sledování na GitHubu](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Podpora pro více překladačů

Okno **prostředí Pythonu** sady Visual Studio (zobrazené níže v celém rozšířeném zobrazení) poskytuje jediné místo pro správu všech vašich globálních prostředí Pythonu, prostředí conda a virtuálních prostředí. Visual Studio automaticky detekuje Instalace Pythonu ve standardních umístěních a umožňuje nakonfigurovat vlastní instalace. U každého prostředí můžete snadno spravovat balíčky, otevírat interaktivní okno pro toto prostředí a přistupovat ke složkám prostředí.

::: moniker range="vs-2017"
![Rozšířené zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozšířené zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Pomocí příkazu **otevřít interaktivní okno** spusťte Python interaktivně v rámci kontextu aplikace Visual Studio. K otevření samostatného příkazového okna ve složce vybraného prostředí použijte příkaz **otevřít v prostředí PowerShell** . Z tohoto příkazového okna můžete spustit libovolný skript Pythonu.

Další informace najdete tady:

- [Správa prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Referenční dokumentace prostředí Pythonu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Bohatá úprava, IntelliSense a porozumění kódu

Visual Studio poskytuje prvotřídní Editor Pythonu, včetně barevného zbarvení, automatického dokončování všech vašich kódů a knihoven, formátování kódu, nápovědy k podpisům, refaktoringu, linting a pomocných parametrů typu. Visual Studio také poskytuje jedinečné funkce, jako je zobrazení tříd, **Přejít na definici**, **Najít všechny odkazy**a fragmenty kódu. Přímá integrace s [interaktivním oknem](#interactive-window) vám pomůže rychle vyvíjet kód v Pythonu, který je už uložený v souboru.

![Dokončování kódu pro kód Pythonu v aplikaci Visual Studio](media/code-editing-completions-simple.png)

Další informace najdete tady:

- Dokumenty: [Úprava kódu Pythonu](editing-python-code-in-visual-studio.md)
- Docs: [formát kódu](formatting-python-code.md)
- Docs: [refaktoring kódu](refactoring-python-code.md)
- Dokumentace: [použití linter](linting-python-code.md)
- Obecné dokumentace k funkcím sady Visual Studio: [funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Interaktivní okno

Pro každé prostředí Pythonu, které je známo v sadě Visual Studio, můžete snadno otevřít stejné interaktivní prostředí (REPL) pro interpret Pythonu přímo v sadě Visual Studio namísto použití samostatného příkazového řádku. Můžete snadno přepínat mezi prostředími i. (Pokud chcete otevřít samostatný příkazový řádek, vyberte požadované prostředí v okně **prostředí Pythonu** a potom vyberte příkaz **otevřít v prostředí PowerShell** , jak je vysvětleno dříve v části [Podpora pro více překladačů](#support-for-multiple-interpreters).)

![Interaktivní okno Pythonu v aplikaci Visual Studio](media/interactive-window.png)

Visual Studio také poskytuje úzkou integraci mezi editorem kódu Python a **interaktivním** oknem. Klávesová zkratka **CTRL** + **ENTER** pohodlně pošle aktuální řádek kódu (nebo bloku kódu) v editoru do **interaktivního** okna a pak se přesune na další řádek (nebo blok). **CTRL** + **Zadejte** umožňuje snadno procházet kód bez nutnosti spustit ladicí program. Můžete také odeslat vybraný kód do **interaktivního** okna se stejnou klávesovou zkratkou a snadno vložit kód z **interaktivního** okna do editoru. Tyto funkce společně umožňují pracovat s podrobnostmi pro segment kódu v **interaktivním** okně a snadno ukládat výsledky do souboru v editoru.

Visual Studio také podporuje IPython/Jupyter v REPL, včetně vložených ploch, .NET a Windows Presentation Foundation (WPF).

Další informace najdete tady:

- [Interaktivní okno](python-interactive-repl-in-visual-studio.md)
- [IPython v aplikaci Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Projektový systém a šablony projektů a položek

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření projektů a souborů řešení sady Visual Studio. Další informace najdete v tématu [rychlý Start: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Existují však výhody použití souboru projektu, jak je vysvětleno v této části.
::: moniker-end

Visual Studio pomáhá spravovat složitost projektu v průběhu času. *Projekt sady Visual Studio* je mnohem více než struktura složky: obsahuje informace o tom, jak se používají různé soubory a jak spolu vzájemně souvisí. Visual Studio vám pomůže rozlišit kód aplikace, otestovat kód, webové stránky, JavaScript, skripty sestavení atd. a pak povolit funkce vhodné pro soubory. Řešení sady Visual Studio navíc pomáhá spravovat více souvisejících projektů, jako je například projekt Pythonu a projekt rozšíření C++.

![Řešení sady Visual Studio obsahující projekty Python i C++](media/projects-solution-explorer-two-projects.png)

Šablony projektů a položek automatizují proces nastavování různých typů projektů a souborů. ušetříte si tak cenné čas a získáte možnost spravovat komplikované a náchylnější podrobnosti k chybám. Visual Studio poskytuje šablony pro web, Azure, datové vědy, konzoly a další typy projektů, spolu se šablonami pro soubory, jako jsou třídy Pythonu, testování částí, Webová konfigurace Azure, HTML a dokonce i aplikace Django.

[![Šablony projektů a položek Pythonu v aplikaci Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Další informace najdete tady:

- Dokumenty: [Správa projektů v Pythonu](managing-python-projects-in-visual-studio.md)
- Docs: [Referenční dokumentace šablon položek](python-item-templates.md)
- Dokumentace: [šablony projektů v Pythonu](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumentace: [práce s C++ a Pythonem](working-with-c-cpp-python-in-visual-studio.md)
- Obecné dokumentace k funkcím sady Visual Studio: [šablony projektů a položek](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Obecné dokumentace k funkcím sady Visual Studio: [řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Bohaté funkce ladění

Jedním z možností sady Visual Studio je výkonný ladicí program. Pro Python zejména Visual Studio zahrnuje ladění ve smíšeném režimu Python/C++, vzdálené ladění v systému Linux, ladění v **interaktivním** okně a ladění testů jednotek Pythonu.

![Ladicí program sady Visual Studio pro Python zobrazující výjimku v překryvném okně](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
V aplikaci Visual Studio 2019 můžete spustit a ladit kód bez použití souboru projektu sady Visual Studio. Příklad najdete [v tématu rychlý Start: otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md) .
::: moniker-end

Další informace najdete tady:

- Dokumentace: [ladění Pythonu](debugging-python-in-visual-studio.md)
- Dokumentace: [ladění ve smíšeném režimu Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumentace: [vzdálené ladění v systému Linux](debugging-python-code-on-remote-linux-machines.md)
- Obecné dokumentace k funkcím sady Visual Studio: [prohlídka funkcí ladicího programu sady Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Nástroje pro profilaci s komplexními vytvářením sestav

Profilace se zabývá tím, jak je čas strávený ve vaší aplikaci. Visual Studio podporuje profilaci s Překladači založenými na CPython a nabízí možnost porovnat výkon mezi různými běhy profilace.

[![Výsledky profileru sady Visual Studio pro projekt v Pythonu](media/profiling-results.png)](media/profiling-results.png#lightbox)

Další informace najdete tady:

- Dokumentace: [Nástroje pro profilaci Pythonu](profiling-python-code-in-visual-studio.md)
- Obecné dokumentace k funkcím sady Visual Studio: [prohlídka funkcí profilace](../profiling/profiling-feature-tour.md). (Ne všechny funkce profilování sady Visual Studio jsou k dispozici pro Python).

## <a name="unit-testing-tools"></a>Nástroje testování částí

Můžete zjišťovat, spouštět a spravovat testy v **Průzkumníku testů**sady Visual Studio a snadno ladit testy jednotek.

![Ladění testu jednotek Pythonu v aplikaci Visual Studio](media/unit-test-debugging.png)

Další informace najdete tady:

- Dokumentace: [Nástroje testování částí pro Python](unit-testing-python-in-visual-studio.md)
- Obecné dokumentace k funkcím sady Visual Studio: [testování částí kódu](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Azure SDK pro Python

Knihovny Azure pro Python zjednodušují využívání služeb Azure z aplikací pro Windows, Mac OS X a Linux. Můžete je použít k vytvoření a správě prostředků Azure a také k připojení ke službám Azure. 

Další informace najdete v tématu [sada Azure SDK pro Python](/azure/python/) a [knihovny Azure pro Python](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Otázky a odpovědi

**Č. Je k dispozici podpora Pythonu v Visual Studio pro Mac?**

A. V tuto chvíli ne, ale můžete si hlasovat o žádosti na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). V dokumentaci [Visual Studio pro Mac](/visualstudio/mac/) se identifikují aktuální typy vývoje, které podporuje. Mezitím Visual Studio Code v systémech Windows, Mac a Linux [dobře funguje s Pythonem prostřednictvím dostupných rozšíření](https://code.visualstudio.com/docs/languages/python).

**Č. Co můžu použít k sestavení uživatelského rozhraní v Pythonu?**

A. Hlavní nabídka v této oblasti je [projekt QT](https://www.qt.io/qt-for-application-development/)s vazbami pro Python označované jako [PySide (oficiální vazba)](https://wiki.qt.io/PySide) (viz také [soubory PySide ke stažení](https://download.qt.io/official_releases/pyside/.)) a [PyQt](https://wiki.python.org/moin/PyQt). V současné době podpora Pythonu v aplikaci Visual Studio nezahrnuje žádné konkrétní nástroje pro vývoj uživatelského rozhraní.

**Č. Může projekt Pythonu vytvořit samostatný spustitelný soubor?**

A. Python je obecně interpretovaný jazyk, se kterým se kód spouští na vyžádání v vhodném prostředí podporujícím Python, jako je například sada Visual Studio a webové servery. Visual Studio sám o sobě neposkytuje způsob vytvoření samostatného spustitelného souboru, který v podstatě znamená program s vloženým překladačem Pythonu. Komunita Pythonu však dodala různé způsoby vytváření spustitelných souborů, jak je popsáno v [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython podporuje také vkládání do nativní aplikace, jak je popsáno v blogovém příspěvku [pomocí souboru ZIP](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)s možnou vloženou do CPython.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Podpora funkcí

Funkce Pythonu lze nainstalovat v následujících edicích sady Visual Studio, jak je popsáno v [instalační příručce](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (všechny edice)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (všechny edice)
- Visual Studio 2015 (všechny edice)
- Edice Visual Studio 2013 Community
- Visual Studio 2013 Express pro web, aktualizace 2 nebo vyšší
- Visual Studio 2013 Express pro stolní počítače, aktualizace 2 nebo vyšší
- Visual Studio 2013 (verze pro nebo vyšší)
- Visual Studio 2012 (verze pro nebo vyšší)
- Visual Studio 2010 SP1 (verze pro nebo vyšší; vyžaduje se .NET 4,5)

Visual Studio 2015 a starší jsou k dispozici na adrese [VisualStudio.Microsoft.com/vs/Older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkce jsou plně podporované a udržované jenom pro nejnovější verzi sady Visual Studio. Funkce jsou k dispozici ve starších verzích, ale nejsou aktivně spravovány.

|          Podpora jazyka Python          |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Správa více překladačů   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatické zjišťování oblíbených překladačů | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Přidat vlastní překladače      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Virtuální prostředí       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/Snadná instalace         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Systém projektu         |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + |      2012 pro +       | 2010 SP1 pro + |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nový projekt z existujícího kódu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Zobrazit všechny soubory         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Správa zdrojového kódu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integrace Gitu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Probíhají úpravy            |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Zvýrazňování syntaxe      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Automatické dokončování         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Podpis – Help        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Rychlé informace          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Prohlížeč objektů/zobrazení tříd   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Navigační panel        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Přejít k definici       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Přejděte na adresu .          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Najít všechny odkazy      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatické odsazení       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formátování kódu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoring – přejmenování       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktor-Extract – metoda   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktorovat – přidat nebo odebrat import | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Interaktivní okno     |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Interaktivní okno     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython s vloženými grafy | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Plocha               |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konzola/aplikace systému Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Ironpythonu WPF (s návrhářem XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Ironpythonu model Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Webový projekt v Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Webový projekt na láhev  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Webový projekt v baňce  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Obecný webový projekt | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop |       Web 2013       |      2013 pro +       |      2012 pro +       |    2010 SP1 pro +     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Nasadit na web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Nasadit do webové role   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Nasadit do role pracovního procesu  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Spustit v emulátoru Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Vzdálené ladění    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Připojit Průzkumník serveru | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Šablony Django           |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop |       Web 2013       |      2013 pro +       | 2012 pro + | 2010 SP1 pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Ladění               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Automatické dokončování             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Automatické dokončování pro CSS a JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Ladění                  |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Ladění                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Ladění bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Ladění – připojení k úpravám        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Ladění ve smíšeném režimu             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Vzdálené ladění (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Ladit interaktivní okno           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilace |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilace | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test      |   2017 +   |   2015   | 2013 komunikace | 2013 Desktop | Web 2013 | 2013 pro + | 2012 pro + | 2010 SP1 pro + |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Průzkumník testů | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Spustit test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Ladit test   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Podpora Gitu pro Visual Studio 2012 je k dispozici v Visual Studio Tools rozšíření pro Git, které jsou k dispozici v [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Nasazení na webu Azure vyžaduje [sadu Azure SDK pro .net 2,1 – Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Novější verze aplikaci Visual Studio 2010 nepodporují.

1. Podpora pro webovou roli Azure a roli pracovního procesu vyžaduje [sadu Azure SDK pro .net 2,3-VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) nebo novější.

1. Podpora pro webovou roli Azure a roli pracovního procesu vyžaduje [sadu Azure SDK pro .net 2,3-VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Editor šablon Django v Visual Studio 2013 obsahuje některé známé problémy, které jsou vyřešeny instalací aktualizace Update 2.

1. Vyžaduje systém Windows 8 nebo novější. Visual Studio 2013 Express for Web nemá dialog **připojit k procesu** , ale vzdálené ladění webu Azure je stále možné pomocí příkazu **připojit ladicí program (Python)** v **Průzkumník serveru**. Vzdálené ladění vyžaduje [sadu Azure SDK pro .net 2,3-Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Vyžaduje systém Windows 8 nebo novější. Příkaz **připojit ladicí program (Python)** v **Průzkumník serveru** vyžaduje [sadu Azure SDK pro .NET 2,3-Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Vyžaduje systém Windows 8 nebo novější.
::: moniker-end
