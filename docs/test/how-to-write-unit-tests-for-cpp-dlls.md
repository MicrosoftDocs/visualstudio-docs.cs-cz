---
title: Zápis testů jednotek pro knihovny DLL C++
description: Přečtěte si o několika způsobech testování kódu knihovny DLL v závislosti na tom, zda knihovna DLL exportuje funkce, které chcete testovat.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: b7eb7b7be524e20ca87c70c3f1f771f4f8a01141
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328623"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Zápis testů jednotek pro knihovny DLL C++ v aplikaci Visual Studio

Existuje několik způsobů, jak otestovat kód knihovny DLL v závislosti na tom, zda exportuje funkce, které chcete testovat. Vyberte jeden z následujících způsobů:

**Testování částí volají pouze funkce, které jsou exportovány z knihovny DLL:** Přidejte samostatný testovací projekt, jak je popsáno v tématu [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md). V testovacím projektu přidejte odkaz na projekt knihovny DLL.

Přejít na postup [pro odkazování na exportované funkce z projektu knihovny DLL](#projectRef).

**Knihovna DLL je sestavena jako soubor. exe:** Přidejte samostatný testovací projekt. Propojte ji s výstupním objektovým souborem.

Pro [propojení testů s objektem nebo knihovnou souborů](#objectRef)použijte postup.

**Testování částí volají nečlenské funkce, které nejsou exportovány z knihovny DLL, a knihovnu DLL lze sestavit jako statickou knihovnu:** Změňte projekt knihovny DLL tak, aby byl zkompilován do souboru *. lib* . Přidejte samostatný testovací projekt, který odkazuje na testovaný projekt.

Tento přístup má výhodu, že umožňuje vašim testům používat neexportované členy, ale zachovají testy v samostatném projektu.

Přejděte na postup [pro změnu knihovny DLL na statickou knihovnu](#staticLink).

**Testy jednotek musí volat nečlenské funkce, které nejsou exportovány, a kód musí být sestaven jako dynamická knihovna (DLL):** Přidejte jednotkové testy do stejného projektu jako kód produktu.

Pro [Přidání jednotkových testů do stejného projektu](#sameProject)použijte postup.

## <a name="create-the-tests"></a>Vytvoření testů

### <a name="to-change-the-dll-to-a-static-library"></a><a name="staticLink"></a> Postup změny knihovny DLL na statickou knihovnu

- Pokud vaše testy musí používat členy, které nejsou exportovány knihovnou DLL, a testovaný projekt je sestaven jako dynamická knihovna, zvažte jeho převod na statickou knihovnu.

  1. V **Průzkumník řešení** v místní nabídce testovaného projektu vyberte možnost **vlastnosti**. Otevře se okno **vlastnosti** projektu.

  2. Vyberte **Vlastnosti konfigurace**  >  **Obecné**.

  3. Nastavte **typ konfigurace** na **statickou knihovnu (. lib)**.

  Pokračujte postupem [propojení testů s objekty nebo soubory knihovny](#objectRef).

### <a name="to-reference-exported-dll-functions-from-the-test-project"></a><a name="projectRef"></a> Odkazování na exportované funkce knihovny DLL z testovacího projektu

- Pokud projekt knihovny DLL exportuje funkce, které chcete otestovat, můžete přidat odkaz na projekt kódu z testovacího projektu.

  1. Vytvořte projekt nativního testu jednotek.

      ::: moniker range="vs-2019"

      1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. V dialogovém okně **Přidat nový projekt** nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **projekt nativního testu jednotek**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **soubor** klikněte na příkaz **Nový** > **projekt** > **Visual C++** > **test** > **projektu testování jednotek C++**.

      ::: moniker-end

  1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt testu a pak zvolte **Přidat**  >  **odkaz**.

  1. Vyberte **projekty** a potom projekt, který chcete otestovat.

       Vyberte tlačítko **Přidat**.

  1. Ve vlastnostech testovacího projektu přidejte do adresáře include umístění testovaného projektu.

       Vyberte možnost **Vlastnosti konfigurace**  >  **adresáře VC + +**  >  **adresáře včetně adresářů**.

       Zvolte **Upravit** a pak přidejte adresář záhlaví testovaného projektu.

  Přejít na [zápis testů jednotek](#addTests).

### <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="objectRef"></a> Propojení testů s objekty nebo soubory knihovny

- Pokud knihovna DLL neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubor *. obj* nebo *. lib* do závislostí testovacího projektu.

  1. Vytvořte projekt nativního testu jednotek.

      ::: moniker range="vs-2019"

      1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. V dialogovém okně **Přidat nový projekt** nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Pak zvolte **projekt nativního testu jednotek**.

      ::: moniker-end

      ::: moniker range="vs-2017"

      1. V nabídce **soubor** klikněte na příkaz **Nový** > **projekt** > **Visual C++** > **test** > **projektu testování jednotek C++**.

      ::: moniker-end

  2. V **Průzkumník řešení** v místní nabídce testovacího projektu vyberte možnost **vlastnosti**.

  3. Vyberte **Vlastnosti konfigurace**  >  **linker**  >  **vstup**  >  **Další závislosti**.

       Vyberte **Upravit** a přidejte názvy souborů **. obj** nebo **. lib** . Nepoužívejte názvy úplných cest.

  4. Vyberte **Vlastnosti konfigurace**  >  **linker**  >  **Obecné**  >  **Další adresáře knihoven**.

       Vyberte **Upravit** a přidejte cestu k adresáři souborů **. obj** nebo **. lib** . Cesta je obvykle ve složce sestavení testovaného projektu.

  5. Vyberte možnost **Vlastnosti konfigurace**  >  **adresáře VC + +**  >  **adresáře včetně adresářů**.

       Zvolte **Upravit** a pak přidejte adresář záhlaví testovaného projektu.

  Přejít na [zápis testů jednotek](#addTests).

### <a name="to-add-unit-tests-in-the-same-project"></a><a name="sameProject"></a> Přidání jednotkových testů do stejného projektu

1. Upravte vlastnosti projektu kódu produktu tak, aby obsahovaly hlavičky a soubory knihoven, které jsou požadovány pro testování částí.

   1. V **Průzkumník řešení** v místní nabídce testovaného projektu vyberte možnost **vlastnosti**. Otevře se okno **vlastnosti** projektu.

   2. Vyberte **Možnosti konfigurace**  >  **adresáře VC + +**.

   3. Upravte adresáře include a knihovny:

       |Adresář|Vlastnost|
       |-|-|
       |**Zahrnout adresáře** | **$ (VCInstallDir) UnitTest\include; $ (IncludePath)**|
       |**Adresáře knihoven** | **$ (VCInstallDir) UnitTest\lib; $ (LibraryPath)**|

2. Přidat soubor testu jednotek C++:

   - V **Průzkumník řešení** v místní nabídce projektu vyberte možnost **Přidat**  >  **novou položku**  >  **C++ test jednotek**.

   Přejít na [zápis testů jednotek](#addTests).

## <a name="write-the-unit-tests"></a><a name="addTests"></a> Zápis testů jednotek

1. V každém souboru kódu testu jednotek přidejte `#include` příkaz pro záhlaví testovaného projektu.

2. Přidejte testovací třídy a metody do souborů kódu testování částí. Příklad:

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

1. V nabídce **test** vyberte **Windows**  >  **Test Explorer**.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumníku testů** zvolte možnost **Spustit vše** nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem na test pro další možnosti, včetně spuštění v režimu ladění se zapnutými zarážkami.

## <a name="see-also"></a>Viz také

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
- [Reference k rozhraní API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití dynamické knihovny DLL (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
- [Rychlý Start: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
