---
title: Jak používat Boost.Test pro C++
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 65ee2d95d85c657057f7ef4494c19f8b5644513e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063244"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak používat Boost.Test pro C++ v sadě Visual Studio

V **Visual Studio 2017 verze 15.5** a později je testovací adaptér pro Boost.Test integrována do integrovaného vývojového prostředí sady Visual Studio jako součást sady **vývoj desktopových aplikací pomocí C++** pracovního vytížení.

![Testovací adaptér pro Boost.Test](media/cpp-boost-component.png)

Pokud nemáte k dispozici **vývoj desktopových aplikací pomocí C++** nainstalovaná, úloha open **instalační program sady Visual Studio** a vyberte **změnit**. Vyberte **vývoj desktopových aplikací pomocí C++** úloh, klikněte na tlačítko **změnit** tlačítko.

## <a name="install-boost"></a>Nainstalujte Boost

Vyžaduje Boost.Test [Boost](http://www.boost.org/)! Pokud nemáte Boost nainstalován, doporučujeme použít Správce balíčků Vcpkg.

1. Postupujte podle pokynů na adrese [Vcpkg: Správce balíčků jazyka C++ pro Windows](/cpp/vcpkg) instalace vcpkg (pokud ho nemáte).

1. Nainstalujte Boost.Test dynamické nebo statické knihovny:

    - Spustit **vcpkg nainstalovat boost test** instalace dynamická knihovna Boost.Test.

       -OR-

    - Spustit **vcpkg nainstalovat boost-test: x 86-windows-static** instalace se statickou knihovnou Boost.Test.

1. Spustit **vcpkg integrovat instalace** konfigurace sady Visual Studio s knihovnou a zahrnout cesty do Boost hlavičkové soubory a binární soubory.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Přidat šablonu položky (Visual Studio 2017 verze 15.6 a novější)

1. Chcete-li vytvořit *.cpp* souboru pro testy, klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a zvolte **přidat novou položku**.

   ![Šablony položek Boost.Test](media/boost_test_item_template.png)

1. Nový soubor obsahuje ukázkové testovací metodu. Sestavení projektu, aby umožňoval **Průzkumník testů** metodu zjišťování.

Šablona položky používá variantu single-header Boost.Test, ale můžete změnit #include cesta pro variantu samostatné knihovny. Další informace najdete v tématu [přidat direktiv](#add-include-directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Vytvoření testovacího projektu (Visual Studio 2017 verze 15.5)

V sadě Visual Studio 2017 verze 15.5 jsou k dispozici pro Boost.Test žádná předem nakonfigurované testovací projekt nebo šablony položek. Proto budete muset vytvořit a nakonfigurovat projekt konzolové aplikace pro uložení vašich testů.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení a zvolte **přidat** > **nový projekt**.

1. V levém podokně vyberte **Visual C++** > **Windows Desktop**a klikněte na tlačítko **Konzolová aplikace Windows** šablony.

1. Pojmenujte projekt a zvolte **OK**.

1. Odstranit `main` fungovat v *.cpp* souboru.

1. Pokud používáte verzi Boost.Test jedním záhlaví nebo dynamické knihovny, přejděte na [přidat direktiv](#add-include-directives). Pokud používáte verzi statické knihovny, budete muset provést některé další konfigurace:

   a. Chcete-li upravit soubor projektu, nejprve uvolněn. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a zvolte **uvolnit projekt**. Potom klikněte pravým tlačítkem na uzel projektu a zvolte **upravit < název\>.vcxproj**.

   b. Přidejte dva řádky **Globals** skupiny vlastností, jak je znázorněno zde:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Uložte a zavřete  *\*.vcxproj* souboru a pak znovu načtěte projekt.

   d. Chcete-li otevřít **stránky vlastností**, klikněte pravým tlačítkem na uzel projektu a zvolte **vlastnosti**.

   d. Rozbalte **C/C++** > **generování kódu**a pak vyberte **knihovny prostředí Runtime**. Vyberte **/MTD** pro statické běhovou ladicí knihovnou nebo **/MT** verze runtime statické knihovny.

   f. Rozbalte **Linkeru** > **systému**. Ověřte, že **subsystému** je nastavena na **konzoly**.

   g. Zvolte **OK** stránku vlastností zavřete.

## <a name="add-include-directives"></a>Přidání direktiv

1. V testu *.cpp* přidejte všechny potřebné `#include` direktivy zviditelnit typy a funkce vaší aplikace k testovacímu kódu. Program je obvykle nahoru o jednu úroveň v hierarchii složek. Pokud zadáte `#include "../"`, zobrazí se okno technologie IntelliSense a umožňuje vybrat úplná cesta k souboru hlaviček.

   ![Přidejte #include](media/cpp-gtest-includes.png)

   Můžete použít samostatné knihovně:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Nebo použijte verzi jedním záhlaví pomocí:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Poté definujte `BOOST_TEST_MODULE`.

V následujícím příkladu je dostatečná pro test zjistitelné v **Průzkumníka testů**:

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

## <a name="write-and-run-tests"></a>Psání a spouštění testů

Teď jste připravení psát a spouštět testy Boost test. Najdete v článku [dokumentaci ke knihovně Boost test](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html) informace o makra testu. Zobrazit [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) informace o zjišťování, spouštění a seskupení testů s použitím **Průzkumník testů**.

## <a name="see-also"></a>Viz také:

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
