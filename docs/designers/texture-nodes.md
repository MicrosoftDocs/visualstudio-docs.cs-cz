---
title: Uzly textury
description: Přečtěte si o uzlech textury, které jsou ukázkou různých typů textur a geometrií, a pak vytvořte nebo Transformujte souřadnice textury v Návrháři shaderu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bf9ea986fde744ec384f68338eca0d2239a3e73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902270"
---
# <a name="texture-nodes"></a>Uzly textury

V Návrháři shaderu jsou v uzlech textury ukázkové různé typy textur a geometriíy a vytváří nebo transformují souřadnice textury. Textury poskytují podrobnosti o barvě a osvětlení objektů.

## <a name="texture-node-reference"></a>Odkaz na uzel textury

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Ukázka cubemap**|Provede vzorek barvy z cubemap na zadaných souřadnicích.<br /><br /> Můžete použít cubemap k poskytnutí detailů barvy pro efekt odrazu nebo pro použití u kulového objektu texturu, která má méně zkreslení než 2D textura.<br /><br /> **Vstup**<br /><br /> `UVW`: `float3`<br /> Vektor, který určuje umístění v datové krychli textury, kde je provedena ukázka. Vzorek je proveden tam, kde tento vektor protíná datovou krychli.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Vzorek barvy.|**Textura**<br /> Registr textury, který je přidružen k vzorkovači.|
|**Ukázka normálního mapování**|Vezme normální vzorek z 2D normálního mapování na zadaných souřadnicích.<br /><br /> Můžete použít normální mapu pro simulaci vzhledu dalších geometrických podrobností na povrchu objektu. Normální mapy obsahují zabalená data, která představují vektor jednotky namísto dat barev.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice, ve kterých je ukázka provedena<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Normální vzorek.|**Úprava osy**<br /> Faktor, který slouží k úpravě uchopení pera normálního vzorku mapy.<br /><br /> **Textura**<br /> Registr textury, který je přidružen k vzorkovači.|
|**Pan – UV**|Posouvá zadané souřadnice textury jako funkci času.<br /><br /> Tuto možnost můžete použít k přesunutí textury nebo normální mapy napříč povrchem objektu.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice pro posun.<br /><br /> `Time`: `float`<br /> Doba, po kterou se má posunout aplikace v sekundách.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Souřadnice s posouváním|**Rychlost X**<br /> Počet texelů, které jsou vyneseny podél osy x za sekundu.<br /><br /> **Rychlost Y**<br /> Počet texelů, které jsou vyneseny podél osy y za sekundu.|
|**Paralaxníý UV**|Umístí zadané souřadnice textury jako funkci výšky a zobrazení úhlu.<br /><br /> Efekt, který tento příkaz vytvoří, se označuje jako *mapování paralaxní* nebo mapování virtuálních přemístění. Můžete ho použít k vytvoření iluze hloubky na plochém povrchu.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice, které mají být umístěny.<br /><br /> `Height`: `float`<br /> Hodnota heightmap, která je přidružena k `UV` souřadnicím.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Posunuté souřadnice.|**Rovina hloubky**<br /> Referenční hloubka pro paralaxní efekt. Ve výchozím nastavení je hodnota 0,5. Menší hodnoty naruší texturu; větší hodnoty se zanoří do povrchu.<br /><br /> **Měřítko hloubky**<br /> Měřítko efektu paralaxní. Tím se zdánlivá hloubka více nebo méně vysloví. Typické hodnoty jsou v rozsahu od 0,02 do 0,1.|
|**Otočit UV**|Otočí zadané souřadnice textury kolem centrálního bodu jako funkci času.<br /><br /> Tuto možnost můžete použít k otočení textury nebo normálního mapování na povrchu objektu.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice pro otočení<br /><br /> `Time`: `float`<br /> Doba, po kterou se má posunout aplikace v sekundách.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Otočené souřadnice.|**Střed ×**<br /> Souřadnice x, která definuje střed otáčení.<br /><br /> **Střed Y**<br /> Souřadnice y, která definuje střed otáčení.<br /><br /> **Rychlost**<br /> Úhel v radiánech, o který se textura otáčí za sekundu.|
|**Souřadnice textury**|Souřadnice textury aktuálního pixelu<br /><br /> Souřadnice textury jsou určeny interpolací z atributů souřadnic textury okolních vrcholů. Můžete si to představit jako pozici aktuálního pixelu v prostoru textury.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Souřadnice textury.|Žádné|
|**Rozměry textury**|Vypíše šířku a výšku 2D mapy textury.<br /><br /> Můžete použít Rozměry textury k zvážení šířky a výšky textury v shaderu.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Šířka a Výška textury vyjádřená jako vektor. Šířka je uložena v prvním prvku vektoru. Výška je uložena v druhém elementu.|**Textura**<br /> Registr textury, který je přidružen k rozměrům textury.|
|**Texel rozdíl**|Vypíše rozdílovou (vzdálenost) mezi texelůou mapy 2D textury.<br /><br /> Rozdíl Texel můžete použít k ukázce sousedních hodnot Texel v shaderu.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`<br /> Rozdíl (vzdálenost) od Texel k dalšímu Texel (úhlopříčně přesunutý v kladném směru) vyjádřený jako vektor v normalizovaném prostoru textury. Pozice všech sousedních texelů můžete odvodit selektivním ignorováním nebo negací souřadnic U nebo V rozdílu.|**Textura**<br /> Registr textury, který je přidružen k Texel rozdílu.|
|**Ukázka textury**|Provede vzorek barvy z 2D mapy textury na zadaných souřadnicích.<br /><br /> Mapu textury můžete použít k poskytnutí detailů barev na povrchu objektu.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice, ve kterých je ukázka provedena<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Vzorek barvy.|**Textura**<br /> Registr textury, který je přidružen k vzorkovači.|
