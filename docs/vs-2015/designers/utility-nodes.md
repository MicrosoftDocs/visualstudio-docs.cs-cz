---
title: Uzly nástroje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff732221-b731-424c-ad5b-82ef5f21dff5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d85735c5fb355163f2003a27a96675ed097d66e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174418"
---
# <a name="utility-nodes"></a>Uzly nástroje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrháři shaderu představují nástroj uzly výpočtech shaderu běžné, užitečné, které se nehodí do jiné kategorie elegantně. Některé uzly nástroje provádět jednoduché operace, jako je například přidávání vektory společně nebo zvolením podmíněně a ostatní provádět složité operace, jako je výpočet přínosů světla podle modely osvětlení Oblíbené.  
  
## <a name="utility-node-reference"></a>Referenční dokumentace nástroje uzlu  
  
|Uzel|Podrobnosti|Vlastnosti|  
|----------|-------------|----------------|  
|**Připojit vektor**|Vytvoří vektor přidáním zadané vstupy dohromady.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float`, `float2`, nebo `float3`<br /> Hodnoty pro připojení k.<br /><br /> `Value to Append`: `float`<br /> Hodnota pro přidání.<br /><br /> **Výstup:**<br /><br /> `Output`: `float2`, `float3`, nebo `float4` v závislosti na typu vstupu `Vector`<br /> Nové vektoru.|Žádné|  
|**Fresnelova**|Vypočítá Fresnelova poklesu podle zadaného normála povrchu.<br /><br /> Hodnota Fresnelova poklesu vyjadřuje, jak blízko se normála povrchu aktuálního pixelu shoduje s vektorem zobrazení. Pokud jsou vektory zarovnané, výsledek funkce je 0; výsledek zvyšuje jsou vektory méně podobné a dosáhne maximálního, pokud jsou vektory ortogonální. Můžete to provést efektu více či méně zřejmé vychází ze vztahu mezi orientací aktuálního pixelu a kamery.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního pixelu, definované v tečném prostoru aktuálního pixelu. Může být využit k perturb normální, stejně jako v normálním mapování na povrchu zřejmý.<br /><br /> **Výstup:**<br /><br /> `Output`: `float`<br /> Odrazivost aktuálního pixelu.|**Exponent**<br /> Exponent, který se používá k výpočtu Fresnelova poklesu.|  
|**If**|Podmíněně vybere jeden ze tří možných výsledků na komponentu. Podmínka je definována vztah mezi dvěma zadané vstupy.<br /><br /> Pro každou komponentu výsledku platí je vybrána odpovídající komponenta jednoho ze tří možných výsledků na základě vztahu mezi odpovídajícími komponentami prvních dvou vstupů.<br /><br /> **Vstup:**<br /><br /> `X`: `float`, `float2`, `float3`, nebo `float4`<br /> Levá strana příkazu hodnota pro porovnání.<br /><br /> `Y`: stejného typu jako vstup `X`<br /> Pravá strana hodnota pro porovnání.<br /><br /> `X > Y`: stejného typu jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` je větší než `Y`.<br /><br /> `X = Y`: stejného typu jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` rovná `Y`.<br /><br /> `X < Y`: stejného typu jako vstup `X`<br /> Hodnoty, které je možné zvolit při `X` je menší než `Y`.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Zvolený způsobit za součást.|Žádné|  
|**Lambertova**|Vypočítá barvy aktuálního pixelu podle Lambertova modelu osvětlení, pomocí zadané normála povrchu.<br /><br /> Tato barva je SUMA okolní barvy a difúzním světlem příspěvků v rámci přímé osvětlení. Okolní barvy celkovému podílu nepřímého světla, ale vypadá ploše a mdle bez pomoci další osvětlení. Rozptýlené světlo pomáhá přidat objektu tvar a hloubku.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního pixelu, definované v tečném prostoru aktuálního pixelu. Může být využit k perturb normální, stejně jako v normálním mapování na povrchu zřejmý.<br /><br /> `Diffuse Color`: `float3`<br /> Rozptýlení barvy aktuálního pixelu, obvykle **barva bodu**. Pokud je k dispozici žádný vstup, výchozí hodnota je bílé.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Rozptýlení barvy aktuálního pixelu.|Žádné|  
|**Maskovat vektor**|Masky součástí zadané vektoru.<br /><br /> Může být využit k odebrání specifického barevného kanálu z hodnoty barvy a proti efektu následných výpočtů.<br /><br /> **Vstup:**<br /><br /> `Vector`: `float4`<br /> Vektor k maskování.<br /><br /> **Výstup:**<br /><br /> `Output`: `float4`<br /> Maskované vektoru.|**Červená / X**<br /> **False** pro zamaskování červené (x); v opačném případě **True**.<br /><br /> **Zelená / Y**<br /> **False** pro zamaskování zelené (y); v opačném případě **True**.<br /><br /> **Modrá / Z**<br /> **False** pro zamaskování modré (z); v opačném případě **True**.<br /><br /> **Alfa / W**<br /> **False** pro zamaskování alfa (w); v opačném případě **True**.|  
|**Zrcadlit vektor**|Vypočítá zrcadlit vektor pro aktuální pixel tečného prostoru na základě pozice kamery.<br /><br /> Může být využit k výpočtu odrazů, souřadnic mapy krychle a podílu rozptylu světla<br /><br /> **Vstup:**<br /><br /> `Tangent Space Surface Normal`: `float3`<br /> Normála povrchu aktuálního pixelu, definované v tečném prostoru aktuálního pixelu. Může být využit k perturb normální, stejně jako v normálním mapování na povrchu zřejmý.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Zrcadlit vektor.|Žádné|  
|**Odlesku**|Vypočítá podíl odraženého světla podle model osvětlení Phong pomocí zadaného normála povrchu.<br /><br /> Odražené světlo dává zářivý a reflexní vzhled objektu, například voda, plasty nebo kovy.<br /><br /> **Vstup:**<br /><br /> `Surface Normal`: `float3`<br /> Normála povrchu aktuálního pixelu, definované v tečném prostoru aktuálního pixelu. Může být využit k perturb normální, stejně jako v normálním mapování na povrchu zřejmý.<br /><br /> **Výstup:**<br /><br /> `Output`: `float3`<br /> Podíl barvy zrcadlovými světly.|Žádné|



