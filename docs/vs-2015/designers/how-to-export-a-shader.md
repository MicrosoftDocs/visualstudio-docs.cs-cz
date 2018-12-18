---
title: 'Postupy: exportování shaderu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8c3a6ea90b43caeb1140cbb9ab7c699bdb09c3e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213288"
---
# <a name="how-to-export-a-shader"></a>Postupy: Exportování shaderu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje způsob použití návrháře shaderu exportovat shader orientovaného grafu Shader Language (DGSL) tak, aby ho můžete používat ve vaší aplikaci.  
  
 Tento dokument ukazuje, tato aktivita:  
  
-   Export shaderu  
  
## <a name="exporting-a-shader"></a>Export shaderu  
 Po vytvoření shaderu pomocí návrháře shaderu a mohli ho používat ve vaší aplikaci, je nutné ho exportovat ve formátu, který se rozumí grafiky rozhraní API. Exportování shaderu různými způsoby pro různé potřeby.  
  
#### <a name="to-export-a-shader"></a>Chcete-li exportovat shader  
  
1.  V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete **vizuální graf shaderu (.dgsl)** souboru.  
  
     Pokud nemáte k dispozici **vizuální graf shaderu (.dgsl)** soubor otevřít, jej vytvořte podle pokynů v [postupy: vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Na **návrháře shaderu** nástrojů, zvolte **Upřesnit**, **exportovat**, **exportovat jako**. **Exportovat Shader** se zobrazí dialogové okno.  
  
3.  V **uložit jako typ** rozevírací seznam, vyberte formát, který chcete exportovat.  
  
     Tady jsou formáty, které můžete použít:  
  
     **HLSL Pixel Shader (\*.hlsl)**  
     Exportuje shaderu High Level Shader Language (HLSL) zdrojového kódu. Tato možnost umožňuje upravit shader tak později, i když je nasazena v aplikaci. Proto může být snazší ladit a opravovat kód založený na problémy koncových uživatelů, ale také usnadňuje uživatelům upravte svůj shader nežádoucí způsoby – například k získání nespravedlivou výhodu v konkurenční hru. Také může zvýšit zatížení doba shaderu.  
  
     **Kompilovaný Pixel Shader (\*.cso)**  
     Exportuje shaderu HLSL bajtového kódu. Tato možnost využívá je možné upravit shader tak později, i když je nasazena v aplikaci. Proto může být snazší ladit a opravovat kód založený na problémy koncových uživatelů, ale protože shader je předem kompilovaných, narůstání režii navíc runtime shaderu při načtení aplikace. Dostatečně zkušení uživatelé můžete upravit shader tak stále nežádoucím způsobem, ale kompilace shaderu to kvůli tomu podstatně obtížnější.  
  
     **Hlaviček jazyka C++ (\*.h)**  
     Exportuje jako záhlaví ve stylu jazyka C, který definuje bajtové pole obsahující HLSL bajtový kód shaderu. Tato možnost může být časově náročnější, ladit a opravovat kód založený na problémy koncových uživatelů, protože aplikace musí být překompilovány Pokud chcete otestovat opravy. Ale vzhledem k tomu, že tato možnost je těžké, i když není možné upravit shader po nasazení v aplikaci, představuje většina potíže s uživateli, který chce nežádoucím způsobem upravit shader.  
  
4.  V **název_souboru** – pole se seznamem, zadejte název pro exportované shaderu a klikněte na tlačítko **Uložit** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření shaderu základní barvy](../designers/how-to-create-a-basic-color-shader.md)   
 [Návrhář shaderů](../designers/shader-designer.md)



