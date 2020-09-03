---
title: Varianty pro rozměry textury s poloviční čtvrti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03485a3b9df9c06b1ef4755a5758cf2c8c997d1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161159"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Varianta polovičních/čtvrtinových dimenzí textury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zmenší Rozměry textury u textur, které nejsou cílem vykreslování.  
  
## <a name="interpretation"></a>Interpretace  
 Menší textury zabírají méně paměti, proto spotřebovávají menší šířku pásma a snižují tlak v mezipaměti textur GPU. Jejich méně podrobností ale může způsobit snížení kvality obrazu, zejména při jejich prohlížení v 3D scéně nebo zobrazení v oblasti zvětšení.  
  
 Pokud tato varianta znázorňuje velký nárůst výkonu, může to znamenat, že vaše aplikace spotřebovává příliš velkou šířku pásma paměti, používá mezipaměť textury neefektivně nebo obojí. Může také indikovat, že vaše textury zabírají více paměti GPU, než je k dispozici, což způsobí, že textury budou stránkovaná v systémové paměti.  
  
 Pokud vaše aplikace spotřebovává příliš velkou šířku pásma paměti nebo neefektivně používá mezipaměť textury, zvažte zmenšení velikosti textur, ale pouze po zvážení povolení map MIP pro příslušné textury. Stejně jako menší textury, textur mapované MIP spotřebovává menší šířku pásma, i když zabírají více paměti GPU – a zvyšují využití mezipaměti, ale neomezují podrobnosti textury. Doporučujeme, aby se mapy MIP pokaždé, když zvýšené využití paměti nezpůsobí, že textury budou stránkovaná v systémové paměti.  
  
 Pokud vaše textury zabírají více paměti GPU, než je k dispozici, zvažte zmenšení velikosti textur, ale pouze po zvážení komprimace příslušných textur. Podobně jako menší textury, komprimované textury zabírají méně paměti a omezují nutnost stránkování na systémovou paměť, ale jejich věrnost barvy je omezená. Komprese není vhodná pro všechny textury, v závislosti na jejich obsahu – například ty, které mají významnou variaci barev v malé oblasti – ale u mnoha textur může komprese zachovat lepší celkovou kvalitu obrazu než zmenšení jejich velikosti.  
  
## <a name="remarks"></a>Poznámky  
 Při každém volání `ID3D11Device::CreateTexture2D` , které vytváří zdrojovou texturu, se zmenší Rozměry textury. Konkrétně jsou zmenšeny Rozměry textury, pokud předaný objekt D3D11_TEXTURE2D_DESC v `pDesc` popisuje texturu, která je použita v vykreslování; to je:  
  
- Člen BindFlags má pouze nastavený příznak D3D11_BIND_SHADER_RESOURCE.  
  
- Člen MiscFlags nemá příznak D3D11_RESOURCE_MISC_TILE_POOL nebo sada příznaků D3D11_RESOURCE_MISC_TILED (vedle prostředků se nezmění velikost).  
  
- Formát textury je podporován jako cíl vykreslování, jak je určen D3D11_FORMAT_SUPPORT_RENDER_TARGET – což je vyžadováno pro zmenšení velikosti textury. Podporovány jsou i formáty BC1, BC2 a BC3, i když nejsou podporované jako cíle vykreslování.  
  
  Pokud aplikace doplní počáteční data, tato varianta škáluje data textury na odpovídající velikost před tím, než vytvoří texturu. Pokud jsou počáteční data dodána v bloku komprimovaném blokem, jako je například BC1, BC2 nebo BC3, je Dekódovaná, zvětšena a znovu zakódována předtím, než se použije k vytvoření menší textury. (Povaha komprese na základě bloku znamená, že dodatečný proces kódování se škálováním na více verzí téměř vždy způsobí nižší kvalitu obrázku, než když je vygenerována textura komprimovaná textura z verze textury, která nebyla dříve kódována.)  
  
  Pokud jsou pro texturu povoleny mapy MIP, hodnota variant odpovídajícím způsobem sníží počet úrovní MIP – o jednu méně při škálování na poloviční velikost nebo o dvě méně při škálování na velikost čtvrtletí.  
  
## <a name="example"></a>Příklad  
 Tato varianta mění textury za běhu před voláním `CreateTexture2D` . Doporučujeme před tímto přístupem k produkčnímu kódu, protože textury pro celou velikost spotřebovávají více místa na disku a protože další krok může prodloužit dobu načítání ve vaší aplikaci – zejména u komprimovaných textur, které vyžadují významné výpočetní prostředky ke kódování. Místo toho doporučujeme, abyste své textury změnili offline pomocí editoru obrázků nebo procesoru obrázků, který je součástí vašeho kanálu sestavení. Tyto přístupy omezují požadavky na místo na disku a odstraňují režii za běhu ve vaší aplikaci a poskytují větší dobu zpracování, abyste si mohli při zmenšování nebo komprimaci textur zachovat nejlepší kvalitu obrazu.  
  
## <a name="see-also"></a>Viz také  
 [MIP – varianta generace mapy](../debugger/mip-map-generation-variant.md)   
 [Varianta komprese textur BC](../debugger/bc-texture-compression-variant.md)
