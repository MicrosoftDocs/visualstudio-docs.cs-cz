---
title: Jak používat zvýšení. test proC++
description: Použijte zvýšení. test k vytvoření testování částí v aplikaci Visual Studio.
ms.date: 05/06/2019
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 966983fa15b60db33f11645b25561a74ad5fadbe
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983437"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak používat zvýšení. test pro C++ v aplikaci Visual Studio

V aplikaci Visual Studio 2017 a novějších se testovací adaptér pro zvýšení zátěže integruje do integrovaného vývojového prostředí (IDE) sady Visual Studio jako součást **vývoje plochy s C++**  úlohou.

![Testovací adaptér pro zvýšení. test](media/cpp-boost-component.png)

Pokud nemáte nainstalovanou úlohu **vývoj C++ desktopových** aplikací, otevřete **instalační program pro Visual Studio**. Vyberte **desktopový vývoj s C++**  úlohou a pak klikněte na tlačítko **Upravit** .

## <a name="install-boost"></a>Zesílení instalace

Zvýšení. test vyžaduje [zvýšení](https://www.boost.org/)! Pokud nemáte nainstalovanou posílení, doporučujeme použít Správce balíčků Vcpkg.

1. Postupujte podle pokynů na adrese [Vcpkg: C++ správce balíčků pro Windows](/cpp/vcpkg) , který nainstaluje Vcpkg (pokud ho ještě nemáte).

1. Nainstalujte dynamickou nebo statickou knihovnu s přízvýšením. test:

    - Spusťte příkaz pro **zvýšení a testování vcpkg instalace** a nainstalujte dynamickou knihovnu pro zvýšení. testování.

       Ani

    - Spusťte příkaz **vcpkg Install dis-test: x86-Windows-static** pro instalaci statické knihovny pro zvýšení. testování.

1. Spusťte **integraci vcpkg Integration** pro konfiguraci sady Visual Studio s knihovnou a přidejte cesty k hlavičkám a binárním souborům pro zvýšení úrovně.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Přidat šablonu položky (Visual Studio 2017 verze 15,6 a novější)

1. Chcete-li vytvořit soubor *. cpp* pro testy, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **Přidat novou položku**.

   ![Zvýšení šablony testovací položky](media/boost_test_item_template.png)

1. Nový soubor obsahuje ukázkovou testovací metodu. Sestavte projekt, aby bylo možné zjistit metodu v **Průzkumníku testů** .

Šablona položky používá variantu s jednou hlavičkou zvýšení. test, ale můžete upravit #include cestu pro použití proměnné variant samostatné knihovny. Další informace najdete v tématu [Přidání direktiv include](#add-include-directives).

## <a name="create-a-test-project"></a>Vytvoření testovacího projektu

V aplikaci Visual Studio 2017 verze 15,5 nejsou k dispozici žádné předem nakonfigurované testovací projekty ani šablony položek pro zvýšení. test. Proto je nutné vytvořit a nakonfigurovat projekt konzolové aplikace pro uložení testů.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a vyberte **Přidat** > **Nový projekt**.

1. V levém podokně vyberte **Visual C++**  > **Desktop Windows**a pak zvolte šablonu **Konzolová aplikace pro Windows** .

1. Zadejte název projektu a klikněte na **tlačítko OK**.

1. Odstraňte funkci `main` v souboru *. cpp* .

1. Pokud používáte verzi s jedním hlavičkou nebo dynamickou knihovnou, použijte příkaz [Přidat direktivy include](#add-include-directives). Pokud používáte statickou verzi knihovny, musíte provést nějakou další konfiguraci:

   a. Chcete-li upravit soubor projektu, nejprve ho uvolněte. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **Uvolnit projekt**. Poté klikněte pravým tlačítkem myši na uzel projektu a zvolte možnost **upravit < název\>. vcxproj**.

   b. Přidejte dva řádky do skupiny vlastností **Globals** , jak je znázorněno zde:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   r. Uložte a zavřete soubor *\*. vcxproj* a pak znovu načtěte projekt.

   trojrozměrné. Chcete-li otevřít **stránky vlastností**, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.

   trojrozměrné. Rozbalte položku **CC++ /**  > **generování kódu**a pak vyberte **Knihovna prostředí runtime**. Vyberte **/MTD** pro ladění knihovny statických runtime nebo **/Mt** pro vydanou verzi statického modulu runtime.

   FJ. Rozbalte **Linker** > **systém**. Ověřte, zda je **podsystém** nastaven na hodnotu **Konzola**.

   věcn. Kliknutím na **tlačítko OK** zavřete stránky vlastností.

## <a name="add-include-directives"></a>Přidat direktivy include

1. V souboru Test *. cpp* přidejte všechny potřebné `#include` direktivy, aby byly typy a funkce programu viditelné pro testovací kód. Obvykle je program o jednu úroveň v hierarchii složek. Pokud zadáte `#include "../"`, zobrazí se okno technologie IntelliSense, které umožňuje vybrat úplnou cestu k souboru hlaviček.

   ![Přidat direktivy #include](media/cpp-gtest-includes.png)

   Samostatnou knihovnu můžete použít k těmto akcím:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Nebo použijte jednu hlavičkovou verzi s:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Pak definujte `BOOST_TEST_MODULE`.

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

## <a name="see-also"></a>Viz také:

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
