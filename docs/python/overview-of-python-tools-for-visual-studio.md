---
title: Podpora Pythonu ve Visual Studiu ve Windows
titleSuffix: ''
description: Shrnutí funkcí Pythonu ve Visual Studiu, což z něj dělá nejlepší Python IDE v systému Windows (také známý jako Python Tools for Visual Studio, PTVS).
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302789"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Práce s Pythonem v Visual Studiu ve Windows

Python je populární programovací jazyk, který je spolehlivý, flexibilní, snadno se učí, zdarma používat na všech operačních systémech, a podporuje jak silné vývojářské komunity a mnoho knihoven zdarma. Python podporuje všechny způsoby vývoje, včetně webových aplikací, webových služeb, desktopových aplikací, skriptování a vědeckých výpočtů, a je používán mnoha univerzitami, vědci, příležitostnými vývojáři i profesionálními vývojáři. Můžete se dozvědět více o jazyce na [python.org](https://www.python.org) a [Python pro začátečníky](https://www.python.org/about/gettingstarted/).

Visual Studio je výkonný Python IDE v systému Windows. Visual Studio poskytuje [open source](https://github.com/Microsoft/ptvs) podporu jazyka Pythonu prostřednictvím úloh pro vývoj a **datové vědy** **v Pythonu** (Visual Studio 2017 a novější) a bezplatné hopythonové nástroje pro rozšíření Visual Studio (Visual Studio 2015 a starší).

Python není v současné době podporován ve Visual Studiu pro Mac, ale je k dispozici na Mac a Linux prostřednictvím Visual Studio Code (viz [otázky a odpovědi](#questions-and-answers)).

Jak začít:

- Podle [pokynů k instalaci](installing-python-support-in-visual-studio.md) nastavte úlohu Pythonu.
- Seznamte se s možnostmi Pythonu visual studia prostřednictvím částí v tomto článku.
::: moniker range="vs-2017"
- Chcete-li vytvořit projekt, projděte si jeden nebo více rychlých startů. Pokud si nejste jisti, začněte s [vytvořením webové aplikace pomocí flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Chcete-li vytvořit projekt, projděte si jeden nebo více rychlých startů. Pokud si nejste jisti, začněte s [úvodním startem: Otevřete a spusťte kód Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md) nebo [Vytvořte webovou aplikaci s Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Postupujte podle [práce s Pythonem v sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) pro úplné prostředí od konce do konce.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio podporuje Python verze 2.7, stejně jako verze 3.5 až 3.7. I když je možné použít Visual Studio k úpravám kódu napsaného v jiných verzích Pythonu, tyto verze nejsou oficiálně podporovány a funkce, jako je IntelliSense a ladění nemusí fungovat. Podpora Pythonu verze 3.8 je stále ve vývoji, konkrétní podrobnosti o podpoře lze vidět v tomto problému sledování [na GitHubu](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Podpora více tlumočníků

Okno Prostředí **Pythonu** sady Visual Studio (zobrazené níže v širokém a rozšířeném zobrazení) poskytuje jediné místo pro správu všech globálních prostředí Pythonu, prostředí conda a virtuálních prostředí. Visual Studio automaticky detekuje instalace Pythonu ve standardních umístěních a umožňuje konfigurovat vlastní instalace. S každým prostředím můžete snadno spravovat balíčky, otevřít interaktivní okno pro toto prostředí a přistupovat ke složkám prostředí.

::: moniker range="vs-2017"
![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Pomocí příkazu **Otevřít interaktivní okno** můžete spouštět Python interaktivně v kontextu sady Visual Studio. Pomocí příkazu **Otevřít v Prostředí PowerShell** otevřete samostatné příkazové okno ve složce vybraného prostředí. Z tohoto příkazového okna můžete spustit libovolný skript pythonu.

Další informace najdete tady:

- [Správa prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Odkaz na prostředí Pythonu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Bohaté úpravy, technologie IntelliSense a porozumění kódu

Visual Studio poskytuje prvotřídní editor Pythonu, včetně zbarvení syntaxe, automatického dokončování ve všech kódech a knihovnách, formátování kódu, nápovědy k podpisu, refaktoringu, lintingu a nápovědy k typu. Visual Studio také poskytuje jedinečné funkce, jako je zobrazení třídy, **přejít na definici**, najít všechny odkazy a **fragmenty**kódu. Přímá integrace s [interaktivním oknem](#interactive-window) vám pomůže rychle vyvinout kód Pythonu, který je již uložen ý v souboru.

![Dokončení kódu pro kód Pythonu v sadě Visual Studio](media/code-editing-completions-simple.png)

Další informace najdete tady:

- Dokumenty: [Úprava kódu Pythonu](editing-python-code-in-visual-studio.md)
- Dokumenty: [Formát kódu](formatting-python-code.md)
- Dokumenty: [Refaktorovatý kód](refactoring-python-code.md)
- Dokumenty: [Použijte linter](linting-python-code.md)
- Obecné dokumenty pro funkce sady Visual Studio: [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Interaktivní okno

Pro každé prostředí Pythonu známé Visual Studio můžete snadno otevřít stejné interaktivní (REPL) prostředí pro interpret pythonu přímo v rámci sady Visual Studio, nikoli pomocí samostatného příkazového řádku. Můžete také snadno přepínat mezi prostředími. (Chcete-li otevřít samostatný příkazový řádek, vyberte požadované prostředí v okně **Prostředí Pythonu** a pak vyberte příkaz **Otevřít v prostředí PowerShell,** jak je vysvětleno dříve v [části Podpora více tlumočníků](#support-for-multiple-interpreters).)

![Interaktivní okno Pythonu v sadě Visual Studio](media/interactive-window.png)

Visual Studio také poskytuje těsnou integraci mezi editorem kódu Pythonu a **interaktivní** okno. Klávesová zkratka **Ctrl**+**Enter** pohodlně odešle aktuální řádek kódu (nebo blok kódu) v editoru do **interaktivního** okna a pak se přesune na další řádek (nebo blok). **Ctrl**+**Enter** umožňuje snadno krokovat kód bez nutnosti spuštění ladicího programu. Můžete také odeslat vybraný kód do **interaktivního** okna se stejným stiskem klávesy a snadno vložit kód z **interaktivního** okna do editoru. Tyto funkce společně umožňují vypracovat podrobnosti o segmentu kódu v **interaktivním** okně a snadno uložit výsledky do souboru v editoru.

Visual Studio také podporuje IPython/Jupyter v REPL, včetně vložkových parcel, .NET a Windows Presentation Foundation (WPF).

Další informace najdete tady:

- [Interaktivní okno](python-interactive-repl-in-visual-studio.md)
- [IPython ve Visual Studiu](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Systém projektu a šablony projektů a položek

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 podporuje otevření složky obsahující kód Pythonu a spuštění tohoto kódu bez vytváření souborů projektu a řešení sady Visual Studio. Další informace naleznete v [tématu Úvodní příručka: Otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md). Použití souboru projektu však přináší výhody, jak je vysvětleno v této části.
::: moniker-end

Visual Studio pomáhá spravovat složitost projektu, jak roste v průběhu času. *Projekt sady Visual Studio* je mnohem více než struktura složek: zahrnuje pochopení, jak se používají různé soubory a jak se vztahují k sobě navzájem. Visual Studio pomáhá rozlišit kód aplikace, testovací kód, webové stránky, JavaScript, vytvářet skripty a tak dále, které pak umožňují funkce odpovídající souboru. Řešení Visual Studio navíc pomáhá spravovat více souvisejících projektů, jako je například projekt Pythonu a projekt rozšíření C++.

![Řešení Visual Studia obsahující projekty Pythonu i C++](media/projects-solution-explorer-two-projects.png)

Šablony projektů a položek automatizují proces nastavování různých typů projektů a souborů, což vám ušetří drahocenný čas a zmírní správu složitých detailů a podrobností náchylných k chybám. Visual Studio poskytuje šablony pro web, Azure, datové vědy, konzoly a další typy projektů, spolu se šablonami pro soubory, jako jsou třídy Pythonu, testy částí, konfigurace webu Azure, HTML a dokonce i aplikace Django.

[![Šablony projektů a položek Pythonu v Sadě Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Další informace najdete tady:

- Dokumenty: [Správa projektů Pythonu](managing-python-projects-in-visual-studio.md)
- Dokumenty: [Odkaz na šablony položek](python-item-templates.md)
- Dokumenty: [Šablony projektů Pythonu](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumenty: [Práce s C++ a Pythonem](working-with-c-cpp-python-in-visual-studio.md)
- Obecné dokumenty pro funkce sady Visual Studio: [Šablony projektů a položek](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Obecné dokumenty visual studia: [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Plně vybavené ladění

Jednou ze silných stránek sady Visual Studio je jeho výkonný ladicí program. Pro Python zejména Visual Studio zahrnuje Python/C++ ladění ve smíšeném režimu, vzdálené ladění na Linuxu, ladění v **interaktivním** okně a ladění testů částí Pythonu.

![Ladicí program Visual Studio pro Python zobrazující vyskakovací okno s výjimkou](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
V sadě Visual Studio 2019 můžete spouštět a ladit kód bez nutnosti souboru projektu sady Visual Studio. Viz [Úvodní příručka: Otevření a spuštění kódu Pythonu ve složce](quickstart-05-python-visual-studio-open-folder.md) pro příklad.
::: moniker-end

Další informace najdete tady:

- Dokumenty: [Ladění Pythonu](debugging-python-in-visual-studio.md)
- Dokumenty: [Ladění v python/c++ ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Docs: [Vzdálené ladění na Linuxu](debugging-python-code-on-remote-linux-machines.md)
- Obecné Visual Studio funkce dokumenty: [Funkce prohlídka visual studio debugger](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Nástroje pro profilování s komplexním vykazováním

Profilování zkoumá, jak se čas tráví v rámci vaší aplikace. Visual Studio podporuje profilování s cpython založené interprety a zahrnuje možnost porovnat výkon mezi různými spuštění profilování.

[![Výsledky profileru visual studia pro projekt Pythonu](media/profiling-results.png)](media/profiling-results.png#lightbox)

Další informace najdete tady:

- Dokumenty: [Nástroje pro profilování v Pythonu](profiling-python-code-in-visual-studio.md)
- Obecné dokumenty pro funkce sady Visual Studio: [Prohlídka funkcí profilování](../profiling/profiling-feature-tour.md). (Ne všechny funkce profilování visual studia jsou k dispozici pro Python).

## <a name="unit-testing-tools"></a>Nástroje pro testování částí

Objevte, spouštěj a spravujte testy v **Průzkumníkovi testů**sady Visual Studio a snadno ladítesty částí.

![Ladění testu částí Pythonu v sadě Visual Studio](media/unit-test-debugging.png)

Další informace najdete tady:

- Dokumenty: [Nástroje pro testování částí pro Python](unit-testing-python-in-visual-studio.md)
- Obecné Visual Studio funkce dokumenty: [Testování částí kódu](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Azure SDK pro Python

Knihovny Azure pro Python zjednodušují využívání služeb Azure z aplikací pro Windows, Mac OS X a Linux. Můžete je použít k vytvoření a správě prostředků Azure a také k připojení ke službám Azure. 

Další informace najdete [v tématu Azure SDK pro Python](/azure/python/) a Azure [knihovny pro Python](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Otázky a odpovědi

**Otázka: Je podpora Pythonu dostupná v Sadě Visual Studio pro Mac?**

A. Ne v tuto chvíli, ale můžete se hlasovat žádost o [Developer Společenství](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). [Visual Studio pro Mac](/visualstudio/mac/) dokumentace identifikuje aktuální typy vývoje, které podporuje. Do té doby Visual Studio Code na Windows, Mac a Linux [funguje dobře s Python prostřednictvím dostupných rozšíření](https://code.visualstudio.com/docs/languages/python).

**Otázka: Co můžu použít k vytvoření ui s Pythonem?**

A. Hlavní nabídkou v této oblasti je [Projekt Qt](https://www.qt.io/qt-for-application-development/), s vazbami pro Python známý jako [PySide (oficiální vazba)](https://wiki.qt.io/PySide) (viz také [PySide ke stažení)](https://download.qt.io/official_releases/pyside/.)a [PyQt](https://wiki.python.org/moin/PyQt). V současné době podpora Pythonu v sadě Visual Studio neobsahuje žádné konkrétní nástroje pro vývoj ui.

**Otázka: Může projekt Pythonu vytvořit samostatný spustitelný soubor?**

A. Python je obecně interpretovaný jazyk, se kterým je kód spuštěn na vyžádání ve vhodném prostředí podporujícím Python, jako je Visual Studio a webové servery. Visual Studio sám v současné době neposkytuje prostředky k vytvoření samostatného spustitelného souboru, což v podstatě znamená program s vloženým překladačem Pythonu. Komunita Pythonu však poskytla různé prostředky k vytvoření spustitelných souborů, jak je popsáno na [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython také podporuje vkládání do nativní aplikace, jak je popsáno v blogu, [pomocí CPython je vložitelný zip soubor](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Podpora funkcí

Funkce Pythonu lze nainstalovat v následujících edicích sady Visual Studio, jak je popsáno v [instalační příručce](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (všechny edice)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (všechny edice)
- Visual Studio 2015 (všechny edice)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express pro web, aktualizace 2 nebo vyšší
- Visual Studio 2013 Express pro stolní počítače, aktualizace 2 nebo vyšší
- Visual Studio 2013 (pro edice nebo vyšší)
- Visual Studio 2012 (pro edice nebo vyšší)
- Visual Studio 2010 SP1 (pro vydání nebo vyšší; .NET 4.5 povinné)

Visual Studio 2015 a starší jsou k dispozici na [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Funkce jsou plně podporovány a udržovány pouze pro nejnovější verzi sady Visual Studio. Funkce jsou k dispozici ve starších verzích, ale nejsou aktivně udržovány.

|          Podpora jazyka Python          |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Správa více tlumočníků   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatická detekce oblíbených tlumočníků | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Přidání vlastních tlumočníků      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Virtuální prostředí       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/ Snadná instalace         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Systém projektu         |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nový projekt z existujícího kódu | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Zobrazit všechny soubory         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Správa zdrojového kódu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integrace Gitu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Úprava            |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Zvýraznění syntaxe      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Automatické dokončování         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Nápověda k podpisu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Rychlé informace          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Zobrazení prohlížeče/třídy objektů   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Navigační panel        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Přejít k definici       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Přejít na          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Najít všechny odkazy      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatické odsazení       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formátování kódu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refaktoring - přejmenování       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refaktor - metoda extrakce   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refaktor - přidat nebo odebrat import | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Interaktivní okno     |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Interaktivní okno     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython s vazavými grafy | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Aplikace klasické pracovní plochy               |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konzolová/windowsová aplikace     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (s návrhářem XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows formuláře       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Webový projekt Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Webový projekt láhve  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Webový projekt Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Obecný webový projekt | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 |       Web 2013       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Nasazení na web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | <sup>2.</sup> &#10004; |
|   Nasazení do webové role   | &#10004; | &#10004; | &#10004;  |   &#10007;   | <sup>&#10004;4</sup> | <sup>&#10004;4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Nasazení do role pracovního procesu  |    ?     |    ?     |     ?     |   &#10007;   | <sup>&#10004;4</sup> | <sup>&#10004;4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Spuštění v emulátoru Azure  |    ?     |    ?     |     ?     |   &#10007;   | <sup>&#10004;4</sup> | <sup>&#10004;4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Vzdálené ladění    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Připojit Průzkumníka serveru | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django šablony           |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 |       Web 2013       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              ladění               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Automatické dokončování             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Automatické dokončování pro CSS a JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  ladění                  |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  ladění                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Ladění bez projektu         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Ladění - připojit k editaci        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Ladění ve smíšeném režimu             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Vzdálené ladění (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Interaktivní okno ladění           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilace |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilace | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test      |   2017+   |   2015   | 2013 Comm | Pracovní plocha 2013 | Web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Průzkumník testů | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Spustit test    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Test ladění   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Podpora Gitu pro Visual Studio 2012 je dostupná v rozšíření Visual Studio Tools for Git, které je dostupné na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Nasazení na webu Azure vyžaduje [Azure SDK pro .NET 2.1 – Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Novější verze nepodporují Visual Studio 2010.

1. Podpora pro azure web role a role pracovního procesu vyžaduje [Azure SDK pro .NET 2.3 – VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) nebo novější.

1. Podpora pro azure web role a role pracovního procesu vyžaduje [Azure SDK pro .NET 2.3 – VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Editor šablon Django ve Visual Studiu 2013 má některé známé problémy, které jsou vyřešeny instalací aktualizace 2.

1. Vyžaduje Windows 8 nebo novější. Visual Studio 2013 Express for Web nemá dialogové okno **Připojit k procesu,** ale vzdálené ladění webu Azure je stále možné pomocí **příkazu Připojit ladicí program (Python)** v **Průzkumníkovi serveru**. Vzdálené ladění vyžaduje [Azure SDK pro .NET 2.3 – Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Vyžaduje Windows 8 nebo novější. **Připojit debugger (Python)** příkaz v **Průzkumníku serveru** vyžaduje [Azure SDK pro .NET 2.3 - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) nebo novější.

1. Vyžaduje Windows 8 nebo novější.
::: moniker-end
