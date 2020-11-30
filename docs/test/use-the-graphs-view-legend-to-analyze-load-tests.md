---
title: Použití legendy zobrazení grafů k analýze zátěžových testů
description: Přečtěte si o zobrazení grafů analyzátoru zátěžového testu, který obsahuje panel legendy, který zobrazuje informace o čítačích výkonu pro vybraný graf.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25200b691e0bebf2e3bd1c6252efb371ed9caeb2
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330066"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Použití legendy zobrazení grafů k analýze zátěžových testů

Zobrazení grafů Analyzéru zátěžového testu obsahuje panel legendy, jenž zobrazuje informace pro každý čítač výkonu, který je přidružen k aktuálně vybranému grafu.

![Legenda zobrazení grafů](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Legenda obsahuje následující informace:

- **Zobrazit v grafu:** Pomocí zaškrtávacích políček určete, zda se má v grafu vykreslovat řádek určitého čítače, například **uživatelské zatížení** nebo **chyby/s**. Zaškrtněte políčko, pokud chcete, aby se řádek vykreslil v grafu. Zrušením zaškrtnutí políčka odeberete čáru vykreslování z grafu. I po odstranění čáry grafu zůstane statistika čítače nadále zobrazena v legendě.

- **Rozsah:** V tomto sloupci se zobrazuje rozsah osy y v čítači výkonu. Ve výchozím nastavení se tato hodnota automaticky upraví, protože se změní rozsah vzorových dat. Automaticky upravený rozsah bude vždy o další mocninu desíti větší než maximální hodnota, včetně záporných mocnin desíti. Graf může obsahovat mnoho různých čítačů, z nichž každý má jiný rozsah. Osa y tedy není popsána žádným konkrétním rozsahem. Namísto toho je popsána hodnotami 0 až 100 představujícími procento celkového rozsahu každého čítače. Například pro čítač s rozsahem 1000 by datový bod 60 na ose y odpovídal hodnotě čítače 600.

    > [!NOTE]
    > Automatickou úpravu hodnoty rozsahu můžete vypnout tak, že zamknete rozsah na určitou hodnotu. Je-li rozsah uzamčen, jsou všechny hodnoty přesahující tento rozsah zobrazeny jako maximální hodnota zadaná v horní části grafu. Použijte dialogové okno **Možnosti grafu** k uzamknutí rozsahu na konkrétní hodnotu.

- **Čítač:** Čtyři sloupce s názvem **čítač**, **instance**, **kategorie** a **počítač** společně identifikují čítač výkonu jednoznačně.

- **Barva:** Sloupec **Color (barva** ) zobrazuje barvu a styl čáry vykreslené čáry pro čítač výkonu. Pomocí dialogového okna **Možnosti grafu** můžete změnit barvu nebo styl čáry čítače výkonu v grafu. Dialogové okno **Možnosti grafu** je k dispozici v místní nabídce legendy.

- **Statistika:** Sloupce **min**, **Max**, **AVG** a **Last** zobrazují příslušné statistiky čítače výkonu. Tyto hodnoty odpovídají datům zobrazeným ve viditelné oblasti grafu. Pokud například přiblížíte zobrazení na nějakou oblast běhu, statistika legendy bude odpovídat hodnotám platným pouze pro přiblíženou oblast. Sloupec "poslední" je hodnota čítače výkonu pro poslední dokončený interval vzorkování.

    > [!NOTE]
    > Sloupec Poslední se zobrazí v legendě Analyzéru zátěžového testu pouze za běhu zátěžového testu.

     Další informace najdete v tématu [Postup: přiblížení v oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Výběr položky v legendě provede následující:

- Umožňuje odebrat položku z legendy i grafu. Buď klikněte pravým tlačítkem myši na položku a vyberte **Odstranit**, nebo stiskněte klávesu **Delete** .

- Zvýrazní vykreslenou čáru v grafu.

- Způsobí, že datová mřížka zobrazí data pro vybranou položku.

- Umožňuje přístup k dialogovému oknu **Možnosti grafu** pro čítač.

> [!TIP]
> K zobrazení nebo skrytí panelu **legendy** , který je přidružen k zobrazení grafu, lze použít tlačítko **rozevíracího seznamu Možnosti grafu** na panelu nástrojů **analyzátor zátěžového testu** a vybrat možnost **Zobrazit legendu** .

## <a name="see-also"></a>Viz také

- [Postupy: přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
