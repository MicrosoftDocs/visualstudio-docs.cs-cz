---
title: Python v kurzu Visual Studia krok 1, vytvoření projektu
titleSuffix: ''
description: Přehled a krok 1 základního návodu možností Pythonu v Sadě Visual Studio, včetně předpokladů a vytvoření nového projektu Pythonu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ed4fdbfe7090a66d955461f2c3a394f6fb661c5a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430714"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Kurz: Práce s Pythonem v Sadě Visual Studio

Python je populární programovací jazyk, který je spolehlivý, flexibilní, snadno se učí, zdarma používat na všech operačních systémech, a podporuje jak silné vývojářské komunity a mnoho knihoven zdarma. Jazyk podporuje všechny způsoby vývoje, včetně webových aplikací, webových služeb, desktopových aplikací, skriptování a vědeckých výpočtů a je používán mnoha univerzitami, vědci, příležitostnými vývojáři i profesionálními vývojáři.

Visual Studio poskytuje prvotřídní jazykovou podporu pro Python. Tento kurz vás provede následujícími kroky:

- [Krok 0: Instalace](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1: Vytvoření projektu Pythonu (tento článek)](#step-1-create-a-new-python-project)
- [Krok 2: Zápis a spuštění kódu pro zobrazení technologie Visual Studio IntelliSense v práci](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3: Vytvoření dalšího kódu v okně Interaktivní REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4: Spuštění dokončeného programu v ladicím programu sady Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5: Instalace balíčků a správa prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6: Práce s Gitem](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1: Vytvoření nového projektu Pythonu

*Projekt* je způsob, jakým Visual Studio spravuje všechny soubory, které se spojí k vytvoření jedné aplikace, včetně zdrojového kódu, prostředků, konfigurací a tak dále. Projekt formalizuje a udržuje vztah mezi všemi soubory projektu i externími zdroji, které jsou sdíleny mezi více projekty. Jako takové projekty umožňují aplikaci snadno rozšířit a růst mnohem jednodušší než jednoduše spravovat vztahy projektu v ad hoc složky, skripty, textové soubory, a dokonce i vlastní mysl.

V tomto kurzu začnete s jednoduchým projektem obsahujícím jeden prázdný soubor kódu.

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt** **(Ctrl**+**Shift**+**N**), který vyvolá dialogové okno Nový **projekt.** Zde procházíte šablony v různých jazycích, pak vyberete jednu pro projekt a určíte, kam aplikace Visual Studio umístí soubory.

1. Chcete-li zobrazit šablony Pythonu, vyberte **Nainstalovaný** > **Python** vlevo nebo vyhledejte "Python". Použití vyhledávání je skvělý způsob, jak najít šablonu, když si nemůžete vzpomenout na její umístění ve stromu jazyků.

    ![Dialogové okno Nového projektu se zobrazenými projekty Pythonu](media/vs-getting-started-python-01-new-project.png)

    Všimněte si, jak podpora Pythonu v sadě Visual Studio obsahuje řadu šablon projektů, včetně webových aplikací pomocí bottle, flask a Django frameworks. Pro účely tohoto návodu však začněme s prázdným projektem.

1. Vyberte šablonu **aplikace Pythonu,** zadejte název projektu a vyberte **OK**.

1. Po chvíli Visual Studio zobrazí strukturu projektu v okně **Průzkumník řešení** (1). Výchozí soubor kódu je otevřen v editoru (2). Zobrazí se také okno **Vlastnosti** (3), které zobrazuje další informace o všech položkách vybraných v **Průzkumníku řešení**, včetně jejího přesného umístění na disku.

    ![Průzkumník řešení s projektem Pythonu](media/vs-getting-started-python-02-windows.png)

1. Udělejte si chvilku, abyste se seznámili s **Průzkumníkem řešení**, který je místo, kde můžete procházet soubory a složky v projektu.

    ![Průzkumník řešení byl rozbalen, aby zobrazoval různé funkce](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Zvýrazněný tučným písmem je váš projekt s použitím názvu, který jste zadali v dialogovém okně **Nový projekt.** Na disku je tento projekt reprezentován souborem *Pyproj* ve složce projektu.

    (2) Na nejvyšší úrovni je *řešení*, které má ve výchozím nastavení stejný název jako váš projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů. Například pokud napíšete rozšíření C++ pro vaši aplikaci Pythonu, tento projekt C++ může být umístěn ve stejném řešení. Řešení může také obsahovat projekt pro webovou službu, spolu s projekty pro vyhrazené testovací programy.

    (3) V rámci projektu se zobrazí zdrojové soubory, v tomto případě pouze jeden *soubor .py.* Výběrsouboru zobrazí jeho vlastnosti v okně **Vlastnosti.** Poklepáním na soubor se soubor otevře jakýmkoli způsobem, který je pro tento soubor vhodný.

    (4) Také v rámci projektu je uzel **Prostředí Pythonu.** Po rozbalení se zobrazí překladače Pythonu, které máte k dispozici. Rozbalte uzel interpreta, chcete-li zobrazit knihovny, které jsou nainstalovány do tohoto prostředí (5).

    Kliknutím pravým tlačítkem myši na libovolný uzel nebo položku v **Průzkumníku řešení** zobrazíte přístup k nabídce příslušných příkazů. Například příkaz **Přejmenovat** umožňuje změnit název libovolného uzlu nebo položky, včetně projektu a řešení.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Zápis a spuštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Projekty Pythonu v sadě Visual Studio](managing-python-projects-in-visual-studio.md).
- [Další informace o jazyce Pythonu na python.org](https://www.python.org)
- [Python pro začátečníky](https://www.python.org/about/gettingstarted/) (python.org)
