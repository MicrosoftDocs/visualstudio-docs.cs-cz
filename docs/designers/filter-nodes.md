---
title: Uzly filtru
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfc74287706976f96a5e565bef3da1493cd44866
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769280"
---
# <a name="filter-nodes"></a>Uzly filtru

V Návrháři shaderu budou uzly filtrovat, transformují vstup – například vzorek barvy nebo textury – na hodnotu figurative barvy. Tyto hodnoty barvy figurative se běžně používají v fotorealistickém vykreslování nebo jako komponenty v jiných vizuálních efektech.

## <a name="filter-node-reference"></a>Odkaz na uzel filtru

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Efekt**|Rozostří pixely v textuře pomocí Gaussovské funkce.<br /><br /> Tuto možnost můžete použít k omezení barevného detailu nebo šumu v textuře.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice Texel k otestování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Hodnota rozmazaných barev|**Textura**<br /> Registr textury, který je přidružen k vzorkovači používanému při rozostření.|
|**Ubrat sytost**|Zmenší velikost barvy v zadané barvě.<br /><br /> Při odebrání barvy se hodnota barvy blíží jejímu ekvivalentu v šedé škále.<br /><br /> **Vstup**<br /><br /> `RGB`: `float3`<br /> Barva, která se má desytost.<br /><br /> `Percent`: `float`<br /> Procento barvy, která se má odebrat, vyjádřená jako normalizovaná hodnota v rozsahu [0, 1].<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Desytost barvy.|**Světlost**<br /> Váhy, které jsou dány pro barevné komponenty červené, zelené a modré.|
|**Detekce hran**|Detekuje hrany v textuře pomocí detektoru Canny Edge. Hranové pixely jsou ve výstupu bílé; jiné než hraniční obrazové body jsou výstupem jako černé.<br /><br /> Tuto možnost můžete použít k identifikaci hran v textuře, aby bylo možné použít další efekty pro zpracování hraničních pixelů.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice Texel k otestování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Bílá, pokud je Texel na okraji; jinak černá.|**Textura**<br /> Registr textury, který je přidružen k vzorkovači používanému při detekci hran.|
|**Míru**|Zostří texturu.<br /><br /> Tuto možnost můžete použít k zdůraznění podrobných podrobností v textuře.<br /><br /> **Vstup**<br /><br /> `UV`: `float2`<br /> Souřadnice Texel k otestování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Hodnota rozmazaných barev|**Textura**<br /> Registr textury, který je přidružen k vzorkovači používanému při zaostření.|