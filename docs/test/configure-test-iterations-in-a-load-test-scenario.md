---
title: Konfigurace iterací testů pro zátěžové testování
description: Naučte se konfigurovat nastavení iterace testu, nakonfigurovat maximální počet iterací ve scénáři a dobu pozastavení mezi nimi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5316b03220a094d3280aba3eb8c46f190a2874f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442557"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurace iterací testů ve scénáři zátěžového testu

Chcete-li konfigurovat nastavení iterace testu, upravte scénář zátěžového testu pomocí Editor zátěžového testu a okna **vlastnosti** . Ve výchozím nastavení je scénář zátěžového testu nastavený bez určení maximálního počtu iterací testu. Máte možnost nakonfigurovat maximální počet iterací ve scénáři a dobu pozastavení mezi nimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Zadejte maximální počet iterací testu pro scénář.

Můžete zadat maximální počet, kolikrát chcete, aby testy běžely pro scénář pomocí Editor zátěžového testu ke změně vlastnosti **maximálního počtu iterací testu** v okně **vlastnosti** .

Vlastnost **maximální počet iterací testu** určuje maximální počet iterací testu, které se mají spustit pro daný scénář. Stejně jako u vlastnosti **iterace testu** v nastavení spuštění zátěžového testu je toto maximum pro všechny uživatele na všech agentech, nikoli na uživatelské nastavení.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

V případě kombinace sekvenčního testu jedna iterace projde všemi testy v kombinaci. U všech ostatních testovaných směsí se každé spuštění testu počítá jako iterace. Další informace naleznete v tématu [o ovládacím prvku míchání](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Pokud zátěžový test je zátěžový test založený na době od doby trvání a vyprší před dokončením počtu iterací, test se pořád zastaví. Pokud je test založen na iteraci a testy testů jsou splněné před iteracemi scénáře, test se zastaví. Doba trvání je nakonfigurována pomocí vlastnosti **trvání běhu** v okně **vlastnosti** přidruženého k nastavení spuštění v rámci zátěžového testu.

V případě splnění počtu iterací scénáře přestane fungovat, ale všechny ostatní aktivní scénáře budou i nadále spuštěny.

> [!NOTE]
> Související vlastnost je **jedinečná** vlastnost na zdroji dat webového testu, která je postupně přesunuta přes data, řádek po řádku, ale pouze jednou pro každý záznam. Další informace najdete v tématu [Přidání zdroje dat do testu výkonnosti webu](../test/add-a-data-source-to-a-web-performance-test.md).

Vlastnost **maximální počet iterací testu** je užitečná pro celou řadu situací. Některé testery zatížení dávají přednost testování založenému na iteraci, zatímco jiné testery zatížení dávají přednost testování na základě doby trvání.

![Určení iterací testu ve scénáři](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Určení maximálních iterací testu

1. Otevřete zátěžový test.

2. Zobrazí se Editor zátěžového testu. Zobrazí se strom zátěžového testu.

3. Ve složce **scénáře** stromů zátěžového testu zvolte uzel scénáře, pro který chcete určit maximální počet iterací testu.

4. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

5. Do textového pole pro vlastnost **maximální počet iterací testu** zadejte hodnotu, která označuje maximální počet testů, které mají být spuštěny pro daný scénář při spuštění zátěžového testu.

    > [!NOTE]
    > Použití hodnoty 0 pro vlastnost **maximální počet iterací testu** určuje maximální počet iterací.

6. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Zátěžový test lze následně spustit pomocí nové hodnoty **maximálního počtu iterací testu** .

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Zadejte dobu přemýšlení mezi iteracemi testu pro scénář.

**Doba přemýšlení mezi iteracemi testu** je nastavena pomocí okna **vlastnosti** při úpravě vlastností scénáře zátěžového testu v Editor zátěžového testu.

**Doba pomýšlení mezi testovacími iteracemi** se používá k určení doby v sekundách, po kterou se má počkat, než se spustí iterace testu.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Určení doby promýšlení mezi testovacími iteracemi

1. Otevřete zátěžový test.

     Zobrazí se **Editor zátěžového testu** . Zobrazí se strom zátěžového testu.

2. Ve složce **scénáře** stromů zátěžového testu zvolte uzel scénář, pro který chcete zadat čas přemýšlení.

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

     Kategorie a vlastnosti scénáře se zobrazí v okně **vlastnosti** .

4. Do hodnoty pro **dobu přemýšlení mezi vlastností iterace testu** zadejte číslo představující počet sekund, po který se má čekat před spuštěním další iterace testu.

5. Po dokončení změny vlastnosti vyberte v nabídce **soubor** možnost **Uložit** . Pak můžete spustit zátěžový test s využitím nového **času pomýšlení mezi hodnotou iterace testu** .

## <a name="see-also"></a>Viz také

- [Úpravy scénářů zátěžového testu](../test/edit-load-test-scenarios.md)
- [Konfigurace testovacích agentů a testovacích kontrolérů pro zátěžové testy](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md)
- [Úprava časů pomýšlení pro simulaci zpoždění lidské interakce webu](../test/edit-think-times-in-load-test-scenarios.md)
