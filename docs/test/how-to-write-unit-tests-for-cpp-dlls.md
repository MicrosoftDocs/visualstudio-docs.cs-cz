---
title: Zápis testů jednotek pro knihovny DLL jazyka C++
description: Seznamte se s několika způsoby testování kódu knihovny DLL v závislosti na tom, jestli knihovna DLL exportuje funkce, které chcete testovat.
ms.custom: SEO-VS-2020
ms.date: 02/16/2021
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 6e8df96c6345d84531ef04eae56f7f60dcc3eefe
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042870"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Zápis testů jednotek pro knihovny DLL jazyka C++ v Visual Studio

Existuje několik způsobů testování kódu knihovny DLL v závislosti na tom, jestli exportuje funkce, které chcete testovat. Zvolte jeden z následujících způsobů:

**Testy jednotek volají pouze funkce, které jsou exportovány z knihovny DLL:** Přidejte samostatný projekt testů, jak je popsáno v [tématu Zápis testů jednotek pro C/C++.](writing-unit-tests-for-c-cpp.md) V projektu testů přidejte odkaz na projekt knihovny DLL.

Přejděte k postupu [Odkazování na exportované funkce z projektu knihovny DLL](#projectRef).

**Knihovna DLL je sestavená jako .exe souborů:** Přidejte samostatný projekt testů. Propojte ho se souborem výstupního objektu.

Přejděte k postupu [Propojení testů se soubory objektu nebo knihovny](#objectRef).

**Testy jednotek volají ne členské** funkce, které nejsou exportovány z knihovny DLL, a knihovnu DLL lze vytvořit jako statickou knihovnu: Změňte projekt knihovny DLL tak, aby byl zkompilován do *souboru .lib.* Přidejte samostatný projekt testů, který odkazuje na testový projekt.

Tento přístup má výhodu v tom, že testy mohou používat neexportované členy, ale stále je uchováte v samostatném projektu.

Přejděte k postupu [Změna knihovny DLL na statickou knihovnu](#staticLink).

**Testy jednotek musí volat ne členské funkce,** které nejsou exportovány, a kód musí být sestaven jako dynamická knihovna (DLL): Přidejte testy jednotek do stejného projektu jako kód produktu.

Přejděte k postupu [Přidání testů jednotek do stejného projektu](#sameProject).

## <a name="create-the-tests"></a>Vytvoření testů

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Změna knihovny DLL na statickou knihovnu

- Pokud testy musí používat členy, které nejsou exportovány projektem knihovny DLL, a testovaný projekt je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.

  1. V **Průzkumník řešení** místní nabídce testového projektu zvolte **Vlastnosti**. Otevře se **okno Vlastnosti** projektu.

  2. Zvolte **Vlastnosti konfigurace**  >  **Obecné.**

  3. Nastavte **Typ konfigurace** na **Statická knihovna (.lib).**

  Pokračujte postupem Propojení testů se soubory [objektu nebo knihovny](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Odkazování na exportované funkce knihovny DLL z testovacího projektu

- Pokud projekt knihovny DLL exportuje funkce, které chcete testovat, můžete přidat odkaz na projekt kódu z testovacího projektu.

  1. Vytvořte projekt nativního testu jednotek.

      ::: moniker range=">=vs-2019"

      1. V **nabídce File (Soubor)** zvolte New Project   >  **(Nový projekt).** V dialogovém **okně Přidat nový projekt** nastavte **Jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **projekt nativního testu jednotek**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **File (Soubor)** zvolte **New** > **Project (Nový** > **projekt) Visual C++** > **Test** > **jednotek C++ Unit Test Project (Projekt testování jednotek C++).**

      ::: moniker-end

  1. V **Průzkumník řešení** klikněte pravým tlačítkem na testovací projekt a pak zvolte **Přidat**  >  **odkaz.**

  1. Vyberte **Projects (Projekty)** a pak projekt, který se má otestovat.

       Vyberte tlačítko **Přidat**.

  1. Ve vlastnostech testovacího projektu přidejte umístění testového projektu do adresáře Include.

       Zvolte **Vlastnosti konfigurace** Adresáře  >  **VC++ Zahrnout**  >  **adresáře**.

       Zvolte **Upravit** a pak přidejte adresář hlaviček projektu v rámci testu.

  Přejděte na [stránku Write the unit tests (Napsat testy jednotek).](#addTests)

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Propojení testů se soubory objektu nebo knihovny

- Pokud knihovna DLL neexportuje funkce, které chcete otestovat, můžete do závislostí testovacího projektu přidat výstupní soubor *.obj* nebo *.lib.*

  1. Vytvořte projekt nativního testu jednotek.

      ::: moniker range=">=vs-2019"

      1. V **nabídce File (Soubor)** zvolte New Project   >  **(Nový projekt).** V dialogovém **okně Přidat nový projekt** nastavte **Jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **projekt nativního testu jednotek**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **File (Soubor)** zvolte **New** > **Project (Nový** > **projekt) Visual C++** > **Test** > **jednotek C++ Unit Test Project (Projekt testování jednotek C++).**

      ::: moniker-end

  1. V **Průzkumník řešení** místní nabídce testovacího projektu zvolte **Vlastnosti**.

  1. Zvolte **Vlastnosti konfigurace** Další závislosti  >  **linkeru**  >    >  **Vstup.**

       Zvolte **Upravit** a přidejte názvy **souborů .obj** nebo **.lib.** Nepoužívejte úplné názvy cest.

  1. Zvolte   >  **Linker Vlastnosti konfigurace**  >  **Obecné** další  >  **adresáře knihovny.**

       Zvolte **Upravit** a přidejte cestu k adresáři **souborů .obj** nebo **.lib.** Cesta je obvykle ve složce sestavení testového projektu.

  1. Zvolte **Vlastnosti konfigurace** Adresáře  >  **VC++ Zahrnout**  >  **adresáře**.

       Zvolte **Upravit** a pak přidejte adresář hlaviček projektu v rámci testu.

  Přejděte na [stránku Write the unit tests (Napsat testy jednotek).](#addTests)

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Přidání testů jednotek do stejného projektu

1. Upravte vlastnosti projektu kódu produktu tak, aby zahrnovaly hlavičky a soubory knihovny potřebné pro testování částí.

   1. V **Průzkumník řešení** místní nabídce testového projektu zvolte **Vlastnosti**. Otevře se **okno Vlastnosti** projektu.

   1. Zvolte **Vlastnosti konfigurace** Adresáře  >  **VC++.**

   1. Upravte adresáře Include a Library:

       |Adresář|Vlastnost|
       |-|-|
       |**Adresáře k zahrnutí** | **$(VCInstallDir)Auxiliary\VS\UnitTest\include** |
       |**Adresáře knihoven** | **$(VCInstallDir)Auxiliary\VS\UnitTest\lib** |

1. Přidejte soubor testu jednotek C++:

   1. Klikněte pravým tlačítkem na uzel projektu v **Průzkumník řešení** **a zvolte Přidat** novou  >  **položku**.

   1. V dialogovém **okně Přidat novou** položku vyberte Soubor  **C++ (.cpp),** dejte mu odpovídající název a pak zvolte **Přidat**.

   Přejděte na [stránku Write the unit tests (Napsat testy jednotek).](#addTests)

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Zápis testů jednotek

1. Do každého souboru kódu testu jednotek přidejte příkaz pro `#include` hlavičky testového projektu.

1. Přidejte testovací třídy a metody do souborů kódu testu jednotek. Příklad:

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

## <a name="run-the-tests"></a>Spuštění testů

1. V **nabídce Test** zvolte Průzkumník **testů Systému Windows.**  >  

1. Pokud se v okně nezobrazí všechny vaše testy, sestavte projekt testů: klikněte pravým tlačítkem na jeho uzel v **Průzkumník řešení** zvolte **Sestavit** nebo **Znovu sestavit**.

1. V **Průzkumníku** testů zvolte **Spustit vše** nebo vyberte konkrétní testy, které chcete spustit. Kliknutím pravým tlačítkem na test zobrazíte další možnosti, například pro jeho spuštění v režimu ladění s povolenými zarážkami.

## <a name="see-also"></a>Viz také

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
- [Referenční informace k rozhraní API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití dynamické knihovny DLL (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
- [Rychlý start: Vývoj řízený testy pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
