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
ms.openlocfilehash: 9843b47e38d5d33a25c455efe619dfcc033fb334
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933469"
---
## <a name="discover-and-view-tests"></a>Zjišťování a zobrazení testů

Podle konvence Visual Studio identifikuje testy jako `test`metody, jejichž názvy začínají . Chcete-li toto chování zobrazit, postupujte takto:

1. Otevřete [projekt Pythonu](../../managing-python-projects-in-visual-studio.md) načtený ve Visual Studiu, klikněte pravým tlačítkem myši na projekt, vyberte **Přidat** > **novou položku**a pak vyberte Test částí **Pythonu** následovaný **addem**.

1. Tato akce vytvoří *soubor test1.py* s kódem, který importuje standardní `unittest` modul, odvodí testovací třídu z `unittest.TestCase`aplikace a vyvolá, `unittest.main()` pokud skript spustíte přímo:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. V případě potřeby soubor uložte a v případě potřeby otevřete **Průzkumníka testů** pomocí příkazu **nabídky Test** > **Průzkumník windows.** > **Test Explorer**

1. **Průzkumník testů** vyhledá v projektu testy a zobrazí je, jak je znázorněno níže. Poklepáním na test se otevře zdrojový soubor.

    ![Průzkumník testů zobrazující výchozí test_A](../../media/unit-test-A.png)

1. Při přidávání dalších testů do projektu můžete uspořádat zobrazení v **Průzkumníkovi testů** pomocí nabídky **Seskupit podle** na panelu nástrojů:

    ![Nabídka Panelu nástrojů Seskupí explorer u skupiny](../../media/unit-test-group-menu.png)

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

Chcete-li zahájit ladění, nastavte počáteční zarážku v kódu, potom klepněte pravým tlačítkem myši na test (nebo výběr) v **Průzkumníkovi testů** a vyberte **ladění vybraných testů**. Visual Studio spustí ladicí program Pythonu stejně jako pro kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít **analyzovat pokrytí kódu pro vybrané testy**. Další informace naleznete [v tématu Použití pokrytí kódu k určení, kolik kódu je testováno](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Známé problémy

- Při spuštění ladění visual studio se zobrazí spustit a zastavit ladění a potom začít znovu. Jde o očekávané chování.
- Při ladění více testů, každý z nich je spuštěn nezávisle, což přeruší relaci ladění.
- Visual Studio občas nepodaří spustit test při ladění. Za normálních okolností pokus o ladění testu znovu úspěšné.
- Při ladění je možné krok z testu do `unittest` implementace. Za normálních okolností další krok spustí na konec programu a zastaví ladění.
