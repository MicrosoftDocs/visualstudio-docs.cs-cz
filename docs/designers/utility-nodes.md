---
title: Uzly nástroje
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9c4c82d74c3878dd9937f81a83510e12f34a82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72634567"
---
# <a name="utility-nodes"></a>Uzly nástroje

V návrháři shaderu představují uzly nástrojů běžné a užitečné výpočty shaderu, které se nevejdou do ostatních kategorií. Některé uzly nástrojů provádějí jednoduché operace, jako je připojení vektorů dohromady nebo podmíněné výběry výsledků, a jiné provádějí složité operace, jako je například výpočetní příspěvky osvětlení podle populárních modelů osvětlení.

## <a name="utility-node-reference"></a>Odkaz na uzel nástroje

|Node|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Připojit vektor**|Vytvoří vektor připojením zadaných vstupů dohromady.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float` `float2`, , , nebo`float3`<br /> Hodnoty, které chcete připojit.<br /><br /> `Value to Append`: `float`<br /> Hodnota připojit.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2` `float3`, `float4` , nebo v závislosti na typu vstupu`Vector`<br /> Nový vektor.|Žádný|
|**Fresnelovy**|Vypočítá Fresnelovu spad ovou na základě zadané povrchové normály.<br /><br /> Fresnelova hodnota pádu vyjadřuje, jak těsně se normála povrchu aktuálního obrazového bodu shoduje s vektorem pohledu. Když jsou vektory zarovnány, výsledek funkce je 0; výsledek se zvyšuje, protože vektory se stávají méně podobnými a dosahují svého maxima, když jsou vektory ortogonové. Pomocí této skutečnosti můžete efekt více či méně zjevit na základě vztahu mezi orientací aktuálního obrazového bodu a fotoaparátem.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního obrazového bodu definovaná v tečném prostoru aktuálního obrazového bodu. Můžete použít k zneklidnění zdánlivé plochy normální, jako v normálnímapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Odrazivost aktuálního pixelu.|**Exponent**<br /> Exponent, který se používá k výpočtu Fresnelova pádu.|
|**Pokud uživatel**|Podmíněně vybere jeden ze tří potenciálních výsledků na komponentu. Podmínka je definována vztahem mezi dvěma dalšími zadanými vstupy.<br /><br /> Pro každou složku výsledku je zvolena odpovídající složka jednoho ze tří potenciálních výsledků na základě vztahu mezi odpovídajícími složkami prvních dvou vstupů.<br /><br /> **Vstup:**<br /><br /> `X`: `float` `float2`, `float3`, , , nebo`float4`<br /> Hodnota na levé straně porovnat.<br /><br /> `Y`: stejný typ jako vstup`X`<br /> Hodnota na pravé straně porovnat.<br /><br /> `X > Y`: stejný typ jako vstup`X`<br /> Hodnoty, které jsou `X` vybrány, když je větší než `Y`.<br /><br /> `X = Y`: stejný typ jako vstup`X`<br /> Hodnoty, které jsou `X` vybrány, když se rovná `Y`.<br /><br /> `X < Y`: stejný typ jako vstup`X`<br /> Hodnoty, které jsou `X` vybrány, pokud je menší než `Y`.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Zvolený výsledek na komponentu.|Žádný|
|**Lambert**|Vypočítá barvu aktuálního obrazového bodu podle modelu osvětlení Lambert pomocí zadaného normálu povrchu.<br /><br /> Tato barva je součtem okolních barev a rozptýleného osvětlení příspěvky pod přímým osvětlením. Okolní barva se blíží celkovému příspěvku nepřímého osvětlení, ale vypadá plochá a nudná bez pomoci dalšího osvětlení. Rozptýlené osvětlení pomáhá přidat objektu tvar a hloubku.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního obrazového bodu definovaná v tečném prostoru aktuálního obrazového bodu. Můžete použít k zneklidnění zdánlivé plochy normální, jako v normálnímapování.<br /><br /> `Diffuse Color`: `float3`<br /> Difuzní barva aktuálního obrazového bodu, obvykle **barva bodu**. Pokud není zadán žádný vstup, výchozí hodnota je bílá.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Difuzní barva aktuálního obrazového bodu.|Žádný|
|**Vektor masky**|Maskuje součásti zadaného vektoru.<br /><br /> Tuto možnost můžete použít k odebrání určitých barevných kanálů z hodnoty barvy nebo k zabránění tomu, aby určité součásti měly vliv na následné výpočty.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float4`<br /> Vektor maskovat.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Maskovaný vektor.|**Červená / X**<br /> **False** maskovat z červené (x) komponenty; jinak **True**.<br /><br /> **Zelená / Y**<br /> **False** maskovat zelené (y) komponenty; jinak **True**.<br /><br /> **Modrá / Z**<br /> **False** maskovat modré (z) komponenty; jinak **True**.<br /><br /> **Alfa / W**<br /> **False** maskovat alfa (w) komponenty; jinak **True**.|
|**Vektor odrazu**|Vypočítá vektor odrazu pro aktuální obrazový bod v tečném prostoru na základě polohy kamery.<br /><br /> Můžete použít k výpočtu odrazy, cubemap souřadnice, a zrcadlové osvětlení příspěvky<br /><br /> **Vstup:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Normála povrchu aktuálního obrazového bodu definovaná v tečném prostoru aktuálního obrazového bodu. Můžete použít k zneklidnění zdánlivé plochy normální, jako v normálnímapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Vektor odrazu.|Žádný|
|**Odlesk**|Vypočítá příspěvek zrcadlového osvětlení podle modelu osvětlení Phong pomocí zadaného normálu povrchu.<br /><br /> Zrcadlové osvětlení dodává objektu lesklý, reflexní vzhled, například vodu, plast nebo kovy.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního obrazového bodu definovaná v tečném prostoru aktuálního obrazového bodu. Můžete použít k zneklidnění zdánlivé plochy normální, jako v normálnímapování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Barevný příspěvek odlesků.|Žádný|