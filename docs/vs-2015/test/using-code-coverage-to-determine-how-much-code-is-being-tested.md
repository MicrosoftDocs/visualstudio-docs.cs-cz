---
title: Použití pokrytí kódu k určení, kolik kódu je testováno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
ms.assetid: 800fc739-acd2-4242-84cb-1d83b4d82cf9
caps.latest.revision: 38
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 737311167fc1f444d5c0f8a5d2c27e2fe321da75
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851241"
---
# <a name="using-code-coverage-to-determine-how-much-code-is-being-tested"></a>Použití pokrytí kódu k určení rozsahu testovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Pro efektivní ochranu před chybami je vhodné testovat, neboli „pokrýt“, velkou část kódu projektu.

 Analýza pokrytí kódu může být použita jak pro spravovaný (CLI), tak pro nespravovaný (nativní) kód.

 Pokrytí kódu je jedna z možností při spouštění testovacích metod pomocí Průzkumníku testů. Tabulka výsledků zobrazuje procentuální podíl kódu, který byl spuštěn v každém sestavení, třídě a metodě. Editor zdrojového kódu navíc ukazuje samotný kód, který byl testován.

 ![Výsledky pokrytí kódu s barvou](../test/media/codecoverage1.png "CodeCoverage1")

 **Požadavky**

- Visual Studio Enterprise

### <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Analýza pokrytí kódu jednotkovými testy v Průzkumníku testů

1. V nabídce **test** vyberte možnost **Analyzovat pokrytí kódu**.

2. Chcete-li zjistit, které řádky byly spuštěny, klikněte na možnost ![Zobrazit ikonu barevného pokrytí kódu](../test/media/codecoverage-showcoloringicon.png "CodeCoverage – ShowColoringIcon")**Zobrazit barvy pokrytí kódu**.

     Chcete-li změnit barvy nebo použít tučnou plochu, vyberte možnost **nástroje**, **Možnosti**, **prostředí**, **písma a barvy**, **Zobrazit nastavení pro: textový editor**. V části **Zobrazit položky**upravte položky pokrytí.

3. Pokud výsledky zobrazují nízké pokrytí, prozkoumejte, které části kódu nejsou testovány, a vytvořte pro ně další testy. Vývojové týmy obvykle usilují o 80% pokrytí kódu. V některých situacích je přijatelné i nižší pokrytí. Nižší pokrytí je například přijatelné tehdy, pokud je část kódu generována ze standardní šablony.

> [!TIP]
> Získání přesných výsledků:
>
> - Ujistěte se, že je vypnuta optimalizace kompilátoru.
>
>   Pokud pracujete s nespravovaným (nativním) kódem, použijte sestavení pro ladění.
>   - Ujistěte se, že jsou generovány soubory s příponou .pdb (soubory symbolů) pro každé sestavení.
>
>   Pokud nezískáte očekávané výsledky, přečtěte si téma [řešení potíží s pokrytím kódu](../test/troubleshooting-code-coverage.md). . Po aktualizaci kódu nezapomeňte znovu spustit pokrytí kódu. Výsledky pokrytí kódu a barevné zvýraznění kódu nejsou po změně kódu nebo při spuštění testů automaticky aktualizovány.

## <a name="reporting-in-blocks-or-lines"></a>Vykazování v blocích nebo řádcích
 Pokrytí kódu se počítá v *blocích*. Blok je část kódu s právě jedním vstupním a výstupním bodem.  Pokud tok řízení programu projde při testovacím běhu blokem, tento blok se započítá jako pokrytý. Počet průchodů blokem nemá na výsledek žádný vliv.

 Výsledky můžete zobrazit také v části řádky kliknutím na možnost **Přidat nebo odebrat sloupce** v záhlaví tabulky. Pokud testovací běh otestoval všechny bloky na jednom řádku kódu, započítá se tento řádek jako úplný řádek. Když řádek obsahuje jak otestované, tak i neotestované bloky, pak se započítá jako částečný řádek.

 Někteří uživatelé dávají přednost určování pokrytí podle počtu řádků, protože jeho procenta lépe odpovídají velikosti fragmentů, které jsou vidět ve zdrojovém kódu. Dlouhý blok výpočtu by byl započítán jako jeden blok i v případě, že zabírá mnoho řádků.

