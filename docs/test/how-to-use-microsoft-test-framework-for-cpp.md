---
title: Použití architektury Microsoft pro testování jednotek pro jazyk C++
description: Pro vytvoření testování částí C++ C++ kódu použijte rozhraní Microsoft Unit Testing Framework.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: 789430e18dfe8e5f7db19273e7298af2f078c0dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755564"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Použít Microsoft rozhraní testování části pro C++ v sadě Visual Studio

Ve výchozím nastavení je zahrnuto Microsoft Unit Testing Framework pro C++ **Desktop Development with C++** pracovního vytížení.

## <a name="separate_project"></a> Pro psaní jednotkových testů testovacího projektu

Obvykle spustíte testovací kód ve svém vlastním projektu ve stejném řešení jako kód, který chcete testovat. Chcete-li vytvořit a nakonfigurovat nový testovací projekt, naleznete v tématu [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="same_project"></a> Pro psaní jednotkových testů do stejného projektu

V některých případech, například při testování neexportovaných funkcí v knihovně DLL, může být nutné vytvořit testy ve stejném projektu jako program, který testujete. Pro psaní jednotkových testů do stejného projektu:

1. Upravte vlastnosti projektu, aby zahrnovaly hlavičkové soubory a soubory knihoven, které jsou požadovány pro testování částí.

   1. V Průzkumník řešení v místní nabídce projektu, který testujete, vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

   1. V dialogovém okně stránky vlastností vyberte možnost **Vlastnosti konfigurace** > **adresáře VC + +** .

   1. Klikněte na šipku dolů v následujících řádcích a vyberte **\<upravit >** . Přidejte tyto cesty:

      | Adresář | Vlastnost |
      |-| - |
      | **Adresáře souborů k zahrnutí** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\include** |
      | **Adresáře knihoven** | **$ (VCInstallDir) Auxiliary\VS\UnitTest\lib** |

1. Přidáte soubor testu jednotek C++:

   - V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat** > nový soubor >  **C++ položky (. cpp)** .

## <a name="object_files"></a> Připojení testů k souborům objektů nebo knihoven

Pokud testovaný kód neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubor **. obj** nebo **. lib** do závislostí testovacího projektu. Upravte vlastnosti projektu testu tak, aby zahrnovaly hlavičky a soubory knihoven nebo objektů, které jsou požadovány pro testování částí.

1. V Průzkumník řešení v místní nabídce testovacího projektu vyberte možnost **vlastnosti**. Otevře se okno Vlastnosti projektu.

1. Vyberte **konfigurační** stránku > **linker** > **input** a pak vyberte **Další závislosti**.

   Zvolte **upravit**a přidejte názvy **.obj** nebo **lib** soubory. Nepoužívejte názvy úplných cest.

1. Vyberte **konfigurační vlastnosti** > **linker** > stránce **Obecné** a pak vyberte **Další adresáře knihoven**.

   Zvolte **upravit**a přidejte cestu k adresáři **.obj** nebo **lib** soubory. Cesta je obvykle ve složce sestavení testovaného projektu.

1. Vyberte **Vlastnosti konfigurace** > **adresáře VC + +** a pak vyberte **Zahrnout adresáře**.

   Zvolte **upravit**a poté přidejte hlavní adresář testovaného projektu.

## <a name="write-the-tests"></a>Zápis testů

Žádné *.cpp* soubor s testovacích tříd musí obsahovat "CppUnitTest.h" a obsahovat using příkazu pro `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Projekt testů už je nakonfigurovaný pro vás. Zahrnuje také definice oboru názvů a TEST_CLASS s TEST_METHOD, které vám pomůžou začít. Můžete upravit název oboru názvů a názvy v závorkách v makrech třídy a metody.

Testovací rozhraní definuje speciální makra pro inicializaci testovacích modulů, tříd a metod a pro vyčištění prostředků po dokončení testů. Tato makra generují kód, který se má provést před prvním otevřením třídy nebo metody, a po spuštění posledního testu. Další informace najdete v tématu [inicializace a vyčištění](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Používají statické metody v [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) třídy definovat podmínky testu. Použití [protokolovací nástroj](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) třídu pro zápis zpráv do **okno výstup**. Přidat atributy s testovacími metodami

## <a name="run-the-tests"></a>Spustit testy

1. Na **testovací** nabídce zvolte **Windows** > **Průzkumník testů**.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumník testů**, zvolte **spustit všechny**, nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění se zarážkami povolené.

1. V **okno výstup** v rozevíracím seznamu vyberte možnost **testy** , abyste zobrazili zprávy zapsané `Logger` třídou:

   ![Okno výstup C++ zkušební zprávy](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definovat vlastnosti, které chcete povolit seskupování

Můžete definovat vlastnosti v testovacích metodách, které umožňují kategorizaci a seskupení testů v **Průzkumníku testů**. Chcete-li definovat vlastnost, použijte `TEST_METHOD_ATTRIBUTE` – makro. Například pro definici znaku s názvem `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Použití definované vlastnosti v testech jednotek:

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

### <a name="c-trait-attribute-macros"></a>Atributy a makra C++ vlastností

Následující předdefinované vlastnosti se nacházejí v `CppUnitTest.h`. Další informace najdete v tématu [Microsoft Unit Testing Framework pro reference k rozhraní API C++](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|– Makro|Popis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Chcete-li definovat vlastnost, použijte makro TEST_METHOD_ATTRIBUTE.|
|`TEST_OWNER(ownerAlias)`|Použijte předdefinovanou vlastnost Owner k zadání vlastníka testovací metody.|
|`TEST_PRIORITY(priority)`|Pomocí předdefinované vlastnosti Priority přiřaďte relativní priority testovacím metodám.|

## <a name="see-also"></a>Viz také:

- [Rychlý start: Testovací řízeného rozvoje pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
