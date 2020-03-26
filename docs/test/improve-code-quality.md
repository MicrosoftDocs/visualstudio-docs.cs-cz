---
title: Testovací nástroje
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 0517d03db180ce76940723ca935be258d0cf1818
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256228"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>První pohled na testovací nástroje v sadě Visual Studio

Nástroje pro testování sady Visual Studio vám a vašemu týmu mohou pomoci vyvíjet a udržovat vysoké standardy dokonalosti kódu.

> [!NOTE]
> Testování částí je k dispozici ve všech edicích sady Visual Studio. Další testovací nástroje, jako je například živé testování částí, IntelliTest a programovaný test ui, jsou k dispozici pouze v edici Visual Studio Enterprise. Další informace o edicích naleznete [v tématu Porovnání ide ide sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Průzkumník testů

Okno **Průzkumník testů** pomáhá vývojářům vytvářet, spravovat a spouštět testy částí. Můžete použít rozhraní Microsoft testování částí nebo jeden z několika rozhraní třetích stran a open source.

::: moniker range="vs-2017"
![Průzkumník testů sady Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Průzkumník testů sady Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Začínáme s testováním částí](unit-test-your-code.md)
* [Spouštění testování částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
* [Instalace systémů pro testování částí od třetích stran](install-third-party-unit-test-frameworks.md)

Visual Studio je také rozšiřitelný a otevírá dveře pro adaptéry testování částí jiných výrobců, jako jsou NUnit a xUnit.net. Kromě toho schopnost klonování kódu jde ruku v ruce s poskytováním vysoce kvalitního softwaru tím, že vám pomůže identifikovat bloky sémanticky podobného kódu, který může být kandidátem na běžné opravy chyb nebo refaktoring.

![Integrace testů třetích stran](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Živé testování částí](../test/live-unit-testing.md) automaticky spustí testy částí na pozadí a graficky zobrazí pokrytí kódu a výsledky testů v editoru kódu Sady Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest automaticky generuje testy částí a testovací data pro spravovaný kód. IntelliTest zlepšuje pokrytí a výrazně snižuje úsilí o vytvoření a údržbu testů částí pro nový nebo existující kód.

![IntelliTest v akci](media/devtest-intellitest.png)

* [Generování testů částí pro kód pomocí funkce IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – jeden test, který je všechny ovládne](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Referenční příručka IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrytí kódu

[Pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) určuje, jaká část kódu projektu je ve skutečnosti testována kódovanými testy, jako jsou testy částí. Chcete-li účinně chránit před chybami, testy by měly vykonávat nebo "pokrýt" velkou část kódu.

Analýzu pokrytí kódu lze použít pro spravovaný i nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

* [Určení rozsahu testovaného kódu pomocí pokrytí kódu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testování částí, pokrytí kódu a analýza klonování kódu pomocí sady Visual Studio (Lab)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Přizpůsobení analýzy pokrytí kódu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Napodobeniny Microsoft

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) vám pomůže izolovat kód, který testujete nahrazením jiných částí aplikace se zástupnými kódy nebo překrytími.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testování uživatelského rozhraní s kódovým uživatelským rozhraním a selenem

Programové testy uživatelského rozhraní poskytují způsob, jak vytvořit plně automatizované testy k ověření funkčnosti a chování uživatelského rozhraní vaší aplikace. Mohou automatizovat testování uživatelského prostředí v různých technologiích, včetně aplikací Upw založených na XAML, aplikací prohlížeče a aplikací SharePoint.

Ať už zvolíte nejlepší kódované testy ui nebo obecné testování ui založené na prohlížeči se selenem, Visual Studio poskytuje všechny nástroje, které potřebujete.

![Testování ui s kódovým ui](media/devtest-codeduitest.png)

* [Testování kódu pomocí automatizace uživatelského rozhraní](use-ui-automation-to-test-your-code.md)
* [Začínáme vytvářet, upravovat a udržovat kódovaný test ui.](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testování aplikací UPW pomocí kódovaných testů ui](test-uwp-app-with-coded-ui-test.md)
* [Úvod k kódovým testům rozhraní s Visual Studio Enterprise (Lab)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Zátěžové testování

[Zátěžové testování](../test/quickstart-create-a-load-test-project.md) simuluje zatížení serverové aplikace spuštěním testů částí a testů výkonu webu.

## <a name="related-scenarios"></a>Související scénáře

* [Průzkumné & ruční testování (plány testů Azure)](/azure/devops/test/index?view=vsts)
* [Zátěžové testování (plány testů Azure)](/azure/devops/test/load-test/index?view=vsts)
* [Průběžné testování (plány testů Azure)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Nástroje pro analýzu kódu](../code-quality/code-analysis-for-managed-code-overview.md)
