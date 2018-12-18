---
title: Dimenze varianta polovičních textury | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94820b2930bbe689c37b90443ac007b137f162d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870195"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Varianta dimenze polovině/textury
Snižuje rozměrů textury na textury, které nejsou cíle vykreslování.  
  
## <a name="interpretation"></a>interpretace  
 Menší textury zabírají méně paměti a proto využívat menší šířku pásma paměti a snížení tlak na GPU mezipaměti textur. Jejich nižší úrovně podrobností však může způsobit snížení kvalitu, zejména v případě, že se jedná o zobrazení úzce ve 3D scéně nebo zobrazit v části zvětšení.  
  
 Pokud se tato varianta zobrazí zisk náročné na výkon, můžete určit, že vaše aplikace využívá příliš velkou šířku pásma, paměti, používá texturu mezipaměti neefektivně nebo obojí. Lze také určit, že vaše textury zabírat větší paměť GPU, než je k dispozici, což způsobí, že textury stránkování na systémové paměti.  
  
 Pokud vaše aplikace spotřebovává příliš mnoho paměti šířky pásma nebo používá mezipaměť textury neefektivně, zvažte snížení velikosti vašeho textury, ale až poté, co můžete zvážit povolení mapy mip odpovídající textury. Stejně jako menší textury textury pro mapovanou mip využívat menší šířku pásma paměti – i když jsou zabírat více paměti GPU – a zvýšení využití mezipaměti, ale není snížit úroveň podrobnosti textury. Doporučujeme, abyste mapy mip pokaždé, když je využití paměti pro zvýšení nezpůsobí textury stránkování na systémové paměti.  
  
 Pokud vaše textury zabírat více paměti GPU, než je k dispozici, zvažte snížení velikost textury, ale až po zvažte komprese odpovídající textury. Podobně jako menší textury komprimované textury zabírají méně paměti a snížení nároků na stránku a systémové paměti, ale jejich barva věrnost je omezeno. Komprese není vhodná pro všechny textury, v závislosti na jejich obsah, například ty, které mají významný barev ve malou oblast –, ale pro mnoho textury, můžete zachovat komprese lepší celkovou kvalitu obrazu než jejich velikost.  
  
## <a name="remarks"></a>Poznámky  
 Rozměry textury jsou zmenšeny na všechna volání `ID3D11Device::CreateTexture2D` , který vytváří zdrojovou texturu. Konkrétně je snížení rozměrů textury při D3D11_TEXTURE2D_DESC objekt předaný v `pDesc` popisuje textury, který se používá vykreslování; který je:  
  
- Člen BindFlags má pouze D3D11_BIND_SHADER_RESOURCE příznak nastaven.  
  
- Člen MiscFlags nemá příznak D3D11_RESOURCE_MISC_TILE_POOL nebo nastaví příznak D3D11_RESOURCE_MISC_TILED (vedle sebe prostředky nelze změnit velikost).  
  
- Formát textura je podporovaný jako cíl vykreslování – podle D3D11_FORMAT_SUPPORT_RENDER_TARGET – což je vyžadováno pro omezení velikosti textury. Podporují se také formátů BC1, BC2 a BC3, a i když nejsou podporovány jako cíle vykreslování.  
  
  Pokud je počáteční údaje poskytnuté aplikací, škáluje Tato varianta data textury, která mají odpovídající velikost, předtím, než vytvoří textury. Pokud počáteční data je zadaný ve formátu komprimovanými například BC1, BC2 nebo BC3, je dekódovat, škálovat a znovu kódován předtím, než se používá k vytvoření menších textury. (Povaze založené na blocích komprese znamená, že proces velmi dekódování škálování – kódování téměř vždy způsobí nižší kvality obrázku, než když textury komprimovanými nevygeneruje škálovaná verze textury, který nebyl dříve zakódován.)  
  
  Pokud mapy mip jsou povolené pro textury, varianty snižuje počet úrovní mip odpovídajícím způsobem – jeden méně při horizontálním škálování poloviční velikost nebo dvě méně při škálování na velikost čtvrtletí.  
  
## <a name="example"></a>Příklad  
 Tato varianta změní velikost textury v době běhu před voláním `CreateTexture2D`. Nedoporučujeme tento přístup pro produkční kód, protože reklamy textury využívat více místa na disku a další krok může zvýšit dobu načítání v aplikaci – zejména pro komprimované textury, které vyžadují významné výpočetní prostředky ke kódování. Namísto toho doporučujeme změnit velikost vašeho textury v režimu offline, a to pomocí editoru obrázků nebo obrázků procesor, který je součástí vašeho kanálu sestavení. Tyto přístupy snížit požadavky na místo na disku a eliminuje režijní náklady na modul runtime ve vaší aplikaci a poskytují více času na zpracování, aby uchováváte nejlepší kvality obrázku během zmenšení nebo komprese vaše textury.  
  
## <a name="see-also"></a>Viz také  
 [Varianta generování Mipmap](mip-map-generation-variant.md)   
 [Varianta komprese textur BC](bc-texture-compression-variant.md)