---
title: Kód Pythonu testu částí
description: Nastavení testování částí pro kód Pythonu v sadě Visual Studio plně využívá funkce Průzkumníka testů ke zjišťování, spouštění a ladění testů.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933445"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Výběr testovacího rámce pro projekt Pythonu

Visual Studio podporuje dvě testovací architektury pro Python, [unittest](https://docs.python.org/3/library/unittest.html) a [pytest](https://pytest.org/en/latest/) (k dispozici v Visual Studiu 2019 počínaje verzí 16.3). Ve výchozím nastavení není při vytváření projektu Pythonu vybrána žádná architektura. Chcete-li určit architekturu, klepněte pravým tlačítkem myši na název projektu v Průzkumníku řešení a vyberte možnost **Vlastnosti.** Tím se otevře návrhář projektu, který umožňuje konfigurovat testy prostřednictvím karty **Test.** Na této kartě můžete vybrat testovací rámec, který chcete použít pro váš projekt. 

* Pro rozhraní **unittest** kořenový adresář projektu se používá pro zjišťování testu. Toto umístění, stejně jako vzor textu pro identifikaci testů, lze upravit na kartě **Test** na hodnoty zadané uživatelem.
* Pro **pytest** framework jsou možnosti testování, jako je testovací umístění a vzory názvů souborů, určeny pomocí standardního konfiguračního souboru pytest .ini. Další podrobnosti naleznete v [referenční dokumentaci pytest.](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)

Po uložení výběru a nastavení architektury se zjišťování testů spustí v Průzkumníkovi testů. Pokud okno Průzkumníka testů ještě není otevřené, přejděte na panel nástrojů a vyberte **test** > **explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurace testování Pythonu bez projektu
Visual Studio umožňuje spustit a otestovat existující kód Pythonu bez projektu [otevřením složky s kódem Pythonu.](../../quickstart-05-python-visual-studio-open-folder.md) Za těchto okolností budete muset ke konfiguraci testování použít soubor **PythonSettings.json.** 
1. Otevřete existující kód Pythonu pomocí možnosti **Otevřít místní složku.** 

   ![Úvodní obrazovka sady Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. V okně Průzkumník řešení klepněte na ikonu **Zobrazit všechny soubory,** abyste zobrazili všechny soubory v aktuální složce.

   ![Tlačítko Zobrazit všechny soubory](../../media/unit-test-show-files.png)

1. Přejděte do souboru **PythonSettings.json** ve složce **Místní nastavení.** Pokud tento soubor nevidíte ve složce **Místní nastavení,** vytvořte jej ručně.
   
1. Přidejte pole **TestFramework** do souboru nastavení a nastavte jej **pytest** nebo **unittest** v závislosti na testování rozhraní, které chcete použít.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Pro **rozhraní unittest,** pokud pole **UnitTestRootDirectory** a **UnitTestPattern** nejsou zadány v souboru PythonSettings.json, jsou přidány a přiřazeny výchozí hodnoty "." a "test*.py".

1. Pokud složka obsahuje adresář **src,** který je oddělený od složky, která obsahuje testy, zadejte cestu ke složce **src** pomocí pole **SearchPaths** v souboru **PythonSettings.json.**

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Uložte změny do souboru PythonSettings.json a iniciujte zjišťování testů pro zadanou architekturu. 
   > [!Note]
   > Pokud je okno Průzkumníka testů již otevřené **ctrl** + **r,A** také aktivuje zjišťování.

## <a name="discover-and-view-tests"></a>Zjišťování a zobrazení testů

Ve výchozím nastavení Visual Studio identifikuje **testování unittest** a **pytest** jako metody, jejichž názvy začínají . `test` Chcete-li zobrazit zjišťování testů, postupujte takto:

1. Otevřete [projekt Pythonu](../../managing-python-projects-in-visual-studio.md).

1. Po načtení projektu v sadě Visual Studio klikněte pravým tlačítkem myši na projekt v Průzkumníku řešení a vyberte **rozhraní unittest** nebo **pytest** na kartě **Testování** vlastností.
   > [!Note]
   > Pokud používáte pytest framework, můžete určit testovací umístění a vzory názvů souborů pomocí standardního konfiguračního souboru pytest .ini. Ve výchozím nastavení se používá složka pracovního prostoru `test_*py` `*_test.py`nebo projektu se vzorem a . Další podrobnosti naleznete v [referenční dokumentaci pytest.](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)

1. Po výběru rozhraní znovu klepněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **novou položku**a pak vyberte Test částí **Pythonu** následovaný **addem**.

1. Tato akce vytvoří soubor *test_1.py* s kódem, který importuje standardní `unittest` modul, odvodí testovací třídu z `unittest.TestCase`aplikace a vyvolá, `unittest.main()` pokud skript spustíte přímo:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. V případě potřeby soubor uložte a **Test** > pak otevřete **Průzkumníka testů** pomocí příkazu nabídky**Průzkumník a test.**

1. **Průzkumník testů** vyhledá v projektu testy a zobrazí je, jak je znázorněno níže. Poklepáním na test se otevře zdrojový soubor.

    ![Průzkumník testů zobrazující výchozí test_A](../../media/unit-test-a-2.png) 

1. Při přidávání dalších testů do projektu můžete uspořádat zobrazení v **Průzkumníkovi testů** pomocí nabídky **Seskupit** podle na panelu nástrojů:

    ![Nabídka Panelu nástrojů Seskupí explorer u skupiny](../../media/unit-test-group-menu-2.png) 

1. Do pole **Hledat** můžete také zadat text a filtrovat testy podle názvu.

Další informace o `unittest` modulu a psaní testů naleznete v [dokumentaci k Pythonu 2.7](https://docs.python.org/2/library/unittest.html) nebo [v dokumentaci k Pythonu 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Spouštění testů

V **Průzkumníkovi testů** můžete spouštět testy různými způsoby:

- **Spustit vše** jasně spustí všechny zobrazené testy (s výhradou filtrů).
- Nabídka **Spustit** poskytuje příkazy pro spuštění neúspěšných, předaný nebo nespouštěné testy jako skupina.
- Můžete vybrat jeden nebo více testů, klepnout pravým tlačítkem myši a vybrat **možnost Spustit vybrané testy**.

Testy spustit na pozadí a **Průzkumník testů** aktualizuje stav každého testu, jak je dokončena:

- Absolvování testů ukazuje zelené klíště a čas, který trvá na spuštění testu:

    ![test_A předán status](../../media/unit-test-A-pass.png)

- Neúspěšné testy ukazují červený kříž s **odkazem Výstup,** který zobrazuje výstup konzoly a `unittest` výstup z testovacího běhu:

    ![test_A stav se nezdařilo.](../../media/unit-test-A-fail.png)

    ![test_A selhals rozumem](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Testy ladění

Vzhledem k tomu, že testy částí jsou části kódu, jsou předmětem chyb, stejně jako jakýkoli jiný kód a občas je třeba spustit v ladicím programu. V ladicím programu můžete nastavit zarážky, prozkoumat proměnné a krokovat kód. Visual Studio také poskytuje diagnostické nástroje pro testování částí.

> [!Note]
> Ve výchozím nastavení používá ladění testu ladicí program PTVSD 4. Pokud chcete místo toho použít ptvsd 3, můžete vybrat možnost **Použít starší debugger** v**možnosti** >  **nástroje** > **Python** > **ladění**. 

Chcete-li zahájit ladění, nastavte počáteční zarážku v kódu, potom klepněte pravým tlačítkem myši na test (nebo výběr) v **Průzkumníkovi testů** a vyberte **ladění vybraných testů**. Visual Studio spustí ladicí program Pythonu stejně jako pro kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít **analyzovat pokrytí kódu pro vybrané testy**. Další informace naleznete [v tématu Použití pokrytí kódu k určení, kolik kódu je testováno](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
