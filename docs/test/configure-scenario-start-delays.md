---
title: Konfigurace zpoždění zahájení scénářů pro zátěžové testování
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d425b457056e256c5c9ed927c99adf002b78dd9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288790"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurace zpoždění spouštění scénářů v zátěžových testech

Určete zpoždění před spuštěním scénáře v zátěžovém testu pomocí Editor zátěžového testu a okna **vlastnosti** .

Například můžete chtít použít vlastnost **zpoždění spuštění** , pokud potřebujete jeden scénář pro zahájení výroby položek, které jiný scénář spotřebovává. Můžete zpozdit nenáročný scénář a umožnit tak scénáři výroby naplnit nějaká data.

Dalším příkladem je, že můžete mít jeden scénář, který se spouští pouze v určitou dobu dne. Chcete tedy odložit začátek scénáře a simulovat ho.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Zadejte čas zahájení zpoždění scénáře.

Můžete zadat zpoždění před začátkem scénáře v zátěžovém testu pomocí Editor zátěžového testu pro změnu vlastnosti **zpoždění spuštění** v okně **vlastnosti** .

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

Příkladem instance, kdy může být vhodné použít vlastnost **zpoždění spuštění** , je, když potřebujete jeden scénář pro zahájení výroby položek, které jiný scénář spotřebovává. Můžete zpozdit nenáročný scénář a umožnit tak scénáři výroby naplnit nějaká data.

Dalším příkladem je, že můžete mít jeden scénář, který se spouští pouze v určitém denním čase. Proto chcete, aby se zazpozdil začátek scénáře, který simuluje tuto situaci.

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Určení prodlevy počátečního času pro scénář

1. Otevřete zátěžový test.

     Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu vyberte uzel scénáře, pro který chcete zadat čas spuštění zpoždění.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

4. Do textového pole vlastnosti **zpoždění spuštění** zadejte hodnotu času, která určuje čas, který se má počkat po spuštění testu zatížení před spuštěním scénáře při spuštění zátěžového testu.

    > [!NOTE]
    > Pokud je hodnota vlastnosti **Disable během zahřívání** pro daný scénář nastavená na **hodnotu true**, použije se po uplynutí doby zahřívání hodnota čas spuštění vlastnosti doba **zpoždění** . Můžete určit, které scénáře jsou zahrnuty do zahřívání, pomocí vlastnosti **zahřívání scénáře zakázat** .

5. Po změně vlastnosti klikněte na možnost **Uložit** v nabídce **soubor** . Zátěžový test lze následně spustit pomocí nové hodnoty **času spuštění** .

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Umožňuje povolit a zakázat, jestli se scénář spouští během období zahřívání.

Vlastnost **Zakázat během zahřívání** je nastavena pomocí okna **vlastnosti** . Úpravy vlastností scénáře zátěžového testu jsou nastaveny pomocí Editor zátěžového testu.

Vlastnost **Zakázat během zahřívání** se používá k označení, zda se má scénář spustit nebo nespustit během doby zahřívání, která je zadána ve vlastnosti **zpoždění spuštění** . Další informace najdete v předchozím postupu [zadání času zpoždění spuštění scénáře](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Povolení nebo zakázání období zahřívání pro scénář

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu vyberte uzel scénáře, pro který chcete změnit chování zahřívání pro.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

     Ve vlastnosti **Zakázat během zahřívání** vyberte buď **true** , nebo **false.**

4. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test pomocí nového **zakazování během zahřívání** hodnoty.

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovacích kontrolérů pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
