---
title: Zápis testů jednotek pro C/C++
description: Zápis jednotkových testů C++ v aplikaci Visual Studio s použitím různých testovacích rozhraní, včetně CTest, zvýšení úrovně testování a Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: d20bcdef769d8cd751230000b0e4d4319b10e46f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217460"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů jednotek pro C/C++ v aplikaci Visual Studio

Můžete napsat a spustit testy jednotek jazyka C++ pomocí okna **Průzkumník testů** . Funguje stejně jako pro jiné jazyky. Další informace o použití **Průzkumníka testů** naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Některé funkce, jako například Live Unit Testing, kódované testy uživatelského rozhraní a IntelliTest, nejsou podporovány pro jazyk C++.

Visual Studio zahrnuje tyto testovací architektury jazyka C++ bez nutnosti dalšího stažení:

- Microsoft Unit Testing Framework pro C++
- Google Test
- Zvýšení. test
- CTest

Společně s použitím nainstalovaných rozhraní můžete napsat vlastní testovací adaptér pro libovolné rozhraní, které chcete použít v sadě Visual Studio. Testovací adaptér může integrovat testy jednotek pomocí okna **Průzkumníka testů** . V [Visual Studio Marketplace](https://marketplace.visualstudio.com)je k dispozici několik adaptérů třetích stran. Další informace najdete v tématu [instalace rozhraní pro testování částí třetích stran](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 a novější (Professional a Enterprise)**

Projekty testů jednotek C++ podporují [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 a novější (všechny edice)**

- **Google test adaptér** je zahrnutý jako výchozí součást **vývoje desktopových aplikací v C++** . Má šablonu projektu, kterou můžete přidat do řešení. Pomocí nabídky **Přidat nový projekt** v uzlu řešení v **Průzkumník řešení** ho přidejte. Obsahuje také možnosti, které můžete konfigurovat prostřednictvím   >  **možností** nástroje. Další informace naleznete v tématu [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- Jako výchozí součást **vývoje desktopových aplikací v jazyce C++** je k dispozici funkce **zvyšování. test** . Je integrována s **průzkumníkem testů**, ale aktuálně nemá šablonu projektu. Je nutné ho nakonfigurovat ručně. Další informace naleznete v tématu [How to: use. test v aplikaci Visual Studio](how-to-use-boost-test-for-cpp.md).

- Podpora **CTest** je součástí komponenty **nástroje c++ cmake** , která je součástí **vývoje plochy pomocí úlohy C++** . Další informace naleznete v tématu [How to: use CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Můžete si stáhnout Google Test adaptér a zvýšit rozšíření testovacího adaptéru na Visual Studio Marketplace. Najdete je na [testovacím adaptéru pro zvýšení](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a [testovací adaptér pro Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Pracovní postup základního testu

V následujících částech jsou uvedeny základní kroky, které vám pomohou začít s testováním částí jazyka C++. Základní konfigurace je podobná jak pro rozhraní Microsoft, tak pro Google Test. Zvýšení. test vyžaduje ruční vytvoření testovacího projektu.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2019

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů do existujícího řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení**. V místní nabídce vyberte možnost **Přidat**  >  **Nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Následující ilustrace znázorňuje projekty testů, které jsou k dispozici v případě, že je nainstalován **vývoj desktopových aplikací v jazyce C++** a úloha **vývoje UWP** :

![Projekty testů C++ v aplikaci VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2017

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **Nový projekt**. V levém podokně vyberte **Visual C++ test**. Pak v prostředním podokně vyberte jeden z typů projektu. Následující ilustrace znázorňuje projekty testů, které jsou k dispozici, když je nainstalovaná úloha **vývoj desktopových aplikací C++** :

![Projekty testů C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytvořit odkazy na jiné projekty v řešení

Chcete-li povolit přístup k funkcím v testovaném projektu, přidejte do projektu testů odkaz na projekt. Klikněte pravým tlačítkem myši na uzel testovací projekt v **Průzkumník řešení** pro místní nabídku. Vyberte možnost **Přidat**  >  **odkaz**. V dialogovém okně Přidat odkaz vyberte projekt (y), který chcete otestovat.

![Přidání odkazu](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Odkaz na soubory objektů nebo knihoven

Pokud kód testu neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubory. obj nebo. lib do závislostí testovacího projektu. Další informace najdete v tématu [propojení testů s objekty nebo soubory knihovny](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Přidat direktivy #include pro hlavičkové soubory

Dále v souboru Test jednotky *. cpp* přidejte `#include` direktivu pro všechny hlavičkové soubory, které deklaruje typy a funkce, které chcete testovat. Typ `#include "` a potom IntelliSense, který vám pomůže vybrat. Opakujte pro další hlavičky.

![Snímek obrazovky Průzkumník řešení zobrazující direktivu #include, která se přidává pomocí technologie IntelliSense, která zvýrazňuje soubor hlaviček pro zahrnutí.](media/cpp-add-includes-test-project.png)

Chcete-li se vyhnout nutnosti zadávat úplnou cestu do každého příkazu include ve zdrojovém souboru, můžete přidat požadované složky v části   >  **vlastnosti** projektu  >    >  **Obecné**  >  **Další adresáře include**.

### <a name="write-test-methods"></a>Zápis testovacích metod

> [!NOTE]
> Tato část ukazuje syntaxi pro Microsoft Unit Testing Framework pro C/C++. Je zde popsána zde: [Reference k rozhraní API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Dokumentaci k Google Test najdete v části [Google test Úvod](https://github.com/google/googletest/blob/master/docs/primer.md). Pro zvýšení. test naleznete v tématu [knihovna Boost test: rozhraní pro testování částí](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Soubor *. cpp* v testovacím projektu má zástupnou třídu a metodu definovanou pro vás. Ukazují příklad, jak napsat testovací kód. Signatury používají makra TEST_CLASS a TEST_METHOD, která umožňují zjistit metody z okna **Průzkumníka testů** .

![Snímek obrazovky okna Průzkumníka testů, které zobrazuje soubor kódu UnitTest1. cpp obsahující zástupnou třídu a metodu pomocí makra TEST_CLASS a TEST_METHOD.](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí [nativního testovacího rozhraní společnosti Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** zjišťuje testovací metody v jiných podporovaných rozhraních podobným způsobem.

TEST_METHOD vrátí typ void. Chcete-li vytvořit výsledek testu, použijte statické metody ve `Assert` třídě k otestování skutečných výsledků oproti očekávání. V následujícím příkladu Předpokládejme, `MyClass` že má konstruktor, který přijímá `std::string` . Můžeme otestovat, že konstruktor inicializuje třídu podle očekávání, například takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu výsledek `Assert::AreEqual` volání Určuje, zda test projde nebo se nezdařil. Třída Assert obsahuje mnoho dalších metod pro porovnání očekávaných vs. skutečných výsledků.

Můžete přidat *vlastnosti* do testovacích metod a zadat vlastníky testů, prioritu a další informace. Tyto hodnoty pak můžete použít k řazení a seskupení testů v **Průzkumníku testů**. Další informace naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **test** vyberte **Windows**  >  **Test Explorer**. Následující ilustrace znázorňuje testovací projekt, jehož testy ještě nebyly spuštěny.

   ![Průzkumník testů před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integrace CTest s **průzkumníkem testů** zatím není k dispozici. Spusťte testy CTest z hlavní nabídky CMake.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumníku testů** zvolte možnost **Spustit vše** nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem na test pro další možnosti, včetně spuštění v režimu ladění se zapnutými zarážkami. Po spuštění všech testů se v okně zobrazí, které testy byly úspěšné a které selhaly:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

U neúspěšných testů obsahuje zpráva podrobnosti, které vám pomůžou diagnostikovat příčinu. Klikněte pravým tlačítkem myši na test selhání pro místní nabídku. Vyberte možnost **ladit vybrané testy** pro krokování funkce, ve které došlo k chybě.

Další informace o použití **Průzkumníka testů** naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

Další informace související s testováním částí najdete v tématu [základy testování částí](unit-test-basics.md) .

## <a name="use-codelens"></a>Použití CodeLens

**Visual Studio 2017 nebo novější (edice Professional a Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav testu jednotek bez nutnosti opustit Editor kódu.

CodeLens pro projekt testování částí v jazyce C++ lze inicializovat některým z těchto způsobů:

- Upravte a sestavte testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Spusťte testy z okna **Průzkumník testů** .

Po inicializaci můžete zobrazit ikony stavu testu nad každým testem jednotky.

![CodeLens C++ – ikony](media/cpp-test-codelens-icons.png)

Kliknutím na ikonu zobrazíte další informace nebo spustíte nebo ladíte test jednotky:

![Spuštění a ladění C++ CodeLens](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](unit-test-your-code.md)
