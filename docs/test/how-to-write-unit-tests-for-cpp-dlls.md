---
title: Zápis testů jednotek pro knihovny DLL C++
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 045f33c2afcb4f37f5ab81beb21e778edbdd1a61
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056172"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Zápis testů jednotek pro knihovny DLL C++ v sadě Visual Studio

 Existuje několik způsobů, jak testovat kód knihovny DLL, v závislosti na tom, jestli exportuje funkce, které chcete testovat. Vyberte jednu z následujících způsobů:

 **Testování částí volání pouze funkce, které byly exportovány z knihovny DLL:** přidejte samostatný testovací projekt, jak je popsáno v [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md). V testovacím projektu přidejte odkaz na projekt knihovny DLL.

 Pokračujte podle postupu [k odkazování z projektu knihovny DLL exportovaných funkcí](#projectRef).

 **Knihovna DLL je vytvořený jako soubor s příponou .exe:** přidejte samostatný testovací projekt. Propojte jej k výstupnímu objektovému souboru.

 Pokračujte podle postupu [připojení testů k souborům objektů nebo knihoven](#objectRef).

 **Funkce bez členů volání testy jednotek, které nebudou exportovány z knihovny DLL a knihovny DLL může být sestaven jako statická knihovna:** změňte projekt knihovny DLL tak, aby byl kompilován do *lib* souboru. Přidejte samostatný testovací projekt, který odkazuje na projekt v rámci testu.

 Tento přístup má výhodu povolení testy používat Neexportované členy, ale zachováním samostatnosti testovacího projektu.

 Pokračujte podle postupu [změnit na statickou knihovnu DLL](#staticLink).

 **Jednotkové testy musí volat funkce bez členů, které se nebudou exportovat, a kód musí být sestaven jako dynamická knihovna (DLL):** přidat testy jednotek ve stejném projektu s testovaným kódem.

 Pokračujte podle postupu [přidání jednotkových testů do stejného projektu](#sameProject).

## <a name="create-the-tests"></a>Vytvořit testy

###  <a name="staticLink"></a> Chcete-li změnit na statickou knihovnu DLL

- Pokud musí testy používat členy Neexportované projektu knihovny DLL a testovaný projekt je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.

  1.  V **Průzkumníka řešení**, v místní nabídce testovaného projektu, zvolte **vlastnosti**. Projekt **vlastnosti** otevře se okno.

  2.  Zvolte **vlastnosti konfigurace** > **Obecné**.

  3.  Nastavte **typ konfigurace** k **statická knihovna (.lib)**.

  Pokračujte postupem [připojení testů k souborům objektů nebo knihoven](#objectRef).

###  <a name="projectRef"></a> Odkazování na exportované funkce DLL z testovacího projektu

- Pokud projekt knihovny DLL exportuje funkce, které chcete testovat, můžete přidat odkaz na projekt kódu z testovacího projektu.

  1.  Vytvořte projekt testu jednotek Native.

      1.  Na **souboru** nabídce zvolte **nový** > **projektu** > **Visual C++**  >  **Testovací** > **projekt testu jednotek C++**.

  2.  V **Průzkumníka řešení**, v místní nabídce testovacího projektu, zvolte **odkazy**. Projekt **vlastnosti** otevře se okno.

  3.  Vyberte **společné vlastnosti** > **rámec a odkazy**a klikněte na tlačítko **přidat nový odkaz** tlačítko.

  4.  Vyberte **projekty**a pak Testovaný projekt.

       Zvolte **přidat** tlačítko.

  5.  Ve vlastnostech testovacího projektu přidejte umístění testovaného projektu do adresáře Include.

       Zvolte **vlastnosti konfigurace** > **adresáře VC ++** > **adresáře souborů k zahrnutí**.

       Zvolte **upravit**a poté přidejte hlavní adresář testovaného projektu.

  Přejděte na [zápis testů jednotek](#addTests).

###  <a name="objectRef"></a> Připojení testů k souborům objektů nebo knihoven

- Pokud knihovna DLL neexportuje funkce, které chcete testovat, můžete přidat výstup *.obj* nebo *lib* souboru do závislostí testovacího projektu.

  1.  Vytvořte projekt testu jednotek Native.

      1.  Na **souboru** nabídce zvolte **nový** > **projektu** > **Visual C++**  >  **Testovací** > **nativní projekt testu jednotek**.

  2.  V **Průzkumníka řešení**, v místní nabídce testovacího projektu, zvolte **vlastnosti**.

  3.  Zvolte **vlastnosti konfigurace** > **Linkeru** > **vstup** > **Další závislosti**.

       Zvolte **upravit**a přidejte názvy **.obj** nebo **lib** soubory. Nepoužívejte úplné cesty k souborům.

  4.  Zvolte **vlastnosti konfigurace** > **Linkeru** > **Obecné** > **další adresáře knihoven** .

       Zvolte **upravit**a přidejte cestu k adresáři **.obj** nebo **lib** soubory. Cesta je obvykle ve složce sestavení testovaného projektu.

  5.  Zvolte **vlastnosti konfigurace** > **adresáře VC ++** > **adresáře souborů k zahrnutí**.

       Zvolte **upravit**a poté přidejte hlavní adresář testovaného projektu.

  Přejděte na [zápis testů jednotek](#addTests).

###  <a name="sameProject"></a> Přidání jednotkových testů do stejného projektu

1. Úprava vlastností projektu kódu produktu k zahrnovaly hlavičkové soubory a soubory knihoven, které jsou požadovány pro testování částí.

   1.  V **Průzkumníka řešení**, v místní nabídce testovaného projektu, zvolte **vlastnosti**. Projekt **vlastnosti** otevře se okno.

   2.  Zvolte **vlastnosti konfigurace** > **adresáře VC ++**.

   3.  Upravte adresáře Include a Library:

       |Adresář|Vlastnost|
       |-|-|
       |**Adresáře souborů k zahrnutí** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Adresáře knihoven** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Přidáte soubor testu jednotek C++:

   -   V **Průzkumníka řešení**, v místní nabídce projektu zvolte **přidat** > **nová položka** > **Jednotkový Test C++**.

   Přejděte na [zápis testů jednotek](#addTests).

##  <a name="addTests"></a> Zápis testů jednotek

1.  Do každého souboru kódu jednotkového testu přidejte `#include` příkaz pro záhlaví testovaného projektu.

2.  Přidejte testovací třídy a metody do souborů s kódy testu jednotek. Příklad:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>Spustit testy

1.  Na **testovací** nabídce zvolte **Windows** > **Průzkumník testů**.

1. Pokud všechny testy nejsou zobrazeny v okně, vytvoření testovacího projektu kliknutím pravým tlačítkem myši v jeho uzel **Průzkumníka řešení** a zvolíte **sestavení** nebo **znovu sestavit**.

1.  V **Průzkumník testů**, zvolte **spustit všechny**, nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění se zarážkami povolené.

## <a name="see-also"></a>Viz také:

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Reference](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití dynamické knihovny (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
- [Rychlý start: testovací řízeného rozvoje pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
