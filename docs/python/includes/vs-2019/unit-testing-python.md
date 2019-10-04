---
title: Testování částí kódu v Pythonu
description: Nastavení testování jednotek pro kód Python v sadě Visual Studio plně využívá funkce Průzkumníka testů, které chcete zjišťovat, spouštějte a laďte testy.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933445"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Výběr testovacího rozhraní pro projekt v Pythonu

Visual Studio podporuje dvě testovací architektury pro Python, [UnitTest](https://docs.python.org/3/library/unittest.html) a [pytest](https://pytest.org/en/latest/) (k dispozici v aplikaci Visual Studio 2019 počínaje verzí 16,3). Ve výchozím nastavení není při vytváření projektu v jazyce Python vybrána žádná architektura. Chcete-li určit rozhraní, klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a vyberte možnost **vlastnosti** . Tím se otevře Návrhář projektu, který umožňuje konfigurovat testy prostřednictvím karty **test** . Na této kartě můžete vybrat testovací rozhraní, které chcete použít pro projekt. 

* Pro **UnitTest** Framework se kořenový adresář projektu používá pro zjišťování testů. Toto umístění, stejně jako textový vzor pro identifikaci testů, lze upravit na kartě **test** na hodnoty zadané uživatelem.
* Pro **pytest** Framework jsou možnosti testování, jako je například umístění testu a vzor názvů souborů, určeny pomocí standardního konfiguračního souboru pytest. ini. Další podrobnosti najdete v [referenční dokumentaci k pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Po uložení výběru a nastavení architektury se zjišťování testů Inicializuje v Průzkumníku testů. Pokud okno Průzkumník testů ještě není otevřené, přejděte na panel nástrojů a vyberte **test** > **Průzkumník testů**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurace testování pro Python bez projektu
Visual Studio umožňuje spustit a otestovat existující kód Pythonu bez projektu [otevřením složky](../../quickstart-05-python-visual-studio-open-folder.md) s kódem Pythonu. Za těchto okolností budete muset ke konfiguraci testování použít soubor **PythonSettings. JSON** . 
1. Pomocí možnosti **otevřít místní složku** otevřete svůj existující kód Pythonu. 

   ![Úvodní obrazovka sady Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. V okně Průzkumník řešení klikněte na ikonu **Zobrazit všechny soubory** , aby se zobrazily všechny soubory v aktuální složce.

   ![Tlačítko Zobrazit všechny soubory](../../media/unit-test-show-files.png)

1. V **místní složce nastavení** přejděte na soubor **PythonSettings. JSON** . Pokud tento soubor nevidíte ve složce **místních nastavení** , vytvořte ho ručně.
   
1. Přidejte pole **TestFramework** do souboru nastavení a nastavte ho na **pytest** nebo **UnitTest** v závislosti na testovacím rozhraní, které chcete použít.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Pokud v **UnitTest** Framework nejsou v souboru PythonSettings. JSON zadaná pole **UnitTestRootDirectory** a **UnitTestPattern** , přidají se a přiřadí se výchozí hodnoty "." a "test *. py" v uvedeném pořadí.

1. Pokud složka obsahuje **zdrojový** adresář, který je oddělený od složky, která obsahuje vaše testy, zadejte cestu ke složce **Src** pomocí pole **SearchPath** v souboru **PythonSettings. JSON** .

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Uložte změny do souboru PythonSettings. JSON pro zahájení zjišťování testů pro zadané rozhraní. 
   > [!Note]
   > Je-li okno Průzkumník testů již otevřeno, je **stisknuto klávesou CTRL** + **R, a** také spustí zjišťování.

## <a name="discover-and-view-tests"></a>Zjištění a zobrazení testů

Ve výchozím nastavení Visual Studio identifikuje **UnitTest** a **pytest** testy jako metody, jejichž názvy začínají na `test`. Chcete-li zobrazit zjišťování testů, postupujte následovně:

1. Otevřete [projekt Python](../../managing-python-projects-in-visual-studio.md).

1. Jakmile je projekt načten v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a na kartě **test** vlastností vyberte rozhraní **UnitTest** nebo **pytest** .
   > [!Note]
   > Pokud používáte pytest Framework, můžete zadat umístění testu a vzory názvů souborů pomocí standardního konfiguračního souboru pytest. ini. Ve výchozím nastavení se používá složka pracovního prostoru nebo projektu se vzorem `test_*py` a `*_test.py`. Další podrobnosti najdete v [referenční dokumentaci k pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Po výběru rozhraní klikněte znovu pravým tlačítkem na projekt a vyberte **přidat** > **novou položku**a pak vyberte možnost **test jednotek Pythonu** a potom **Přidat**.

1. Tato akce vytvoří soubor *test_1. py* s kódem, který importuje standardní modul `unittest`, odvodí testovací třídu z `unittest.TestCase` a vyvolá `unittest.main()`, pokud spouštíte skript přímo:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. V případě potřeby soubor uložte a pak spusťte **Průzkumníka testů** pomocí příkazu **test** >  test**Exploreru** .

1. **Průzkumník testů** prohledává váš projekt pro testy a zobrazí je uvedeno dále. Dvojitým kliknutím test otevře jeho zdrojový soubor.

    ![Test Explorer test_A výchozí zobrazení](../../media/unit-test-a-2.png) 

1. Při přidávání dalších testů do projektu můžete zobrazení uspořádat v **Průzkumníku testů** pomocí nabídky **Seskupit podle** na panelu nástrojů:

    ![Skupiny Průzkumníka testů pomocí nabídky panelu nástrojů](../../media/unit-test-group-menu-2.png) 

1. Můžete také zadat text v **hledání** pole k filtrování testů podle názvu.

Další informace o modulu `unittest` a zápis testů naleznete v [dokumentaci k python 2,7](https://docs.python.org/2/library/unittest.html) nebo v dokumentaci k [python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Spouštění testů

V **Průzkumník testů** testy můžete spustit v mnoha různými způsoby:

- **Spustit všechny** jasně spustí všechny testy zobrazených (v souladu s filtry).
- **Spustit** nabídka poskytuje příkazy ke spuštění testů selhalo, úspěch nebo nelze spustit jako se skupinou.
- Můžete vybrat jeden nebo více testů, klikněte pravým tlačítkem a vyberte **spustit vybrané testy**.

Spustit testy na pozadí a **Průzkumníka testů** aktualizuje stav každého testu při dokončení:

- Předávání testů ukazují zelené značky a doba trvání testu:

    ![test_A předaného stavu](../../media/unit-test-A-pass.png)

- Zobrazit neúspěšné testy červený křížek s **výstup** odkaz, který zobrazuje výstup na konzole a `unittest` výstup z testovacího běhu:

    ![Stav test_A se nezdařilo](../../media/unit-test-A-fail.png)

    ![test_A úspěšný z tohoto důvodu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Ladit testy

Vzhledem k tomu, že jednotkové testy jsou části kódu, podléhají stejným způsobem jako jakýkoli jiný kód chyby a někdy je nutné spustit v ladicí program. V ladicím programu můžete nastavit zarážky, zkontrolujte proměnné a krokovat kód. Visual Studio také poskytuje diagnostické nástroje pro testování částí.

> [!Note]
> Ve výchozím nastavení používá ladění testu použití ladicího programu ptvsd 4. Pokud místo toho chcete použít ptvsd 3, můžete vybrat možnost **použít starší verzi ladicího programu** pro **nástroje** > **Možnosti**–  > **Python** > **ladění**. 

Spustit ladění, nastavte počáteční zarážky v kódu a pak klikněte pravým tlačítkem na zkoušku (nebo výběr) v **Průzkumníka testů** a vyberte **ladit vybrané testy**. Visual Studio spustí ladicí program Pythonu, stejně jako pro kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít možnost **Analyzovat pokrytí kódu pro vybrané testy**. Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je testována](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
