---
title: Uzly textury
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3bd146460c57df12b446bead5a4462b14e4cfce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925195"
---
# <a name="texture-nodes"></a>Texture uzly

V Návrháři shaderu texture uzly ukázkové různé typy texture a geometrie a vytvořit nebo transformace texture souřadnice. Textury zadejte barvy a osvětlení podrobností u objektů.

## <a name="texture-node-reference"></a>Texture uzlu odkazu

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Ukázka Cubemap**|Načítá vzorku barvy z cubemap na zadaný souřadnice.<br /><br /> Cubemap můžete použít k barva podrobné informace o reflexe důsledky, a instalaci na objekt kulovým texture, který má méně narušení než 2D texture.<br /><br /> **Vstup:**<br /><br /> `UVW`: `float3`<br /> Vektor, který určuje umístění v datové krychli texture kde vzorku. Odebrání vzorku, kde tato vektoru protíná datové krychle.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Ukázka barev.|**Texture**<br /> Texture registrace, který je spojen s ho.|
|**Ukázka normální mapy**|Načítá ukázku normální z 2D normální mapy na zadaných souřadnic<br /><br /> Normální mapa můžete použít k simulaci vzhled geometrickou podrobnější informace na ploše objektu. Normální maps obsahují sbalené data, která představuje jednotku vektoru místo barva data<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice, kde vzorku.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Normální ukázka.|**Úpravy osy**<br /> Faktor, který slouží k úpravě uchopení pera vzorku normální mapy.<br /><br /> **Texture**<br /> Texture registrace, který je spojen s ho.|
|**Pan UV**|Zvětšení zadaný texture koordinuje jako funkce čas.<br /><br /> Můžete použít k přesunutí texture nebo normální mapa na povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice posunete zobrazení.<br /><br /> `Time`: `float`<br /> Doba běhu posunete zobrazení, v sekundách.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Panned souřadnice.|**Rychlost X**<br /> Počet texels, který se posouvá v okně podél osy x, za sekundu.<br /><br /> **Rychlost Y**<br /> Počet texels, který se posouvá v okně podél osy y, za sekundu.|
|**Paralaxy UV**|Posouvá souřadnice zadaný texture jako funkce výšky a zobrazení úhlu.<br /><br /> Tím se vytvoří účinek se označuje jako *paralaxy mapování*, nebo virtuální přestavění mapování. Můžete ho vytvořit dojem hloubky ploše.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice odsadit.<br /><br /> `Height`: `float`<br /> Hodnota heightmap, který je spojen s `UV` souřadnice.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Špatně umístěné souřadnice.|**Hloubka roviny**<br /> Hloubka odkaz pro paralaxy účinek. Výchozí hodnota je 0,5. Menší hodnoty navýšení texture; vyšší hodnoty jímky ho do povrchu.<br /><br /> **Hloubka škálování**<br /> Měřítko paralaxy účinek. Díky tomu zřejmá hloubka vyslovováno vyšší nebo nižší. Typické hodnoty rozsahu od 0,02 0,1.|
|**Otočit UV**|Otočí zadaný texture souřadnice z centrálního bodu jako funkce čas.<br /><br /> To vám pomůže číselníku texture nebo normální mapovat na povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice otočení.<br /><br /> `Time`: `float`<br /> Doba běhu posunete zobrazení, v sekundách.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Otočený souřadnice.|**Center X**<br /> Souřadnici x středu otočení definuje.<br /><br /> **Center Y**<br /> Souřadnici y středu otočení definuje.<br /><br /> **Rychlost**<br /> Úhel v radiánech, ve kterém textury otočí za sekundu.|
|**Souřadnice textury**|Texture souřadnice aktuální pixelů.<br /><br /> Určuje souřadnice texture interpolace mezi texture souřadnic atributy blízkým vrcholy. To si lze představit jako umístění aktuální pixelů v texture místa.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Texture souřadnice.|Žádné|
|**Texture dimenze**|Výstupy šířka a výška mapy 2D textury.<br /><br /> Texture dimenze můžete vzít v úvahu šířka a výška texture v shaderu.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Šířka a výška texture, vyjádřené jako vektor. Šířka jsou uloženy v první prvek vektoru. Výška je uložený v druhé elementu.|**Texture**<br /> Texture registrace, který je spojen s texture dimenze.|
|**Texel rozdílů**|Výstupy rozdíl (vzdálenost) mezi texels 2D texture mapy.<br /><br /> Můžete zkusit sousedních texel hodnoty v shaderu texel delta.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`<br /> Delta (vzdálenost) z texel na další texel (šikmo v kladné směru), vyjádřené jako vektoru normalizovaný texture prostoru. Pozice všech sousedních texels lze odvozovat selektivně ignoruje nebo negace U nebo V souřadnice delta.|**Texture**<br /> Texture registrace, který je spojen s texel delta.|
|**Ukázka textury**|Načítá vzorku barvy z mapy 2D textury na zadaný souřadnice.<br /><br /> Mapy textury můžete uvést podrobnosti barvu na povrchu objektu.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice, kde vzorku.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Ukázka barev.|**Texture**<br /> Texture registrace, který je spojen s ho.|