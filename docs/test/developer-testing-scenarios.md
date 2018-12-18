---
title: Testovací nástroje pro vývojáře
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 396bbfdb915d0e3ecc31f516d60eab80cca6a421
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295147"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Testovací nástroje, scénáře a možnosti pro vývojáře

Údržba stavu kódu pomocí testování částí. Visual Studio poskytuje širokou škálu výkonné nástroje a techniky pro vývojáře pro použití při testování aplikací.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Regresí a dosáhnout pokrytí kódu pomocí funkce IntelliTest

V tradičních jednotky testovací sady každý testovací případ představuje scénáři EXEMPLÁRNÍ využití a vztah mezi vstup a výstup začleněné kontrolní výrazy.  Ověřuje se, že několik takových scénářích může být i stačit, ale zkušení vývojáři by vědět, že chyby lurk i v dobře otestovaný kód, při správné ale netestované vstupy způsobit nesprávné odpovědi.

Lepší pokrytí a regresí s Intellitestem. IntelliTest dramaticky redukuje objem úsilí nezbytné k vytváření a údržbě testů jednotek pro nový nebo existující kód.

![IntelliTest v akci](media/devtest-intellitest.png)

* [Úvod k Intellitestu pomocí sady Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest – jeden test pro vládne všem.](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)
* [IntelliTest videa](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Začínáme s IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Referenční příručka funkce IntelliTest](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Uživatelské rozhraní testování pomocí uživatelského rozhraní a serverem Selenium

Testování uživatelského rozhraní (UI) s využitím nejlepší emulátorem nebo community schválení testování uživatelského rozhraní. Programové testy UI poskytují způsob, jak vytvořit plně automatizované testy pro ověření chování vaší aplikace uživatelského rozhraní a funkcí. Můžete se automatizují toto testování v různých technologií, včetně aplikací pro UWP založené na XAML, prohlížečových aplikací a aplikací pro SharePoint.

Jestli si to nejlepší z vyvíjet programových testů uživatelského rozhraní nebo obecný webové rozhraní testování s Selenium, Visual Studio poskytuje všechny nástroje, které potřebujete.

![Testování pomocí uživatelského rozhraní programového uživatelského rozhraní](media/devtest-codeduitest.png)

* [Použití automatizace uživatelského rozhraní k testování kódu](use-ui-automation-to-test-your-code.md)
* [Začínáme vytvářet, úpravy a údržba programového testu uživatelského rozhraní](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testování aplikací pro UWP pomocí programových testů uživatelského rozhraní](test-uwp-app-with-coded-ui-test.md)
* [Testování aplikací pro SharePoint pomocí programových testů uživatelského rozhraní](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Úvod do programové testy UI pomocí sady Visual Studio Enterprise (prostředí)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Efektivní testování s pokrytím kódu sady Visual Studio

Pokud chcete zjistit, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako je například testy jednotek, můžete použít funkci pokrytí kódu sady Visual Studio. Pro efektivní ochranu před chybami, testy by měly neboli "pokrýt" velká část kódu.

Analýza pokrytí kódu lze použít pro spravovaný i nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

* [Použití pokrytí kódu k určení, kolik kódu je právě testováno.](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testování částí, pokrytí kódu a analýza duplicit pomocí sady Visual Studio (prostředí) v kódu](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Přizpůsobení analýzy pokrytí kódu](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Průzkumník testů

**Průzkumník testů** pomáhá vývojářům vytvářet, spravovat a spouštět testy jednotek.

![Průzkumník testů sady Visual Studio](media/devtest-testexplorer.png)

* [Začínáme s testováním částí](unit-test-your-code.md)
* [Spouštění testování částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
* [Instalace systémů pro testování částí od třetích stran](install-third-party-unit-test-frameworks.md)

Visual Studio je rozšiřitelné a otevře dveře pro adaptéry jako například NUnit a xUnit.net testování jednotky třetí strany. Kromě toho přejde funkce klonování kódu ručně spolupráce s doručování vysoce kvalitního softwaru díky tomu můžete identifikovat bloky sémanticky podobné kódu, který se může jednat o kandidáty na běžné opravy chyby nebo refaktoring.

![Integrace testování třetích stran](media/devtest-thirdparty.png)

## <a name="see-also"></a>Viz také:

* [Začínáme s testováním částí](getting-started-with-unit-testing.md)
* [Zrychlení provádění testů jednotek v sadě Team Foundation Server](https://blogs.msdn.microsoft.com/devops/2015/07/30/speeding-up-unit-test-execution-in-tfs/)
* [Paralelní a kontext provádění testů jednotek citlivé](https://blogs.msdn.microsoft.com/devops/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Testování částí, pokrytí kódu a analýza duplicit pomocí sady Visual Studio (prostředí) v kódu](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
