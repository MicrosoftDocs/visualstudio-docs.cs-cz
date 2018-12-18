---
title: 16bpp vykreslování cílového formátu Variant | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9c72abaaf1a799316686c77b127952f1fe4f689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832885"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bitů na pixel vykreslování cílového formátu typu Variant
Nastaví formát pixelu DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a zpět vyrovnávací paměti.  
  
## <a name="interpretation"></a>interpretace  
 Cíl vykreslování nebo přípravné vyrovnávací paměti používá obvykle 32 bitů na pixel (32 bitů na pixel) formát jako je například B8G8R8A8_UNORM. formáty 32 bitů na pixel může spotřebovat velké množství paměti šířky pásma. Protože B5G6R5_UNORM formát je 16 bitů na pixel formátu, který je poloviční velikost 32 bitů na pixel formáty, můžete ho pomocí obdobná tlak na šířce pásma paměti, ale za cenu sníženou barva věrnost.  
  
 Pokud tato varianta zobrazuje velké výkonnější, pravděpodobně znamená, že vaše aplikace využívá příliš velkou šířku pásma, paměti. Významné výkonnostní zlepšení, můžete získat, zejména v případě, že rámec profilovaných měl značné množství overdraw nebo alfa blending.

16 bitů na pixel vykreslování cílového formátu můžete zmenšit obsluhy vzdálené správy paměti s využitím aplikace obsahuje následující podmínky:
- Nevyžaduje, aby reprodukce a věrného barev.
- Nevyžaduje, aby kanál alfa.
- Nemá ofent smooth přechody (které jsou náchylné k řazení do pásem artefakty pod věrnost sníženou barvu).

Další strategie zaměřené na ke snížení šířky pásma paměti patří:
- Snížíte množství overdraw nebo prolnutí alfa.
- Snížení velikosti vyrovnávací paměť snímku.
- Snižte rozměry textury prostředků.
- Snižte komprimace prostředky textur.
 
Obvyklým způsobem je nutné zvážit kvality kompromisy, které jsou součástí některý z těchto optimalizacích bitovou kopii.  

Aplikace, které jsou součástí řetězce přepnutí mít formát vyrovnávací paměti (DXGI_FORMAT_B5G6R5_UNORM), který nepodporuje 16 bitů na pixel. Tyto řetězce přepnutí se vytvářejí pomocí `D3D11CreateDeviceAndSwapChain` nebo `IDXGIFactory::CreateSwapChain`. Chcete-li toto omezení obejít, postupujte takto:
1. Vytvořit cíl B5G6R5_UNORM formát vykreslování pomocí `CreateTexture2D` a vykreslování, které cílí. 
2. Zkopírujte cíl vykreslování do přípravné vyrovnávací paměti řetězce přepnutí kreslením quad celé obrazovky se cíl vykreslení jako zdrojovou texturu.
3. Nevolají Present na vaše řetězec přepnutí.

   Pokud tato strategie uloží větší šířku pásma, než je využívána kopírování cíle vykreslování přípravné vyrovnávací paměti řetězce přepnutí, je lepší výkon při vykreslování.

   Architektury GPU, používající techniky vedle sebe vykreslování můžete zobrazit výhody výkonu pomocí formátu 16 bitů na pixel rámce vyrovnávací paměti. Toto vylepšení totiž větší část vyrovnávací paměť snímku lze zobrazit v mezipaměti Každá dlaždice místní snímek vyrovnávací paměti. Vedle sebe vykreslování architektury jsou někdy součástí grafickými procesory v mobilních telefonů a tabletů počítače; zřídka nacházet mimo tento volné místo.  
  
## <a name="remarks"></a>Poznámky  
 Cílový formát vykreslení se resetují na DXGI_FORMAT_B5G6R5_UNORM na všechna volání `ID3D11Device::CreateTexture2D` , který vytvoří cíl vykreslování. Konkrétně je formát přepsána při D3D11_TEXTURE2D_DESC objekt předaný v pDesc popisuje cíl vykreslování; To je:  
  
-   Člen BindFlags má příznak D3D11_BIND_REDNER_TARGET nastavený.  
  
-   Člen BindFlags má příznak D3D11_BIND_DEPTH_STENCIL vymazána.  
  
-   Využití člen je nastavený na D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Omezení a omezení  
 Protože formátu B5G6R5 nemá kanál alfa, nezachová se tato varianta alfa obsah. Pokud vaše aplikace vykreslování vyžaduje alfa kanál v vaše cíle vykreslování, nebudete moci přepnout jen na B5G6R5 formátu.  
  
## <a name="example"></a>Příklad  
 **16 bitů na pixel vykreslování cílového formátu** možné reprodukovat typu variant pro vykreslení cíle vytvořené využitím `CreateTexture2D` pomocí kódu takto:  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
