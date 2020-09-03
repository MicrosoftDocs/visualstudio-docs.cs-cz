---
title: Použití architektury Microsoft pro testování jednotek pro jazyk C++
description: Pro vytváření testů jednotek pro kód jazyka C++ použijte Microsoft Unit Testing Framework pro C++.
ms.date: 01/08/2020
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a9393fd248f4e6520c261d405bc624a75d8cf69f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287113"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Použití architektury Microsoft Unit Testing Framework pro C++ v aplikaci Visual Studio

Microsoft Unit Testing Framework pro C++ je ve výchozím nastavení součástí **vývoj desktopových aplikací v jazyce c++** .

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a> Zápis testů jednotek do samostatného projektu

Obvykle spouštíte testovací kód ve vlastním projektu ve stejném řešení jako kód, který chcete testovat. Chcete-li nastavit a nakonfigurovat nový projekt testů, přečtěte si téma [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a> Zápis testů jednotek ve stejném projektu

V některých případech, například při testování neexportovaných funkcí v knihovně DLL, může být nutné vytvořit testy ve stejném projektu jako program, který testujete. Zápis testů jednotek do stejného projektu:

1. Upravte vlastnosti projektu tak, aby obsahovaly hlavičky a soubory knihoven, které jsou požadovány pro testování částí.

   1. V Průzkumník řešení v místní nabídce projektu, který testujete, vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

   1. V dialogovém okně stránky vlastností vyberte možnost **Vlastnosti konfigurace**  >  **adresáře VC + +**.

   1. Klikněte na šipku dolů v následujících řádcích a vyberte **\<Edit>** . Přidejte tyto cesty:

      | Adresář | Vlastnost |
      |-| - |
      | **Zahrnout adresáře** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\include** |
      | **Adresáře knihoven** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\lib** |

1. Přidat soubor testu jednotek C++:

   - V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **nový soubor s položkou**  >  **C++ (. cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a> Propojení testů s objekty nebo soubory knihovny

Pokud testovaný kód neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubor **. obj** nebo **. lib** do závislostí testovacího projektu. Upravte vlastnosti projektu testu tak, aby zahrnovaly hlavičky a soubory knihoven nebo objektů, které jsou požadovány pro testování částí.

1. V Průzkumník řešení v místní nabídce testovacího projektu vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

1. Vyberte stránku **Vlastnosti konfigurace**  >  **vstup linkeru**  >  **Input** a potom vyberte **Další závislosti**.

   Vyberte **Upravit**a přidejte názvy souborů **. obj** nebo **. lib** . Nepoužívejte názvy úplných cest.

1. Vyberte stránku **Vlastnosti konfigurace**  >  **Obecné linkeru**  >  **General** a pak vyberte **Další adresáře knihoven**.

   Vyberte **Upravit**a přidejte cestu k adresáři souborů **. obj** nebo **. lib** . Cesta je obvykle ve složce sestavení testovaného projektu.

1. Vyberte stránku **Vlastnosti konfigurace**  >  **adresáře VC + +** a pak vyberte **Zahrnout adresáře**.

   Zvolte **Upravit**a pak přidejte adresář záhlaví testovaného projektu.

## <a name="write-the-tests"></a>Zápis testů

Libovolný soubor *. cpp* s testovacími třídami musí zahrnovat "CppUnitTest. h" a obsahovat příkaz using pro `using namespace Microsoft::VisualStudio::CppUnitTestFramework` . Testovací projekt je už pro vás nakonfigurovaný. Zahrnuje také definici oboru názvů a TEST_CLASS s TEST_METHOD, které vám pomohou začít. Můžete upravit název oboru názvů a názvy v závorkách v makrech třídy a metody.

Testovací rozhraní definuje speciální makra pro inicializaci testovacích modulů, tříd a metod a pro vyčištění prostředků po dokončení testů. Tato makra generují kód, který se má provést před prvním otevřením třídy nebo metody, a po spuštění posledního testu. Další informace naleznete v tématu [inicializace a vyčištění](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Použijte statické metody ve třídě [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) k definování testovacích podmínek. K zápisu zpráv do **okno výstup**použijte třídu [protokolovacího](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) nástroje. Přidání atributů do testovacích metod

## <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **test** vyberte **Windows**  >  **Test Explorer**.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumníku testů**zvolte možnost **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem na test pro další možnosti, včetně spuštění v režimu ladění se zapnutými zarážkami.

1. V **okno výstup** v rozevíracím seznamu vyberte **testy** , abyste zobrazili zprávy zapsané `Logger` třídou:

   ![C++ okno Výstup zobrazení zkušebních zpráv](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definovat vlastnosti pro povolení seskupení

Můžete definovat vlastnosti v testovacích metodách, které umožňují kategorizaci a seskupení testů v **Průzkumníku testů**. Pro definování vlastností použijte `TEST_METHOD_ATTRIBUTE` makro. Například pro definování vlastnosti s názvem `TEST_MY_TRAIT` :

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Použití definovaného vlastností při testování částí:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Makra atributů vlastností C++

Následující předem definované vlastnosti se nacházejí v `CppUnitTest.h` . Další informace najdete v [referenčních informacích k rozhraní Microsoft Unit Testing Framework pro C++ API](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Podokně|Popis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Pro definování vlastností použijte makro TEST_METHOD_ATTRIBUTE.|
|`TEST_OWNER(ownerAlias)`|Použijte předdefinovaný vlastnický vlastník a určete vlastníka testovací metody.|
|`TEST_PRIORITY(priority)`|Pomocí předdefinované vlastnosti priority můžete přiřadit relativní priority k testovacím metodám.|

## <a name="see-also"></a>Viz také

- [Rychlý Start: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
