---
title: Uzly konstanty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b062f6190213fc2b18670f50fdd527c4c3f212a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260061"
---
# <a name="constant-nodes"></a>Uzly konstanty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzly konstanty v Návrháři shaderu představují hodnoty literálu a interpolovaných atributy vrcholů ve výpočtech pixel shaderu. Protože vrchol atributy jsou interpolovány – a tedy se liší pro každý pixel – každá instance pixel shader obdrží jinou verzi konstanty. To poskytuje každý pixel jedinečný vzhled.  
  
## <a name="vertex-attribute-interpolation"></a>Interpolace atributů vrcholu  
 Obrázek 3D scény ve hře nebo aplikaci se provádí pomocí matematicky transformace počet objektů, které – které jsou definovány vrcholy, vrcholu atributy a primitivní definice – do na obrazovce pixelů. Všechny informace, které je nutné poskytnout pixel jedinečný vzhled poskytnutý prostřednictvím vrcholu atributy, které jsou prolnuty společně podle blízkosti je pixel různých vrcholy, které tvoří jeho *primitivní*. Jednoduchého typu je základní vykreslování element. To znamená jednoduché obrazce jako je například bod, řádku nebo trojúhelník. Pixel, který je velmi blízko pouze jedna z vrcholy obdrží konstanty, které jsou téměř stejné jako tento vrchol, ale obdrží konstanty, které je průměrem těchto vrcholy pixel, který má rovnoměrně rozloženy mezi všechny vrcholy jednoduchého typu. V programování grafiky, se označují jako konstanty, které přijímají pixely *interpolované*. Poskytuje konstantních dat na pixelů tímto způsobem vytváří velmi dobré vizuální kvality a současně snižuje požadavky na paměť nároky na místo a šířky pásma.  
  
 I když každá instance pixel shader přijímá pouze jednu sadu hodnot konstant a tyto hodnoty nedají změnit, jiné shaderem instance přijímat různých sad dat konstantní. Tento návrh umožňuje program shaderu na jinou barvu výstup pro každý pixel v primitivní vlastnost.  
  
## <a name="constant-node-reference"></a>Odkaz na konstantního uzlu  
  
|Uzel|Podrobnosti|Vlastnosti|  
|----------|-------------|----------------|  
|**Vektor kamery**|Vektor, který se táhne od aktuálního pixelu až po kameru v prostoru světa.<br /><br /> Vám může být využit k výpočtu odrazů v prostoru světa.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vektor od aktuálního pixelu až po kameru.|Žádné|  
|**Barevná konstanta**|Hodnota konstanty barvy.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Output**<br /> Hodnota barvy.|  
|**Konstanty**|Konstantní skalární hodnota.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Skalární hodnota.|**Output**<br /> Skalární hodnota.|  
|**2D konstanta**|Konstantu dvousložkového vektoru.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Hodnota vektoru.|**Output**<br /> Hodnota vektoru.|  
|**3D konstanta**|Konstantu třísložkového vektoru.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Hodnota vektoru.|**Output**<br /> Hodnota vektoru.|  
|**4D konstanta**|Konstantu čtyřsložkového vektoru.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Hodnota barvy.|**Output**<br /> Hodnota vektoru.|  
|**Normalizované umístění**|Pozice aktuálního pixelu vyjádřena v souřadnicích normalizované zařízení.<br /><br /> Souřadnice x a osy y mají hodnoty v rozsahu [-1, 1], souřadnice z má hodnotu v rozsahu [0, 1], a w komponenta obsahuje hodnotu hloubka bodu v prostoru zobrazení; w není normalizovaná.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádné|  
|**Barva bodu**|Rozptýlení barvy aktuálního pixelu, což je kombinací materiálu rozptýlení barvy a vrcholu barevnými atributy.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Rozptýlení barvy aktuálního pixelu.|Žádné|  
|**Hloubka bodu**|Hloubka aktuálního pixelu v prostoru zobrazení.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádné|  
|**Normalizovaná hloubka bodu**|Hloubka aktuálního pixelu vyjádřena v souřadnicích normalizované zařízení.<br /><br /> Výsledek obsahuje hodnotu v rozsahu [0, 1].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Hloubka aktuálního pixelu.|Žádné|  
|**Umístění obrazovky**|Pozice aktuálního pixelu vyjádřena v souřadnicovém systému obrazovky.<br /><br /> Souřadnice obrazovky jsou založeny na aktuální zobrazení. X a y součásti obsahují souřadnice obrazovky, z komponenty obsahuje hloubky normalizovány na rozsah [0, 1], a w komponenta obsahuje hodnotu hloubky v prostoru zobrazení.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádné|  
|**Normála povrchu**|Normála povrchu aktuálního pixelu v prostoru objektu.<br /><br /> To můžete použít pro výpočet přínosů světla a odrazů v prostoru objektu.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normála povrchu aktuálního pixelu.|Žádné|  
|**Vektor kamery prostoru tečny**|Vektor, který se táhne od aktuálního pixelu až po kameru v tečném prostoru.<br /><br /> Vám může být využit k výpočtu odrazů v tečném prostoru.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Vektor od aktuálního pixelu až po kameru.|Žádné|  
|**Směr světla prostoru tečny**|Vektor definující směr, ve kterém dopadá světlo ze světelného zdroje v tečném prostoru aktuálního pixelu.<br /><br /> To slouží k výpočtu osvětlení a množství odrazů v tečném prostoru.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Vektor od aktuálního pixelu ke zdroji světla.|Žádné|  
|**Normála ve světových souřadnicích**|Normála povrchu aktuálního pixelu v prostoru světa.<br /><br /> To můžete použít pro výpočet přínosů světla a odrazů v prostoru světa.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normála povrchu aktuálního pixelu.|Žádné|  
|**Pozice světa**|Pozice aktuálního pixelu v prostoru světa.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozice aktuálního pixelu.|Žádné|



