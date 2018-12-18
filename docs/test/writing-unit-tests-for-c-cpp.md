---
title: Zápis testů jednotek pro C/C++
ms.date: 10/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: e19eb3bb421a69c902d9a10f0cdb3c5ac2244a04
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053741"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů jednotek pro C/C++ v sadě Visual Studio

Můžete napsat a spouštět testy jednotek C++ s použitím **Průzkumník testů** okno, stejně jako u ostatních jazyků. Další informace o používání **Průzkumník testů**, naleznete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Některé funkce, jako je Live Unit Testing, programových testů uživatelského rozhraní a IntelliTest nejsou podporovány pro jazyk C++.

Visual Studio obsahuje tyto testovací rozhraní C++ se žádné další soubory ke stažení vyžaduje:

- Microsoft Unit Testing Framework pro C++
- Google Test
- Boost.Test
- CTest

Kromě rozhraní nainstalované můžete napsat vlastní testovací adaptér pro libovolné framework, které chcete použít v sadě Visual Studio. Testovací adaptér můžete integrovat testů jednotek s **Průzkumníka testů** okna. Několik adaptérů třetích stran jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com). Další informace najdete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 verze 15.7 (Professional a Enterprise)**

Projekty testování částí C++ podporu [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 verze 15.5**

- **Google Test Adapter** je zahrnutý jako součást výchozí **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Obsahuje šablony projektů, můžete přidat do řešení prostřednictvím **přidat nový projekt** místní nabídky uzlu řešení v **Průzkumníka řešení**a možnosti, které můžete nakonfigurovat přes **nástroje**  >  **Možnosti**. Další informace najdete v tématu [postupy: použití Google testu v sadě Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** je zahrnutý jako součást výchozí **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Je integrován s **Průzkumník testů** aktuálně nepodporuje, ale není nutné šablonu projektu, proto musí být ručně nakonfigurovat. Další informace najdete v tématu [postupy: použití testu Boost.Test v sadě Visual Studio](how-to-use-boost-test-for-cpp.md).

- **CTest** podpora je součástí [nástroje CMake pro Visual Studio](/cpp/ide/cmake-tools-for-visual-cpp) komponenta, která je součástí sady **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Nicméně CTest není dosud plně integrovaná **Průzkumník testů**. Další informace najdete v tématu [postupy: použití testu CTest v sadě Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Si můžete stáhnout adaptér pro Google Test a Boost.Test adaptér rozšíření na Visual Studio Marketplace na [testovací adaptér pro Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a [testovací adaptér pro Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Základní test pracovního postupu

V následujících částech se dozvíte základní kroky, které vám pomůžou začít s testováním částí C++. Základní konfigurace je velmi podobný pro rozhraní Microsoft a Google Test. Boost.Test vyžaduje ručně vytvořte projekt testu.

### <a name="create-a-test-project"></a>Vytvoření testovacího projektu

Definovat a spouštět testy v jedné nebo více projekty testů, které jsou ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový testovací projekt do existujícího řešení, klikněte pravým tlačítkem na uzel řešení v **Průzkumníka řešení** a zvolte **přidat** > **nový projekt**. V levém podokně zvolte **Visual C++ Test** a zvolte jeden z typů projektu v prostředním podokně. Následující obrázek znázorňuje projekty testů, které jsou k dispozici, při **Desktop Development with C++** je nainstalovaná úloha:

![Projekty testů C++](media/cpp-new-test-project.png)

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytvořit odkazy na jiné projekty v řešení

Pokud chcete povolit váš testovací kód pro přístup k funkcím v projektu, který má být testována, přidejte odkaz na projekt v projektu testu. Klikněte pravým tlačítkem na uzel projektu testu v **Průzkumníka řešení** a zvolte **přidat** > **odkaz**. V dialogovém okně vyberte projekty, které chcete testovat.

![Přidat odkaz](media/cpp-add-ref-test-project.png)

### <a name="add-include-directives-for-header-files"></a>Přidejte #include pro soubory hlaviček

Vedle testování částí *.cpp* přidejte `#include` směrnice pro všechny soubory hlaviček, které deklarují typy a funkce, které chcete testovat. Typ `#include "` a potom se budou aktivovat IntelliSense vám pomůže vybrat. Opakujte pro další záhlaví.

![Přidání direktiv](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Zápis testovacích metod

> [!NOTE]
> Tato část popisuje syntaxe pro rozhraní testování částí Microsoft pro C/C++. Jsou zde uvedeny: [reference k rozhraní API atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Dokumentace ke službě Google Test, naleznete v tématu [Úvod do Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Boost.Test, naleznete v tématu [knihovny Boost Test: testy jednotek](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

*.Cpp* soubor v projektu testu obsahuje zástupné třídy a metody definovány jako příklad toho, jak napsat test kódu. Mějte na paměti, že podpisy používat TEST_CLASS a TEST_METHOD makra, která zjistitelnost z metody **Průzkumník testů** okna.

![Přidání direktiv](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí [nativní testovací rozhraní Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** zjistí testovacích metod v jiné podporované architektury podobným způsobem.

TEST_METHOD vrací hodnotu void. K vytvoření výsledku testu, použijte statické metody v `Assert` se třídou k testování skutečné výsledky oproti očekávání. V následujícím příkladu předpokládejme `MyClass` má konstruktor, který přijímá `std::string`. Abychom mohli otestovat, že konstruktor inicializuje třídu podle očekávání takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu, výsledek `Assert::AreEqual` volání Určuje, zda testovací projde nebo selže. Třída kontrolní výraz obsahuje mnoho metod pro porovnávání, byl očekáván vs. skutečné výsledky.

Můžete přidat *osobnostní rysy* s testovacími metodami určit vlastníky testu, priority a další informace. Tyto hodnoty pak můžete použít k řazení a seskupení testů v **Průzkumník testů**. Další informace najdete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Spustit testy

1. Na **testovací** nabídce zvolte **Windows** > **Průzkumník testů**. Následující ilustrace znázorňuje testovací projekt, jejichž testy dosud nebyly spuštěny.

   ![Průzkumník testů, před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integraci CTest s **Průzkumník testů** ještě není k dispozici. Testy CTest z hlavní nabídky CMake.

1. Pokud všechny testy nejsou zobrazeny v okně, vytvoření testovacího projektu kliknutím pravým tlačítkem myši v jeho uzel **Průzkumníka řešení** a zvolíte **sestavení** nebo **znovu sestavit**.

1. V **Průzkumník testů**, zvolte **spustit všechny**, nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění se zarážkami povolené. V okně se zobrazí po spuštění všech testů, které testy předaný a ty, které se nezdařilo:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

Zpráva pro neúspěšné testy, nabízí podrobnosti, které pomůžou určování příčin problémů. Můžete kliknout pravým tlačítkem na neúspěšného testu a zvolit **ladit vybrané testy** krokovat funkce, kde došlo k chybě.

Další informace o používání **Průzkumník testů**, naleznete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

Osvědčené postupy související s testování částí, naleznete v tématu [základní informace o testování částí](unit-test-basics.md)

## <a name="use-codelens"></a>Použití CodeLens

**Visual Studio 2017 verze 15.7 pouze edice Enterprise a Professional**: [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav jednotky testování bez opuštění editoru kódu. Inicializovat CodeLens pro projekt testování částí C++ v některém z těchto způsobů:

- Upravit a vytvořit testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Spustit testy z **Průzkumníka testů** okna.

Po **CodeLens** je inicializována, zobrazí se test ikony stavu nad každý Jednotkový test.

![Ikony C++ CodeLens](media/cpp-test-codelens-icons.png)

 Klikněte na ikonu pro další informace nebo chcete spustit nebo ladit testování částí:

![C++ CodeLens spouštění a ladění](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také:

[Testování částí kódu](unit-test-your-code.md)
