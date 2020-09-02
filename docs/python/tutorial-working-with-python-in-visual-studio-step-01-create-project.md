---
title: Python v aplikaci Visual Studio – Krok 1, vytvoření projektu
titleSuffix: ''
description: Přehled a krok 1 základního návodu k funkcím Pythonu v aplikaci Visual Studio, včetně požadavků a vytvoření nového projektu v jazyce Python.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430714"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Kurz: práce s Pythonem v aplikaci Visual Studio

Python je oblíbený programovací jazyk, který je spolehlivý, flexibilní a snadný, snadno se naučíte používat na všech operačních systémech a který podporuje jak silnou komunitu vývojářů, tak i mnoho bezplatných knihoven. Tento jazyk podporuje všechny způsoby vývoje, včetně webových aplikací, webových služeb, aplikací klasické pracovní plochy, skriptování a vědeckého výpočetního prostředí a používá ho spousta vysokých škol, vědců, příležitostného vývojáře a profesionálních vývojářů.

Visual Studio poskytuje prvotřídní jazykovou podporu pro Python. Tento kurz vás provede následujícími kroky:

- [Krok 0: instalace](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1: vytvoření projektu v Pythonu (Tento článek)](#step-1-create-a-new-python-project)
- [Krok 2: zápis a spuštění kódu pro zobrazení sady Visual Studio IntelliSense v práci](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3: vytvoření dalšího kódu v interaktivním okně REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4: spuštění dokončeného programu v ladicím programu sady Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5: Instalace balíčků a Správa prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6: práce s Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1: vytvoření nového projektu v Pythonu

*Projekt* je způsob, jakým Visual Studio spravuje všechny soubory, které jsou spojeny k vytvoření jedné aplikace, včetně zdrojového kódu, prostředků, konfigurací a tak dále. Projekt formalizes a udržuje vztah mezi všemi soubory projektu i s externími prostředky, které jsou sdíleny mezi více projekty. V takovém případě projekty umožňují vaší aplikaci snadno rozšířit a zvětšovat mnohem jednodušší, než jednoduše spravujete vztahy projektu ve složkách ad hoc, skriptech, textových souborech a dokonce i na své vlastní myšlenky.

V tomto kurzu začnete s jednoduchým projektem obsahujícím jeden prázdný soubor kódu.

1. V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt** (**CTRL** + **SHIFT** + **N**), které se zobrazí v dialogovém okně **Nový projekt** . Zde můžete procházet šablony v různých jazycích a pak vybrat jednu pro svůj projekt a určit, kde aplikace Visual Studio umístí soubory.

1. Pokud chcete zobrazit šablony Pythonu **Installed**, vyberte  >  na levé straně nainstalované**Python** nebo vyhledejte Python. Použití hledání je skvělý způsob, jak najít šablonu, když si nepamatujete umístění ve stromu jazyků.

    ![Dialogové okno Nový projekt se zobrazenými projekty Pythonu](media/vs-getting-started-python-01-new-project.png)

    Všimněte si, jak podpora Pythonu v aplikaci Visual Studio zahrnuje řadu šablon projektů, včetně webových aplikací využívajících láhev, baňku a Django architektury. Pro účely tohoto návodu ale začněte s prázdným projektem.

1. Vyberte šablonu **aplikace Python** , zadejte název projektu a vyberte **OK**.

1. Po chvíli aplikace Visual Studio zobrazí strukturu projektu v okně **Průzkumník řešení** (1). Výchozí soubor kódu je otevřen v editoru (2). Zobrazí se také okno **vlastnosti** (3), ve kterém se zobrazí další informace pro libovolnou položku vybranou v **Průzkumník řešení**, včetně jejího přesného umístění na disku.

    ![Průzkumník řešení s projektem Pythonu](media/vs-getting-started-python-02-windows.png)

1. Seznámení s **Průzkumník řešení**, kde můžete procházet soubory a složky v projektu, chvíli trvat.

    ![Průzkumník řešení rozbalené pro zobrazení různých funkcí](media/vs-getting-started-python-03-solution-explorer.png)

    (1) zvýrazněná tučně je váš projekt pomocí názvu, který jste zadali v dialogovém okně **Nový projekt** . Na disku je tento projekt reprezentován souborem *. pyproj* ve složce projektu.

    (2) na nejvyšší úrovni je *řešení*, které ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů. Například pokud napíšete rozšíření C++ pro aplikaci Python, může být projekt C++ umístěn ve stejném řešení. Řešení může obsahovat také projekt webové služby společně s projekty pro vyhrazené testovací programy.

    (3) ve vašem projektu vidíte zdrojové soubory, v tomto případě pouze jeden soubor *. py* . Výběr souboru zobrazí své vlastnosti v okně **vlastnosti** . Dvojím kliknutím se soubor otevře jakýmkoli způsobem, který je vhodný pro tento soubor.

    (4) také v rámci projektu je uzel **prostředí Pythonu** . Po rozbalení uvidíte interprety Pythonu, které jsou pro vás k dispozici. Rozbalením uzlu překladače zobrazíte knihovny, které jsou nainstalovány do daného prostředí (5).

    Kliknutím pravým tlačítkem myši na libovolný uzel nebo položku v **Průzkumník řešení** získáte přístup k nabídce příslušných příkazů. Například příkaz **Přejmenovat** umožňuje změnit název libovolného uzlu nebo položky, včetně projektu a řešení.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Zápis a spuštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Projekty Pythonu v aplikaci Visual Studio](managing-python-projects-in-visual-studio.md).
- [Další informace o jazyce Python na python.org](https://www.python.org)
- [Python pro začátečníky](https://www.python.org/about/gettingstarted/) (Python.org)
