---
title: Přidání čítačů do sad čítačů pro zátěžové testování
description: Při vytváření zátěžového testu pomocí Průvodce zátěžovým testem přidáte počáteční sadu čítačů. Naučte se přidávat čítače pomocí Editor zátěžového testu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ddfdf00a366c18524d2a666a74c7b7a164400402
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966965"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Postupy: Přidání čítačů do sad čítačů pomocí Editor zátěžového testu

Při vytváření zátěžového testu pomocí **Průvodce zátěžovým testem** přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Další informace naleznete v tématu [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o použití vzdálených počítačů v rámci zátěžového testu naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Čítače můžete spravovat v **Editor zátěžového testu**. Sady čítačů, které jsou již přidány do testu, jsou zobrazeny v uzlu **sady čítačů** zátěžového testu. Po vytvoření zátěžového testu můžete přidat nové čítače do existujících sad čítačů.

## <a name="to-add-counters-to-a-counter-set"></a>Přidání čítačů do sady čítačů

1. Otevřete zátěžový test.

2. Rozbalte uzel **sady čítačů** . Jsou zobrazeny všechny sady čítačů, které byly přidány do zátěžového testu.

    > [!NOTE]
    > Strom hierarchie zátěžového testu také obsahuje uzel **nastavení spuštění** . Tento uzel obsahuje uzel **mapování sady čítačů** , ve kterém se zobrazují všechny počítače a sady čítačů, které jsou namapované na tyto počítače.

3. Klikněte pravým tlačítkem na existující sadu čítačů a pak zvolte **Přidat čítače**.

     Zobrazí se dialogové okno **Vybrat čítače výkonu** .

4. V rozevíracím seznamu **počítač** zadejte název počítače, na který chcete namapovat. Případně vyberte jeden z počítačů v rozevíracím seznamu.

    > [!NOTE]
    > Vzhledem k tomu, že sady čítačů musí být namapovány na počítač před tím, než se shromažďují údaje o výkonu, je nutné zadat počítač, ke kterému chcete shromažďovat údaje o výkonu.

5. Vyberte **kategorii výkonu** pro filtrování kategorií čítačů dat výkonu. Zobrazí se dva sloupce dat, ze kterých se mají vybírat čítače výkonu.

    > [!NOTE]
    > Některé kategorie čítače budou vyžadovat, abyste vybrali také instanci. Pokud například vyberete čítač SQL, je nutné vybrat instanci SQL, protože v cílovém počítači může být nainstalována více než jedna instance serveru SQL.

6. Vyberte čítač a instanci, které chcete přidat do vlastní sady čítačů.

     \- ani

     Vyberte přepínač **všechny čítače** a vyberte všechny dostupné čítače.

7. Vyberte **OK**.

    > [!NOTE]
    > Čítače můžete do sady čítačů přidat také tak, že vyberete existující kategorii čítače nebo čítače, zvolíte kopírovat a pak ji vložíte do jiného uzlu sady čítačů. Nadbytečné čítače, které jsou zkopírovány, ale nejsou potřeba, je možné odstranit.

## <a name="see-also"></a>Viz také

- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
