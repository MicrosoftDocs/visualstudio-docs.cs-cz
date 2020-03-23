---
title: Uzly textury
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3393bb979b73694c4ac65120ae794ef1205b37c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589810"
---
# <a name="texture-nodes"></a>Uzly textury

V návrháři shaderu vzorkují uzly textury různé typy textur a geometrie a vytvářejí nebo transformují souřadnice textur. Textury poskytují barevné a světelné detaily na objektech.

## <a name="texture-node-reference"></a>Odkaz na uzel textury

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Ukázka cubemap**|Odebere vzorek barvy z krychle na zadaných souřadnicích.<br /><br /> Mapu krychle můžete použít k poskytnutí barevných detailů pro efekty odrazu nebo k aplikování textury, která má menší zkreslení než 2D textura, na sférický objekt.<br /><br /> **Vstup:**<br /><br /> `UVW`: `float3`<br /> Vektor, který určuje umístění na krychli textury, kde je vzorek odebrán. Vzorek se odebere tam, kde tento vektor protíná krychli.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Ukázka barvy.|**Textura**<br /> Registr textur, který je přidružen k sampler.|
|**Ukázka normální mapy**|Pořídí normální vzorek z 2D normální mapy na zadaných souřadnicích.<br /><br /> Normální mapu můžete použít k simulaci vzhledu dalších geometrických detailů na povrchu objektu. Normální mapy obsahují zabalená data, která představují vektor jednotky namísto barevných dat<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice, kde se vzorek odebere.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Normální vzorek.|**Nastavení osy**<br /> Faktor, který se používá k nastavení handness normální mapy vzorku.<br /><br /> **Textura**<br /> Registr textur, který je přidružen k sampler.|
|**Pan UV**|Posune zadané souřadnice textury v závislosti na čase.<br /><br /> Pomocí této možnosti můžete přesunout texturu nebo normální mapu po povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice k posouvání.<br /><br /> `Time`: `float`<br /> Doba, po kterou se posune, v sekundách.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Posouvané souřadnice.|**Rychlost X**<br /> Počet texelů, které jsou posunuty podél osy x za sekundu.<br /><br /> **Rychlost Y**<br /> Počet texelů, které jsou posunuty podél osy y za sekundu.|
|**Parapozitu UV**|Přemístí zadané souřadnice textury jako funkci výšky a úhlu pohledu.<br /><br /> Efekt, který to vytváří, se označuje jako *mapování paraallaxu*nebo virtuální mapování posunutí. Můžete ji použít k vytvoření iluze hloubky na rovném povrchu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice se musí přemístit.<br /><br /> `Height`: `float`<br /> Hodnota heightmap, která je `UV` přidružena ke souřadnicím.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Vysídlené souřadnice.|**Rovina hloubky**<br /> Referenční hloubka paraallaxového efektu. Ve výchozím nastavení je hodnota 0,5. Menší hodnoty zvedají texturu; větší hodnoty jej ponořte do povrchu.<br /><br /> **Hloubková stupnice**<br /> Měřítko paraléxového efektu. To činí zdánlivou hloubku více či méně výraznou. Průměrné hodnoty se pohybují od 0,02 do 0,1.|
|**Otočit UV**|Otočí zadané souřadnice textury kolem centrálního bodu v závislosti na čase.<br /><br /> Můžete to použít k otočení textury nebo normální mapy na povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice k otočení.<br /><br /> `Time`: `float`<br /> Doba, po kterou se posune, v sekundách.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Otočené souřadnice.|**Střed X**<br /> Souřadnice x, která definuje střed otáčení.<br /><br /> **Střed Y**<br /> Souřadnice y, která definuje střed otáčení.<br /><br /> **Rychlost**<br /> Úhel v radiánech, o který se textura otáčí za sekundu.|
|**Souřadnice textury**|Souřadnice textury aktuálního obrazového bodu.<br /><br /> Souřadnice textury jsou určeny interpolací mezi atributy souřadnic textury blízkých vrcholů. Můžete si to myslet jako pozici aktuálního obrazového bodu v prostoru textury.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Souřadnice textury.|Žádný|
|**Rozměry textury**|Vyvýstupe šířku a výšku 2D mapy textury.<br /><br /> Kóty textury můžete použít k tomu, abyste zvážili šířku a výšku textury v shaderu.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Šířka a výška textury vyjádřená jako vektor. Šířka je uložena v prvním prvku vektoru. Výška je uložena v druhém prvku.|**Textura**<br /> Registr textur, který je spojen s kótami textury.|
|**Texel Delta**|Vyvýstupe rozdíl (vzdálenost) mezi texels 2D mapy textury.<br /><br /> Delta texelu můžete použít k vzorkování sousedních hodnot texel v shaderu.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Delta (vzdálenost) od texelu k dalšímu texelu (pohybující se diagonálně v kladném směru), vyjádřená jako vektor v normalizovaném prostoru textury. Pozice všech sousedních texelů můžete odvodit selektivním ignorováním nebo negací souřadnic U nebo V delta.|**Textura**<br /> Registr textur, který je spojen s delta texel.|
|**Ukázka textury**|Pořídí vzorek barvy z 2D mapy textury na určených souřadnicích.<br /><br /> Mapu textury můžete použít k poskytnutí barevných detailů na povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice, kde se vzorek odebere.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Ukázka barvy.|**Textura**<br /> Registr textur, který je přidružen k sampler.|
