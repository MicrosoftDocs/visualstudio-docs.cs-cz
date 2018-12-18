---
title: Uzly filtru
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cf0902847899f8796ac34765c66c79530248e81
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922224"
---
# <a name="filter-nodes"></a>Uzly filtrů

V Návrháři shaderu uzly filtrů transformace vstup – například ukázku barvu nebo texture – na hodnotu názorné barev. Tyto hodnoty názorné barva běžně se používají v jiných fotorealistické vykreslování nebo jako součásti v jiných vizuálních efektů.

## <a name="filter-node-reference"></a>Odkaz na uzlu filtru

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Rozostření**|Rozostří pixelů texturou pomocí Gaussovské funkce.<br /><br /> Můžete použít ke snížení podrobnosti barvu nebo šumu v texturou.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel k testování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Hodnota rozostřeného barvy.|**Texture**<br /> Texture registrace, který je spojen s sampler, který se používá během rozostření.|
|**Snížit sytost**|Snižuje množství barvy v určené barvy.<br /><br /> Barva odstraněno, hodnoty barvy blíží šedé ekvivalentní.<br /><br /> **Vstup:**<br /><br /> `RGB`: `float3`<br /> Barvy, která má snížit sytost.<br /><br /> `Percent`: `float`<br /> Procento barvu, kterou chcete odebrat, vyjádřené jako normalizovanou hodnotu v rozsahu [0, 1].<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Odbarvený barva.|**Světlostí**<br /> Váhu, které jsou přiřazeny k součástem červenou, zelenou a modrou barvu.|
|**Detekce okrajů**|Detekuje okraje v texturou pomocí detektor Canny okraj. Okrajové jsou výstupem jako bílé; jako černá jsou výstupem bez edge pixelů.<br /><br /> Můžete použít k identifikaci okraje v texturou tak, aby může používat další důsledky zacházet s hraniční pixelů.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel k testování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Prázdné, pokud texel na okraj; začernit, jinak hodnota.|**Texture**<br /> Texture registrace, který je spojen s sampler, který se používá během zjišťování okraj.|
|**Zostřit**|Zvýší texturou.<br /><br /> To vám pomůže zvýrazněte podrobné detaily v texturou.<br /><br /> **Vstup:**<br /><br /> `UV`: `float2`<br /> Souřadnice texel k testování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Hodnota rozostřeného barvy.|**Texture**<br /> Texture registrace, který je spojen s sampler, který se používá během zostření.|