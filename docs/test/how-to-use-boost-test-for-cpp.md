---
title: Jak používat Boost.Test pro C++
description: Použijte zvýšení. test k vytvoření testování částí v aplikaci Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922912"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak používat Boost.Test pro C++ v sadě Visual Studio

V aplikaci Visual Studio 2017 a novějších se testovací adaptér pro zvýšení a testování integruje do integrovaného vývojového prostředí (IDE) sady Visual Studio. Je to součást **vývoje plochy s C++**  úlohou.

![Testovací adaptér pro Boost.Test](media/cpp-boost-component.png)

Pokud nemáte nainstalovanou úlohu **vývoj C++ desktopových** aplikací, otevřete **instalační program pro Visual Studio**. Vyberte **vývoj desktopových aplikací pomocí C++** úloh, klikněte na tlačítko **změnit** tlačítko.

## <a name="install-boost"></a>Nainstalujte Boost

Vyžaduje Boost.Test [Boost](https://www.boost.org/)! Pokud nemáte nainstalovanou posílení, doporučujeme použít Správce balíčků Vcpkg.

1. Postupujte podle pokynů na adrese [Vcpkg: Správce balíčků jazyka C++ pro Windows](/cpp/vcpkg) instalace vcpkg (pokud ho nemáte).

1. Nainstalujte Boost.Test dynamické nebo statické knihovny:

    - Spusťte `vcpkg install boost-test` pro instalaci dynamické knihovny pro zvýšení. testování.

       -OR-

    - Spusťte `vcpkg install boost-test:x86-windows-static` pro instalaci statické knihovny pro zvýšení. testování.

1. Spusťte `vcpkg integrate install` pro konfiguraci sady Visual Studio s knihovnou a zahrnutí cest k hlavičkám a binárním souborům pro zvýšení úrovně.

Můžete si vybrat, jak nakonfigurovat testy v rámci řešení v sadě Visual Studio: můžete do testovaného projektu zahrnout testovací kód, nebo můžete vytvořit samostatný testovací projekt pro vaše testy. Obě možnosti mají své výhody i nevýhody.

## <a name="add-tests-inside-your-project"></a>Přidat testy do projektu

V aplikaci Visual Studio 2017 verze 15,6 a novější můžete přidat šablonu položky pro testy do projektu. Testy i váš kód jsou aktivní ve stejném projektu. Budete muset vytvořit samostatnou konfiguraci sestavení pro vygenerování testovacího sestavení. A, budete muset zachovávat testy z buildů pro ladění a vydaných verzí.

V sadě Visual Studio 2017 verze 15.5 jsou k dispozici pro Boost.Test žádná předem nakonfigurované testovací projekt nebo šablony položek. Použijte pokyny k vytvoření a konfiguraci samostatného testovacího projektu.

### <a name="create-a-boosttest-item"></a>Vytvořit zvýšení testovací položky

1. Chcete-li vytvořit soubor *. cpp* pro testy, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalované** > **Visual C++**  > **test**. Vyberte **zvýšit. test**a pak zvolte **Přidat** a přidejte do projektu *test. cpp* .

   ![Šablony položek Boost.Test](media/boost_test_item_template.png)

Nový soubor *test. cpp* obsahuje ukázkovou testovací metodu. Do tohoto souboru můžete zahrnout vlastní hlavičkové soubory a napsat testy pro vaši aplikaci.

Testovací soubor také používá makra k definování nové rutiny `main` pro konfigurace testu. Pokud projekt sestavíte nyní, zobrazí se chyba LINKERŮ LNK2005, například "_main již byla definována v Main. obj".

### <a name="create-and-update-build-configurations"></a>Vytvoření a aktualizace konfigurací sestavení

1. Chcete-li vytvořit konfiguraci testu, v řádku nabídek vyberte možnost **sestavit** > **Configuration Manager**. V dialogovém okně **Configuration Manager** otevřete rozevírací nabídku v části **Konfigurace aktivního řešení** a vyberte možnost **Nový**. V dialogovém okně **Nová konfigurace řešení** zadejte název, například "Debug UnitTests". V části **Kopírovat nastavení** vyberte **ladění**a pak zvolte **OK**.

1. Vylučte testovací kód z vašich konfigurací ladění a vydání: v **Průzkumník řešení**klikněte pravým tlačítkem na test. cpp a vyberte **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** možnost **všechny konfigurace** . Vyberte **Vlastnosti konfigurace** > **Obecné** a otevřete rozevírací seznam pro **vyloučení z vlastnosti Build** . Vyberte **Ano**a pak změny uložte kliknutím na **použít** .

1. Chcete-li zahrnout kód testu do konfigurace UnitTests ladění, v dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** položku **ladit UnitTests** . Ve vlastnosti **vyloučeno ze sestavení** vyberte **ne** a pak změny uložte kliknutím na **tlačítko OK** .

1. Vylučte z konfigurace UnitTests pro ladění hlavní kód. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor, který obsahuje vaši funkci `main` a vyberte **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** možnost **ladění UnitTests** . Vyberte **Vlastnosti konfigurace** > **Obecné** a otevřete rozevírací seznam pro **vyloučení z vlastnosti Build** . Pokud chcete změny uložit, vyberte **Ano**a pak zvolte **OK** .

1. Nastavte konfiguraci řešení tak, aby **UnitTests ladit**, a pak Sestavte projekt, aby bylo možné zjistit metodu v **Průzkumníku testů** .

Dokud název konfigurace, který vytvoříte, začíná slovy "debug" nebo "Release", odpovídající zvýšení. knihovny testů se vystaví automaticky.

Šablona položky používá variantu single-header Boost.Test, ale můžete změnit #include cesta pro variantu samostatné knihovny. Další informace najdete v tématu [přidat direktiv](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

V mnoha případech je snazší použít samostatný projekt pro testy. Pro váš projekt nebudete muset vytvořit speciální konfiguraci testu. Nebo vylučte testovací soubory z sestavení pro ladění a vydání.

### <a name="to-create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení a zvolte **přidat** > **nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte možnost **C++** , **Windows**a **Konzola** v rozevíracích seznamech filtru. Vyberte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

1. Zadejte název projektu a klikněte na **vytvořit**.

1. Odstranit `main` fungovat v *.cpp* souboru.

1. Pokud používáte verzi s jedním hlavičkou nebo dynamickou knihovnou, použijte příkaz [Přidat direktivy include](#add-include-directives). Pokud používáte statickou verzi knihovny, musíte provést nějakou další konfiguraci:

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

   e. Rozbalte **C/C++**  > **generování kódu**a pak vyberte **knihovny prostředí Runtime**. Vyberte **/MTD** pro statické běhovou ladicí knihovnou nebo **/MT** verze runtime statické knihovny.

   f. Rozbalte **Linkeru** > **systému**. Ověřte, zda je **podsystém** nastaven na hodnotu **Console**.

   g. Zvolte **OK** stránku vlastností zavřete.

## <a name="add-include-directives"></a>Přidání direktiv

1. V testu *.cpp* přidejte všechny potřebné `#include` direktivy zviditelnit typy a funkce vaší aplikace k testovacímu kódu. Pokud používáte samostatný testovací projekt, je obvykle program na úrovni stejné úrovně v hierarchii složek. Pokud zadáte `#include "../"`, zobrazí se okno technologie IntelliSense a umožňuje vybrat úplná cesta k souboru hlaviček.

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

Teď jste připravení psát a spouštět testy Boost test. Najdete v článku [dokumentaci ke knihovně Boost test](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) informace o makra testu. Zobrazit [spouštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) informace o zjišťování, spouštění a seskupení testů s použitím **Průzkumník testů**.

## <a name="see-also"></a>Viz také:

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
