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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634567"
---
# <a name="utility-nodes"></a>Uzly nástroje

Uzly nástrojů v Návrháři shaderu reprezentují běžné, užitečné výpočty shaderu, které se nevejdou do ostatních kategorií. Některé uzly nástroje provádějí jednoduché operace, jako jsou například přidávání vektorů nebo výběr výsledků, a jiné provádějí komplexní operace, jako je například výpočetních příspěvků na základě oblíbených světelných modelů.

## <a name="utility-node-reference"></a>Odkaz na uzel nástroje

|Uzel|Podrobnosti|Vlastnosti|
|----------|-------------|----------------|
|**Připojit vektor**|Vytvoří vektor připojením zadaných vstupů dohromady.<br /><br /> **Vstup**<br /><br /> `Vector`: `float`, `float2` nebo `float3`<br /> Hodnoty, ke kterým se má připojit.<br /><br /> `Value to Append`: `float`<br /> Hodnota, která má být připojena.<br /><br /> **Výkonem**<br /><br /> `Output`: `float2`, `float3` nebo `float4` v závislosti na typu vstupu `Vector`<br /> Nový vektor.|Žádné|
|**Fresnelova poklesu**|Vypočítá Fresnelova poklesuy, které jsou založené na konkrétní ploše normální.<br /><br /> Hodnota poklesu Fresnelova poklesu vyjadřuje, jak blízko normálního povrchu aktuálního pixelu se shoduje s vektorem zobrazení. Když jsou vektory zarovnány, výsledek funkce je 0; výsledek se zvětšuje, protože vektory jsou méně podobné a dosáhnou maximální hodnoty, pokud jsou vektory kolmé. Tuto možnost můžete použít, chcete-li na základě vztahu mezi orientací aktuálního pixelu a fotoaparátem udělat větší nebo menší efekt.<br /><br /> **Vstup**<br /><br /> `Surface Normal`: `float3`<br /> Normální plocha aktuálního pixelu definovaná v tečném prostoru aktuálního pixelu. To můžete použít k perturbí zjevné normální plochy, jako je běžné mapování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float`<br /> Odrazivost aktuálního pixelu|**Zmocněn**<br /> Exponent, který se používá k výpočtu Fresnelova poklesuy.|
|**If**|Podmíněně zvolí jeden ze tří potenciálních výsledků na komponentu. Podmínka je definována vztahem mezi dvěma dalšími zadanými vstupy.<br /><br /> Pro každou komponentu výsledku se vybere odpovídající komponenta jednoho ze tří potenciálních výsledků na základě vztahu mezi odpovídajícími součástmi prvních dvou vstupů.<br /><br /> **Vstup**<br /><br /> `X`: `float`, `float2`, `float3` nebo `float4`<br /> Hodnota levé strany, která se má porovnat<br /><br /> `Y`: stejný typ jako vstupní `X`<br /> Hodnota pravé strany pro porovnání<br /><br /> `X > Y`: stejný typ jako vstupní `X`<br /> Hodnoty, které jsou zvoleny, když `X`, jsou větší než `Y`.<br /><br /> `X = Y`: stejný typ jako vstupní `X`<br /> Hodnoty, které jsou zvoleny, když je `X` rovna `Y`.<br /><br /> `X < Y`: stejný typ jako vstupní `X`<br /> Hodnoty, které jsou zvoleny, když je `X` menší než `Y`.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Zvolený výsledek na komponentu.|Žádné|
|**Lambert**|Vypočítá barvu aktuálního pixelu podle modelu osvětlení Lambert pomocí definovaného normálního povrchu.<br /><br /> Tato barva je součet okolních barev a rozptýlené světelné příspěvky v rámci přímého osvětlení. Okolní barva je přibližná z celkového podílu nepřímého osvětlení, ale vypadá plochě a matné bez pomoci dalšího osvětlení. Difúze světla pomáhá přidat tvar a hloubku objektu.<br /><br /> **Vstup**<br /><br /> `Surface Normal`: `float3`<br /> Normální plocha aktuálního pixelu definovaná v tečném prostoru aktuálního pixelu. To můžete použít k perturbí zjevné normální plochy, jako je běžné mapování.<br /><br /> `Diffuse Color`: `float3`<br /> Barva difúze aktuálního pixelu, obvykle **Barva bodu**. Pokud není zadaný žádný vstup, výchozí hodnota je bílá.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Barva difúze aktuálního pixelu|Žádné|
|**Vektor masky**|Maskuje součásti zadaného vektoru.<br /><br /> Tuto možnost můžete použít k odebrání specifických barevných kanálů z hodnoty barvy nebo k tomu, aby se určité komponenty neprojevily na dalších výpočtech.<br /><br /> **Vstup**<br /><br /> `Vector`: `float4`<br /> Vektor, který se má maskovat<br /><br /> **Výkonem**<br /><br /> `Output`: `float4`<br /> Maskovaný vektor.|**Červená/X**<br /> **False** pro maskování červené (x) komponenty; v opačném případě **true**.<br /><br /> **Zelená/Y**<br /> **False** pro maskování zelené (y) komponenty; v opačném případě **true**.<br /><br /> **Modrá/Z**<br /> **False** pro maskování složky Blue (z); v opačném případě **true**.<br /><br /> **Alfa/W**<br /> **False** pro maskování komponenty alfa (w); v opačném případě **true**.|
|**Vektor reflexe**|Vypočítá vektor odrazu pro aktuální pixel v prostoru tečny na základě pozice kamery.<br /><br /> Tuto možnost můžete použít k výpočtu odrazů, souřadnic cubemap a příspěvků po odlesku.<br /><br /> **Vstup**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Normální plocha aktuálního pixelu definovaná v tečném prostoru aktuálního pixelu. To můžete použít k perturbí zjevné normální plochy, jako je běžné mapování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Vektor reflexe.|Žádné|
|**Zrcadlový**|Vypočítá příspěvek na odlesky světla v závislosti na modelu osvětlení Phongova pomocí konkrétního povrchu, který je normální.<br /><br /> Zrcadlové osvětlení nabízí lesklý, odrážející vzhled objektu, například vodu, plast nebo kovy.<br /><br /> **Vstup**<br /><br /> `Surface Normal`: `float3`<br /> Normální plocha aktuálního pixelu definovaná v tečném prostoru aktuálního pixelu. To můžete použít k perturbí zjevné normální plochy, jako je běžné mapování.<br /><br /> **Výkonem**<br /><br /> `Output`: `float3`<br /> Příspěvek barvy pro odlesky světel.|Žádné|