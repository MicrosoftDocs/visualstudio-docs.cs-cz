---
title: Konfigurace zpoždění spuštění scénáře pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f962306462538717df694d3bc47719fe31b1e1fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111473"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurace zpoždění spuštění scénáře v zátěžových testech

Zadejte zpoždění před spuštěním scénáře v zátěžovém testu pomocí editoru zátěžového testu a okna **Vlastnosti.**

Například můžete chtít použít **zpoždění čas zahájení** vlastnost, pokud potřebujete jeden scénář začít vyrábět položky, které spotřebovává jiný scénář. Můžete zpozdit náročný scénář povolit vytváření scénář naplnit některá data.

Dalším příkladem je, že můžete mít jeden scénář, který je spuštěn pouze v určitou denní dobu. Takže chcete odložit začátek scénáře simulovat to.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Určení času zahájení zpoždění scénáře

Můžete určit zpoždění před zahájením scénáře v zátěžovém testu pomocí Editoru zátěžového testu pro změnu **vlastnosti Zpoždění počátečního času** v okně **Vlastnosti.**

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Příkladem instance, kdy můžete chtít použít vlastnost **Zpoždění počáteční čas** je, když potřebujete jeden scénář začít vyrábět položky, které spotřebovává jiný scénář. Můžete zpozdit náročný scénář povolit vytváření scénář naplnit některá data.

Dalším příkladem je, že můžete mít jeden scénář, který je spuštěn pouze v určitou denní dobu. Proto chcete odložit začátek scénáře simulovat to.

> [!NOTE]
> Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Určení času zahájení zpoždění pro scénář

1. Otevřete zátěžový test.

     Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

2. Ve **složce** scénáře zátěžového testu zvolte uzel scénáře, pro který chcete zadat čas zahájení zpoždění.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

4. Do textového pole pro vlastnost **Zpoždění počátečního času** zadejte hodnotu času, která označuje čas čekání po spuštění zátěžového testu před spuštěním scénáře při spuštění zátěžového testu.

    > [!NOTE]
    > Pokud je hodnota **vlastnosti Disable During Warmup** pro scénář nastavena na **hodnotu True**, bude po zahřívací můloží použita hodnota čas vlastností **zpoždění.** Můžete určit, které scénáře jsou zahrnuty v warm-up pomocí **zakázat během zahřívání** scénář vlastnost.

5. Po změně vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **čas spuštění zpoždění.**

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Povolení a zakázání, zda se scénář spustí během zahřívací hodu

Vlastnost **Zakázat během zahřívání** je nastavena pomocí okna **Vlastnosti.** Úpravy vlastností scénáře zátěžového testu jsou nastaveny editorem zátěžového testu.

Vlastnost **Zakázat během zahřívání** se používá k označení, zda by měl být scénář spuštěn nebo nespuštěn během období zahřívání, které je zadáno ve vlastnosti **Delay Start Time.** Další informace naleznete v předchozím postupu [Zadejte čas zahájení zpoždění scénáře](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Úplný seznam vlastností nastavení spuštění a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Povolení nebo zakázání doby zahřívání scénáře

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve **složce** scénáře zátěžového testu zvolte uzel scénáře, pro který chcete změnit chování zahřívání.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

     Ve vlastnosti **Zakázat během zahřívání** vyberte **true** nebo **false.**

4. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové **hodnoty Zakázat během zahřívání.**

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovacích řadičů pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
