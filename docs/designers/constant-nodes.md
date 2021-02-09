---
title: Uzly konstanty
description: Přečtěte si o konstantních uzlech, které reprezentují hodnoty literálu a interpolované atributy vrcholu ve výpočtech obrazového shaderu v Návrháři shaderu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79fd16f42629bdf242d70432065d077efd5883eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917209"
---
# <a name="constant-nodes"></a>Uzly konstanty

V Návrháři shaderu konstantní uzly reprezentují hodnoty literálu a interpolované atributy vrcholu ve výpočtech obrazového shaderu. Vzhledem k tomu, že atributy vrcholu jsou interpolované – a proto jsou pro každý pixel rozdílné, každá instance pixel-shader obdrží jinou verzi konstanty. To dává každému obrazovému obrazci jedinečný vzhled.

## <a name="vertex-attribute-interpolation"></a>Interpolace atributu vrcholu

Obrázek 3D scény ve hře nebo aplikaci vytváří matematicky transformující počet objektů, které jsou definovány vrcholy, atributy vrcholů a primitivní definice – do pixelů na obrazovce. Všechny informace, které jsou vyžadovány k přidělení pixelu jeho jedinečného vzhledu, jsou dodány prostřednictvím atributů vrcholu, které jsou kombinovány podle blízkosti obrazového bodu s různými vrcholy, které tvoří *primitivní*. Primitivum je základní element vykreslování; To znamená jednoduchý tvar, jako je například bod, čára nebo trojúhelník. Pixel, který je blízko pouze jednoho z vrcholů, přijímá konstanty, které jsou téměř totožné s tímto vrcholem, ale pixel, který je rovnoměrně rozložen mezi všechny vrcholy primitivních hodnot, přijímá konstanty, které jsou průměrem těchto vrcholů. V programování grafiky jsou konstanty, které pixely obdrží, označeny jako *interpolované*. Poskytnutí konstantních dat na pixely tímto způsobem vytváří velmi dobrou vizuální kvalitu a zároveň omezuje nároky na paměť a požadavky na šířku pásma.

I když každá instance pixel-shaderu přijímá jenom jednu sadu konstantních hodnot a nemůže tyto hodnoty změnit, jiné instance pixel shaderu obdrží různé sady konstantních dat. Tento návrh umožňuje programu shaderu vytvořit jiný barevný výstup pro každý pixel v primitivu.

## <a name="constant-node-reference"></a>Odkaz na konstantní uzel

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Vektor kamery**|Vektor, který se od aktuálního pixelu rozšíří do kamery v prostoru světa.<br /><br /> Tuto možnost můžete použít k výpočtu odrazů v prostoru světa.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu do kamery.|Žádné|
|**Barevná konstanta**|Hodnota konstantní barvy.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Výstup**<br /> Hodnota barvy.|
|**Změnil**|Konstantní skalární hodnota.<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Skalární hodnota.|**Výstup**<br /> Skalární hodnota.|
|**2D konstanta**|Vektorová konstanta dvou komponent.<br /><br /> **Výstup**<br /><br /> `Output`: `float2`<br /> Hodnota Vector.|**Výstup**<br /> Hodnota Vector.|
|**3D konstanta**|Vektorová konstanta se třemi komponentami.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Hodnota Vector.|**Výstup**<br /> Hodnota Vector.|
|**4D – konstanta**|Vektorová konstanta se čtyřmi komponentami.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Výstup**<br /> Hodnota Vector.|
|**Normalizovaná poloha**|Pozice aktuálního pixelu vyjádřená v normalizovaných souřadnicích zařízení.<br /><br /> Souřadnice x a y mají hodnoty v rozsahu [-1, 1], souřadnice z-souřadnic má hodnotu v rozsahu [0, 1] a komponenta w obsahuje hodnotu hloubky bodu v prostoru zobrazení; w není normalizován.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu|Žádné|
|**Barva bodu**|Barva difúze aktuálního pixelu, která je kombinací atributů barva difúze a barvy vrcholu.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Barva difúze aktuálního pixelu|Žádné|
|**Hloubka bodu**|Hloubka aktuálního pixelu v prostoru zobrazení<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádné|
|**Normalizovaná hloubka bodu**|Hloubka aktuálního pixelu vyjádřená v normalizovaných souřadnicích zařízení.<br /><br /> Výsledek má hodnotu v rozsahu [0, 1].<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádné|
|**Pozice obrazovky**|Pozice aktuálního pixelu vyjádřená v souřadnicích obrazovky<br /><br /> Souřadnice obrazovky jsou založené na aktuálním zobrazení. Komponenty x a y obsahují souřadnice obrazovky, komponenta z obsahuje normalizovanou hloubku do rozsahu [0, 1] a komponenta w obsahuje hodnotu hloubky v prostoru zobrazení.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu|Žádné|
|**Normální povrch**|Normální plocha aktuálního pixelu v prostoru objektu.<br /><br /> Tuto možnost můžete použít k výpočtu příspěvků světla a odrazů v prostoru objektu.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Normální plocha aktuálního pixelu.|Žádné|
|**Vektor kamery prostoru tečny**|Vektor, který se od aktuálního pixelu rozšíří na kameru v tečném prostoru.<br /><br /> Tuto možnost můžete použít k výpočtu odrazů v tečném prostoru.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu do kamery.|Žádné|
|**Směr světla prostoru tečny**|Vektor definující směr, ve kterém je světlo ze zdroje světla v tečném prostoru aktuálního pixelu.<br /><br /> Tuto možnost můžete použít k výpočtu osvětlení a odlesků příspěvků v tečném prostoru.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu ke zdroji světla.|Žádné|
|**Světový normální**|Normální plocha aktuálního pixelu v prostoru světa.<br /><br /> Tuto možnost můžete použít k výpočtu příspěvků světla a odrazů v prostoru světa.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Normální plocha aktuálního pixelu.|Žádné|
|**Světová pozice**|Pozice aktuálního pixelu v prostoru světa.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu|Žádné|