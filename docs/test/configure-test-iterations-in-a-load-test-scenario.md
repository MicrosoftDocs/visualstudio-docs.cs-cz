---
title: Konfigurace testovacích iterací pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e95ca27ace50c7b28d1ffb1d3fc02589daddee2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590979"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurace iterace testů ve scénáři zátěžového testu

Chcete-li konfigurovat nastavení testovací iterace, upravte scénář zátěžového testu pomocí editoru zátěžového testu a okna **Vlastnosti.** Ve výchozím nastavení je nastaven scénář zátěžového testu bez zadání maximálních iterací testu. Máte možnost nakonfigurovat maximální počet iterací ve scénáři a jak dlouho mezi nimi pozastavit.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Určení maximálních iterací testu pro scénář

Můžete určit maximální počet, kolikrát chcete testy spustit pro scénář pomocí Editoru zátěžového testu změnit **maximální test iterací** vlastnost v okně **Vlastnosti.**

**Vlastnost Maximum Test Iterations** řídí maximální počet iterací testu, které mají být spuštěny pro scénář. Stejně jako pro **test iterací** vlastnost v nastavení spuštění zátěžového testu, toto je maximum napříč všemi uživateli na všech agentech, nikoli na uživatelské nastavení.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

Pro sekvenční kombinace testů je jedna iterace jeden průchod všemi testy v mixu. Pro všechny ostatní kombinace testů se každé spuštění testu počítá jako iterace. Další informace naleznete [v tématu O ovládacím prvku mix](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Pokud je zátěžový test zátěžový test založený na době trvání a doba trvání vyprší před dokončením počtu iterací, test se stále zastaví. Pokud je test založen na iteraci a iterace testu jsou splněny před iterací scénáře, test se zastaví. Doba trvání je konfigurována pomocí vlastnosti **Doba běhu** v okně **Vlastnosti** přidruženém k nastavení spuštění v zátěžovém testu.

Když je splněn počet iterace scénáře, scénář se zastaví, ale všechny ostatní aktivní scénáře budou nadále spuštěny.

> [!NOTE]
> Související vlastnost je **Jedinečná** vlastnost na webovém testovacím zdroji, která se postupně pohybuje mezi daty, řádek po řádku, ale pouze jednou pro každý záznam. Další informace naleznete [v tématu Přidání zdroje dat do testu výkonu webu](../test/add-a-data-source-to-a-web-performance-test.md).

**Maximální test iterací** vlastnost je užitečná pro různé situace. Některé testery zatížení dávají přednost provádění testování na základě iterace, zatímco jiné testery zatížení dávají přednost provádění testování na základě doby trvání.

![Určení iterací testu ve scénáři](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Určení maximálních iterací testu

1. Otevřete zátěžový test.

2. Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

3. Ve **složce** scénáře zátěžového testu zvolte uzel scénáře, pro který chcete zadat maximální počet iterací testu.

4. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

5. Do textového pole pro vlastnost **Maximum Test Iterations** zadejte hodnotu, která označuje maximální počet testů, které mají být spuštěny pro scénář při spuštění zátěžového testu.

    > [!NOTE]
    > Použití hodnoty 0 pro vlastnost **Maximální test iterací** neurčuje žádné maximální iterace.

6. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **Maximální test iterací.**

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Určení doby přemýšlení mezi iteracemi testu pro scénář

Vlastnost **Think Time Between Test Iterations** je nastavena pomocí okna **Vlastnosti** při úpravách vlastností scénáře zátěžového testu v editoru zátěžového testu.

Think **Time Between Test Iterace** vlastnost se používá k určení množství sekund čekat před spuštěním iterace testu.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Určení doby přemýšlení mezi iteracemi testu

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu.** Zobrazí se strom zátěžového testu.

2. Ve **složce** Scénáře zátěžového testu zvolte uzel scénáře, pro který chcete zadat čas přemýšlení.

3. V nabídce **Zobrazení** vyberte **Okno vlastnosti**.

     Kategorie a vlastnosti scénáře jsou zobrazeny v okně **Vlastnosti.**

4. Do hodnoty **think time mezi iterací testu** zadejte číslo představující počet sekund čekání před spuštěním další iterace testu.

5. Po dokončení změny vlastnosti zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test pomocí nové hodnoty **Think Time Between Test Iterations.**

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovacích řadičů pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Upravit doby přemýšlení pro simulaci zpoždění interakce s lidmi na webových stránkách](../test/edit-think-times-in-load-test-scenarios.md)
