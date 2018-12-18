---
title: Uzly nástroje
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4d3371001c3df3b5233562ce7b30e711ed12d4c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918202"
---
# <a name="utility-nodes"></a>Nástroj uzly

V Návrháři shaderu nástroj uzly představují běžné, užitečné shaderu výpočty, které se nehodí přehledně do jiné kategorie. Některé uzly nástroj provádějí jednoduché operace, například připojování vektory společně nebo podmíněně výběr výsledky a ostatní provádět komplexní operace například computing osvětlení příspěvky podle oblíbených osvětlení modelů.

## <a name="utility-node-reference"></a>Odkaz na nástroj uzlu

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Připojit vektoru**|Vytvoří vektor připojením zadané vstupy společně.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float`, `float2`, nebo `float3`<br /> Hodnoty k připojení k.<br /><br /> `Value to Append`: `float`<br /> Hodnota pro připojení.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`, `float3`, nebo `float4` v závislosti na typu vstupu `Vector`<br /> Nové vektoru.|Žádné|
|**Fresnel**|Vypočítá podzim – vypnuté Fresnel podle zadaného prostor normální.<br /><br /> Fresnel poklesu hodnota vyjadřuje, jak přesně shoduje s vektoru zobrazení článku prostor normální z aktuální pixelů. Když je zarovnán vektory, je výsledkem funkce 0; výsledek zvyšuje vektory jsou méně podobné a dosáhne maximálního po ortogonální vektory. Můžete to být vyšší nebo nižší zřejmá vliv na základě vztahu mezi orientaci aktuální pixelů a kamera.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Prostor normální aktuální pixelů, definované v prostoru tečný aktuální pixelů. To vám pomůže perturb zřejmá prostor normální, stejně jako normální mapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Odrazivostí aktuální pixelů.|**Exponent**<br /> Exponent, na který se používá k výpočtu patří – vypnuté Fresnel.|
|**Pokud**|Podmíněná zvolí jeden z tři potenciální výsledky podle součásti. Podmínka je definována vztah mezi dvěma zadané vstupy.<br /><br /> Pro každou součást výsledku odpovídající součást jednu ze tří potenciální výsledků jste vybrali, na základě vztahu mezi odpovídající součástí první dva vstupy.<br /><br /> **Vstup:**<br /><br /> `X`: `float`, `float2`, `float3`, nebo `float4`<br /> Na levé straně hodnoty k porovnání.<br /><br /> `Y`: stejný typ jako vstup `X`<br /> Pravé straně hodnoty k porovnání.<br /><br /> `X > Y`: stejný typ jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` je větší než `Y`.<br /><br /> `X = Y`: stejný typ jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` rovná `Y`.<br /><br /> `X < Y`: stejný typ jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` je menší než `Y`.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Zvolený způsobit za součást.|Žádné|
|**Společnost Lambert**|Vypočítá barva aktuální pixelů podle modelu osvětlení společnost Lambert, pomocí zadané prostor normální.<br /><br /> Tato barva je součet hodnot vedlejším barvy a rozptýlených osvětlení příspěvky za přímé osvětlení. Okolní barva blíží celkový příspěvek nepřímého osvětlení, ale vypadá plochý a matné bez pomoci další osvětlení. Rozptýlené osvětlení pomáhá přidat tvar a hloubku k objektu.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Prostor normální aktuální pixelů, definované v prostoru tečný aktuální pixelů. To vám pomůže perturb zřejmá prostor normální, stejně jako normální mapování.<br /><br /> `Diffuse Color`: `float3`<br /> Rozptýlené barva aktuální pixelů, obvykle **bodu barva**. Pokud je k dispozici žádný vstup, výchozí hodnota je bílé.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Rozptýlené barva aktuální pixelů.|Žádné|
|**Maska vektoru**|Masek součástí zadaný vektoru.<br /><br /> Můžete to odebrání kanály konkrétní barev hodnotu barvu nebo zabránit konkrétní součásti mají vliv na následné výpočty.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float4`<br /> Vektoru k maskování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Maskované vektoru.|**Red / X**<br /> **False** k maskování na komponentu červený (x); jinak **True**.<br /><br /> **Zelená / Y**<br /> **False** k maskování na komponentu zelený (y); jinak **True**.<br /><br /> **Modrá nebo Z**<br /> **False** k maskování na komponentu blue (z); jinak **True**.<br /><br /> **Alpha / W**<br /> **False** k maskování na komponentu alpha (w); jinak **True**.|
|**Vektor reflexe**|Vypočítá vektoru reflexe pro aktuální pixelů v tečný prostoru, na základě pozice fotoaparát.<br /><br /> Můžete použít k výpočtu odrazů, cubemap souřadnice a zrcadlová osvětlení příspěvky<br /><br /> **Vstup:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Prostor normální aktuální pixelů, definované v prostoru tečný aktuální pixelů. To vám pomůže perturb zřejmá prostor normální, stejně jako normální mapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Reflexe vektoru.|Žádné|
|**Zrcadlová**|Vypočítá příspěvku zrcadlová osvětlení podle modelu osvětlení Phong, pomocí zadané prostor normální.<br /><br /> Zrcadlová osvětlení dává lesklý a reflexivní vzhled do objektu, například horních, plastu nebo kovů.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Prostor normální aktuální pixelů, definované v prostoru tečný aktuální pixelů. To vám pomůže perturb zřejmá prostor normální, stejně jako normální mapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Barva podíl zrcadlová světla.|Žádné|