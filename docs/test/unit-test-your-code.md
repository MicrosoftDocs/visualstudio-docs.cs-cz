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
ms.openlocfilehash: ffe383d2195feb6689954a8ec858b196bae8c06a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565991"
---
# <a name="unit-test-your-code"></a>Testování částí kódu

Testy částí poskytují vývojářům a testerům rychlý způsob, jak hledat logické chyby v metodách tříd v projektech Jazyka C#, Visual Basic a C++.

Nástroje testování částí zahrnují:

* **Průzkumník testů**&mdash;Spusťte testy částí a podívejte se na jejich výsledky v **Průzkumníkovi testů**. Můžete použít libovolnou architekturu testování částí, včetně rozhraní jiného výrobce, která má adaptér pro **Průzkumníka testů**.

* **Microsoft testování částí rámec pro spravovaný kód**&mdash;Rozhraní testování částí společnosti Microsoft pro spravovaný kód je nainstalován s Visual Studio a poskytuje rozhraní pro testování kódu .NET.

* **Microsoft testování částí rámec pro C++**&mdash;Rozhraní testování částí Microsoft pro C++ je nainstalován jako součást **vývoje plochy s c++** zatížení. Poskytuje rámec pro testování nativního kódu. Součástí jsou také rozhraní Google Test, Boost.Test a CTest a pro další testovací architektury jsou k dispozici adaptéry třetích stran. Další informace naleznete v [tématu Write testování částí pro C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Nástroje pokrytí kódu**&mdash;Můžete určit množství kódu produktu, který testy jednotek vykonávají pomocí jednoho příkazu v Průzkumníkovi testů.

* **Microsoft Fakes izolace rámec**&mdash;Microsoft Fakes izolace framework můžete vytvořit náhradní třídy a metody pro produkční a systémový kód, který vytváří závislosti v kódu testovaného. Implementací napodobenin delegátů pro funkci je možné kontrolovat chování a výstup závislého objektu.

[IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) můžete také použít k prozkoumání kódu .NET ke generování testovacích dat a sady testů částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí.  Pro každou podmíněnou větev v kódu se provede případová analýza. 

## <a name="key-tasks"></a>Klíčové úkoly

Následující články vám pomohou pochopit a vytvořit testy částí:

|Úlohy|Související témata|
|-|-----------------------|
|**Rychlé starty a návody:** Další informace o testování částí v sadě Visual Studio z příkladů kódu.|- [Návod: Vytvoření a spuštění testů částí spravovaného kódu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Úvodní příručka: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Postup: Přidání testů částí do aplikací jazyka C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Testování částí pomocí Průzkumníka testů:** Zjistěte, jak může Průzkumník testů pomoci vytvořit produktivnější a efektivnější testování částí.|- [Základy testování částí](../test/unit-test-basics.md)<br />- [Vytvoření projektu testování částí](../test/create-a-unit-test-project.md)<br />- [Spuštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalace testovacích rámců částí jiných výrobců](../test/install-third-party-unit-test-frameworks.md)|
|**Kód C++ testu částí**|- [Zapsat testy částí pro C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Izolování testů částí**|- [Izolovat testovaný kód pomocí Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Pokrytí kódu slouží k určení, jaký podíl kódu projektu se testuje:** Přečtěte si o funkci pokrytí kódu v testovacích nástrojích sady Visual Studio.|- [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Provádějte analýzu napětí a výkonu pomocí zátěžových testů:** Zjistěte, jak vytvořit zátěžové testy, které vám pomůžou izolovat problémy s výkonem a stresem ve vaší aplikaci.|- [Úvodní příručka: Vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md)<br />- [Zátěžové testování (plány testů Azure a TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Nastavit brány kvality:** Zjistěte, jak vytvořit brány kvality k vynucení, že testy jsou spuštěny před vrácením kódu nebo sloučení.|- [Zásady vrácení se změnami (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Nastavení možností testování:** Zjistěte, jak nakonfigurovat možnosti testování, například kde jsou uloženy výsledky testů.|[Konfigurace testů částí s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Referenční dokumentace k rozhraní API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>popisuje obor názvů UnitTesting, který poskytuje atributy, výjimky, nepodmíněných výrazů a další třídy, které podporují testování částí.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>Popisuje obor názvů UnitTesting.Web, který rozšiřuje obor názvů UnitTesting tím, že poskytuje podporu pro testy ASP.NET a jednotkové jednotky webové služby.

## <a name="see-also"></a>Viz také

- [Zlepšení kvality kódu](../test/improve-code-quality.md)
