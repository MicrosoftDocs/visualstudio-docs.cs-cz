---
title: Zápis testů jednotek pro C/C++
description: Pište testy jednotek C++ v Visual Studio různých testovacích architektur, včetně CTest, Boost.Test a Google Test.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 877c9163d05f458ce45a46d6b3e6d14e354df591
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042884"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Zápis testů jednotek pro C/C++ v Visual Studio

Testy jednotek jazyka C++ můžete psát a spouštět pomocí okna **Průzkumníka** testů. Funguje stejně jako v jiných jazycích. Další informace o používání **Průzkumníka testů najdete** v tématu [Spouštění testů jednotek pomocí Průzkumníka testů.](run-unit-tests-with-test-explorer.md)

> [!NOTE]
> Některé funkce, jako Live Unit Testing, programové testy uživatelského rozhraní a IntelliTest, nejsou podporovány pro jazyk C++.

Visual Studio zahrnuje tyto testovací architektury C++ bez dalších požadovaných stahování:

- Microsoft Unit Testing Framework pro C++
- Google Test
- Boost.Test
- CTest

Společně s nainstalovanými rozhraními můžete napsat vlastní testovací adaptér pro jakékoli rozhraní, které chcete v rámci Visual Studio. Testovací adaptér může integrovat testy jednotek s **oknem Průzkumníka** testů. V systému je k dispozici několik adaptérů [třetích Visual Studio Marketplace](https://marketplace.visualstudio.com). Další informace najdete v tématu Instalace rozhraní testování částí [třetích stran.](install-third-party-unit-test-frameworks.md)

**Visual Studio 2017 a novější (Professional a Enterprise)**

Projekty testů jednotek C++ podporují [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 a novější (všechny edice)**

- **Google Test Adapter je** součástí výchozí součásti úlohy **Vývoj desktopových aplikací pomocí jazyka C++.** Obsahuje šablonu projektu, kterou můžete přidat do řešení. Pomocí nabídky **Přidat nový projekt** klikněte pravým tlačítkem na uzlu řešení v **Průzkumník řešení** ho přidejte. Nabízí také možnosti, které můžete konfigurovat prostřednictvím **nástroje**  >  **Možnosti**. Další informace najdete v tématu [Postupy: Použití Google Test v Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** je součástí výchozí komponenty vývoje **desktopových aplikací v jazyce C++.** Je integrovaný s **Průzkumníkem testů,** ale v současné době nemá šablonu projektu. Musí být ručně nakonfigurovaný. Další informace najdete v tématu [Postupy: Použití boost.test v Visual Studio](how-to-use-boost-test-for-cpp.md).

- **Podpora CTest** je součástí komponenty **nástrojů C++ CMake,** která je součástí úlohy **Vývoj desktopových aplikací v jazyce C++.** Další informace najdete v tématu [Postupy: Použití CTest v Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 a starší**

Rozšíření Google Test a Boost.Test Adapter si můžete stáhnout na Visual Studio Marketplace. Najdete je v [adaptéru test pro adaptér Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) a Test pro [Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Základní testovací pracovní postup

Následující části popisují základní kroky, které vám pohánět s testováním částí jazyka C++. Základní konfigurace je podobná pro microsoftovou i Google Test architektury. Boost.Test vyžaduje ruční vytvoření testovacího projektu.

::: moniker range=">=vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Vytvoření testovacího projektu v Visual Studio 2019

Testy definujete a spustíte v jednom nebo více testovacích projektech. Projekty vytvoříte ve stejném řešení jako kód, který chcete otestovat. Pokud chcete přidat nový projekt testů do existujícího řešení, klikněte pravým tlačítkem na uzel Řešení v **Průzkumník řešení**. V místní nabídce zvolte **Přidat**  >  **nový projekt.** Nastavte **Jazyk** na C++ a do vyhledávacího pole zadejte "test". Následující obrázek znázorňuje projekty testů, které jsou k dispozici při instalaci úloh Vývoj desktopových **aplikací v jazyce C++** a Vývoj **pro** UPW:

![Projekty testů C++ v nástroji VIsual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Vytvoření testovacího projektu v Visual Studio 2017

Testy definujete a spustíte v jednom nebo více testovacích projektech. Projekty vytvoříte ve stejném řešení jako kód, který chcete otestovat. Pokud chcete přidat nový projekt testů, klikněte pravým tlačítkem na uzel Řešení v **Průzkumník řešení** a zvolte **Přidat**  >  **nový projekt**. V levém podokně zvolte Visual C++ **Test**. Pak vyberte jeden z typů projektu ze středového podokna. Následující obrázek znázorňuje projekty testů, které jsou k dispozici při instalaci **úlohy Vývoj desktopových aplikací pomocí jazyka C++:**

![Projekty testů C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Vytváření odkazů na jiné projekty v řešení

Pokud chcete povolit přístup k funkcím v projektu v rámci testu, přidejte odkaz na projekt v projektu testů. Klikněte pravým tlačítkem na uzel testovacího projektu **v Průzkumník řešení** a zobrazí se automaticky otevíraná nabídka. Zvolte **Přidat**  >  **odkaz.** V dialogovém okně Přidat odkaz zvolte projekty, které chcete otestovat.

![Přidání odkazu](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Propojení se soubory objektů nebo knihoven

Pokud testovací kód neexportuje funkce, které chcete otestovat, můžete do závislostí testovacího projektu přidat výstupní soubory .obj nebo .lib. Další informace najdete v tématu [Propojení testů se soubory objektu nebo knihovny](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Přidání #include pro soubory hlaviček

Dále do souboru *.cpp* testu jednotek přidejte direktivu pro všechny soubory hlaviček, které deklarují typy a funkce, `#include` které chcete testovat. Zadejte `#include "` a IntelliSense se aktivuje, aby vám pomohl s výběrem. Postup opakujte pro všechny další hlavičky.

![Snímek obrazovky Průzkumník řešení s přidanou direktivou #include intellisense se zvýrazněným souborem záhlaví pro zahrnutí](media/cpp-add-includes-test-project.png)

Abyste se vyhnuli nutnosti zazadat úplnou cestu ke každému příkazu include ve zdrojovém souboru, můžete požadované složky přidat do části **Vlastnosti** projektu  >    >  **C/C++** Obecné další  >    >  **adresáře k zahrnutí.**

### <a name="write-test-methods"></a>Psaní testovacích metod

> [!NOTE]
> Tato část ukazuje syntaxi rozhraní Microsoft Unit Testing Framework pro C/C++. Je zdokumentovaný tady: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Další Google Test najdete v tématu [Google Test.](https://github.com/google/googletest/blob/master/docs/primer.md) Informace o boost.test najdete [v Boost Test: Rozhraní testování částí](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Soubor *.cpp v* testovacím projektu má definovanou třídu zástupné procedury a metodu. Ukazují příklad, jak napsat testovací kód. Podpisy používají TEST_CLASS a TEST_METHOD, která zjišťovatelné metody z okna **Průzkumníka** testů.

![Snímek obrazovky s oknem Průzkumníka testů, které zobrazuje soubor kódu unittest1.cpp obsahující zástupnou třídu a metodu pomocí TEST_CLASS a TEST_METHOD maker](media/cpp-write-test-methods.png)

TEST_CLASS a TEST_METHOD jsou součástí rozhraní [Microsoft Native Test Framework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Průzkumník testů** podobným způsobem zjišťuje testovací metody v jiných podporovaných architekturách.

Metoda TEST_METHOD void. Pokud chcete vytvořit výsledek testu, použijte statické metody ve třídě k otestování skutečných `Assert` výsledků na základě očekávaného výsledku. V následujícím příkladu předpokládejme, `MyClass` že má konstruktor, který přebírá `std::string` . Můžeme otestovat, že konstruktor inicializuje třídu podle očekávání takto:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

V předchozím příkladu výsledek volání určuje, `Assert::AreEqual` jestli je test úspěšný nebo neúspěšný. Třída Assert obsahuje mnoho dalších metod pro porovnání očekávaných a skutečných výsledků.

K testovacím *metodám můžete přidat* vlastnosti, které určují vlastníky testů, prioritu a další informace. Tyto hodnoty pak můžete použít k řazení a seskupování testů v **Průzkumníku testů.** Další informace najdete v tématu [Spouštění testů jednotek pomocí Průzkumníka testů.](run-unit-tests-with-test-explorer.md)

### <a name="run-the-tests"></a>Spuštění testů

1. V **nabídce Test** zvolte Průzkumník **testů Systému Windows.**  >   Následující obrázek znázorňuje projekt testů, jehož testy ještě nebyly spuštěny.

   ![Průzkumník testů před spuštěním testů](media/cpp-test-explorer.png)

   > [!NOTE]
   > Integrace CTestu **s Průzkumníkem testů** ještě není dostupná. Spouštění testů CTest z hlavní nabídky CMake

1. Pokud se v okně nezobrazí všechny vaše testy, sestavte projekt testů tak, že kliknete pravým tlačítkem na jeho uzel v **Průzkumník řešení** zvolíte **Sestavit** nebo **Znovu sestavit**.

1. V **Průzkumníku** testů zvolte **Spustit vše** nebo vyberte konkrétní testy, které chcete spustit. Kliknutím pravým tlačítkem na test zobrazíte další možnosti, včetně jeho spuštění v režimu ladění s povolenými zarážkami. Po spuštění všech testů se v okně zobrazí, které testy byly úspěšně prošly a které selhaly:

![Průzkumník testů po spuštění testů](media/cpp-test-explorer-passed.png)

V případě neúspěšných testů zpráva obsahuje podrobnosti, které vám pomůžou diagnostikovat příčinu. V místní nabídce klikněte pravým tlačítkem na neúspěšný test. Zvolte **Ladit vybrané testy** a projdete funkci, ve které došlo k selhání.

Další informace o používání **Průzkumníka testů najdete** v tématu [Spouštění testů jednotek pomocí Průzkumníka testů.](run-unit-tests-with-test-explorer.md)

Další informace související s testováním jednotek najdete v tématu [Základy testování jednotek.](unit-test-basics.md)

## <a name="use-codelens"></a>Použití CodeLens

**Visual Studio 2017 a novější (edice Professional a Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umožňuje rychle zobrazit stav testu jednotek, aniž byste opustili editor kódu.

CodeLens pro projekt testování částí jazyka C++ můžete inicializovat libovolným z těchto způsobů:

- Upravte a sestavte testovací projekt nebo řešení.
- Znovu sestavte projekt nebo řešení.
- Testy můžete spustit z **okna Průzkumníka** testů.

Po inicializaci se nad jednotlivými testy jednotek zobrazí ikony stavu testů.

![Ikony CodeLens v jazyce C++](media/cpp-test-codelens-icons.png)

Kliknutím na ikonu zobrazíte další informace nebo spustíte nebo ladíte test jednotek:

![C++ CodeLens – spuštění a ladění](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Viz také

- [Testování částí kódu](unit-test-your-code.md)
