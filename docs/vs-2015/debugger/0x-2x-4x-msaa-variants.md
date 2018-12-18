---
title: Varianty 0 x-2 x-4 x MSAA | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e661823a07945c22679832dc716ad2f25f4f6aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793773"
---
# <a name="0x2x4x-msaa-variants"></a>0 x / 2 x / 4 x MSAA variant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přepsání více ukázka vyhlazování (MSAA) nastavení ve všech cíle vykreslování a Prohodit řetězy.  
  
## <a name="interpretation"></a>interpretace  
 Více ukázka vyhlazení zvyšuje vizuální kvality pomocí odběru vzorků na více místech každý pixel; vyšší úrovně MSAA více vzorky a bez MSAA, pouze jeden vzorek odebírán z centra je pixel. Povolení MSAA v aplikaci obvykle má středně velká ale znatelný nákladů vykreslování výkonu, ale v rámci určitých úloh nebo na určité GPU, může být měli s téměř žádný vliv.  
  
 Pokud je vaše aplikace už MSAA povolena, označení menší varianty MSAA náklady relativní výkon, který způsobuje MSAA existující, vyšší úrovně. Zejména x MSAA varianty 0 označuje relativní výkon vaší aplikace bez MSAA.  
  
 Pokud vaše aplikace ještě nemá MSAA povolena, 2 x MSAA a 4 variant x MSAA udávající náklady relativní výkon povolení v aplikaci. Po přijatelně nízké náklady na zvažte povolení MSAA vylepšit kvalitu vaší aplikace.  
  
> [!NOTE]
>  Hardware nemusí podporovat plně MSAA pro všechny formáty. Pokud některá z těchto variant dojde k omezení hardwaru, který nemůže být pracoval kolem, jeho sloupec v tabulce souhrnu výkonu je prázdný a je vytvořen chybovou zprávu.  
  
## <a name="remarks"></a>Poznámky  
 Ukázka počet a kvalita ukázky argumenty ve volání přepsat tyto varianty `ID3DDevice::CreateTexture2D` , vytvoření cíle vykreslování. Konkrétně se tyto parametry přepsat při:  
  
- `D3D11_TEXTURE2D_DESC` Objekt předaný v `pDesc` popisuje cíl vykreslování; který je:  
  
  -   Člen BindFlags má příznak D3D11_BIND_TARGET nebo nastavený příznak D3D11_BIND_DEPTH_STENCIL.  
  
  -   Využití člen je nastavený na D3D11_USAGE_DEFAULT.  
  
  -   Člen CPUAccessFlags je nastavený na hodnotu 0.  
  
  -   Člen MipLevels je nastavený na hodnotu 1.  
  
- Zařízení podporuje počet vzorků požadovaný (0, 2 nebo 4) a kvalita ukázky (0) pro požadovaný cílový formát (D3D11_TEXTURE2D_DESC::Format člen), vzhledem k vykreslení `ID3D11Device::CheckMultisampleQualityLevels`.  
  
  Pokud člen D3D11_TEXTURE2D_DESC::BindFlags nemá nastaveny příznaky D3D_BIND_SHADER_RESOUCE nebo D3D11_BIND_UNORDERED_ACCESS, vytvoří se dvě verze textury; první má tyto příznaky pro použití jako cíl vykreslování a druhý je bez MSAA texturu, která má tyto příznaky ponechána beze změn tak, aby fungoval jako řešení vyrovnávací paměť pro první verzi. To je nezbytné, protože použití MSAA textury jako prostředek shaderu nebo neuspořádaným přístupem je pravděpodobně platný – například shaderu, který funguje na něm bude generovat nesprávné výsledky, protože očekáváte textury bez MSAA. Pokud varianty vytvořil sekundární bez MSAA textury, pak pokaždé, když cíl vykreslování MSAA není nastavena v kontextu zařízení, jsou vyřešeny její obsah do jiných MSAA textury. Podobně, pokaždé, když MSAA vykreslení cíl by měl být vázaný jako prostředek shaderu, nebo se používá v zobrazení s neuspořádaným přístupem, vyřešené bez MSAA textury vázán místo.  
  
  Tyto varianty také přepsat nastavení MSAA na všechny řetězce přepnutí vytvořené využitím `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition`, a `ID3D11CreateDeviceAndSwapChain`.  
  
  Výsledkem těchto změn je, že dokončení veškerého vykreslování do cíl vykreslování MSAA, ale pokud vaše aplikace používá jednu z těchto takto cíle nebo vyrovnávací paměti řetězce přepnutí na zobrazení prostředků shaderu nebo zobrazení s neuspořádaným přístupem, a potom Vzorkovaná data z vyřešení , bez MSAA kopii cíl vykreslování.  
  
## <a name="restrictions-and-limitations"></a>Omezení a omezení  
 V Direct3D11 MSAA textur jsou omezeny více než jiné MSAA textury. Například nelze volat `ID3D11DeviceContext::UpdateSubresource` na MSAA textury a volání `ID3D11DeviceContext::CopySubresourceRegion` selže, pokud počet vzorků a kvalita ukázky prostředku zdrojového a cílového prostředku se neshodují, které může dojít, pokud tato varianta přepíše nastavení MSAA prostředek, ale nikoli u druhého.  
  
 Při přehrávání rozpoznává tyto druhy je v konfliktu, provádí nezaručené replikovat zamýšlené chování, ale nemusí být možné přesně shodovat jeho výsledky. I když neobvyklé, že to mít vliv na výkon z těchto variant způsobem, který zkresluje skutečnost jejich dopadu, je možné – například při řízení toku v pixel shader je určeno přesný obsah textury – protože replikované textury nemusí mít identické obsah.  
  
## <a name="example"></a>Příklad  
 Možné reprodukovat tyto varianty pro vykreslení cíle vytvořené využitím `ID3D11Device::CreateTexture2D` pomocí kódu takto:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Příklad  
 Nebo pro řetězce přepnutí vytvořené s použitím IDXGISwapChain::CreateSwapChain nebo D3D11CreateDeviceAndSwapChain pomocí kódu takto:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```



