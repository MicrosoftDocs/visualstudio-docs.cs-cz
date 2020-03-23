---
title: Uzly konstanty
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fd5a9b2d179a27ec0cf34f5388b30ebb563ad4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637360"
---
# <a name="constant-nodes"></a>Uzly konstanty

V návrháři shaderu představují konstantní uzly hodnoty literálu a interpolované atributy vrcholů ve výpočtech shaderu obrazových bodů. Vzhledem k tomu, že atributy vrcholu jsou interpolovány – a tak se pro každý obrazový bod liší – každá instance shaderu obrazových bodů obdrží jinou verzi konstanty. To dává každému pixelu jedinečný vzhled.

## <a name="vertex-attribute-interpolation"></a>Interpolace atributu vrcholu

Obraz 3D scény ve hře nebo aplikaci je tvořen matematicky transformací několika objektů, které jsou definovány vrcholy, atributy vrcholů a primitivními definicemi, na obrazové body na obrazovce. Všechny informace, které jsou požadovány k tomu, aby pixel jeho jedinečný vzhled je dodáván prostřednictvím atributy vrchol, které jsou prolnuty podle pixelu blízkosti různých vrcholů, které tvoří jeho *primitivní*. Primitivní je základní prvek vykreslování; to znamená jednoduchý tvar, například bod, čáru nebo trojúhelník. Obrazový bod, který je velmi blízko pouze jednoho z vrcholů, obdrží konstanty, které jsou téměř identické s tímto vrcholem, ale obrazový bod, který je rovnoměrně rozložen mezi všechny vrcholy primitiva, přijímá konstanty, které jsou průměrem těchto vrcholů. V programování grafiky jsou konstanty, které pixely přijímají, *údajně interpolovány*. Poskytování konstantních dat pixelům tímto způsobem vytváří velmi dobrou vizuální kvalitu a současně snižuje nároky na paměť a šířku pásma.

Přestože každá instance shaderu obrazových bodů obdrží pouze jednu sadu konstantních hodnot a nemůže tyto hodnoty změnit, různé instance shaderu obrazových bodů obdrží různé sady konstantních dat. Tento návrh umožňuje programu shaderu vytvářet jiný barevný výstup pro každý obrazový bod v primitivu.

## <a name="constant-node-reference"></a>Odkaz na konstantní uzel

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Vektor fotoaparátu**|Vektor, který sahá od aktuálního pixelu ke kameře ve světovém prostoru.<br /><br /> Můžete použít k výpočtu odrazy ve světovém prostoru.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu do fotoaparátu.|Žádný|
|**Barevná konstanta**|Konstantní hodnota barvy.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Výstup**<br /> Hodnota barvy.|
|**Trvalé**|Konstantní skalární hodnota.<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Skalární hodnota.|**Výstup**<br /> Skalární hodnota.|
|**2D konstanta**|Dvousložková vektorová konstanta.<br /><br /> **Výstup**<br /><br /> `Output`: `float2`<br /> Vektorová hodnota.|**Výstup**<br /> Vektorová hodnota.|
|**3D konstanta**|Třísložková vektorová konstanta.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Vektorová hodnota.|**Výstup**<br /> Vektorová hodnota.|
|**4D konstanta**|Čtyřsložková vektorová konstanta.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Výstup**<br /> Vektorová hodnota.|
|**Normalizovaná pozice**|Pozice aktuálního pixelu vyjádřená v normalizovaných souřadnicích zařízení.<br /><br /> Souřadnice x a souřadnice y mají hodnoty v rozsahu [-1, 1], souřadnice z má hodnotu v rozsahu [0, 1] a komponenta w obsahuje hodnotu hloubky bodu v prostoru pohledu; w není normalizován.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádný|
|**Barva bodu**|Difuzní barva aktuálního obrazového bodu, což je kombinace difúzní barvy materiálu a atributů barvy vrcholu.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Difuzní barva aktuálního obrazového bodu.|Žádný|
|**Hloubka bodu**|Hloubka aktuálního obrazového bodu v prostoru zobrazení.<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádný|
|**Normalizovaná hloubka bodu**|Hloubka aktuálního pixelu vyjádřená v normalizovaných souřadnicích zařízení.<br /><br /> Výsledek má hodnotu v rozsahu [0, 1].<br /><br /> **Výstup**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádný|
|**Poloha obrazovky**|Pozice aktuálního pixelu vyjádřená v souřadnicích obrazovky.<br /><br /> Souřadnice obrazovky jsou založeny na aktuálním výřezu. Komponenty x a y obsahují souřadnice obrazovky, komponenta z obsahuje hloubku normalizovanou na rozsah [0, 1] a komponenta w obsahuje hodnotu hloubky v prostoru pohledu.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádný|
|**Normální povrch**|Normála povrchu aktuálního obrazového bodu v prostoru objektu.<br /><br /> Můžete to použít k výpočtu příspěvků osvětlení a odrazů v prostoru objektu.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Normála povrchu aktuálního obrazového bodu.|Žádný|
|**Vektor tečné vesmírné kamery**|Vektor, který sahá od aktuálního pixelu ke kameře v tečném prostoru.<br /><br /> Můžete to použít k výpočtu odrazů v tečném prostoru.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu do fotoaparátu.|Žádný|
|**Směr světla tečného prostoru**|Vektor, který definuje směr, ve kterém je světlo vrháno ze zdroje světla v tečném prostoru aktuálního obrazového bodu.<br /><br /> Můžete to použít k výpočtu osvětlení a odlesků příspěvků v tečném prostoru.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního obrazového bodu do zdroje světla.|Žádný|
|**Svět Normální**|Normála povrchu aktuálního obrazového bodu ve světovém prostoru.<br /><br /> Můžete použít k výpočtu osvětlení příspěvky a odrazy ve světovém prostoru.<br /><br /> **Výstup**<br /><br /> `Output`: `float3`<br /> Normála povrchu aktuálního obrazového bodu.|Žádný|
|**Světová pozice**|Pozice aktuálního pixelu ve světovém prostoru.<br /><br /> **Výstup**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádný|