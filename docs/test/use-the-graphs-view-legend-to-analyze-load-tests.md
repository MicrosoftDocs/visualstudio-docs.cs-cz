---
title: Použití legendy zobrazení grafů k analýze zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1455c67c3cb6d8dc99aeab91a7bfa63cce009c51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590797"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Analýza zátěžových testů pomocí legendy zobrazení grafů

Zobrazení grafů Analyzéru zátěžového testu obsahuje panel legendy, jenž zobrazuje informace pro každý čítač výkonu, který je přidružen k aktuálně vybranému grafu.

![Legenda zobrazení grafů](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Legenda obsahuje následující informace:

- **Zobrazit v grafu:** Pomocí zaškrtávacích políček určete, zda je v grafu vykreslen řádek pro určitý čítač, například **Načtení uživatele** nebo **Chyby/s**. Pokud chcete, aby byla čára vykreslena v grafu, zaškrtněte políčko. Zaškrtnutím políčka odeberete čáru parcely z grafu. I po odstranění čáry grafu zůstane statistika čítače nadále zobrazena v legendě.

- **Rozsah:** V tomto sloupci se zobrazí rozsah osy y čítače výkonu. Ve výchozím nastavení se tato hodnota automaticky upraví podle toho, jak se mění rozsah ukázkových dat. Automaticky upravený rozsah bude vždy o další mocninu desíti větší než maximální hodnota, včetně záporných mocnin desíti. Graf může obsahovat mnoho různých čítačů, z nichž každý má jiný rozsah. Osa y tedy není popsána žádným konkrétním rozsahem. Namísto toho je popsána hodnotami 0 až 100 představujícími procento celkového rozsahu každého čítače. Například pro čítač s rozsahem 1000 by datový bod 60 na ose y odpovídal hodnotě čítače 600.

    > [!NOTE]
    > Automatické nastavení hodnoty rozsahu můžete vypnout uzamčením rozsahu na určitou hodnotu. Je-li rozsah uzamčen, jsou všechny hodnoty přesahující tento rozsah zobrazeny jako maximální hodnota zadaná v horní části grafu. Dialogové okno **Volby vykreslení** slouží k uzamčení rozsahu na určitou hodnotu.

- **Čítač:** Čtyři sloupce s názvem **Čítač**, **Instance**, **Kategorie**a **Počítač** společně jednoznačně identifikují čítač výkonu.

- **Barva:** Sloupec **Barva** zobrazuje barvu a styl čáry vykreslené čáry pro čítač výkonu. Dialogové okno **Volby vykreslení** slouží ke změně barvy nebo stylu čáry čítače výkonu v grafu. Dialogové okno **Volby vykreslení** je k dispozici v místní nabídce legendy.

- **Statistiky:** Sloupce **Min**, **Max**, **Avg** a **Poslední** zobrazují příslušné statistiky čítače výkonu. Tyto hodnoty odpovídají datům, která jsou zobrazena ve viditelné oblasti grafu. Pokud například přiblížíte zobrazení na nějakou oblast běhu, statistika legendy bude odpovídat hodnotám platným pouze pro přiblíženou oblast. Sloupec "Poslední" je hodnota čítače výkonu v naposledy dokončeném intervalu vzorkování.

    > [!NOTE]
    > Sloupec Poslední se zobrazí v legendě Analyzéru zátěžového testu pouze za běhu zátěžového testu.

     Další informace naleznete [v tématu Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Výběr položky v legendě provede následující:

- Umožňuje položku odebrat z legendy i grafu. Klepněte pravým tlačítkem myši na položku a vyberte **odstranit**nebo stiskněte klávesu **Delete.**

- Zvýrazní vykreslenou čáru v grafu.

- Způsobí, že mřížka dat zobrazí data pro vybranou položku.

- Umožňuje přístup k dialogovému oknu **Možnosti vykreslení** pro čítač.

> [!TIP]
> Na panelu nástrojů Load Test **Analyzer** můžete použít **rozevírací** tlačítko Volby grafu a výběrem **možnosti Zobrazit legendu** zobrazíte nebo skryjete panel **Legenda,** který je přidružen k zobrazení grafu.

## <a name="see-also"></a>Viz také

- [Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md)
