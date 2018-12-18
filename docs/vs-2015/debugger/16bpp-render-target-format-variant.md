---
title: 16bpp vykreslování cílového formátu Variant | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00bf536e5f1ee140a818ee59c66703906860f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727641"
---
# <a name="16bpp-render-target-format-variant"></a>Varianta 16bpp vykreslování cílového formátu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastaví formát pixelu DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a zpět vyrovnávací paměti.  
  
## <a name="interpretation"></a>interpretace  
 Cíl vykreslování nebo přípravné vyrovnávací paměti používá obvykle 32 bitů na pixel (32 bitů na pixel) formát jako je například B8G8R8A8_UNORM. formáty 32 bitů na pixel může spotřebovat velké množství paměti šířky pásma. Formát B5G6R5_UNORM je 16bpp formátu, který je poloviční velikost 32 bitů na pixel formáty, můžete ho pomocí obdobná tlak na šířce pásma paměti, ale za cenu věrnost sníženou barvu.  
  
 Pokud tato varianta zobrazuje velké výkonnější, pravděpodobně znamená, že vaše aplikace využívá příliš velkou šířku pásma, paměti. Zvýšení výkonu můžete zejména vyslovováno při PROFILOVANÉHO rámce vykazuje značné množství overdraw nebo obsahuje velké množství prolnutí alfa.  
  
 Pokud druhy scény, které jsou generovány s vaší aplikace nevyžadují reprodukce a věrného barev, nevyžadují cíl vykreslování mít alfa kanál a často neobsahují hladké přechody, které jsou náchylné k řazení do pásem artefaktů v rámci sníženou barva věrnost, zvažte použití 16bpp vykreslování cílového formátu ke snížení využití šířky pásma paměti.  
  
 Pokud na pozadí, které jsou generovány ve vaší aplikaci vyžadovat barvu a věrného reprodukce nebo alfa kanál nebo technologie smooth přechody jsou společné, zvažte další strategie zaměřené na ke snížení využití šířky pásma paměti – například snižuje množství overdraw nebo alfa blending snížení velikosti framebuffer nebo upravit prostředky textury využívat menší šířku pásma paměti povolení komprese nebo snížením příslušnými rozměry. Obvyklým způsobem je nutné zvážit kvality kompromisy, které jsou součástí některý z těchto optimalizacích bitovou kopii.  
  
 Pokud vaše aplikace je výhodná přepínání 16bpp přípravné vyrovnávací paměti, ale je součástí vašeho řetězce přepnutí, budete muset provést další kroky, protože DXGI_FORMAT_B5G6R5_UNORM není formát podporovaný přípravné vyrovnávací paměti řetězce přepnutí vytvořené pomocí `D3D11CreateDeviceAndSwapChain` nebo `IDXGIFactory::CreateSwapChain`. Místo toho je nutné vytvořit cíl B5G6R5_UNORM formát vykreslování pomocí `CreateTexture2D` a vykreslovat, místo toho. Poté předtím, než je na vaší řetězec přepnutí nevolají Present, zkopírujte cíl vykreslování do přípravné vyrovnávací paměti řetězce přepnutí kreslením quad celé obrazovky se cíl vykreslení jako zdrojovou texturu. I když jde přidat další krok, který bude využívat některé paměti šířky pásma, většina operací vykreslování spotřebuje menší šířku pásma, protože ovlivňují 16bpp vykreslování cílového; Pokud to uloží větší šířku pásma, než je využívána kopírování cíle vykreslování přípravné vyrovnávací paměti řetězce přepnutí, je lepší výkon při vykreslování.  
  
 Architektury GPU, používající techniky vedle sebe vykreslování můžete zobrazit výhody výkonu pomocí formátu framebuffer 16bpp protože větší část framebuffer lze zobrazit v každé dlaždici framebuffer místní mezipaměti. Vedle sebe vykreslování architektury jsou někdy součástí grafickými procesory v mobilních telefonů a tabletů počítače; zřídka nacházet mimo tento volné místo.  
  
## <a name="remarks"></a>Poznámky  
 Cílový formát vykreslení se resetují na DXGI_FORMAT_B5G6R5_UNORM na všechna volání `ID3D11Device::CreateTexture2D` , který vytvoří cíl vykreslování. Konkrétně je formát přepsána při D3D11_TEXTURE2D_DESC objekt předaný v pDesc popisuje cíl vykreslování; To je:  
  
-   Člen BindFlags má příznak D3D11_BIND_REDNER_TARGET nastavený.  
  
-   Člen BindFlags má příznak D3D11_BIND_DEPTH_STENCIL vymazána.  
  
-   Využití člen je nastavený na D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Omezení a omezení  
 Protože formátu B5G6R5 nemá kanál alfa, nezachová se tato varianta alfa obsah. Pokud vaše aplikace vykreslování vyžaduje alfa kanál v vaše cíle vykreslování, nebudete moci přepnout jen na B5G6R5 formátu.  
  
## <a name="example"></a>Příklad  
 **16bpp vykreslování cílového formátu** možné reprodukovat typu variant pro vykreslení cíle vytvořené využitím `CreateTexture2D` pomocí kódu takto:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```



