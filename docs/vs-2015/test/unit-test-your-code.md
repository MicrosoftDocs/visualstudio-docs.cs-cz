---
title: Testování částí kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851263"
---
# <a name="unit-test-your-code"></a>Testy jednotek kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednotek poskytují vývojářům a testerům rychlý způsob vyhledávání logických chyb v metodách třídy v projektech [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]a [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].

 Nástroje testování částí zahrnují:

1. **Průzkumník testů.** Průzkumník testů dovoluje spouštět testy částí a zobrazit jejich výsledky. Průzkumník testů může použít libovolné rozhraní testování částí, včetně rozhraní třetích stran, které má adaptér pro Průzkumníka.

2. **Microsoft Unit Test Framework pro spravovaný kód.** Rozhraní společnosti Microsoft pro testování částí spravovaného kódu je nainstalováno spolu se sadou Visual Studio a poskytuje rozhraní pro testování kódu rozhraní .NET.

3. **Rozhraní Microsoft pro testování částí C++pro.** Rozhraní Microsoft pro testování částí kódu v jazyce C++ je nainstalováno spolu se sadou Visual Studio a poskytuje rozhraní pro testování nativního kódu.

4. **Nástroje pokrytí kódu.** Množství kódu produktu, které testování částí kontroluje, je možné určit jedním příkazem v Průzkumníku testů.

5. **Microsoft předstírá izolační rozhraní.** Izolační rozhraní Microsoft Fakes může vytvořit zástupné třídy a metody pro produkční a systémový kód, které během testu vytváří závislosti v kódu. Implementací napodobenin delegátů pro funkci je možné kontrolovat chování a výstup závislého objektu.

   Můžete také použít [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) prozkoumat kód .NET a vygenerovat testovací data a sady testování částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí. Pro každou podmíněnou větev v kódu se provede Případová analýza.

## <a name="key-tasks"></a>Klíčové úkoly
 V následujících tématech naleznete informace týkající se vytváření testování částí a sloužící k jeho lepšímu pochopení:

|Tasks|Související témata|
|-----------|-----------------------|
|**Rychlé začátky a návody:** další testování v sadě Visual Studio z příkladů kódů použijte následující témata.|-   [Návod: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [rychlé zprovoznění: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [přidávání jednotkových testů do C++ stávajících aplikací](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [testování částí nativního kódu pomocí Průzkumníka testů](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Testování částí pomocí Průzkumníka testů:** zjistěte, jak může Průzkumník testů pomoci vytváření produktivnějších a efektivnějších testů jednotek.|[základy testování částí](../test/unit-test-basics.md) -   <br />-   [Vytvořte projekt testu jednotek](../test/create-a-unit-test-project.md)<br />-   [Spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)<br />-   [Nainstalujte rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)<br />-   [upgradovat testy jednotek ze sady Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Testování částí spravovaného kódu:**|-   [zápis testů částí pro .NET Framework pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Testování částí kódu C++**|-   [zápis testů částí pro C/C++ s architekturou testování částí společnosti Microsoft C++ pro](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Izolující testování částí**|-   [izolování testovaného kódu s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Použití pokrytí kódu k určení toho, jaká část kódu projektu je testována pomocí jednotkových testů:** Přečtěte si o funkci pokrytí kódu [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]ch testovacích nástrojů.|-   [Použití pokrytí kódu k určení množství testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Proveďte zátěžové a výkonnostní analýzy pomocí zátěžových testů pro testování částí:** Můžete vytvořit zátěžový test a přidat do něj testy jednotek, které vám pomůžou izolovat problémy s výkonem a zátěží ve vaší aplikaci. **Poznámka:**  Vytváření a používání zátěžových testů vyžaduje Visual Studio Enterprise.|-   [vytváření a úpravy zátěžových testů](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Postupy: Přidání testů výkonnosti webu a testování částí do scénáře zátěžového testu](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Postupy: odebrání webových testů a testů jednotek z scénáře zátěžového testu](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Nastavit a vymáhat brány kvality:** Můžete vytvořit brány kvality k vyzkoušení testů, které jsou spuštěny před vrácením kódu se změnami, aby bylo zajištěno zvýšení kvality kódu.|-   [nastavit a vymáhat brány kvality](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Zvětšete typ testu jednotek:** Do testů můžete přidat funkci, která nemusí být v rozhraní testování částí. Například je možné přidat vlastnost testu, která specifikuje, zda má test běžet pod běžným uživatelem nebo ne. Nebo je možné rozšířit rozhraní přidáním atributů řádku do metody a použít data v tomto řádku uvnitř testu.|Vzorový kód pro rozšiřování rozhraní testování částí naleznete na následujícím webu [společnosti Microsoft](https://msdn.microsoft.com/vstudio/ff420671.aspx).|
|**Nastavení možností testování:** například můžete určit, kde jsou uloženy výsledky testů.|[Konfigurace testů částí s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>Související úlohy
 [Kontrola Výsledky testů v Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Popisuje výsledky testů a způsoby, jak s nimi pracovat, včetně jejich prohlížení, uložení a odstranění.

 [Spouštění systémových testů pomocí Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Obsahuje odkazy na informace o použití sady Visual Studio na rozdíl od použití [!INCLUDE[TCMext](../includes/tcmext-md.md)] ke spouštění automatizovaných testů.

## <a name="reference"></a>Odkaz
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> popisuje obor názvů UnitTesting, který poskytuje atributy, výjimky, kontrolní výrazy a další třídy, které podporují testování částí.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> popisuje obor názvů UnitTesting. Web, který rozšiřuje obor názvů UnitTesting tím, že poskytuje podporu pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a testování částí webové služby.

## <a name="external-resources"></a>Externí zdroje

### <a name="videos"></a>Videa
 [Kanál 9: testování částí aplikací pro Windows Store vytvořených pomocí jazyka XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Diskuzní fóra
 [Testování částí sady Visual Studio](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Odkaz
 [Index obsahu pro testování částí](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>Viz také
 [Zlepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [při testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
