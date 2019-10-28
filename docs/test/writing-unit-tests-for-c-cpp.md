---
title: Zápis testů jednotek pro C/C++
description: Zapište C++ testy jednotek v aplikaci Visual Studio pomocí různých testovacích rozhraní, včetně CTest, zvyšování. test a Google test.
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 9d69c91af316c755b2dcf4f339d8f47d49096b6a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982914"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů jednotek pro C/C++ v aplikaci Visual Studio

Můžete napsat a spustit testy C++ jednotek pomocí okna **Průzkumník testů** , podobně jako u jiných jazyků. Další informace o použití **Průzkumníka testů**naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Některé funkce, jako například Live Unit Testing, programové testy uživatelského rozhraní a IntelliTest, nejsou C++podporovány pro.

Visual Studio zahrnuje tyto C++ testovací architektury bez nutnosti dalšího stažení:

- Microsoft Unit Testing Framework proC++
- Google Test
- Zvýšení. test
- CTest

Kromě instalovaných rozhraní můžete napsat vlastní testovací adaptér pro libovolné rozhraní, které chcete použít v sadě Visual Studio. Testovací adaptér může integrovat testy jednotek pomocí okna **Průzkumníka testů** . V [Visual Studio Marketplace](https://marketplace.visualstudio.com)je k dispozici několik adaptérů třetích stran. Další informace najdete v tématu [instalace rozhraní pro testování částí třetích stran](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 a novější (Professional a Enterprise)**

C++projekty testů jednotek podporují [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 a novější (všechny edice)**

- **Google test adaptér** je součástí jako výchozí součást **vývoje C++ desktopových** aplikací. Má šablonu projektu, kterou můžete přidat do řešení pomocí nabídky **Přidat nový projekt** v uzlu řešení v **Průzkumník řešení**a možnosti, které můžete konfigurovat prostřednictvím **nástrojů** > **Možnosti**. Další informace naleznete v tématu [How to: Use Google test in Visual Studio](how-to-use-google-test-for-cpp.md).

- Jako výchozí součást **vývoje pro stolní počítače s C++**  úlohou je k dispozici funkce **zvýšení. test.** Je integrována s **průzkumníkem testů** , ale aktuálně nemá šablonu projektu, proto musí být ručně nakonfigurována. Další informace naleznete v tématu [How to: use. test v aplikaci Visual Studio](how-to-use-boost-test-for-cpp.md).

- Součástí  **C++ nástrojů cmake** je podpora **CTest** , která je součástí  **C++ vývoje plochy s** úlohou. CTest ale ještě není plně integrovaná s **průzkumníkem testů**. Další informace naleznete v tématu [How to: use CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Můžete si stáhnout Google Test adaptér a zvýšit rozšíření testovacího adaptéru na Visual Studio Marketplace na [testovacím adaptéru pro zvýšení](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a [testovací adaptér pro Google test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Pracovní postup základního testu

V následujících částech jsou uvedeny základní kroky, které vám pomohou C++ začít s testováním částí. Základní konfigurace je velmi podobná pro rozhraní Microsoft a Google Test. Zvýšení. test vyžaduje ruční vytvoření testovacího projektu.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2019

Definujete a spouštíte testy uvnitř jednoho nebo více testovacích projektů, které jsou ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů do existujícího řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte **Přidat** > **Nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Následující ilustrace znázorňuje projekty testů, které jsou k dispozici v případě, že je nainstalován **vývoj C++ desktopových** aplikací a úloha **vývoje UWP** :

![C++Projekty testů v aplikaci VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Vytvoření testovacího projektu v aplikaci Visual Studio 2017

Definujete a spouštíte testy uvnitř jednoho nebo více testovacích projektů, které jsou ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový projekt testů do existujícího řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte **Přidat** > **Nový projekt**. Pak v levém podokně zvolte **Visual C++ test** a v prostředním podokně vyberte jeden z typů projektu. Následující ilustrace znázorňuje projekty testů, které jsou k dispozici v případě, že je nainstalován **desktopový vývoj s C++**  úlohou:

![C++Projekty testů](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytvořit odkazy na jiné projekty v řešení

Chcete-li povolit testovací kód pro přístup k funkcím projektu, který má být testován, přidejte do projektu testů odkaz na projekt. Klikněte pravým tlačítkem myši na uzel testovací projekt v **Průzkumník řešení** a vyberte možnost **Přidat** > **odkaz**. Pak v dialogovém okně vyberte projekt (y), který chcete otestovat.

![Přidat odkaz](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Odkaz na soubory objektů nebo knihoven

Pokud kód testu neexportuje funkce, které chcete otestovat, můžete přidat výstupní soubory. obj nebo. lib do závislostí testovacího projektu. Viz [propojení testů s objekty nebo soubory knihovny](unit-testing-existing-cpp-applications-with-test-explorer.md).

### <a name="add-include-directives-for-header-files"></a>Přidat direktivy #include pro hlavičkové soubory

Dále v souboru *. cpp* testu jednotky přidejte direktivu `#include` pro všechny hlavičkové soubory, které deklaruje typy a funkce, které chcete testovat. Zadejte `#include "` a potom se aktivuje IntelliSense, který vám pomůže vybrat. Opakujte pro další hlavičky.

![Přidat direktivy include](media/cpp-add-includes-test-project.png)

Chcete-li se vyhnout nutnosti zadávat úplnou cestu do každého příkazu include ve zdrojovém souboru, můžete přidat požadované složky v **projektu** > **vlastnosti** > **C/C++**  > **Obecné** > **Další zahrnutí Adresáře**.

### <a name="write-test-methods"></a>Zápis testovacích metod

> [!NOTE]
> V této části se zobrazuje syntaxe pro Microsoft Unit Testing Framework proC++C/. Je zde popsána zde: [Reference k rozhraní API Microsoft. VisualStudio. TestTools. CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Dokumentaci k Google Test najdete v části [Google test Úvod](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Pro zvýšení. test naleznete v tématu [knihovna Boost test: rozhraní pro testování částí](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Soubor *. cpp* v testovacím projektu má zástupnou třídu a metodu definovanou jako příklad, jak napsat testovací kód. Všimněte si, že signatury používají makra TEST_CLASS a TEST_METHOD, která umožňuje zjistit metody z okna **Průzkumníka testů** .

![Přidat direktivy include](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí [nativního testovacího rozhraní společnosti Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** zjišťuje testovací metody v jiných podporovaných rozhraních podobným způsobem.

TEST_METHOD vrací typ void. Chcete-li vytvořit výsledek testu, použijte statické metody ve třídě `Assert` k otestování skutečných výsledků oproti očekávání. V následujícím příkladu Předpokládejme, že `MyClass` má konstruktor, který přebírá `std::string`. Můžeme otestovat, že konstruktor inicializuje třídu podle očekávání, například takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu výsledek volání `Assert::AreEqual` určuje, zda test projde nebo se nezdařil. Třída Assert obsahuje mnoho dalších metod pro porovnání očekávaných vs. skutečných výsledků.

Můžete přidat *vlastnosti* do testovacích metod a zadat vlastníky testů, prioritu a další informace. Tyto hodnoty pak můžete použít k řazení a seskupení testů v **Průzkumníku testů**. Další informace naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Spustit testy

1. V nabídce **test** vyberte možnost **Windows** > **Průzkumník testů**. Následující ilustrace znázorňuje testovací projekt, jehož testy ještě nebyly spuštěny.

   ![Průzkumník testů před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integrace CTest s **průzkumníkem testů** zatím není k dispozici. Spusťte testy CTest z hlavní nabídky CMake.

1. Pokud nejsou všechny testy v okně viditelné, sestavte projekt testu kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumník řešení** a výběrem možnosti **sestavit** nebo **znovu sestavit**.

1. V **Průzkumníku testů**zvolte možnost **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klikněte pravým tlačítkem na test pro další možnosti, včetně spuštění v režimu ladění se zapnutými zarážkami. Po spuštění všech testů se v okně zobrazí, které testy byly úspěšné a které selhaly:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

U neúspěšných testů obsahuje zpráva podrobnosti, které vám pomůžou diagnostikovat příčinu. Můžete kliknout pravým tlačítkem na neúspěšný test a zvolit **ladit vybrané testy** pro krokování funkce, ve které došlo k chybě.

Další informace o použití **Průzkumníka testů**naleznete v tématu [Run Unit Tests with Test Explorer](run-unit-tests-with-test-explorer.md).

Osvědčené postupy související s testováním částí najdete v tématu [základní informace](unit-test-basics.md) o testování částí

## <a name="use-codelens"></a>Použití CodeLens

**Visual Studio 2017 nebo novější (edice Professional a Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav testu jednotek bez nutnosti opustit Editor kódu. CodeLens pro projekt testování C++ částí můžete inicializovat některým z těchto způsobů:

- Upravte a sestavte testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Spustit test (y) z okna **Průzkumníka testů** .

Po inicializaci **CodeLens** uvidíte ikony stavu testu nad každým testem jednotky.

![C++Ikony CodeLens](media/cpp-test-codelens-icons.png)

Kliknutím na ikonu zobrazíte další informace nebo spustíte nebo ladíte test jednotky:

![C++CodeLens spuštění a ladění](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](unit-test-your-code.md)
