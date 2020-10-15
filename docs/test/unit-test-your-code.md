---
title: Testování částí
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: be0f8f7eeb116a251477ce57027a2176119c2d17
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099307"
---
# <a name="unit-test-your-code"></a>Testování částí kódu

Testy jednotek poskytují vývojářům a testerům rychlý způsob vyhledávání logických chyb v rámci metod tříd v projektech C#, Visual Basic a C++.

Nástroje testování částí zahrnují:

* **Průzkumník testů** &mdash; Spusťte testy jednotek a podívejte se na výsledky v **Průzkumníku testů**. Můžete použít libovolné rozhraní testování částí, včetně rozhraní třetí strany, které má adaptér pro **Průzkumníka testů**.

* **Microsoft Unit Test Framework pro spravovaný kód** &mdash; Rozhraní Microsoft Unit Test Framework pro spravovaný kód je nainstalováno se sadou Visual Studio a poskytuje rozhraní pro testování kódu .NET.

* **Microsoft Unit Test Framework pro C++** &mdash; Rozhraní Microsoft Unit Test Framework pro C++ je nainstalováno jako součást **vývoje desktopových aplikací v jazyce c++** . Poskytuje rozhraní pro testování nativního kódu. K dispozici jsou také Google Test, zvyšování a CTest architektury a adaptéry třetích stran jsou k dispozici pro další testovací architektury. Další informace najdete v tématu [zápis testů jednotek pro C/C++](../test/writing-unit-tests-for-c-cpp.md).

* Nástroje pro pokrytí **kódu** &mdash; Můžete určit množství kódu produktu, který testuje Jednotkový Test z jednoho příkazu v Průzkumníku testů.

* Rozhraní pro izolaci **falešného od Microsoftu** &mdash; Rozhraní pro izolaci falešného od společnosti Microsoft může vytvořit náhradní třídy a metody pro produkční a systémový kód, které v testovaném kódu vytvářejí závislosti. Implementací napodobenin delegátů pro funkci je možné kontrolovat chování a výstup závislého objektu.

Pomocí [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) můžete také prozkoumat kód .NET a vygenerovat testovací data a sadu testů jednotek. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí.  Pro každou podmíněnou větev v kódu se provede případová analýza. 

## <a name="key-tasks"></a>Klíčové úkoly

Následující články vám pomůžou pochopit a vytvářet testy jednotek:

|Úlohy|Související témata|
|-|-----------------------|
|**Rychlé starty a návody:** Přečtěte si o testování částí v aplikaci Visual Studio z příkladů kódu.|- [Návod: vytvoření a spuštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Rychlý Start: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Postupy: Přidání testů jednotek do aplikací C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testování částí pomocí Průzkumníka testů:** Přečtěte si, jak může Průzkumník testů přispět k vytváření produktivity a efektivních testů jednotek.|- [Základy testování částí](../test/unit-test-basics.md)<br />- [Vytvořit projekt testu jednotek](../test/create-a-unit-test-project.md)<br />- [Spuštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md)|
|**Kód jednotkového testu C++**|- [Zápis testů jednotek pro C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Izolace testů jednotek**|- [Izolace testovaného kódu pomocí napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Použití pokrytí kódu k určení toho, jaká část kódu vašeho projektu je testována:** Přečtěte si o funkci pokrytí kódu v testovacích nástrojích sady Visual Studio.|- [Použití pokrytí kódu k určení množství testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Provést zátěžové a výkonnostní analýzy pomocí zátěžových testů:** Naučte se vytvářet zátěžové testy, které vám pomůžou izolovat problémy s výkonem a zátěží ve vaší aplikaci.|- [Rychlý Start: vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md)<br />- [Zátěžové testování (Azure Test Plans a TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Nastavit brány kvality:** Naučte se vytvořit brány kvality k vyzkoušení testů, které se spustí, než se kód vrátí nebo sloučí.|- [Zásady vracení se změnami (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Nastavit možnosti testování:** Naučte se konfigurovat možnosti testu, například, kde jsou uloženy výsledky testů.|[Konfigurace testování částí s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Referenční dokumentace k rozhraní API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Popisuje obor názvů UnitTesting, který poskytuje atributy, výjimky, kontrolní výrazy a další třídy, které podporují testování částí.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> Popisuje obor názvů UnitTesting. Web, který rozšiřuje obor názvů UnitTesting tím, že poskytuje podporu pro ASP.NET a testování částí webové služby.

## <a name="see-also"></a>Viz také

- [Zlepšení kvality kódu](../test/improve-code-quality.md)