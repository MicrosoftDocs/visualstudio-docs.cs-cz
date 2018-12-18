---
title: Testování částí kódu v Pythonu
description: Nastavení testování jednotek pro kód Python v sadě Visual Studio plně využívá funkce Průzkumníka testů, které chcete zjišťovat, spouštějte a laďte testy.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 57076aa4bf86b8053a38e6b8af96b6006bbdfa0a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052527"
---
# <a name="set-up-unit-testing-for-python-code"></a>Nastavení testování jednotek pro kód v Pythonu

Testování částí jsou části kódu, které testují jiné jednotky kódu v aplikaci, obvykle izolované funkce, třídy a tak dále. Když aplikace úspěšně projde všemi jeho testy jednotek, můžete alespoň důvěřovat správnost její nízké úrovně funkčnosti.

Testy jednotek Python často používá k ověření scénáře při návrhu programu. Podpora Pythonu v sadě Visual Studio obsahuje zjišťování, spouštění a ladění testů jednotek v rámci vašeho vývojového procesu, aniž by bylo potřeba spustit samostatně.

Tento článek poskytuje stručný přehled testování funkce v sadě Visual Studio pomocí Pythonu. Další informace o testování obecně najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) na testování jednotek v Pythonu (2 miliony 31s). |

## <a name="discover-and-view-tests"></a>Zjištění a zobrazení testů

Podle konvence sady Visual Studio identifikuje testy jako metody, jejichž jména začínají `test`. Pokud chcete zobrazit toto chování, postupujte takto:

1. Otevřít [projektu Pythonu](managing-python-projects-in-visual-studio.md) načten v sadě Visual Studio, klikněte pravým tlačítkem na projekt, vyberte **přidat** > **nová položka**a pak vyberte **Test jednotky Pythonu**  následovaný **přidat**.

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

    ![Test Explorer test_A výchozí zobrazení](media/unit-test-A.png)

1. Jak budete přidávat další testy do projektu, můžete uspořádat zobrazení **Průzkumník testů** pomocí **Seskupit podle** nabídka na panelu nástrojů:

    ![Skupiny Průzkumníka testů pomocí nabídky panelu nástrojů](media/unit-test-group-menu.png)

1. Můžete také zadat text v **hledání** pole k filtrování testů podle názvu.

Další informace o `unittest` modulu a psaní testů, najdete v článku [dokumentace k Pythonu 2.7](https://docs.python.org/2/library/unittest.html) nebo [dokumentace pro Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Spouštění testů

V **Průzkumník testů** testy můžete spustit v mnoha různými způsoby:

- **Spustit všechny** jasně spustí všechny testy zobrazených (v souladu s filtry).
- **Spustit** nabídka poskytuje příkazy ke spuštění testů selhalo, úspěch nebo nelze spustit jako se skupinou.
- Můžete vybrat jeden nebo více testů, klikněte pravým tlačítkem a vyberte **spustit vybrané testy**.

Spustit testy na pozadí a **Průzkumníka testů** aktualizuje stav každého testu při dokončení:

- Předávání testů ukazují zelené značky a doba trvání testu:

    ![test_A předaného stavu](media/unit-test-A-pass.png)

- Zobrazit neúspěšné testy červený křížek s **výstup** odkaz, který zobrazuje výstup na konzole a `unittest` výstup z testovacího běhu:

    ![Stav test_A se nezdařilo](media/unit-test-A-fail.png)

    ![test_A úspěšný z tohoto důvodu](media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Ladit testy

Vzhledem k tomu, že jednotkové testy jsou části kódu, podléhají stejným způsobem jako jakýkoli jiný kód chyby a někdy je nutné spustit v ladicí program. V ladicím programu můžete nastavit zarážky, zkontrolujte proměnné a krokovat kód. Visual Studio také poskytuje diagnostické nástroje pro testování částí.

Spustit ladění, nastavte počáteční zarážky v kódu a pak klikněte pravým tlačítkem na zkoušku (nebo výběr) v **Průzkumníka testů** a vyberte **ladit vybrané testy**. Visual Studio spustí ladicí program Pythonu, stejně jako pro kód aplikace.

![Ladění testu](media/unit-test-debugging.png)

Můžete také použít **analyzovat pokrytí kódu pro vybrané testy** a **testovací profil** příkazů v závislosti na vaší verzi sady Visual Studio (najdete v článku [matice funkcí](overview-of-python-tools-for-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Známé problémy

- Při spouštění, ladění, Visual Studio se zobrazí spuštění a zastavení ladění a spusťte znovu. Toto chování je očekávané.
- Při ladění více testů, každý z nich běží nezávisle na sobě, což přerušení relace ladění.
- Visual Studio přerušovaně nepodaří spustit test při ladění. Za normálních okolností pokusem o ladění znovu test proběhne úspěšně.
- Při ladění, je možné krok z testovacího do `unittest` implementace. Za normálních okolností dál běží na konci programu a zastaví ladění.
