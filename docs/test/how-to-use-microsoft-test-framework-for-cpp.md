---
title: Použití architektury Microsoft pro testování jednotek pro jazyk C++
description: Pomocí rozhraní Microsoft Unit Testing Framework pro C++ vytvořte testy částí pro váš kód C++.
ms.date: 01/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 5c8cb794ce7891e74610f1a73164ce403d294925
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75755564"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Použití rozhraní Microsoft Unit Testing Framework pro jazyk C++ v sadě Visual Studio

Microsoft Unit Testing Framework pro C++ je součástí standardně ve vývoji plochy s úlohou **C++.**

## <a name="to-write-unit-tests-in-a-separate-project"></a><a name="separate_project"></a>Zápis testů částí v samostatném projektu

Obvykle spustíte testovací kód ve vlastním projektu ve stejném řešení jako kód, který chcete testovat. Chcete-li nastavit a nakonfigurovat nový testovací projekt, naleznete [v tématu Zápis testů částí pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-write-unit-tests-in-the-same-project"></a><a name="same_project"></a>Zápis testů částí ve stejném projektu

V některých případech, například při testování neexportovaných funkcí v knihovně DLL, může být nutné vytvořit testy ve stejném projektu jako testovaný program. Chcete-li psát testy částí ve stejném projektu:

1. Upravte vlastnosti projektu tak, aby zahrnovaly záhlaví a soubory knihovny, které jsou požadovány pro testování částí.

   1. V Průzkumníku řešení v místní nabídce projektu, který testujete, zvolte **Vlastnosti**. Otevře se okno vlastností projektu.

   1. V dialogovém okně Stránky vlastností vyberte **Vlastnosti** > konfigurace**Adresáře VC++**.

   1. Klikněte na šipku dolů v ** \< **následujících řádcích a zvolte Upravit>. Přidejte tyto cesty:

      | Adresář | Vlastnost |
      |-| - |
      | **Zahrnout adresáře** | **$(VCInstallDir)Pomocné\VS\UnitTest\include** |
      | **Adresáře knihoven** | **$(VCInstallDir)Pomocné\VS\UnitTest\lib** |

1. Přidejte testovací soubor jednotky C++:

   - Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a zvolte **Přidat** > nový soubor**c++** > **(.cpp)**.

## <a name="to-link-the-tests-to-the-object-or-library-files"></a><a name="object_files"></a>Propojení testů se soubory objektu nebo knihovny

Pokud testovaný kód neexportuje funkce, které chcete testovat, můžete přidat výstupní **soubor OBJ** nebo **.lib** do závislostí testovacího projektu. Upravte vlastnosti testovacího projektu tak, aby zahrnovaly záhlaví a soubory knihovny nebo objektů, které jsou požadovány pro testování částí.

1. V Průzkumníku řešení v místní nabídce testovacího projektu zvolte **Vlastnosti**. Otevře se okno vlastností projektu.

1. Vyberte vstupní stránku > **Položky** **linkeru** **vlastností** > konfigurace a pak vyberte **Další závislosti**.

   Zvolte **Upravit**a přidejte názvy souborů **OBJ** nebo **LIB.** Nepoužívejte úplné názvy cest.

1. Vyberte stránku Configuration **Properties** > **Linker** > **General** a pak vyberte **Další adresáře knihovny**.

   Zvolte **Upravit**a přidejte cestu k adresáři souborů **OBJ** nebo **LIB.** Cesta je obvykle ve složce sestavení testovného projektu.

1. Vyberte stránku **Vlastnosti** > konfigurace**VC++ Adresáře** a pak vyberte **Zahrnout adresáře**.

   Zvolte **Upravit**a přidejte adresář záhlaví testovce projektu.

## <a name="write-the-tests"></a>Napište testy

Jakýkoli soubor *CPP* s testovacími třídami musí obsahovat "CppUnitTest.h" a musí mít příkaz using pro `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Testovací projekt je již nakonfigurován pro vás. Obsahuje také definici oboru názvů a TEST_CLASS s TEST_METHOD, který vám pomůže začít. Název oboru názvů a názvy v závorcích v makrech třídy a metody můžete změnit.

Testovací rámec definuje speciální makra pro inicializaci testovacích modulů, tříd a metod a pro vyčištění prostředků po dokončení testů. Tato makra generují kód, který se má spustit před prvním přístupem třídy nebo metody a po spuštění posledního testu. Další informace naleznete v [tématu Inicializovat a vyčistit](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Použijte statické metody ve třídě [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) k definování testovacích podmínek. Pomocí třídy [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) zapisovat zprávy do **okna výstup .** Přidání atributů do testovacích metod

## <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **Test** zvolte**Průzkumník testů systému** **Windows** > .

1. Pokud nejsou všechny testy viditelné v okně, vytvořte testovací projekt kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumníku řešení** a zvolte **Sestavit** nebo **znovu sestavit**.

1. V **Průzkumníkovi testů**zvolte **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klepněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění s povolenými zarážkymi.

1. V **okně Výstup** zvolte **testy** v rozevíracím seznamku pro zobrazení zpráv zapsaných třídou: `Logger`

   ![Výstupní okno C++ zobrazující testovací zprávy](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Definování vlastností umožňujících seskupování

Můžete definovat vlastnosti testovacích metod, které umožňují kategorizovat a seskupit testy v **Průzkumníku testů**. Chcete-li definovat vlastnost, `TEST_METHOD_ATTRIBUTE` použijte makro. Chcete-li například definovat `TEST_MY_TRAIT`vlastnost s názvem :

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

Použití definovanévlastnosti v testování částí:

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

### <a name="c-trait-attribute-macros"></a>Makra atributu vlastností jazyka C++

Následující předdefinované znaky se nacházejí `CppUnitTest.h`v . Další informace naleznete [v tématu Microsoft Unit Testing Framework for C++ API reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makro|Popis|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Pomocí TEST_METHOD_ATTRIBUTE makra definujte vlastnost.|
|`TEST_OWNER(ownerAlias)`|Pomocí předdefinované vlastnosti vlastníka určete vlastníka testovací metody.|
|`TEST_PRIORITY(priority)`|Pomocí předdefinovaného znaku Priorita přiřaďte testovacím metodám relativní priority.|

## <a name="see-also"></a>Viz také

- [Úvodní příručka: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)
