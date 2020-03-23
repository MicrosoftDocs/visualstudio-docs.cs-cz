---
title: Jak používat Boost.Test pro C++
description: Pomocí boost.test vytvořit testy částí v sadě Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922912"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Použití boost.test pro C++ v sadě Visual Studio

V sadě Visual Studio 2017 a novější adaptér test Boost.Test je integrován do ide Sady Visual Studio. Je součástí vývoje plochy s úlohami **Jazyka C++.**

![Testovací adaptér pro boost.test](media/cpp-boost-component.png)

Pokud nemáte nainstalovanou **aplikaci Desktop development with C++** workload, otevřete **Instalační službu sady Visual Studio**. Vyberte vývoj plochy s úlohami **c++** a pak zvolte **tlačítko Změnit.**

## <a name="install-boost"></a>Nainstalovat Boost

Boost.Test vyžaduje [boost!](https://www.boost.org/) Pokud nemáte nainstalovanou podporu, doporučujeme použít správce balíčků Vcpkg.

1. Postupujte podle pokynů na [Vcpkg: Správce balíčků C++ pro Windows](/cpp/vcpkg) k instalaci vcpkg (pokud ho ještě nemáte).

1. Nainstalujte dynamickou nebo statickou knihovnu Boost.Test:

    - Spusťte `vcpkg install boost-test` instalaci dynamické knihovny Boost.Test.

       - nebo -

    - Spuštěním `vcpkg install boost-test:x86-windows-static` nainstalujete statickou knihovnu Boost.Test.

1. Spuštěním `vcpkg integrate install` nakonfigurujete Visual Studio s knihovnou a zahrňte cesty k záhlavím a binárním souborům boost.

Máte na výběr, jak nakonfigurovat testy v rámci řešení v sadě Visual Studio: Testovací kód můžete zahrnout do testovaného projektu nebo můžete vytvořit samostatný testovací projekt pro vaše testy. Obě možnosti mají své výhody i nevýhody.

## <a name="add-tests-inside-your-project"></a>Přidání testů v rámci projektu

V Sadě Visual Studio 2017 verze 15.6 a novější, můžete přidat šablonu položky pro testy do projektu. Testy a váš kód žijí ve stejném projektu. Budete muset vytvořit samostatnou konfiguraci sestavení pro generování testovacího sestavení. A budete muset zachovat testy z ladění a vydání sestavení.

Ve Visual Studiu 2017 verze 15.5 nejsou pro Boost.Test k dispozici žádné předem nakonfigurované šablony testovacího projektu nebo položek. Pomocí pokynů vytvořte a nakonfigurujte samostatný testovací projekt.

### <a name="create-a-boosttest-item"></a>Vytvoření položky Boost.Test

1. Chcete-li pro testy vytvořit soubor *CPP,* klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** rozbalte **položku Installed** > **Visual C++** > **Test**. Vyberte **Boost.Test**, pak zvolte **Přidat** přidat *Test.cpp* do projektu.

   ![Šablona položky Boost.Test](media/boost_test_item_template.png)

Nový soubor *Test.cpp* obsahuje vzorkovací testovací metodu. Tento soubor je místo, kde můžete zahrnout vlastní soubory hlaviček a psát testy pro vaši aplikaci.

Testovací soubor také používá makra `main` k definování nové rutiny pro testovací konfigurace. Pokud vytvoříte projekt nyní, zobrazí se chyba LNK2005, například "_main již definována v main.obj."

### <a name="create-and-update-build-configurations"></a>Vytvoření a aktualizace konfigurací sestavení

1. Chcete-li vytvořit testovací konfiguraci, vyberte na řádku nabídek položku **Build** > **Configuration Manager**. V dialogovém okně **Správce konfigurace** otevřete rozevírací program v části **Konfigurace aktivního řešení** a zvolte **Nový**. V dialogovém okně **Nová konfigurace řešení** zadejte název, například "Ladění testů jednotek". V **části Kopírovat nastavení vyberte** **Ladit**a pak zvolte **OK**.

1. Vylučte testovací kód z konfigurací ladění a vydání: V **Průzkumníku řešení**klikněte pravým tlačítkem myši na test.cpp a vyberte **vlastnosti**. V dialogovém okně **Stránky vlastností** vyberte v rozevíracím souboru **Konfigurace** **položku Všechny konfigurace.** Vyberte **Vlastnosti** > konfigurace**Obecné** a otevřete rozevírací seznam pro vlastnost **Vyloučeno ze sestavení.** Vyberte **Ano**a pak zvolte **Použít,** chcete-li změny uložit.

1. Chcete-li zahrnout testovací kód do konfigurace Testy ladicí jednotky, vyberte v dialogovém okně **Stránky vlastností** v rozevíracím řádu **Konfigurace** testy **ladící jednotky.** Ve vlastnosti **Vyloučeno ze sestavení** vyberte **Ne** a pak zvolte **OK,** chcete-li změny uložit.

1. Vylučte hlavní kód z konfigurace Ladění unittests. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor, který obsahuje vaši `main` funkci, a vyberte příkaz **Vlastnosti**. V dialogovém okně **Stránky vlastností** vyberte v rozevíracím okně Konfigurace testy **ladící** **jednotky.** Vyberte **Vlastnosti** > konfigurace**Obecné** a otevřete rozevírací seznam pro vlastnost **Vyloučeno ze sestavení.** Vyberte **Ano**, pak zvolte **OK,** chcete-li změny uložit.

1. Nastavte konfiguraci řešení na **ladění UnitTests**, pak sestavení projektu povolit **Průzkumníka testů** ke zjištění metody.

Tak dlouho, dokud název konfigurace, který vytvoříte, začíná slovy "Ladění" nebo "Vydání", odpovídající knihovny Boost.Test se automaticky vyzvedne.

Šablona položky používá variantu boost.test s jedním záhlavím, ale můžete upravit cestu #include a použít samostatnou variantu knihovny. Další informace naleznete v tématu [Add include directives](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

V mnoha případech je jednodušší použít samostatný projekt pro vaše testy. Nebudete muset vytvořit speciální testovací konfiguraci pro váš projekt. Nebo vyloučit testovací soubory z ladění a vydání sestavení.

### <a name="to-create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel řešení a zvolte **Přidat** > **nový projekt**.

1. V **dialogovém** okně Přidat nový projekt zvolte v rozevíracích seznamech filtrů v rozevíracích seznamech s filtrem **možnost C++**, **Windows**a **Console.** Vyberte šablonu **Konzolové aplikace** a pak zvolte **Další**.

1. Pojmenujte projekt a zvolte **Vytvořit**.

1. Odstraňte `main` funkci v souboru *CPP.*

1. Pokud používáte jednohlavou nebo dynamickou verzi knihovny Boost.Test, přejděte na [Přidat direktivy zahrnutí](#add-include-directives). Pokud používáte statickou verzi knihovny, musíte provést další konfiguraci:

   a. Chcete-li soubor projektu upravit, nejprve jej uvolněte. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a zvolte **Uvolnit project**. Potom klepněte pravým tlačítkem myši na uzel projektu a zvolte **Upravit <název\>.vcxproj**.

   b. Přidejte dva řádky do **skupiny vlastností Globals,** jak je znázorněno zde:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Uložte a zavřete soubor * \*.vcxproj* a potom projekt znovu načtěte.

   d. Chcete-li otevřít **stránky vlastností**, klepněte pravým tlačítkem myši na uzel projektu a zvolte **vlastnosti**.

   e. Rozbalte**generování kódu** **c/c++** > a pak vyberte **Runtime Library**. Vyberte **/MTd** pro ladění statické runtime knihovny nebo **/MT** pro uvolnění statické runtime knihovny.

   f. Rozbalte > **linkerový systém**. **Linker** Ověřte, zda je **podsystém** nastaven na **konzolu**.

   g. Chcete-li zavřít stránky vlastností, zvolte **OK.**

## <a name="add-include-directives"></a>Přidat direktivy zahrnutí

1. Do testovacího souboru *CPP* `#include` přidejte všechny potřebné direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Pokud používáte samostatný testovací projekt, obvykle je program na úrovni na stejné úrovni v hierarchii složek. Pokud zadáte `#include "../"`, zobrazí se okno IntelliSense, které umožňuje vybrat úplnou cestu k souboru záhlaví.

   ![Přidání direktiv #include](media/cpp-gtest-includes.png)

   Samostatnou knihovnu můžete použít s:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Nebo použijte verzi s jedním záhlavím s:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Potom definujte `BOOST_TEST_MODULE`.

Následující příklad je dostačující pro test, který má být zjistitelný v **Průzkumníku testů**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Zápis a spuštění testů

Nyní jste připraveni k zápisu a spuštění testů Boost. Informace o testovacích marech naleznete v [dokumentaci k testovací knihovně](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) Boost. Informace o zjišťování, spouštění a seskupování testů pomocí **Průzkumníka testů**naleznete v tématu Spuštění testů částí pomocí [Průzkumníka testů](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Viz také

- [Zapsat testy částí pro C/C++](writing-unit-tests-for-c-cpp.md)
