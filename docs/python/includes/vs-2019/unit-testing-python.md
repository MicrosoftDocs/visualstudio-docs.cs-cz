---
title: Kód Pythonu pro testování částí
description: Nastavení testování částí pro kód Pythonu v aplikaci Visual Studio plně využívá funkce Průzkumníka testů pro zjišťování, spouštění a ladění testů.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6b611657db104a4b74e784df8925627ff41f3c33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535321"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Výběr testovacího rozhraní pro projekt v Pythonu

Visual Studio podporuje dvě testovací architektury pro Python, [UnitTest](https://docs.python.org/3/library/unittest.html) a [pytest](https://pytest.org/en/latest/) (k dispozici v aplikaci Visual Studio 2019 počínaje verzí 16,3). Ve výchozím nastavení není při vytváření projektu v jazyce Python vybrána žádná architektura. Chcete-li určit rozhraní, klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a vyberte možnost **vlastnosti** . Tím se otevře Návrhář projektu, který umožňuje konfigurovat testy prostřednictvím karty **test** . Na této kartě můžete vybrat testovací rozhraní, které chcete použít pro projekt. 

* Pro **UnitTest** Framework se kořenový adresář projektu používá pro zjišťování testů. Toto umístění, stejně jako textový vzor pro identifikaci testů, lze upravit na kartě **test** na hodnoty zadané uživatelem.
* Pro **pytest** Framework jsou možnosti testování, jako je například umístění testu a vzor názvů souborů, určeny pomocí standardního konfiguračního souboru pytest. ini. Další podrobnosti najdete v [referenční dokumentaci k pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Po uložení výběru a nastavení architektury se zjišťování testů Inicializuje v Průzkumníku testů. Pokud okno Průzkumník testů ještě není otevřené, přejděte na panel nástrojů a vyberte **test**  >  **Test Explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurace testování pro Python bez projektu
Visual Studio umožňuje spustit a otestovat existující kód Pythonu bez projektu [otevřením složky](../../quickstart-05-python-visual-studio-open-folder.md) s kódem Pythonu. Za těchto okolností budete muset pro konfiguraci testování použít **PythonSettings.js** pro soubor. 
1. Pomocí možnosti **otevřít místní složku** otevřete svůj existující kód Pythonu. 

   ![Úvodní obrazovka sady Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. V okně Průzkumník řešení klikněte na ikonu **Zobrazit všechny soubory** , aby se zobrazily všechny soubory v aktuální složce.

   ![Tlačítko Zobrazit všechny soubory](../../media/unit-test-show-files.png)

1. V souboru **místní složky nastavení** přejděte na **PythonSettings.js** . Pokud tento soubor nevidíte ve složce **místních nastavení** , vytvořte ho ručně.
   
1. Přidejte pole **TestFramework** do souboru nastavení a nastavte ho na **pytest** nebo **UnitTest** v závislosti na testovacím rozhraní, které chcete použít.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Pro **UnitTest** Framework, pokud nejsou pole **UnitTestRootDirectory** a **UnitTestPattern** v souboru zadány, jsou přidány a přiřazeny výchozí hodnoty "." a "test *. py" PythonSettings.jsv uvedeném pořadí.

1. Pokud složka obsahuje **zdrojový** adresář, který je oddělený od složky, která obsahuje vaše testy, zadejte cestu ke složce **Src** pomocí pole **SearchPath** v **PythonSettings.js** souboru.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Uložte změny do PythonSettings.jsv souboru pro zahájení zjišťování testů pro zadané rozhraní. 
   > [!Note]
   > Je-li okno Průzkumník testů **již otevřeno**  +  **,** spustí se také funkce zjišťování.

## <a name="discover-and-view-tests"></a>Zjišťování a zobrazení testů

Ve výchozím nastavení Visual Studio identifikuje **UnitTest** a **pytest** testy jako metody, jejichž názvy začínají na `test` . Chcete-li zobrazit zjišťování testů, postupujte následovně:

1. Otevřete [projekt Python](../../managing-python-projects-in-visual-studio.md).

1. Jakmile je projekt načten v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a na kartě **test** vlastností vyberte rozhraní **UnitTest** nebo **pytest** .
   > [!Note]
   > Pokud používáte pytest Framework, můžete zadat umístění testu a vzory názvů souborů pomocí standardního konfiguračního souboru pytest. ini. Ve výchozím nastavení se používá složka pracovního prostoru nebo projektu se vzorem `test_*py` a `*_test.py` . Další podrobnosti najdete v [referenční dokumentaci k pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Po výběru rozhraní klikněte znovu pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou položku**a pak vyberte **Test jednotky Pythonu** a potom klikněte na **Přidat**.

1. Tato akce vytvoří soubor *test_1. py* s kódem, který importuje standardní `unittest` modul, odvodí testovací třídu z `unittest.TestCase` a vyvolá, `unittest.main()` Pokud spouštíte skript přímo:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. V případě potřeby soubor uložte a pak otevřete **Průzkumníka testů** pomocí příkazu nabídky **test**  >  **Test Exploreru** .

1. **Průzkumník testů** vyhledá v projektu testy a zobrazí je, jak je znázorněno níže. Dvojím kliknutím na test se otevře jeho zdrojový soubor.

    ![Průzkumník testů zobrazující výchozí test_A](../../media/unit-test-a-2.png) 

1. Při přidávání dalších testů do projektu můžete zobrazení uspořádat v **Průzkumníku testů** pomocí nabídky **Seskupit podle** na panelu nástrojů:

    ![Průzkumník testuje skupinu Průzkumníka podle nabídky panelu nástrojů](../../media/unit-test-group-menu-2.png) 

1. Můžete také zadat text do **vyhledávacího** pole, chcete-li filtrovat testy podle názvu.

Další informace o `unittest` modulu a zápisu testů naleznete v [dokumentaci k pythonu 2,7](https://docs.python.org/2/library/unittest.html) nebo v [dokumentaci k Python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Spouštění testů

V **Průzkumníku testů** můžete spouštět testy různými způsoby:

- **Spustit všechny** jasně spuštěné testy (podléhající filtrům).
- Nabídka **Spustit** poskytuje příkazy pro spuštění neúspěšných, úspěšných nebo nespuštěných testů jako skupiny.
- Můžete vybrat jeden nebo více testů, kliknout pravým tlačítkem a vybrat možnost **Spustit vybrané testy**.

Testy spuštěné na pozadí a **Průzkumník testů** aktualizují stav každého testu při jeho dokončení:

- Průchody testy ukazují zelenou značku a dobu trvání spuštění testu:

    ![stav předaných test_A](../../media/unit-test-A-pass.png)

- Neúspěšné testy ukazují červené křížové propojení s odkazem na **výstup** , který zobrazuje výstup a `unittest` výstup konzoly z testovacího běhu:

    ![neúspěšný stav test_A](../../media/unit-test-A-fail.png)

    ![test_A se nezdařilo z důvodu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Ladit testy

Vzhledem k tomu, že testy jednotek jsou části kódu, podléhají chybám stejně jako jakýkoli jiný kód a občas je nutné spustit v ladicím programu. V ladicím programu můžete nastavit zarážky, kontrolovat proměnné a krokovat kód. Visual Studio také poskytuje diagnostické nástroje pro testování částí.

> [!Note]
> Ve výchozím nastavení používá test ladění pro Visual Studio 2017 ladicí program ptvsd 4 (verze 15,8 a novější) a debugpy pro Visual Studio 2019 (verze 16,5 a novější). Pokud místo toho chcete použít ptvsd 3, můžete vybrat možnost **použít starší verzi ladicího programu** pro **nástroje**s  >  **možnostmi**  >  ladění v**Pythonu**  >  **Debugging**. 

Chcete-li spustit ladění, nastavte počáteční zarážku v kódu, potom klikněte pravým tlačítkem na test (nebo na výběr) v **Průzkumníku testů** a vyberte možnost **ladit vybrané testy**. Visual Studio spustí ladicí program Pythonu jako kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít možnost **Analyzovat pokrytí kódu pro vybrané testy**. Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
