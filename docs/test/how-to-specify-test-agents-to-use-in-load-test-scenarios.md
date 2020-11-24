---
title: Určení testovacích agentů pro použití ve scénářích zátěžových testů
description: Zjistěte, jak určit agenty k použití ve scénáři nastavením agentů k použití vlastnosti v okno Vlastnosti Editor zátěžového testu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: af0dac96bef5218a80e01c3ec205b58d122677c6
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440906"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Postupy: Určení testovacích agentů pro použití ve scénářích zátěžových testů

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem** můžete pomocí **Editor zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim požadavkům na testování a cílům.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Agenti jsou určeni pomocí **Editor zátěžového testu** ke změně vlastnosti **agenti na použití** v okně **vlastnosti** .

Můžete určit agenty, které má váš scénář používat, pokud používáte řadiče a agenty ke vzdálenému spuštění testu zatížení. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Agenti mohou být také geograficky distribuováni, aby existovalo spřažení mezi skripty, které jsou spuštěny a kde se nachází agent.

> [!TIP]
> Místo fyzického uvedení agenta na vzdálenou lokalitu je další možností, jak emulovat pomalou síť pomocí emulace sítě. Další informace najdete v tématu [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Další informace naleznete v tématu  [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Dalším důvodem je, že někteří agenti, ale ne všichni, můžou mít nainstalovaný software, který je nutný pro konkrétní scénář.

Můžete ovládat výběr agenta pro daný testovací běh pomocí rolí v nastaveních testu. Další informace najdete v tématu  [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Pokud má počítač s testovacím agentem více než 75 procent využití CPU nebo má méně než 10 procent dostupné fyzické paměti, přidejte do zátěžového testu více agentů, abyste se ujistili, že počítač agenta se nestane kritickým bodem v zátěžovém testu.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Určení agentů pro použití ve scénáři

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu vyberte uzel scénáře, pro který chcete zadat agenty, které chcete použít.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

4. Do textového pole pro **agenty, kteří mají použít** vlastnost zadejte seznam agentů, u kterých se může scénář spustit.

     Agenty musí být odděleny čárkami, například "**obdrží agent1, obdrží Agent2, obdrží Agent3**". Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.

    > [!NOTE]
    > Pro místní spuštění je vlastnost **Agents to use** ignorována. Pro vzdálené spuštění, pokud žádný z agentů uvedených v **agentech k použití** neexistuje, testy ve scénáři se nespustí.

5. Po změně vlastnosti klikněte na možnost **Uložit** v nabídce **soubor** . Pak můžete spustit zátěžový test pomocí nových **agentů k použití** hodnoty.

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
