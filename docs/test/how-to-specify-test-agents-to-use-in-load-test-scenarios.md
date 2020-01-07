---
title: Určení testovacích agentů pro použití ve scénářích zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d565752d81bff960027090ddaaf88e9d78ed5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588925"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Postupy: určení testu agentů v zátěžového testování scénářů

Po vytvoření zátěžového testu s použitím **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti scénářů pro splnění potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastnosti scénáře zátěžového testu a jejich popis najdete v tématu [vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Agenti jsou zadány pomocí **editoru zátěžových testů** změnit **agenty k použití** vlastnost v **vlastnosti** okna.

Můžete zadat agenty, které má váš scénář použít, pokud používáte kontroléry a agenty ke spuštění zátěžového testu vzdáleně. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Navíc agentů může být geograficky distribuovanou, tak, že existuje spřažení mezi skripty, které mohou být spuštěny a kde se nachází agent.

> [!TIP]
> Místo vložíte fyzicky agenta ve vzdálené lokalitě, Další možností je použití emulace sítě emulovat pomalou síť. Další informace najdete v tématu [určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Další informace najdete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Dalším důvodem je, že některé, ale ne ve všech agentů může být software nainstalovaný v nich, která je požadována pro konkrétní scénář.

Můžete řídit výběr agenta pro daný test spustit s použitím rolí v nastavení testu. Další informace najdete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Pokud počítač testovacího agenta má více než 75 % využití procesoru nebo má méně než 10 procent fyzické paměti, ujistěte se, že přidejte další agenty do zátěžového testu počítači agenta se nestane problémem při zátěžovém testu.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Chcete-li určit agentů pro scénář

1. Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2. V zátěžového testu stromů **scénáře** složky, vyberte uzel scénář, pro kterou chcete určit agenty k použití.

3. Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v **vlastnosti** okna.

4. V textovém poli pro **agenty k použití** vlastnost, zadejte seznam agentů, se kterými se může spouštět scénář.

     Agenty musí být odděleny čárkami, například "**Agent1, Agent2, Agent3**". Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.

    > [!NOTE]
    > **Agenty k použití** vlastnost se ignoruje pro místní běhy. Pro vzdálená spuštění, pokud žádná z agentů uvedených v **agenty k použití** neexistuje, nebudou spouštět testy ve scénáři.

5. Po změně vlastnosti zvolte **Uložit** na **souboru** nabídky. Potom můžete spustit zátěžový test pomocí nového **agenty k použití** hodnotu.

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
