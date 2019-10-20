---
title: Testovací nástroje
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b68793e512cdb367375cc9f27d61ae5a85e4f078
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653270"
---
# <a name="testing-tools-in-visual-studio"></a>Testovací nástroje v sadě Visual Studio

Testovací nástroje sady Visual Studio vám můžou a vašemu týmu přispět k vývoji a udržování vysoké úrovně kvality kódu.

> [!NOTE]
> Testování částí je k dispozici ve všech edicích sady Visual Studio. Další testovací nástroje, například Live Unit Testing, IntelliTest a programový test uživatelského rozhraní, jsou k dispozici pouze v edici Visual Studio Enterprise. Další informace o edicích najdete v tématu [porovnání prostředí Visual Studio](https://visualstudio.microsoft.com/vs/compare/)s více procesory.

## <a name="test-explorer"></a>Průzkumník testů

Okno **Průzkumník testů** pomáhá vývojářům vytvářet, spravovat a spouštět testy jednotek. Můžete použít rozhraní Microsoft Unit Test Framework nebo jednu z několika platforem pro open source od jiných výrobců.

::: moniker range="vs-2017"
![Průzkumník testů sady Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Visual Studio Test Explorer 16,2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Začínáme s testováním částí](unit-test-your-code.md)
* [Spouštění testování částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Průzkumník testů – nejčastější dotazy](test-explorer-faq.md)
* [Instalace systémů pro testování částí od třetích stran](install-third-party-unit-test-frameworks.md)

Visual Studio je také rozšiřitelné a otevírá dvířka adaptérů pro testování částí třetích stran, jako jsou NUnit a xUnit.net. Kromě toho se schopnost klonování kódu doručí za vysoce kvalitní software tím, že vám pomůže identifikovat bloky sémanticky podobného kódu, které mohou být kandidáty na běžné opravy chyb nebo refaktoring.

![Integrace testů třetích stran](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) automaticky spouští testy jednotek na pozadí a graficky zobrazuje pokrytí kódu a výsledky testů v editoru kódu sady Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest automaticky generuje jednotkové testy a testovací data pro váš spravovaný kód. IntelliTest vylepšuje pokrytí a významně snižuje úsilí při vytváření a údržbě testů jednotek pro nový nebo existující kód.

![IntelliTest v akci](media/devtest-intellitest.png)

* [Generování testů částí pro kód pomocí funkce IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – jeden test pro všechna pravidla](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Referenční příručka funkce IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Pokrytí kódu

[Pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) určuje, který podíl kódu projektu je skutečně testován pomocí kódovaných testů, jako je například testování částí. Aby bylo možné efektivně chránit proti chybám, testy by měly vyvolávat nebo "krýt" velkou část kódu.

Analýza pokrytí kódu se dá použít pro spravovaný i nespravovaný (nativní) kód.

Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

* [Použití pokrytí kódu k určení množství testovaného kódu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Testování částí, pokrytí kódu a analýza klonování kódu pomocí sady Visual Studio (testovací prostředí)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Přizpůsobení analýzy pokrytí kódu](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Napodobeniny Microsoft

[Napodobeniny společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) vám pomůžou izolovat testovaný kód nahrazením jiných částí aplikace pomocí zástupných procedur nebo překrytí.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testování uživatelského rozhraní pomocí kódovaného uživatelského rozhraní a programu selen

Programové testy uživatelského rozhraní poskytují způsob, jak vytvořit plně automatizované testy pro ověření funkčnosti a chování uživatelského rozhraní vaší aplikace. Můžou automatizovat testování uživatelského rozhraní napříč různými technologiemi, včetně aplikací UWP založených na jazyce XAML, aplikací prohlížeče a aplikací služby SharePoint.

Bez ohledu na to, zda jste zvolili nejlepší programové testy uživatelského rozhraní nebo obecné testování uživatelského rozhraní založeného na prohlížeči pomocí programu selen, Visual Studio poskytuje všechny nástroje, které potřebujete.

![Testování uživatelského rozhraní pomocí kódovaného uživatelského rozhraní](media/devtest-codeduitest.png)

* [Použití automatizace uživatelského rozhraní k testování kódu](use-ui-automation-to-test-your-code.md)
* [Začínáme vytvářet, upravovat a udržovat kódovaný test uživatelského rozhraní](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testování aplikací pro UWP pomocí programových testů uživatelského rozhraní](test-uwp-app-with-coded-ui-test.md)
* [Úvod k programovým testům uživatelského rozhraní pomocí Visual Studio Enterprise (testovací prostředí)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Zátěžové testování

[Zátěžové testování](../test/quickstart-create-a-load-test-project.md) simuluje zatížení serverové aplikace spuštěním testů jednotek a testů výkonnosti webu.

## <a name="related-scenarios"></a>Související scénáře

* [Průzkumné & Manuální testování (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Zátěžové testování (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Průběžné testování (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Nástroje pro analýzu kódu](../code-quality/code-analysis-for-managed-code-overview.md)
