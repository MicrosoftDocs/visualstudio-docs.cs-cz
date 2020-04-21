---
title: Zapsat testy částí pro C/C++
description: Napište testy částí C++ v sadě Visual Studio pomocí různých testovacích architektur, včetně CTest, Boost.Test a Google Test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 0eaf41dc0bf3e21dfbf4018261844181d594f0d5
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649603"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů částí pro C/C++ v sadě Visual Studio

Můžete psát a spouštět testy jednotek C++ pomocí okna **Průzkumník testů.** Funguje to stejně jako pro jiné jazyky. Další informace o použití **Průzkumníka testů**naleznete v [tématu Spuštění testů částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Některé funkce, jako je například testování živých částí, programové testy ui a IntelliTest nejsou podporovány pro C++.

Visual Studio obsahuje tyto testovací architektury jazyka C++ bez nutnosti dalšího stahování:

- Rozhraní Microsoft Unit Testing Framework pro c++
- Google Test
- Boost.Test
- CTest

Spolu s použitím nainstalovaných rozhraní můžete napsat vlastní testovací adaptér pro jakékoli rozhraní, které chcete použít v rámci sady Visual Studio. Testovací adaptér může integrovat testy částí s oknem **Průzkumníka testů.** Na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com)je k dispozici několik adaptérů jiných výrobců . Další informace naleznete [v tématu Instalace rozhraní test ů částí jiných výrobců](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 a novější (profesionální a podnikové)**

C++ projekty testování částí podporují [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 a novější (všechny edice)**

- **Testovací adaptér Google** je součástí výchozí součásti vývoje plochy s úlohami **jazyka C++.** Má šablonu projektu, kterou můžete přidat do řešení. Pomocí nabídky **Přidat nový projekt** pravým tlačítkem myši v uzlu řešení v **Průzkumníku řešení** ji přidejte. Má také možnosti, které můžete konfigurovat prostřednictvím**možností** **nástrojů** > . Další informace najdete v [tématu Postup: Použití testu Google ve Visual Studiu](how-to-use-google-test-for-cpp.md).

- **Boost.Test** je součástí jako výchozí součást vývoje plochy s úlohou **C++.** Je integrován s **Průzkumníkem testů**, ale v současné době nemá šablonu projektu. Musí být ručně nakonfigurován. Další informace najdete v [tématu Postup: Použití boost.test v sadě Visual Studio](how-to-use-boost-test-for-cpp.md).

- **Podpora CTest** je součástí **komponenty nástrojů C++ CMake,** která je součástí vývoje plochy s úlohami **C++.** Další informace naleznete v [tématu How to: Use CTest in Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Na webu Visual Studio Marketplace si můžete stáhnout adaptér Google Test a rozšíření Boost.Test Adapter. Najdete je na [testovacím adaptéru pro boost.test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a [testovací adaptér pro Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Základní testovací pracovní postup

Následující části ukazují základní kroky, jak začít s testováním částí C++. Základní konfigurace je podobná pro rozhraní Microsoft a Google Test. Boost.Test vyžaduje ruční vytvoření testovacího projektu.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Vytvoření testovacího projektu ve Visual Studiu 2019

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový testovací projekt do existujícího řešení, klepněte pravým tlačítkem myši na uzel Řešení v **Průzkumníku řešení**. V místní nabídce zvolte **Přidat** > **nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test". Následující obrázek znázorňuje testovací projekty, které jsou k dispozici při **instalaci vývoje plochy s C++** a pracovního vytížení vývoje **UPW:**

![C++ Testovací projekty ve VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Vytvoření testovacího projektu ve Visual Studiu 2017

Můžete definovat a spustit testy uvnitř jednoho nebo více testovacích projektů. Projekty vytvoříte ve stejném řešení jako kód, který chcete testovat. Chcete-li přidat nový testovací projekt, klikněte pravým tlačítkem myši na uzel Řešení v **Průzkumníku řešení** a zvolte **Přidat** > **nový projekt**. V levém podokně zvolte **Visual C++ Test**. Potom zvolte jeden z typů projektu ze středového podokna. Následující obrázek znázorňuje testovací projekty, které jsou k dispozici při instalaci **úlohy Pro vývoj plochy s c++:**

![Testovací projekty jazyka C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytvoření odkazů na jiné projekty v řešení

Chcete-li povolit přístup k funkcím v testu projektu, přidejte odkaz na projekt v testovacím projektu. Klikněte pravým tlačítkem myši na uzel testovacího projektu v **Průzkumníku řešení** pro rozbalovací nabídku. Zvolte **Přidat** > **odkaz**. V dialogovém okně Přidat odkaz zvolte projekty, které chcete testovat.

![Přidání odkazu](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Propojení se soubory objektů nebo knihoven

Pokud testovací kód neexportuje funkce, které chcete testovat, můžete přidat výstupní soubory OBJ nebo .lib do závislostí testovacího projektu. Další informace naleznete [v tématu Propojení testů se soubory objektu nebo knihovny](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Přidání #include direktiv pro soubory hlaviček

Dále v souboru *cpp* testování částí `#include` přidejte direktivu pro všechny soubory hlaviček, které deklarují typy a funkce, které chcete testovat. Zadejte `#include "` a potom se intelliSense aktivuje, abyste si je vybrali. Tento postup opakujte pro všechna další záhlaví.

![Přidat direktivy zahrnutí](media/cpp-add-includes-test-project.png)

Chcete-li se vyhnout nutnosti zadávat úplnou cestu do každého příkazu include do zdrojového souboru, můžete přidat požadované složky do **seznamu** > **Vlastnosti** > projektu**C/C++** > **Obecné** > další včetně**adresářů**.

### <a name="write-test-methods"></a>Zapsat testovací metody

> [!NOTE]
> Tato část ukazuje syntaxi pro rozhraní Microsoft Unit Testing Framework pro C/C++. Je dokumentován zde: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework odkaz na rozhraní API](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Dokumentace k testu Google najdete v tématu [Základní nátěr testu Google](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Pro Boost.Test, najdete [v tématu Boost Test knihovny: rozhraní testování částí](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Soubor *CPP* v testovacím projektu má třídu se zakázaným inzerováním a metodu definovanou pro vás. Ukazují příklad, jak psát testovací kód. Podpisy používají TEST_CLASS a TEST_METHOD makra, díky nimž jsou metody zjistitelné z okna **Průzkumníka testů.**

![Přidat direktivy zahrnutí](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí architektury [Microsoft Native Test Framework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** zjišťuje testovací metody v jiných podporovaných architekturách podobným způsobem.

TEST_METHOD vrátí prázdnotu. Chcete-li vytvořit výsledek testu, použijte `Assert` statické metody ve třídě k testování skutečných výsledků proti tomu, co se očekává. V následujícím příkladu `MyClass` assume má konstruktor, který trvá `std::string`. Můžeme otestovat, že konstruktor inicializuje třídu podle očekávání takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu výsledek `Assert::AreEqual` volání určuje, zda test projde nebo selže. Třída Assert obsahuje mnoho dalších metod pro porovnání očekávaných a skutečných výsledků.

Můžete přidat *vlastnosti* testovací metody určit vlastníky testů, priority a další informace. Tyto hodnoty pak můžete použít k řazení a seskupit testy v **Průzkumníku testů**. Další informace naleznete v [tématu Spuštění testů částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Spuštění testů

1. V nabídce **Test** zvolte**Průzkumník testů systému** **Windows** > . Následující obrázek znázorňuje testovací projekt, jehož testy ještě nebyly spuštěny.

   ![Průzkumník testů před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integrace CTest s **Průzkumníkem testů** ještě není k dispozici. Spusťte testy CTest z hlavní nabídky CMake.

1. Pokud nejsou všechny testy viditelné v okně, vytvořte testovací projekt kliknutím pravým tlačítkem myši na jeho uzel v **Průzkumníku řešení** a zvolte **Sestavit** nebo **znovu sestavit**.

1. V **Průzkumníkovi testů**zvolte **Spustit vše**nebo vyberte konkrétní testy, které chcete spustit. Klepněte pravým tlačítkem myši na test pro další možnosti, včetně spuštění v režimu ladění s povolenými zarážkymi. Po spuštění všech testů, okno ukazuje, které testy proběhly a které z nich se nezdařilo:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

U neúspěšných testů zpráva nabízí podrobnosti, které pomáhají diagnostikovat příčinu. Klikněte pravým tlačítkem myši na neúspěšný test pro rozbalovací nabídku. Zvolte **Ladění vybraných testů,** chcete-li procházet funkci, kde došlo k chybě.

Další informace o použití **Průzkumníka testů**naleznete v [tématu Spuštění testů částí pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md).

Další informace týkající se testování částí naleznete v [tématu Základy testování částí](unit-test-basics.md)

## <a name="use-codelens"></a>Použít CodeLens

**Visual Studio 2017 a novější (edice Professional a Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav testování částí bez opuštění editoru kódu.

CodeLens pro projekt testování částí c++ můžete inicializovat libovolným z těchto způsobů:

- Upravte a sestavte testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Spusťte testy z okna **Průzkumníka testů.**

Po inicializování se nad každým testem jednotky zobrazí ikony stavu testu.

![Ikony C++ CodeLens](media/cpp-test-codelens-icons.png)

Klikněte na ikonu pro více informací, nebo spustit nebo ladit testování částí:

![Spuštění a ladění c++ codelens](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](unit-test-your-code.md)