## <a name="managing-code-coverage-results"></a>Správa výsledků pokrytí kódu
 Okno Výsledky pokrytí kódu obvykle zobrazuje výsledek posledního běhu. Výsledky se budou lišit, pokud dojde ke změně zkušebních dat nebo jsou pokaždé spuštěny jen některé testy.

 Okno pokrytí kódu lze také použít k zobrazení předchozích výsledků nebo výsledků získaných na jiných počítačích.

 Je také možné sloučit výsledky několika běhů, pokud například používají jiná testovací data.

- Pokud **chcete zobrazit předchozí sadu výsledků**, vyberte ji z rozevírací nabídky. Nabídka obsahuje dočasný seznam, který je po otevření nového řešení vyprázdněn.

- Pokud **chcete zobrazit výsledky z předchozí relace**, vyberte možnost **importovat výsledky pokrytí kódu**, přejděte do složky TestResults ve vašem řešení a importujte soubor. pokrytí.

     Vybarvení pokrytí může být nesprávné v případě, že byl zdrojový kód změněn od chvíle vygenerování souboru s příponou .coverage.

- Pokud chcete, aby **výsledky byly čitelné jako text**, vyberte **Exportovat výsledky pokrytí kódu**. Tím se vytvoří soubor s příponou .coveragexml, který je možné zpracovat v jiných nástrojích nebo jednoduše odeslat e-mailem.

- **Chcete-li odeslat výsledky někomu jinému**, odešlete soubor. pokrytí nebo exportovaný soubor. coveragexml. Tento soubor je pak možné importovat. Pokud se navíc shodují verze zdrojového kódu, je možné zobrazit i vybarvení pokrytí.

## <a name="merging-results-from-different-runs"></a>Sloučení výsledků různých běhů
 V některých situacích se na základě testovacích dat použijí různé bloky kódu. Může být tedy nutné sloučit výsledky různých testovacích běhů.

 Například při spuštění testu se vstupem „2“ je zjištěno 50% pokrytí určité funkce. Při druhém spuštění testu se vstupem „-2“ se v okně pokrytí zobrazí pokrytí zbylých 50 % funkce. Po sloučení výsledků těchto dvou testovacích běhů ukáže sestava i vybarvení 100% pokrytí funkce.

 K tomu slouží ![Ikona tlačítka pro sloučení v okně pokrytí kódu](../test/media/codecoverage-mergeicon.png "CodeCoverage – MergeIcon")pro**sloučení výsledků pokrytí kódu** . Ke sloučení je možné použít libovolnou kombinaci předešlých běhů nebo importovaných výsledků. Pokud je potřeba sloučit exportované výsledky, je nejprve nutné je importovat.

 Pomocí **exportu výsledků pokrytí kódu** uložte výsledky operace sloučení.

### <a name="limitations-in-merging"></a>Omezení při slučování

- Při sloučení dat pokrytí rozdílných verzí kódu jsou výsledky zobrazeny odděleně, ale nejsou sloučeny. Pro kompletní sloučení výsledků je potřeba použít stejné sestavení kódu pouze s odlišnými testovacími daty.

- Pokud dojde ke sloučení souboru výsledků, který byl exportován a poté importován, je možné zobrazit výsledky jen podle řádků, nikoli podle bloků. K zobrazení dat řádku použijte příkaz **Přidat nebo odebrat sloupce** .

- Při sloučení výsledků testů projektu aplikace ASP.NET dojde k zobrazení výsledků samostatných testů, ale ne k jejich sloučení. To platí pouze pro samotné artefakty ASP.NET, výsledky pro jakákoli jiná sestavení budou sloučeny.

## <a name="excluding-elements-from-the-code-coverage-results"></a>Vyloučení prvků z výsledků pokrytí kódu
 Je možné vyloučit určité prvky v kódu z výpočtů pokrytí, například proto, že je kód generován z textové šablony. Přidejte atribut `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` do některého z následujících prvků kódu: třída, struktura, metoda, vlastnost, setter vlastnosti nebo getter, Event. Za povšimnutí stojí, že vyloučení třídy nevylučuje její odvozené třídy.

 Příklad:

```csharp

using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }

```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class

```

```cpp#
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }

}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }

```

### <a name="excluding-elements-in-native-c-code"></a>Vyloučení prvků v nativním kódu jazyka C++
 Vyloučení nespravovaných (nativních) prvků kódu jazyka C++:

```cpp

#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)

