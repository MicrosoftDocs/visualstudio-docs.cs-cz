---
title: Testování částí
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: fd6d6dca2680dcfcaa42912333b080c428ba78d2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659850"
---
# <a name="unit-test-your-code"></a>Testování částí kódu

Testy jednotek umožňují vývojářům a testerům rychlý způsob vyhledávání logických chyb v metodách tříd v C#, Visual Basic a C++ projektech.

Nástroje testování částí zahrnují:

* **Průzkumník testů** &mdash;Run testy jednotek a jejich výsledky se zobrazí v **Průzkumníku testů**. Můžete použít libovolné rozhraní testování částí, včetně rozhraní třetí strany, které má adaptér pro **Průzkumníka testů**.

* **Microsoft Unit Test Framework pro spravovaný kód** &mdash;The Microsoft Unit Test Framework pro spravovaný kód se instaluje se sadou Visual Studio a poskytuje rozhraní pro testování kódu .NET.

* **Microsoft Unit Test Framework pro C++**  &mdash;The Microsoft Unit Test Framework pro C++ je nainstalovaná jako součást **vývoje C++ desktopových** aplikací. Poskytuje rozhraní pro testování nativního kódu. K dispozici jsou také Google Test, zvyšování a CTest architektury a adaptéry třetích stran jsou k dispozici pro další testovací architektury. Další informace najdete v tématu [zápis testů jednotek pro C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Nástroje pokrytí kódu** &mdash;You mohou určit množství kódu produktu, který testování částí vykonává z jednoho příkazu v Průzkumníku testů.

* **Microsoft předstírá izolaci – rozhraní** pro izolaci &mdash;The společnosti Microsoft falešné rozhraní může vytvořit náhradní třídy a metody pro produkční a systémový kód, který v testovaném kódu vytvoří závislosti. Implementací napodobenin delegátů pro funkci je možné kontrolovat chování a výstup závislého objektu.

Pomocí [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) můžete také prozkoumat kód .NET a vygenerovat testovací data a sadu testů jednotek. Pro každý příkaz v kódu se generuje vstupní test, který spustí tento příkaz. Pro každou podmíněnou větev v kódu se provede analýza případu.

## <a name="key-tasks"></a>Klíčové úkoly

Následující články vám pomůžou pochopit a vytvářet testy jednotek:

|Úkoly|Související témata|
|-|-----------------------|
|**Rychlé starty a návody:** Přečtěte si o testování částí v aplikaci Visual Studio z příkladů kódu.|- [Návod: vytvoření a spuštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />[rychlý start - : Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Postupy: Přidání testů jednotek do C++ aplikací](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testování částí pomocí Průzkumníka testů:** Přečtěte si, jak může Průzkumník testů přispět k vytváření produktivity a efektivních testů jednotek.|[základy testování částí](../test/unit-test-basics.md) - <br />- [vytvořit projekt testu jednotek](../test/create-a-unit-test-project.md)<br />- [Spustit testy jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)<br />- [nainstalovat rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md)|
|**Kód testu C++ jednotek**|- [napsat testy jednotek pro C/C++ ](../test/writing-unit-tests-for-c-cpp.md)|
|**Izolace testů jednotek**|- [izolujte testovaný kód s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Použití pokrytí kódu k určení toho, jaká část kódu vašeho projektu je testována:** Přečtěte si o funkci pokrytí kódu v testovacích nástrojích sady Visual Studio.|- [Použití pokrytí kódu k určení množství testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Provést zátěžové a výkonnostní analýzy pomocí zátěžových testů:** Naučte se vytvářet zátěžové testy, které vám pomůžou izolovat problémy s výkonem a zátěží ve vaší aplikaci.|[rychlý start - : vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md)<br />[zátěžové testování -  (Azure test Plans a TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Nastavit brány kvality:** Naučte se vytvořit brány kvality k vyzkoušení testů, které se spustí, než se kód vrátí nebo sloučí.|- [Zásady vracení se změnami (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Nastavit možnosti testování:** Naučte se konfigurovat možnosti testu, například, kde jsou uloženy výsledky testů.|[Konfigurace testů částí s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Referenční dokumentace k rozhraní API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> popisuje obor názvů UnitTesting, který poskytuje atributy, výjimky, kontrolní výrazy a další třídy, které podporují testování částí.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> popisuje obor názvů UnitTesting. Web, který rozšiřuje obor názvů UnitTesting tím, že poskytuje podporu pro ASP.NET a testování částí webové služby.

## <a name="see-also"></a>Viz také:

- [Zlepšení kvality kódu](../test/improve-code-quality.md)
