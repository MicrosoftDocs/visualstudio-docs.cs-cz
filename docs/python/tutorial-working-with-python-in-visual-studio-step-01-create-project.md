---
title: Python v sadě Visual Studio kurz – krok 1, vytvoření projektu
titleSuffix: ''
description: Přehled a krok 1 Průvodce základní funkce Pythonu v sadě Visual Studio, včetně požadavků a vytvoření nového projektu Pythonu.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1aaf0c0258d502693b771cad66f9347dd60f80e8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049846"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Kurz: Práce s využitím Pythonu v sadě Visual Studio

Python je oblíbený programovací jazyk, který je spolehlivé, flexibilní, snadno se jej naučíte, bezplatné použití ve všech operačních systémech a podporovaná smlouvou do komunity vývojářů silné a free mnoho knihoven. Jazyk podporuje všechny způsoby vývoje, včetně webových aplikací, webových služeb, aplikací klasické pracovní plochy, skriptování a vědecké výpočty a používá mnoho univerzity, odborníky, příležitostné vývojáři a nabídne profesionální vývojáři.

Visual Studio poskytuje prvotřídní podporu pro Python. Tento kurz vás provede následující kroky:

- [Krok 0: instalace](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Krok 1: Vytvoření projektu Pythonu (Tento článek)](#step-1-create-a-new-python-project)
- [Krok 2: Zápis a spouštění kódu zobrazíte IntelliSense ve Visual Studio v práci](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Krok 3: Vytvoření více kódu v okně interaktivní okno REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Krok 4: Dokončení program spustit v ladicím programu sady Visual Studio](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Krok 5: Instalace balíčků a spravovat prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Krok 6: Práce s Gitem](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Krok 1: Vytvoření nového projektu Pythonu

A *projektu* je způsob, jakým Visual Studio spravuje všechny soubory, které společně k vytvoření jedné aplikace, včetně zdrojového kódu, prostředky, konfigurace a tak dále. Projekt aplikaci umožňuje formalizovat a udržuje vztah mezi všechny projektu soubory i externí prostředky, které jsou sdíleny mezi více projekty. V důsledku toho projekty povolit aplikace k bez námahy rozšíření a mnohem jednodušší, než se jednoduše spravují pouze vztahy projektu v ad hoc složek, skripty, textové soubory a dokonce i vlastní paměti.

V tomto kurzu začnete s Jednoduchý projekt obsahující jeden prázdný soubor kódu.

1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu** (**Ctrl** + **Shift**+**N**), která se vyvolá **nový projekt** dialogového okna. Tady můžete procházet šablony v různých jazycích, pak vyberte jednu pro váš projekt a zadejte, kam umístí soubory sady Visual Studio.

1. Chcete-li zobrazit šablony Pythonu, vyberte **nainstalováno** > **Python** na levé straně nebo vyhledejte "Python". Pomocí vyhledávání je skvělý způsob, jak najít šablonu, pokud si nepamatujete její umístění ve stromu jazyky.

    ![Dialogové okno nového projektu se zobrazí projektů v Pythonu](media/vs-getting-started-python-01-new-project.png)

    Všimněte si, jak podpora Pythonu v sadě Visual Studio obsahuje několik šablon projektů, včetně webových aplikací s využitím rozhraní Bottle, Flask a Django. Pro účely tohoto návodu ale Začněme prázdný projekt.

1. Vyberte **aplikace v Pythonu** šablony, zadejte název projektu a vyberte **OK**.

1. Po chvíli se sada Visual Studio zobrazí strukturu projektu v **Průzkumníka řešení** okno (1). Soubor výchozího kódu je otevřen v editoru (2). **Vlastnosti** zobrazíte další informace pro všechny položky vybrané v se také zobrazí okno (3) **Průzkumníka řešení**, včetně jeho přesné umístění na disku.

    ![Průzkumník řešení s projektem Python](media/vs-getting-started-python-02-windows.png)

1. Chvíli se seznámit s **Průzkumníka řešení**, což je, kde můžete procházet soubory a složky ve vašem projektu.

    ![Rozbalit a zobrazit různé funkce Průzkumníka řešení](media/vs-getting-started-python-03-solution-explorer.png)

    (1) je zvýrazněný tučným písmem je váš projekt, pomocí názvu, který jste zadali v **nový projekt** dialogového okna. Na disku, je reprezentována tento projekt *.pyproj* souboru ve složce vašeho projektu.

    (2) na nejvyšší úrovni je *řešení*, která ve výchozím nastavení má stejný název jako projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů. Například pokud píšete rozšíření C++ pro aplikaci v Pythonu, tento projekt C++ může nacházet ve stejném řešení. Řešení může obsahovat také projekt pro webové služby, spolu s projekty pro programy vyhrazené testu. 

    (3) v rámci projektu naleznete v tématu zdrojových souborů, v tomto případě jedné *.py* souboru. Výběr souboru zobrazí její vlastnosti v **vlastnosti** okna. Poklepáním na soubor otevře v dle svého je vhodný pro tento soubor.

    (4) v rámci projektu je také **prostředí Pythonu** uzlu. Po rozbalení zobrazí interpretů Pythonu, které jsou k dispozici. Rozbalte uzel interpretu zobrazíte knihoven, které jsou nainstalovány do daného prostředí (5).

    Klikněte pravým tlačítkem na libovolný uzel nebo položky v **Průzkumníka řešení** pro přístup k nabídce použitelných příkazů. Například **přejmenovat** příkaz umožňuje změnit název uzlu nebo položky, včetně projektu a řešení.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Psání a spouštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Projekty v Pythonu v sadě Visual Studio](managing-python-projects-in-visual-studio.md).
- [Další informace o jazyku Python na webu python.org](https://www.python.org)
- [Python pro začátečníky](https://www.python.org/about/gettingstarted/) (python.org)
- [Bezplatné kurzy Pythonu v Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Začátek Python dotazy na webu Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
