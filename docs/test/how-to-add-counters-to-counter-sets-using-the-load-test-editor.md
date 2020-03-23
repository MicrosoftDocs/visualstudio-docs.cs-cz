---
title: Přidat čítače do sad čítačů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b83d9c3624a4a268bfeba8a02b224fb9813ad7d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594327"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Postup: Přidání čítačů k balíčkům čítačů pomocí Editoru zátěžového testu

Při vytváření zátěžového testu pomocí **Průvodce zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Další informace naleznete [v tématu Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, jak používat vzdálené počítače v zátěžovém testu, naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Čítače spravujete v **Editoru zátěžových testů**. Sady čítačů, které jsou již přidány do testu jsou viditelné v uzlu **sady čítačů** zátěžového testu. Po vytvoření zátěžového testu můžete do existujících sad čítačů přidat nové čítače.

## <a name="to-add-counters-to-a-counter-set"></a>Přidání čítačů do sady čítačů

1. Otevřete zátěžový test.

2. Rozbalte uzel **sady čítačů.** Jsou zobrazeny všechny sady čítačů, které byly přidány do zátěžového testu.

    > [!NOTE]
    > Strom hierarchie zátěžového testu také obsahuje uzel **Spustit nastavení.** Tento uzel obsahuje uzel **Mapování sad čítačů,** který zobrazuje všechny počítače a sady čítačů mapované na tyto počítače.

3. Klepněte pravým tlačítkem myši na existující sadu čítačů a pak zvolte **Přidat čítače**.

     Zobrazí se dialogové okno **Vyskladnění čítačů výkonu.**

4. Do rozevíracího pole **Seseznampočítače** zadejte název počítače, na který chcete mapovat. Případně vyberte jeden z počítačů v rozevíracím seznamu.

    > [!NOTE]
    > Vzhledem k tomu, že sady čítačů musí být před shromažďováním dat o výkonu mapovány na počítač, je nutné zadat počítač, ve kterém mají být shromažďována data o výkonu.

5. Vyberte **kategorii Výkon,** chcete-li filtrovat kategorie čítačů dat výkonu. Zobrazí se dva sloupce dat, ze kterých chcete vybrat čítače výkonu.

    > [!NOTE]
    > Některé kategorie čítačů budou vyžadovat, abyste také vybrali instanci. Pokud například vyberete čítač SQL, musíte vybrat instanci SQL, protože v cílovém počítači může být nainstalována více než jedna instance sql.

6. Vyberte čítač a instanci, které chcete přidat do vlastní sady čítačů.

     \-nebo -

     Vyberte přepínací tlačítko **Všechny čítače** a vyberte všechny dostupné čítače.

7. Vyberte **OK**.

    > [!NOTE]
    > Je také možné přidat čítače do sady čítačů výběrem existujícího čítače nebo kategorie čítače, výběrem kopie a vložením do jiného uzlu sady čítačů. Další čítače, které jsou zkopírovány, ale nejsou potřeba, lze odstranit.

## <a name="see-also"></a>Viz také

- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