```

 Použijte následující makra:

 `ExcludeFromCodeCoverage(` *vyloučení* `, L"` *Function* `");`

 `ExcludeSourceFromCodeCoverage(` *vyloučení* `, L"` *SourceFilePath* `");`

- Název *vyloučení* je libovolný jedinečný název.

- Název *funkce* je plně kvalifikovaný název funkce. Může obsahovat zástupné znaky. Chcete-li například vyloučit všechny funkce třídy, zapište `MyNamespace::MyClass::*`

- *SourceFilePath* je místní cesta nebo cesta UNC k souboru. cpp. Může obsahovat zástupné znaky. Následující příklad vyloučí všechny soubory v konkrétním adresáři: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Umístěte volání maker vyloučení do globálního oboru názvů a nikoli v rámci libovolného oboru názvů nebo třídy.

- Vyloučení se umisťuje buď do souboru kódu jednotkového testu, nebo do souboru kódu aplikace.

- Vyloučení musí být zkompilována jako nespravovaný (nativní) kód, a to buď nastavením možnosti kompilátoru, nebo pomocí `#pragma managed(off)`.

> [!NOTE]
> Chcete-li vyloučit C++funkce v kódu/CLI, použijte atribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` na funkci. Toto je stejné použití jako v jazyce C#.

### <a name="including-or-excluding-additional-elements"></a>Zahrnutí nebo vyloučení dalších prvků
 Analýza pokrytí kódu je provedena pouze u sestavení, která jsou načtena a pro něž je k dispozici soubor s příponou .pdb ve stejném adresáři jako soubor s příponou .dll nebo .exe. Proto je v některých případech možné rozšířit sadu zahrnutých sestavení získáním kopie jejich souborů s příponou .pdb.

 Je také možné získat větší kontrolu nad sestaveními a prvky vybranými pro analýzu pokrytí kódu vytvořením souboru .runsettings. Je tak například možné vyloučit určitá sestavení bez nutnosti přidávání atributů jejich třídám. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="analyzing-code-coverage-in-the-build-service"></a>Analýza pokrytí kódu ve službě sestavení
 Při vrácení kódu se změnami jsou testy spuštěny na serveru sestavení společně se všemi dalšími testy ostatních členů týmu. (Pokud jste to ještě neudělali, přečtěte si téma [spuštění testů v procesu sestavení](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Je vhodné analyzovat pokrytí kódu ve službě sestavení, protože poskytuje nejaktuálnější a komplexní přehled o pokrytí celého projektu. Takový postup bude také zahrnovat automatizované systémové testy a další kódované testy, které nejsou obvykle spouštěny na počítačích vývojářů.

1. V Team Explorer otevřete **sestavení**a pak přidejte nebo upravte definici sestavení.

2. Na stránce **proces** rozbalte položku **automatizované testy**, **zdroj testu**, **parametry spuštění**. Nastavte **typ souboru parametrů běhu** na možnost **pokrytí kódu povoleno**.

    Pokud máte více než jednu definici Zdroje testu, opakujte tento krok pro každou z nich.

   - <em>Ale k dispozici není žádné pole s názvem **typ souboru parametrů běhu</em>* . *

      V části **automatizované testy**vyberte možnost **test sestavení** a zvolte tlačítko se třemi tečkami **[...]** na konci řádku. V dialogovém okně **Přidat/upravit testovací běh** vyberte v části **Test Runner**možnost **Visual Studio Test Runner**.

   ![Nastavení definice sestavení pro pokrytí kódu](../test/media/codecoverage-plaincc.png "CodeCoverage – plainCC")

   Když sestavení proběhne, jsou výsledků pokrytí kódu připojeny k testovacímu běhu a zobrazí se v přehledu sestavení.

## <a name="analyzing-code-coverage-in-a-command-line"></a>Analýza pokrytí kódu v příkazovém řádku
 Pro spuštění testů z příkazového řádku se používá příkaz vstest.console.exe. Pokrytí kódu je jednou z možností tohoto nástroje. Další informace najdete v tématu [Možnosti příkazového řádku VSTest. Console. exe](https://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11).

1. Spusťte příkazový řádek pro vývojáře v sadě Visual Studio:

     V nabídce **Start** systému Windows vyberte **všechny programy**, **Microsoft Visual Studio**, **Visual Studio Tools** **Developer Command Prompt**.

2. Spustit:

     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshooting"></a>Odstraňování problémů
 Pokud nevidíte výsledky pokrytí kódu, přečtěte si téma [řešení potíží s pokrytím kódu](../test/troubleshooting-code-coverage.md).

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Viz také
 [Přizpůsobení analýzy pokrytí](../test/customizing-code-coverage-analysis.md) kódu [řešení potíží](../test/troubleshooting-code-coverage.md) [testování částí](../test/unit-test-your-code.md) pokrytí kódu kód
