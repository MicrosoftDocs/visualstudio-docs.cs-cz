---
title: Sady čítačů zátěžových zkoušek
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 224ac14a0d670648f8047a82a8abef0c2b7b2654
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113423"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Postup: Správa sad čítačů pomocí Editoru zátěžového testu

Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy.

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, jak používat vzdálené počítače v zátěžovém testu, naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Správa sad čítačů zahrnuje výběr sady počítačů, ze kterých chcete shromažďovat data o výkonu, a přiřazení sady čítačů, které lze shromažďovat z každého jednotlivého počítače. Čítače spravujete v **Editoru zátěžových testů**.

![Správa sad čítačů](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Správa sad čítačů

1. Otevřete zátěžový test.

2. Zvolte tlačítko **Spravovat sady čítačů.**

     – nebo –

     Ve stromu zátěžových testů klepněte pravým tlačítkem myši na složku **Sady čítačů** a zvolte **Spravovat sady čítačů**.

     Zobrazí se dialogové okno Spravovat sady čítačů. **Manage Counter Sets**

3. (Nepovinné) V seznamu **Vybrané počítače a sady čítačů budou přidány do následujícího** seznamu nastavení spuštění, vyberte jiné nastavení spuštění.

    > [!NOTE]
    > To platí pouze v případě, že máte více než jedno nastavení spuštění v zátěžovém testu.

4. (Nepovinné) Chcete-li přidat nový počítač ke sledování, zvolte **Přidat počítač.** Budete vyzváni k zadání jména. Zadejte název počítače a pod novou položkou uvidíte uzly. Například **ASP.NET**, **IIS**, **SQL**a další. Zaškrtněte políčka před uzly, které chcete vybrat. Nové čítače se zobrazí v podokně **Náhled výběrů.**

5. (Nepovinné) Do textového pole **Počítačové značky** zadejte značku, kterou chcete přidružit k počítači. Například "TestMachine12 v laboratoři3".

     Značky počítače umožňují identifikovat počítač se snadno rozpoznatelným názvem.

     Značky jsou zobrazeny v uzlu **Mapování sad čítačů** ve stromu v Editoru zátěžového testu. Ještě důležitější je, že značky jsou zobrazeny v sestavách aplikace Excel, které pomáhají zúčastněným stranám určit, jakou roli má počítač v zátěžovém testu. Například "Web Server1 v laboratoři2" nebo "SQL Server2 v kanceláři Phoenix". Další informace naleznete [v tématu Zpráva o výsledcích zátěžových testů pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md).

6. Vyberte **OK**.

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md)
