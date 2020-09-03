---
title: Uzly parametrů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e6d90e882e40bff84898efdd20579abbfd4d309
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664147"
---
# <a name="parameter-nodes"></a>Uzly parametru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrháři shaderu uzly parametrů představují vstupy do shaderu, který je pod kontrolou aplikace na jednom vykreslení, například vlastnosti materiálu, směrové svítilny, pozice kamery a čas. Vzhledem k tomu, že tyto parametry lze změnit pomocí každého volání remíz, můžete použít stejný shader k přidělení objektu různým vzhledům.

## <a name="parameter-node-reference"></a>Odkaz na uzel parametru

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Pozice kamery ve světě**|Pozice kamery v prostoru světa.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Pozice kamery|Žádné|
|**Směr světla**|Vektor definující směr, ve kterém je světlo z světelného zdroje v prostoru světa.<br /><br /> Tuto možnost můžete použít k výpočtu osvětlení a odlesků příspěvků v prostoru světa.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního pixelu ke zdroji světla.|Žádné|
|**Okolí materiálu**|Podíl barvy difúze aktuálního pixelu, který je přidělený na nepřímý osvětlení.<br /><br /> Barva difúze v pixelu simuluje, jak světlo pracuje s hrubou rovinou. Pomocí parametru materiál Ambientd se můžete rozblížit, jak nepřímé osvětlení přispívá k vzhledu objektu v reálném světě.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Rozptýlení barvy aktuálního pixelu, která je způsobena nepřímým osvětlením – to znamená vnější.|**Přístup**<br /> **Veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**<br /> Rozptýlení barvy aktuálního pixelu, která je způsobena nepřímým osvětlením – to znamená vnější.|
|**Materiálové difúze**|Barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.<br /><br /> Barva difúze v pixelu simuluje, jak světlo pracuje s hrubou rovinou. Pomocí parametru materiál difúze můžete změnit, jak aktuální pixel rozptýlí přímé osvětlení – to znamená, směrové, nebo bodové světlo.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.|**Přístup**<br /> **Veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**<br /> Barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.|
|**Vyzařující materiálu**|Podíl barvy aktuálního pixelu, který je přidělený na osvětlení, které poskytuje sám sobě.<br /><br /> Tuto možnost můžete použít k simulaci objektu záře; To znamená, že objekt, který poskytuje vlastní světlo. Toto světlo nemá vliv na jiné objekty.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Podíl barvy aktuálního pixelu, který je z důvodu samostatně poskytnutého osvětlení.|**Přístup**<br /> **Veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**<br /> Podíl barvy aktuálního pixelu, který je z důvodu samostatně poskytnutého osvětlení.|
|**Odlesky materiálu**|Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.<br /><br /> Zrcadlová barva pixelu simuluje, jak světlo pracuje s hladkými, zrcadlově podobnými povrchy. Pomocí parametru materiálové odlesky můžete změnit, jak aktuální pixel odráží přímé osvětlení – to znamená, směrové, bodové a bodové světlo.<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|**Přístup**<br /> **Veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**<br /> Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|
|**Materiálově odlesky energie**|Skalární hodnota, která popisuje intenzitu zrcadlových světel.<br /><br /> Čím větší dojde k odlesku, tím přesnější a daleko se blíží odleskům.<br /><br /> **Výkonem**<br /><br /> `Output`: `float`<br /> Exponenciální pojem, který popisuje intenzitu zrcadlových světel na aktuálním pixelu.|**Přístup**<br /> **Veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**<br /> Exponent, který definuje intenzitu zrcadlových světel na aktuálním pixelu.|
|**Normalizovaný čas**|Čas v sekundách normalizovaný na rozsah [0, 1], který v případě, že čas dosáhne hodnoty 1, se resetuje na 0.<br /><br /> Můžete ji použít jako parametr ve výpočtech shaderu, například pro animaci souřadnic textury, barevné hodnoty nebo jiné atributy.<br /><br /> **Výkonem**<br /><br /> `Output`: `float`<br /> Normalizovaný čas (v sekundách).|Žádné|
|**Čas**|Čas v sekundách.<br /><br /> Můžete ji použít jako parametr ve výpočtech shaderu, například pro animaci souřadnic textury, barevné hodnoty nebo jiné atributy.<br /><br /> **Výkonem**<br /><br /> `Output`: `float`<br /> Čas (v sekundách).|Žádné|
