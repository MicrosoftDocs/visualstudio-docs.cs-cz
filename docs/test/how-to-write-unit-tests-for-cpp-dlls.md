---
title: Zapsat testy částí pro knihovny DLL jazyka C++
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 856bc21fdee8945ddcd97e3978f46af0008af616
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279271"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Zápis testů částí pro knihovny DLL jazyka C++ v sadě Visual Studio

Existuje několik způsobů, jak otestovat kód DLL, v závislosti na tom, zda exportuje funkce, které chcete testovat. Zvolte jeden z následujících způsobů:

**Testy částí volají pouze funkce, které jsou exportovány z dll:** Přidejte samostatný testovací projekt, jak je popsáno v [testech jednotek Zápis u C/C++](writing-unit-tests-for-c-cpp.md). V testovacím projektu přidejte odkaz na projekt DLL.

Přejděte na postup [Chcete-li odkazovat na exportované funkce z projektu DLL](#projectRef).

**DLL je vytvořena jako soubor EXE:** Přidejte samostatný testovací projekt. Propojte jej se souborem výstupního objektu.

Přejděte na [postup: Chcete-li testy propojit se soubory objektu nebo knihovny](#objectRef).

**Jednotkové testy volají nečlenské funkce, které nejsou exportovány z knihovny DLL, a knihovnu DLL lze sestavit jako statickou knihovnu:** Změňte projekt DLL tak, aby byl zkompilován do souboru *LIB.* Přidejte samostatný testovací projekt, který odkazuje na testovaného projektu.

Tento přístup má tu výhodu, že umožňuje testy používat neexportované členy, ale stále zachovat testy v samostatném projektu.

Přejděte na postup [Chcete-li změnit knihovnu DLL na statickou knihovnu](#staticLink).

**Testy jednotek musí volat nečlenské funkce, které nejsou exportovány, a kód musí být vytvořen jako knihovna dynamických propojení (DLL):** Přidejte testy částí ve stejném projektu jako kód produktu.

Přejděte k postupu [Chcete-li přidat testy částí ve stejném projektu](#sameProject).

## <a name="create-the-tests"></a>Vytvoření testů

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a>Změna knihovny DLL na statickou knihovnu

- Pokud testy musí používat členy, které nejsou exportovány projektem Knihovny DLL a testovaný projekt je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.

  1. V **Průzkumníku řešení**v místní nabídce testovného projektu zvolte **Vlastnosti**. Otevře se okno **Vlastnosti** projektu.

  2. Zvolte**Obecné** **vlastnosti** > konfigurace .

  3. Nastavte **typ konfigurace** na **statickou knihovnu (.lib).**

  Pokračujte postupem [Propojení testů se soubory objektu nebo knihovny](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a>Chcete-li odkazovat na exportované funkce DLL z testovacího projektu

- Pokud projekt DLL exportuje funkce, které chcete testovat, můžete přidat odkaz na projekt kódu z testovacího projektu.

  1. Vytvořte nativní projekt testování částí.

      ::: moniker range="vs-2019"

      1. V nabídce **Soubor** zvolte **Nový** > **projekt**. V **dialogovém** okně Přidat nový projekt nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **nativní projekt testování částí**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **Soubor** zvolte **Nový** > **projekt Visual** > **C++** > **Test** > **C++ Projekt testování částí .**

      ::: moniker-end

  1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na testovací projekt a pak zvolte **Přidat** > **odkaz**.

  1. Vyberte **projekty**a potom projekt, který má být testován.

       Vyberte tlačítko **Přidat**.

  1. Ve vlastnostech testovacího projektu přidejte umístění testovného projektu do možnosti Zahrnout adresáře.

       Zvolte **Vlastnosti** > konfigurace > **Adresáře VC++****Včetně adresářů**.

       Zvolte **Upravit**a přidejte adresář záhlaví testovce projektu.

  Přejděte na [na pište testy částí](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a>Propojení testů se soubory objektu nebo knihovny

- Pokud dll neexportuje funkce, které chcete testovat, můžete přidat výstupní *soubor OBJ* nebo *LIB* do závislostí testovacího projektu.

  1. Vytvořte nativní projekt testování částí.

      ::: moniker range="vs-2019"

      1. V nabídce **Soubor** zvolte **Nový** > **projekt**. V **dialogovém** okně Přidat nový projekt nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **nativní projekt testování částí**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **Soubor** zvolte **Nový** > **projekt Visual** > **C++** > **Test** > **C++ Projekt testování částí .**

      ::: moniker-end

  2. V **Průzkumníku řešení**v místní nabídce testovacího projektu zvolte **Vlastnosti**.

  3. Zvolte Další závislosti**vstupu** > **linkeru** > **vlastností** **Configuration Properties** > konfigurace .

       Zvolte **Upravit**a přidejte názvy souborů **OBJ** nebo **LIB.** Nepoužívejte úplné názvy cest.

  4. Zvolte **Položky** > **propojení** > vlastností**Obecné** > **další adresáře knihovny**.

       Zvolte **Upravit**a přidejte cestu k adresáři souborů **OBJ** nebo **LIB.** Cesta je obvykle ve složce sestavení testovného projektu.

  5. Zvolte **Vlastnosti** > konfigurace > **Adresáře VC++****Včetně adresářů**.

       Zvolte **Upravit**a přidejte adresář záhlaví testovce projektu.

  Přejděte na [na pište testy částí](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a>Přidání testů částí ve stejném projektu

1. Upravte vlastnosti projektu kódu produktu tak, aby zahrnovaly záhlaví a soubory knihovny, které jsou požadovány pro testování částí.

   1. V **Průzkumníku řešení**v místní nabídce testovného projektu zvolte **Vlastnosti**. Otevře se okno **Vlastnosti** projektu.

   2. Zvolte **vlastnosti** > konfigurace**VC++ Adresáře**.

   3. Upravte adresáře zahrnout a knihovnu:

       |Adresář|Vlastnost|
       |-|-|
       |**Zahrnout adresáře** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
       |**Adresáře knihoven** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2. Přidejte testovací soubor jednotky C++:

   - V **Průzkumníku řešení**zvolte v místní nabídce projektu **přidat** > **novou položku** > **C++ jednotkový test**.

   Přejděte na [na pište testy částí](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a>Napište testy částí

1. V každém souboru kódu `#include` testování částí přidejte příkaz pro záhlaví testovaného projektu.

2. Přidejte testovací třídy a metody do souborů kódu testování částí. Například:

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

1. V nabídce **Test** zvolte**Průzkumník testů systému** **Windows** > .

1. Pokud všechny testy nejsou viditelné v okně, vytvořte testovací projekt klepnutím pravým tlačítkem myši na jeho uzel v **Průzkumníku řešení** a výběrem **sestavení** nebo **znovu sestavit**.

1. V **Průzkumníkovi testů**zvolte **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klepněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění s povolenými zarážkymi.

## <a name="see-also"></a>Viz také

- [Zapsat testy částí pro C/C++](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework odkaz na rozhraní API](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití knihovny dynamických odkazů (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
- [Úvodní příručka: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
