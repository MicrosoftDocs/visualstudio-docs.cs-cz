---
title: Kód Pythonu pro testování částí
description: Nastavení testování částí pro kód Pythonu v aplikaci Visual Studio plně využívá funkce Průzkumníka testů pro zjišťování, spouštění a ladění testů.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 612d4bd7d66add8c3fe7c45e8f03ca3531b0b4c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920664"
---
## <a name="discover-and-view-tests"></a>Zjišťování a zobrazení testů

Podle konvence Visual Studio identifikuje testy jako metody, jejichž názvy začínají na `test` . Chcete-li toto chování zobrazit, postupujte následovně:

1. Otevřete [projekt Python](../../managing-python-projects-in-visual-studio.md) načtený v aplikaci Visual Studio, klikněte pravým tlačítkem na projekt, vyberte možnost **Přidat**  >  **novou položku** a pak vyberte možnost **Test jednotky Pythonu** a potom klikněte na **Přidat**.

1. Tato akce vytvoří soubor *test1.py* s kódem, který importuje standardní `unittest` modul, odvodí testovací třídu z `unittest.TestCase` a vyvolá, `unittest.main()` Pokud spouštíte skript přímo:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. V případě potřeby soubor uložte a pak spusťte **Průzkumníka testů** pomocí příkazu **test** Průzkumníka testů  >  **systému Windows**  >   .

1. **Průzkumník testů** vyhledá v projektu testy a zobrazí je, jak je znázorněno níže. Dvojím kliknutím na test se otevře jeho zdrojový soubor.

    ![Průzkumník testů zobrazující výchozí test_A](../../media/unit-test-A.png)

1. Při přidávání dalších testů do projektu můžete zobrazení uspořádat v **Průzkumníku testů** pomocí nabídky **Seskupit podle** na panelu nástrojů:

    ![Průzkumník testuje skupinu Průzkumníka podle nabídky panelu nástrojů](../../media/unit-test-group-menu.png)

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

Chcete-li spustit ladění, nastavte počáteční zarážku v kódu, potom klikněte pravým tlačítkem na test (nebo na výběr) v **Průzkumníku testů** a vyberte možnost **ladit vybrané testy**. Visual Studio spustí ladicí program Pythonu jako kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít možnost **Analyzovat pokrytí kódu pro vybrané testy**. Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Známé problémy

- Při spuštění ladění se Visual Studio zdá spustit a zastavit ladění a znovu spustit. Jde o očekávané chování.
- Při ladění více testů se každý z nich spouští nezávisle, což přerušuje relaci ladění.
- V aplikaci Visual Studio se občas nepovede spustit test při ladění. Normální pokus o ladění testu proběhne úspěšně.
- Při ladění je možné krokovat z testu do `unittest` implementace. V normálním případě se další krok spustí na konci programu a zastaví ladění.
