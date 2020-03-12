---
title: Zápis testů jednotek pro C/C++
description: Zapište C++ testy jednotek v aplikaci Visual Studio pomocí různých testovacích rozhraní, včetně CTest, zvyšování a Google test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 354ccad121884c99541057a2e0e0a47d9d2a4341
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937557"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů jednotek pro C/C++ v sadě Visual Studio

Můžete napsat a spustit testy C++ jednotek pomocí okna **Průzkumník testů** . Funguje stejně jako pro jiné jazyky. Další informace o použití **Průzkumníka testů**naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Některé funkce, jako je Live Unit Testing, programových testů uživatelského rozhraní a IntelliTest nejsou podporovány pro jazyk C++.

Visual Studio obsahuje tyto testovací rozhraní C++ se žádné další soubory ke stažení vyžaduje:

- Microsoft Unit Testing Framework pro C++
- Google Test
- Boost.Test
- CTest

Společně s použitím nainstalovaných rozhraní můžete napsat vlastní testovací adaptér pro libovolné rozhraní, které chcete použít v sadě Visual Studio. Testovací adaptér může integrovat testy jednotek pomocí okna **Průzkumníka testů** . V [Visual Studio Marketplace](https://marketplace.visualstudio.com)je k dispozici několik adaptérů třetích stran. Další informace najdete v tématu [instalace rozhraní pro testování částí třetích stran](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 a novější (Professional a Enterprise)**

C++projekty testů jednotek podporují [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 a novější (všechny edice)**

- **Google test adaptér** je součástí jako výchozí součást **vývoje C++ desktopových** aplikací. Má šablonu projektu, kterou můžete přidat do řešení. Pomocí nabídky **Přidat nový projekt** v uzlu řešení v **Průzkumník řešení** ho přidejte. Máte také možnosti, které můžete konfigurovat prostřednictvím **nástrojů** > **možností**. Další informace naleznete v tématu [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- Jako výchozí součást **vývoje pro stolní počítače s C++**  úlohou je k dispozici funkce **zvýšení. test.** Je integrována s **průzkumníkem testů**, ale aktuálně nemá šablonu projektu. Je nutné ho nakonfigurovat ručně. Další informace naleznete v tématu [How to: use. test v aplikaci Visual Studio](how-to-use-boost-test-for-cpp.md).

- Součástí  **C++ nástrojů cmake** je podpora **CTest** , která je součástí  **C++ vývoje plochy s** úlohou. Další informace naleznete v tématu [How to: use CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Můžete si stáhnout Google Test adaptér a zvýšit rozšíření testovacího adaptéru na Visual Studio Marketplace. Najdete je na [testovacím adaptéru pro zvýšení](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a [testovací adaptér pro Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Základní test pracovního postupu

V následujících částech se dozvíte základní kroky, které vám pomůžou začít s testováním částí C++. Základní konfigurace je podobná jak pro rozhraní Microsoft, tak pro Google Test. Boost.Test vyžaduje ručně vytvořte projekt testu.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2019

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů do existujícího řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení**. V místní nabídce vyberte **přidat** > **Nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Následující ilustrace znázorňuje projekty testů, které jsou k dispozici v případě, že je nainstalován **vývoj C++ desktopových** aplikací a úloha **vývoje UWP** :

![C++Projekty testů v aplikaci VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2017

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte **Přidat** > **Nový projekt**. V levém podokně vyberte **vizuální C++ test**. Pak v prostředním podokně vyberte jeden z typů projektu. Následující ilustrace znázorňuje projekty testů, které jsou k dispozici v případě, že je nainstalován **desktopový vývoj s C++**  úlohou:

![Projekty testů C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytvořit odkazy na jiné projekty v řešení

Chcete-li povolit přístup k funkcím v testovaném projektu, přidejte do projektu testů odkaz na projekt. Klikněte pravým tlačítkem myši na uzel testovací projekt v **Průzkumník řešení** pro místní nabídku. Vyberte možnost **přidat** > **odkaz**. V dialogovém okně Přidat odkaz vyberte projekt (y), který chcete otestovat.

![Přidat odkaz](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Odkaz na soubory objektů nebo knihoven

Pokud kód testu neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubory. obj nebo. lib do závislostí testovacího projektu. Další informace najdete v tématu [propojení testů s objekty nebo soubory knihovny](/visualstudio/test/how-to-use-microsoft-test-framework-for-cpp#object_files).

### <a name="add-include-directives-for-header-files"></a>Přidejte #include pro soubory hlaviček

Dále v souboru *. cpp* testu jednotky přidejte direktivu `#include` pro všechny hlavičkové soubory, které deklaruje typy a funkce, které chcete testovat. Zadejte `#include "` a potom se aktivuje IntelliSense, který vám pomůže vybrat. Opakujte pro další záhlaví.

![Přidání direktiv](media/cpp-add-includes-test-project.png)

Chcete-li se vyhnout nutnosti zadávat úplnou cestu do každého příkazu include ve zdrojovém souboru, můžete přidat požadované složky v **projektu** > **vlastnosti** > **C/C++**  > **Obecné** > **Další adresáře include**.

### <a name="write-test-methods"></a>Zápis testovacích metod

> [!NOTE]
> Tato část popisuje syntaxe pro rozhraní testování částí Microsoft pro C/C++. Je zde popsána zde: [Reference k rozhraní API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Dokumentaci k Google Test najdete v části [Google test Úvod](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Pro zvýšení. test naleznete v tématu [knihovna Boost test: rozhraní pro testování částí](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Soubor *. cpp* v testovacím projektu má zástupnou třídu a metodu definovanou pro vás. Ukazují příklad, jak napsat testovací kód. Signatury používají makra TEST_CLASS a TEST_METHOD, která umožňují zjistit metody z okna **Průzkumníka testů** .

![Přidání direktiv](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí [nativního testovacího rozhraní společnosti Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** zjišťuje testovací metody v jiných podporovaných rozhraních podobným způsobem.

TEST_METHOD vrací hodnotu void. Chcete-li vytvořit výsledek testu, použijte statické metody ve třídě `Assert` k otestování skutečných výsledků oproti očekávání. V následujícím příkladu Předpokládejme, že `MyClass` má konstruktor, který přebírá `std::string`. Abychom mohli otestovat, že konstruktor inicializuje třídu podle očekávání takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu výsledek volání `Assert::AreEqual` určuje, zda test projde nebo se nezdařil. Třída kontrolní výraz obsahuje mnoho metod pro porovnávání, byl očekáván vs. skutečné výsledky.

Můžete přidat *vlastnosti* do testovacích metod a zadat vlastníky testů, prioritu a další informace. Tyto hodnoty pak můžete použít k řazení a seskupení testů v **Průzkumníku testů**. Další informace naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Spustit testy

1. V nabídce **test** vyberte možnost **Windows** > **Průzkumník testů**. Následující ilustrace znázorňuje testovací projekt, jejichž testy dosud nebyly spuštěny.

   ![Průzkumník testů před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integrace CTest s **průzkumníkem testů** zatím není k dispozici. Testy CTest z hlavní nabídky CMake.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumníku testů**zvolte možnost **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění se zarážkami povolené. V okně se zobrazí po spuštění všech testů, které testy předaný a ty, které se nezdařilo:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

Zpráva pro neúspěšné testy, nabízí podrobnosti, které pomůžou určování příčin problémů. Klikněte pravým tlačítkem myši na test selhání pro místní nabídku. Vyberte možnost **ladit vybrané testy** pro krokování funkce, ve které došlo k chybě.

Další informace o použití **Průzkumníka testů**naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

Další informace související s testováním částí najdete v tématu [základy testování částí](unit-test-basics.md) .

## <a name="use-codelens"></a>Použití CodeLens

**Visual Studio 2017 nebo novější (edice Professional a Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav testu jednotek bez nutnosti opustit Editor kódu.

Inicializovat CodeLens pro projekt testování částí C++ v některém z těchto způsobů:

- Upravit a vytvořit testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Spusťte testy z okna **Průzkumník testů** .

Po inicializaci můžete zobrazit ikony stavu testu nad každým testem jednotky.

![Ikony C++ CodeLens](media/cpp-test-codelens-icons.png)

Klikněte na ikonu pro další informace nebo chcete spustit nebo ladit testování částí:

![C++ CodeLens spouštění a ladění](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](unit-test-your-code.md)
