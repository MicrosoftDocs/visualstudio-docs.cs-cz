---
title: Uzly parametru
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f749d4ed6338919132e1c48d6da0572e3efe88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635016"
---
# <a name="parameter-nodes"></a>Uzly parametru

V návrháři shaderu představují uzly parametrů vstupy do shaderu, které jsou pod kontrolou aplikace na základě kreslení, například vlastnosti materiálu, směrová světla, poloha kamery a čas. Protože tyto parametry můžete změnit při každém volání kreslení, můžete použít stejný shader, který objektu poskytne různé vzhledy.

## <a name="parameter-node-reference"></a>Odkaz na uzel parametru

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Pozice světa kamery**|Pozice kamery ve světovém prostoru.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Poloha kamery.|Žádný|
|**Směr světla**|Vektor, který definuje směr, ve kterém je světlo vrháno ze světelného zdroje ve světovém prostoru.<br /><br /> Můžete použít k výpočtu osvětlení a odlesky příspěvky ve světovém prostoru.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Vektor z aktuálního obrazového bodu do zdroje světla.|Žádný|
|**Okolní materiál**|Příspěvek rozptýlené barvy aktuálního obrazového bodu, který je přiřazen k nepřímému osvětlení.<br /><br /> Difuzní barva obrazového bodu simuluje interakci osvětlení s drsnými povrchy. Parametr Okolní materiál můžete použít k aproximaci toho, jak nepřímé osvětlení přispívá k vzhledu objektu v reálném světě.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Difuzní barva aktuálního obrazového bodu, která je způsobena nepřímým osvětlením .|**Přístup**<br /> **Public** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnotu**<br /> Difuzní barva aktuálního obrazového bodu, která je způsobena nepřímým osvětlením – tedy okolním osvětlením.|
|**Materiál Difuzní**|Barva, která popisuje, jak aktuální pixel rozptyluje přímé osvětlení.<br /><br /> Difuzní barva obrazového bodu simuluje interakci osvětlení s drsnými povrchy. Pomocí parametru Difuza materiálu můžete změnit způsob, jakým aktuální obrazový bod rozptyluje přímé osvětlení – tedy směrové, bodové a bodové světlo.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Barva, která popisuje, jak aktuální pixel rozptyluje přímé osvětlení.|**Přístup**<br /> **Public** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnotu**<br /> Barva, která popisuje, jak aktuální pixel rozptyluje přímé osvětlení.|
|**Materiál emisivní**|Barevný příspěvek aktuálního obrazového bodu, který je připisován osvětlení, které poskytuje sám sobě.<br /><br /> Můžete použít k simulaci zářící objekt; to znamená objekt, který dodává své vlastní světlo. Toto světlo nemá vliv na jiné objekty.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Barevný příspěvek aktuálního pixelu, který je způsoben vlastním osvětlením.|**Přístup**<br /> **Public** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnotu**<br /> Barevný příspěvek aktuálního pixelu, který je způsoben vlastním osvětlením.|
|**Materiál zrcadlový**|Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.<br /><br /> Zrcadlová barva obrazového bodu simuluje interakci osvětlení s hladkými povrchy podobnými zrcadlům. Pomocí parametru Odlesk materiálu můžete změnit způsob, jakým aktuální obrazový bod odráží přímé osvětlení – tedy směrové, bodové a bodové světlo.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|**Přístup**<br /> **Public** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnotu**<br /> Barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|
|**Zrcadlová síla materiálu**|Skalární hodnota, která popisuje intenzitu odlesků.<br /><br /> Čím větší je zrcadlová síla, tím intenzivnější a dalekosáhlejší jsou zrcadlová světla.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Exponenciální termín, který popisuje intenzitu odlesků na aktuálním obrazovém bodu.|**Přístup**<br /> **Public** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnotu**<br /> Exponent, který definuje intenzitu odlesků na aktuálním obrazovém bodu.|
|**Normalizovaný čas**|Čas v sekundách, normalizované na rozsah [0, 1], tak, že když čas dosáhne 1, obnoví se na 0.<br /><br /> Můžete použít jako parametr ve výpočtech shaderu, například k animaci souřadnic textury, barevných hodnot nebo jiných atributů.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Normalizovaný čas v sekundách.|Žádný|
|**Čas**|Čas v sekundách.<br /><br /> Můžete použít jako parametr ve výpočtech shaderu, například k animaci souřadnic textury, barevných hodnot nebo jiných atributů.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Čas, v sekundách.|Žádný|