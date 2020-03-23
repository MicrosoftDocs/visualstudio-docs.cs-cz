---
title: Uzly filtru
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7627a5df1b3fcc5d26e33353e91f525b8083ccdf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637300"
---
# <a name="filter-nodes"></a>Uzly filtru

V návrháři shaderu převedou uzly filtrů vstup – například vzorek barvy nebo textury – na obrazovou hodnotu barvy. Tyto obrazové hodnoty barev se běžně používají v nefotorealistickém rendrování nebo jako součásti jiných vizuálních efektů.

## <a name="filter-node-reference"></a>Odkaz na uzel filtru

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Rozostření**|Rozostří obrazové body ve struktuře pomocí Gaussovy funkce.<br /><br /> Můžete to použít ke snížení detailů barev nebo šumu ve struktuře.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel u testovat.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Hodnota rozmazané barvy.|**Textura**<br /> Registr textur, který je přidružen k vzorkovači, který se používá při rozostření.|
|**Odsycení**|Snižuje množství barvy v zadané barvě.<br /><br /> Při odebrání barvy se hodnota barvy blíží ekvivalentu šedé stupnice.<br /><br /> **Vstup:**<br /><br /> `RGB`: `float3`<br /> Barva odsycení.<br /><br /> `Percent`: `float`<br /> Procento barvy odebrat, vyjádřené jako normalizované hodnoty v rozsahu [0, 1].<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Odsycená barva.|**Světlostí**<br /> Váhy, které jsou uvedeny na červené, zelené a modré barvy složek.|
|**Detekce hran**|Detekuje hrany v textury pomocí detektoru hran Canny. Obrazové body okrajů jsou výstupem jako bílé; obrazové body bez okrajů jsou výstupem jako černé.<br /><br /> Můžete to použít k identifikaci hran v textuře, takže můžete použít další efekty k léčbě obrazových bodů okrajů.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel u testovat.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Bílá, pokud je texel na okraji; jinak černá.|**Textura**<br /> Registr textur, který je přidružen k vzorkovači, který se používá při detekci hran.|
|**Zostřit**|Zostří texturu.<br /><br /> Můžete to použít ke zvýraznění jemných detailů ve struktuře.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel u testovat.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Hodnota rozmazané barvy.|**Textura**<br /> Registr textur, který je přidružen k vzorkovači, který se používá při ostření.|