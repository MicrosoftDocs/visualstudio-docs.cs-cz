---
title: Testování částí kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: gewarren
manager: douge
ms.openlocfilehash: f79fb0ac4945253f1a10ce98a7e1ed17eaa6de63
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950417"
---
# <a name="unit-test-your-code"></a>Testy jednotek kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testování částí poskytuje vývojářům a testerům rychlý způsob vyhledávání logických chyb v rámci metod tříd v [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)], a [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] projekty.  
  
 Nástroje testování částí zahrnují:  
  
1. **Průzkumník testů.** Průzkumník testů dovoluje spouštět testy částí a zobrazit jejich výsledky. Průzkumník testů může použít libovolné rozhraní testování částí, včetně rozhraní třetích stran, které má adaptér pro Průzkumníka.  
  
2. **Oddělení Microsoft unit test framework pro spravovaný kód.** Rozhraní společnosti Microsoft pro testování částí spravovaného kódu je nainstalováno spolu se sadou Visual Studio a poskytuje rozhraní pro testování kódu rozhraní .NET.  
  
3. **Microsoft pro testování částí C++.** Rozhraní Microsoft pro testování částí kódu v jazyce C++ je nainstalováno spolu se sadou Visual Studio a poskytuje rozhraní pro testování nativního kódu.  
  
4. **Nástroje pokrytí kódu.** Množství kódu produktu, které testování částí kontroluje, je možné určit jedním příkazem v Průzkumníku testů.  
  
5. **Izolační rozhraní Microsoft Fakes.** Izolační rozhraní Microsoft Fakes může vytvořit zástupné třídy a metody pro produkční a systémový kód, které během testu vytváří závislosti v kódu. Implementací napodobenin delegátů pro funkci je možné kontrolovat chování a výstup závislého objektu.  
  
   Můžete také použít [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) prozkoumat kód .NET a vygenerovat testovací data a sady testování částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí. Pro každou podmíněnou větev v kódu se provede Případová analýza.  
  
## <a name="key-tasks"></a>Klíčové úkoly  
 V následujících tématech naleznete informace týkající se vytváření testování částí a sloužící k jeho lepšímu pochopení:  
  
|Úlohy|Související témata|  
|-----------|-----------------------|  
|**Rychlé začátky a návody:** další testování v sadě Visual Studio z příkladů kódů použijte následující témata.|-   [Postupy: Vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Rychlý Start: Testovací vývoj řízený testy s použitím Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Testování částí nativního kódu pomocí Průzkumníka testů](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Testování částí pomocí Průzkumníka testů:** zjistěte, jak může Průzkumník testů pomoci vytváření produktivnějších a efektivnějších testů jednotek.|-   [Základní informace o testování částí](../test/unit-test-basics.md)<br />-   [Vytvořte projekt testu jednotek](../test/create-a-unit-test-project.md)<br />-   [Spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)<br />-   [Nainstalujte rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)<br />-   [Upgradování testů částí z produktu Visual Studio 2010](http://msdn.microsoft.com/en-us/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Testování částí spravovaného kódu:**|-   [Zápis testů částí pro rozhraní .NET Framework s použitím rozhraní Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Testování částí kódu C++**|-   [Zápis testů jednotek pro C/C++ se sadou Microsoft Unit Testing Framework pro C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Izolující testování částí**|-   [Izolace testovaného kódu pomocí napodobenin Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Použití pokrytí kódu k identifikaci, jaká část projektového kódu je testována pomocí testů jednotek:** přečtěte si víc o funkcích pokrytí kódu [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] testovací nástroje.|-   [Použití pokrytí kódu k určení jak mnohem kódu je testována](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Provedení zátěžové a výkonnostní analýzy použitím zátěžových testů pro testování částí:** můžete vytvořit zátěžový test a testování částí přidejte do ní pro lepší izolaci výkonnostních a zátěžových problémů aplikace. **Poznámka:** vytváření a používání zátěžových testů vyžaduje Visual Studio Enterprise.|-   [Vytváření a úpravy zátěžových testů](http://msdn.microsoft.com/en-us/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Postupy: Přidání testy webového výkonu a testování částí do scénáře zátěžového testu](http://msdn.microsoft.com/en-us/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Postupy: odebrání do scénáře zátěžového testu webové testy a testy jednotek](http://msdn.microsoft.com/en-us/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Nastavení a vynucení bran kvality:** můžete vytvořit brány kvality k vynucení spuštění testů předtím, než kód se změnami pro zajištění kvality kódu.|-   [Nastavení a vynucení bran kvality](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Rozšíření typu testování částí:** můžete přidat funkci do testů, které nemusí být v rozhraní testování částí. Například je možné přidat vlastnost testu, která specifikuje, zda má test běžet pod běžným uživatelem nebo ne. Nebo je možné rozšířit rozhraní přidáním atributů řádku do metody a použít data v tomto řádku uvnitř testu.|Ukázkový kód pro rozšíření rozhraní testování částí, naleznete na následujícím [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Nastavení možností testování:** například můžete určit, kde jsou uloženy výsledky testů.|[Konfigurace testů částí s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
 [Vyhodnocení výsledků testů v nástroji Microsoft Test Manager](http://msdn.microsoft.com/en-us/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Popisuje výsledky testů a způsoby, jak s nimi pracovat, včetně jejich prohlížení, uložení a odstranění.  
  
 [Spouštění systémových testů pomocí sady Microsoft Visual Studio](http://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)  
  
 Obsahuje odkazy na informace o používání sady Visual Studio místo [!INCLUDE[TCMext](../includes/tcmext-md.md)] ke spuštění automatizovaných testů.  
  
## <a name="reference"></a>Odkaz  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Popisuje obor názvů UnitTesting, který poskytuje atributy, výjimky, kontrolní výrazy a další třídy, které podporují testování částí.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Popisuje obor názvů UnitTesting.Web, který rozšiřuje obor názvů UnitTesting poskytováním podpory pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a jednotkové testy webových služeb.  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="videos"></a>Videa  
 [Kanál 9: Testování vašich aplikací Windows Store vyvíjené v XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Diskuzní fóra  
 [Testování částí sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Odkaz  
 [Index obsahu pro testování částí](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Viz také  
 [Zlepšení kvality kódu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Testování aplikace](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)



