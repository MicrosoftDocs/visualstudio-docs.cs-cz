---
title: Zadejte testovací agenty, kteří se mají použít ve scénářích zátěžového testu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588925"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Postup: Určení testovacích agentů, kteří se mají použít ve scénářích zátěžového testu

Po vytvoření zátěžového testu pomocí **Průvodce novým zátěžovými testy**můžete pomocí **Editoru zátěžového testu** změnit vlastnosti scénářů tak, aby vyhovovaly vašim potřebám a cílům testování.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Agenti jsou určeny pomocí **Editoru zátěžového testu** ke změně **vlastnosti Agenti na Použití** v okně **Vlastnosti.**

Můžete určit agenty, které chcete, aby váš scénář použít, pokud používáte řadiče a agenty ke vzdálenému spuštění zátěžového testu. Může být například potřeba určit konkrétní sadu agentů, aby byla při analýze trendů výkonu zachována konzistence. Agenti mohou být také geograficky distribuovány, takže existuje spřažení mezi skripty, které spouštějí a kde je umístěn agent.

> [!TIP]
> Spíše než fyzicky uvedení agenta na vzdálené mnoství, další možností je použít emulaci sítě k emulaci pomalé sítě. Další informace naleznete v [tématu Specify virtual network types](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Další informace naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Dalším důvodem je, že někteří, ale ne všichni agenti mohou mít software nainstalovaný na nich, který je vyžadován pro konkrétní scénář.

Výběr agenta pro daný test můžete řídit pomocí rolí v nastavení testu. Další informace naleznete [v tématu Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

Pokud má počítač testovacího agenta více než 75 procent využití procesoru nebo má k dispozici méně než 10 procent fyzické paměti, přidejte další agenty do zátěžového testu, abyste se ujistili, že se počítač agenta nestane kritickým bodem v zátěžovém testu.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Určení agentů, kteří mají být pro scénář používáni

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve **složce** scénáře zátěžového testu zvolte uzel scénáře, pro který chcete zadat agenty, které chcete použít.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

4. Do textového pole **pro vlastnost Agenti k použití** zadejte seznam agentů, na kterých může být scénář spuštěn.

     Agenti musí být odděleni čárkami, například**Agent1, Agent2, Agent3**.. Je-li tato vlastnost ponechána prázdná, scénář bude používat všechny dostupné agenty.

    > [!NOTE]
    > **Vlastnost Agenti k použití** je ignorována pro místní spuštění. Pro vzdálená spuštění, pokud žádný z agentů zadaných v **Agenti použít** existují, testy ve scénáři nebude spuštěna.

5. Po změně vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové **agenti použít** hodnotu.

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
