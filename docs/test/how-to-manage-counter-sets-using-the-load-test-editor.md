---
title: Sady čítačů zátěžového testu
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: 1eeb99d58a9fc0547d118c529878d8b02cc83dda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287685"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Postupy: Správa sad čítačů pomocí Editor zátěžového testu

Při vytváření zátěžového testu s **novým Průvodce zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy.

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o použití vzdálených počítačů v rámci zátěžového testu naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Správa sad čítačů zahrnuje výběr sady počítačů, ze kterých chcete shromažďovat údaje o výkonu, a přiřazení sady čítačů pro shromažďování dat z jednotlivých počítačů. Čítače můžete spravovat v **Editor zátěžového testu**.

![Správa sad čítačů](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Správa sad čítačů

1. Otevřete zátěžový test.

2. Klikněte na tlačítko **Spravovat sady čítačů** .

     ani

     Klikněte pravým tlačítkem na složku **sady čítačů** ve stromu zátěžového testu a vyberte možnost **Spravovat sady čítačů**.

     Zobrazí se dialogové okno **Spravovat sady čítačů** .

3. Volitelné V **části vybrané počítače a sady čítačů budou přidány do následujících polí seznam parametrů spuštění** vyberte jiné nastavení spuštění.

    > [!NOTE]
    > To platí pouze v případě, že máte více než jedno nastavení spuštění v rámci zátěžového testu.

4. Volitelné Zvolením možnosti **Přidat počítač** přidejte nový počítač, který chcete monitorovat. Zobrazí se výzva k zadání názvu. Zadejte název počítače a zobrazí se uzly pod novou položkou. Například **ASP.NET**, **IIS**, **SQL**a další. Zaškrtněte políčka před uzly, které chcete vybrat. Nové čítače se zobrazí v podokně **výběr ve verzi Preview** .

5. Volitelné Do textového pole **značky počítače** zadejte značku, kterou chcete přidružit k počítači. Například "TestMachine12 in lab3".

     Značky počítače umožňují identifikovat počítač se snadno rozpoznatelným názvem.

     Značky se zobrazí v uzlu **mapování sady čítačů** ve stromové struktuře v Editor zátěžového testu. Důležitější je, že značky se zobrazí v sestavách aplikace Excel, které účastníkům pomohou určit, jakou roli má počítač v rámci zátěžového testu. Například "Web Server1 v lab2" nebo "SQL Server2" v Phoenixu pobočky ". Další informace naleznete v tématu [výsledky testů zatížení sestav pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md).

6. Vyberte **OK**.

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurovat nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md)
