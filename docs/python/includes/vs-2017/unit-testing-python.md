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
ms.openlocfilehash: 9843b47e38d5d33a25c455efe619dfcc033fb334
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933469"
---
## <a name="discover-and-view-tests"></a>Zjištění a zobrazení testů

Podle konvence sady Visual Studio identifikuje testy jako metody, jejichž jména začínají `test`. Pokud chcete zobrazit toto chování, postupujte takto:

1. Otevřít [projektu Pythonu](../../managing-python-projects-in-visual-studio.md) načten v sadě Visual Studio, klikněte pravým tlačítkem na projekt, vyberte **přidat** > **nová položka**a pak vyberte **Test jednotky Pythonu**  následovaný **přidat**.

1. Tato akce vytvoří *test1.py* souboru s kódem, který importuje standardní `unittest` modulu, je odvozena testovací třídy z `unittest.TestCase`a vyvolá `unittest.main()` přímo při spuštění skriptu:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Uložte soubor, pokud potřebné a pak otevřete **Průzkumník testů** s **testovací** > **Windows** > **Průzkumník testů**příkazu nabídky.

1. **Průzkumník testů** prohledává váš projekt pro testy a zobrazí je uvedeno dále. Dvojitým kliknutím test otevře jeho zdrojový soubor.

    ![Test Explorer test_A výchozí zobrazení](../../media/unit-test-A.png)

1. Jak budete přidávat další testy do projektu, můžete uspořádat zobrazení **Průzkumník testů** pomocí **Seskupit podle** nabídka na panelu nástrojů:

    ![Skupiny Průzkumníka testů pomocí nabídky panelu nástrojů](../../media/unit-test-group-menu.png)

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

Spustit ladění, nastavte počáteční zarážky v kódu a pak klikněte pravým tlačítkem na zkoušku (nebo výběr) v **Průzkumníka testů** a vyberte **ladit vybrané testy**. Visual Studio spustí ladicí program Pythonu, stejně jako pro kód aplikace.

![Ladění testu](../../media/unit-test-debugging.png)

Můžete také použít možnost **Analyzovat pokrytí kódu pro vybrané testy**. Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je testována](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Známé problémy

- Při spouštění, ladění, Visual Studio se zobrazí spuštění a zastavení ladění a spusťte znovu. Toto chování je očekávané.
- Při ladění více testů, každý z nich běží nezávisle na sobě, což přerušení relace ladění.
- Visual Studio přerušovaně nepodaří spustit test při ladění. Za normálních okolností pokusem o ladění znovu test proběhne úspěšně.
- Při ladění, je možné krok z testovacího do `unittest` implementace. Za normálních okolností dál běží na konci programu a zastaví ladění.
