---
title: Jak používat zvýšení. test pro C++
description: Použijte zvýšení. test k vytvoření testování částí v aplikaci Visual Studio.
ms.date: 01/29/2020
ms.topic: how-to
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34c593469a586d1314c7ee52f3aeb3ab6faf334c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287269"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak používat zvýšení. test pro C++ v aplikaci Visual Studio

V aplikaci Visual Studio 2017 a novějších se testovací adaptér pro zvýšení a testování integruje do integrovaného vývojového prostředí (IDE) sady Visual Studio. Je to součást **vývoje desktopových aplikací pomocí C++** .

![Testovací adaptér pro zvýšení. test](media/cpp-boost-component.png)

Pokud nemáte nainstalovanou úlohu **vývoj desktopových aplikací s C++** , otevřete **instalační program pro Visual Studio**. Vyberte úlohu **vývoj pro stolní počítače pomocí C++** a pak klikněte na tlačítko **Upravit** .

## <a name="install-boost"></a>Nainstalovat Boost

Zvýšení. test vyžaduje [zvýšení](https://www.boost.org/)! Pokud nemáte nainstalovanou posílení, doporučujeme použít Správce balíčků Vcpkg.

1. Postupujte podle pokynů na adrese [Vcpkg: Správce balíčků C++ pro Windows](/cpp/vcpkg) k instalaci Vcpkg (pokud ho ještě nemáte).

1. Nainstalujte dynamickou nebo statickou knihovnu s přízvýšením. test:

    - Spusťte `vcpkg install boost-test` pro instalaci dynamické knihovny pro zvýšení. testování.

       - nebo -

    - Spusťte `vcpkg install boost-test:x86-windows-static` pro instalaci statické knihovny pro zvýšení. testování.

1. Spusťte `vcpkg integrate install` pro konfiguraci sady Visual Studio pomocí knihovny a zahrňte cesty k hlavičkám a binárním souborům pro zvýšení úrovně.

Můžete si vybrat, jak nakonfigurovat testy v rámci řešení v sadě Visual Studio: můžete do testovaného projektu zahrnout testovací kód, nebo můžete vytvořit samostatný testovací projekt pro vaše testy. Obě možnosti mají své výhody i nevýhody.

## <a name="add-tests-inside-your-project"></a>Přidat testy do projektu

V aplikaci Visual Studio 2017 verze 15,6 a novější můžete přidat šablonu položky pro testy do projektu. Testy i váš kód jsou aktivní ve stejném projektu. Budete muset vytvořit samostatnou konfiguraci sestavení pro vygenerování testovacího sestavení. A, budete muset zachovávat testy z buildů pro ladění a vydaných verzí.

V aplikaci Visual Studio 2017 verze 15,5 nejsou k dispozici žádné předem nakonfigurované testovací projekty ani šablony položek pro zvýšení. test. Použijte pokyny k vytvoření a konfiguraci samostatného testovacího projektu.

### <a name="create-a-boosttest-item"></a>Vytvořit zvýšení testovací položky

1. Chcete-li vytvořit soubor *. cpp* pro testy, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **Přidat**  >  **novou položku**.

1. V dialogovém okně **Přidat novou položku** rozbalte položku **nainstalované**  >  **Visual C++**  >  **test**. Vyberte **zvýšit. test**a pak zvolte **Přidat** a přidejte do projektu *test. cpp* .

   ![Zvýšení šablony testovací položky](media/boost_test_item_template.png)

Nový soubor *test. cpp* obsahuje ukázkovou testovací metodu. Do tohoto souboru můžete zahrnout vlastní hlavičkové soubory a napsat testy pro vaši aplikaci.

Testovací soubor také používá makra k definování nové `main` rutiny pro konfigurace testu. Pokud projekt sestavíte nyní, zobrazí se chyba LINKERŮ LNK2005, například "_main již byla definována v Main. obj".

### <a name="create-and-update-build-configurations"></a>Vytvoření a aktualizace konfigurací sestavení

1. Chcete-li vytvořit konfiguraci testu, v řádku nabídek vyberte možnost **sestavit**  >  **Configuration Manager**. V dialogovém okně **Configuration Manager** otevřete rozevírací nabídku v části **Konfigurace aktivního řešení** a vyberte možnost **Nový**. V dialogovém okně **Nová konfigurace řešení** zadejte název, například "Debug UnitTests". V části **Kopírovat nastavení** vyberte **ladění**a pak zvolte **OK**.

1. Vylučte testovací kód z vašich konfigurací ladění a vydání: v **Průzkumník řešení**klikněte pravým tlačítkem na test. cpp a vyberte **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** možnost **všechny konfigurace** . Vyberte **Vlastnosti konfigurace**  >  **Obecné** a otevřete rozevírací seznam pro **vyloučení z vlastnosti Build** . Vyberte **Ano**a pak změny uložte kliknutím na **použít** .

1. Chcete-li zahrnout kód testu do konfigurace UnitTests ladění, v dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** položku **ladit UnitTests** . Ve vlastnosti **vyloučeno ze sestavení** vyberte **ne** a pak změny uložte kliknutím na **tlačítko OK** .

1. Vylučte z konfigurace UnitTests pro ladění hlavní kód. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor, který obsahuje vaši `main` funkci, a vyberte **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte v rozevíracím seznamu **Konfigurace** možnost **ladění UnitTests** . Vyberte **Vlastnosti konfigurace**  >  **Obecné** a otevřete rozevírací seznam pro **vyloučení z vlastnosti Build** . Pokud chcete změny uložit, vyberte **Ano**a pak zvolte **OK** .

1. Nastavte konfiguraci řešení tak, aby **UnitTests ladit**, a pak Sestavte projekt, aby bylo možné zjistit metodu v **Průzkumníku testů** .

Dokud název konfigurace, který vytvoříte, začíná slovy "debug" nebo "Release", odpovídající zvýšení. knihovny testů se vystaví automaticky.

Šablona položky používá variantu s jednou hlavičkou zvýšení. test, ale můžete upravit #include cestu pro použití proměnné variant samostatné knihovny. Další informace najdete v tématu [Přidání direktiv include](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

V mnoha případech je snazší použít samostatný projekt pro testy. Pro váš projekt nebudete muset vytvořit speciální konfiguraci testu. Nebo vylučte testovací soubory z sestavení pro ladění a vydání.

### <a name="to-create-a-separate-test-project"></a>Vytvoření samostatného testovacího projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte možnost **Přidat**  >  **Nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte v rozevíracích seznamech filtru možnost **C++**, **Windows**a **Konzola** . Vyberte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

1. Zadejte název projektu a klikněte na **vytvořit**.

1. Odstraňte `main` funkci v souboru *. cpp* .

1. Pokud používáte verzi s jedním hlavičkou nebo dynamickou knihovnou, použijte příkaz [Přidat direktivy include](#add-include-directives). Pokud používáte statickou verzi knihovny, musíte provést nějakou další konfiguraci:

   a. Chcete-li upravit soubor projektu, nejprve ho uvolněte. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **Uvolnit projekt**. Poté klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **upravit <název \> . vcxproj**.

   b. Přidejte dva řádky do skupiny vlastností **Globals** , jak je znázorněno zde:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Uložte a zavřete soubor * \* . vcxproj* a pak znovu načtěte projekt.

   d. Chcete-li otevřít **stránky vlastností**, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.

   e. Rozbalte položku generování kódu **jazyka C/C++**  >  **Code Generation**a pak vyberte možnost **Knihovna prostředí runtime**. Vyberte **/MTD** pro ladění knihovny statických runtime nebo **/Mt** pro vydanou verzi statického modulu runtime.

   f. Rozbalte položku systém **linkeru**  >  **System**. Ověřte, zda je **podsystém** nastaven na hodnotu **Console**.

   například Kliknutím na **tlačítko OK** zavřete stránky vlastností.

## <a name="add-include-directives"></a>Přidat direktivy include

1. V souboru Test *. cpp* přidejte všechny potřebné `#include` direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Pokud používáte samostatný testovací projekt, je obvykle program na úrovni stejné úrovně v hierarchii složek. Pokud zadáte `#include "../"` , zobrazí se okno technologie IntelliSense, které umožňuje vybrat úplnou cestu k souboru hlaviček.

   ![Přidat direktivy #include](media/cpp-gtest-includes.png)

   Samostatnou knihovnu můžete použít k těmto akcím:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Nebo použijte jednu hlavičkovou verzi s:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Pak definujte `BOOST_TEST_MODULE` .

Následující příklad je dostačující pro to, aby byl test zjistitelný v **Průzkumníku testů**:

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

## <a name="write-and-run-tests"></a>Zápis a spouštění testů

Nyní jste připraveni napsat a spustit testy zvýšení úrovně. Informace o makrech testu naleznete v [dokumentaci ke knihovně pro zvýšení úrovně](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) . Informace o zjišťování, spouštění a seskupování testů pomocí **Průzkumníka testů**naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) .

## <a name="see-also"></a>Viz také

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
