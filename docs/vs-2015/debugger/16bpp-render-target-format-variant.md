---
title: Varianta cílového formátu 16bpp vykreslování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157575"
---
# <a name="16bpp-render-target-format-variant"></a>Varianta 16bpp vykreslování cílového formátu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastaví formát pixelu na DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a zpětnou vyrovnávací paměť.  
  
## <a name="interpretation"></a>Interpretace  
 Cílová nebo zadní vyrovnávací paměť vykreslování obvykle používá formát pixel (32 bitů na pixel), jako je například B8G8R8A8_UNORM. formáty pixel můžou spotřebovat velkou šířku pásma paměti. Vzhledem k tomu, že formát B5G6R5_UNORM je poloviční velikost formátů 16bpp, může použití IT snížit tlak na šířku pásma, ale s náklady na zmenšenou přesnost barev.  
  
 Pokud tato varianta znázorňuje velký nárůst výkonu, nejspíš to znamená, že vaše aplikace spotřebovává příliš velkou šířku pásma paměti. Zvýšení výkonu může být obzvláště vyslovované, když se profilový rámeček od značné míry překreslí nebo obsahuje spoustu alfa prolnutí.  
  
 Pokud typy scén, které vaše aplikace vykresluje, nevyžadují barevnou reprodukci s vysokou věrností, nevyžaduje cíl vykreslování, aby měl alfa kanál, a často neobsahují hladké přechody, které jsou náchylné k rozřazení artefaktů pod zmenšenou přesností barev, zvažte použití cílového formátu 16bpp vykreslování, aby se snížilo využití šířky pásma paměti.  
  
 Pokud scény, které jsou vykreslené ve vaší aplikaci, vyžadují barevné vybarvení s vysokou věrností nebo alfa kanál, nebo jsou běžné přechody běžné, zvažte jiné strategie pro omezení využití šířky pásma paměti – například zmenšení množství překreslování nebo alfa míchání, zmenšení rozměrů framebuffer nebo úpravou prostředků textury tak, že se povolí komprese nebo sníží jejich rozměry. V obvyklých případech je nutné zvážit kompromisy v kvalitě obrazu, které jsou součástí kterékoli z těchto optimalizací.  
  
 Pokud by vaše aplikace mohla přepínat do vyrovnávací paměti 16bpp, ale je součástí vašeho řetězce přepnutí, je nutné provést další kroky, protože DXGI_FORMAT_B5G6R5_UNORM není podporovaným formátem vyrovnávací paměti pro výměnu řetězců vytvořených pomocí `D3D11CreateDeviceAndSwapChain` nebo `IDXGIFactory::CreateSwapChain` . Místo toho je třeba vytvořit B5G6R5_UNORM cíl vykreslování formátu pomocí `CreateTexture2D` a vykreslit k tomuto cíli. Pak před voláním v řetězci přepnutí zkopírujte cíl vykreslení do vyrovnávací paměti swap-řetězu tak, že nakreslíte celou obrazovku s cílem vykreslování jako zdrojovou texturou. I když se jedná o dodatečný krok, který spotřebuje určitou šířku pásma paměti, většina operací vykreslování spotřebuje menší šířku pásma, protože má vliv na cíl vykreslování 16bpp; Pokud se tím ušetří větší šířka pásma, než se spotřebuje, zkopírováním cíle vykreslování do přístupné paměti swap-Chain se zlepší výkon vykreslování.  
  
 Architektury GPU, které používají dlaždici vykreslování, můžou zobrazit významné výhody výkonu pomocí formátu 16bpp framebuffer, protože větší část framebuffer se může vejít do místní mezipaměti framebuffer v každé dlaždici. V procesorech GPU v mobilních sluchátkech a tabletových počítačích se někdy nacházejí vedle architektury vykreslování. zřídka se vyskytují mimo tento mezery.  
  
## <a name="remarks"></a>Poznámky  
 Formát cíle vykreslování je resetován na DXGI_FORMAT_B5G6R5_UNORM při každém volání `ID3D11Device::CreateTexture2D` , které vytvoří cíl vykreslování. Konkrétně je formát přepsán, pokud D3D11_TEXTURE2D_DESC objekt předaný v pDesc popisuje cíl vykreslování; To je:  
  
- Člen BindFlags má nastaven příznak D3D11_BIND_REDNER_TARGET.  
  
- Člen BindFlags má nezaškrtnutý příznak D3D11_BIND_DEPTH_STENCIL.  
  
- Člen použití je nastaven na D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Omezení a omezení  
 Vzhledem k tomu, že formát B5G6R5 nemá alfa kanál, neuchová se v této variantě obsah alfa. Pokud vykreslování vaší aplikace vyžaduje alfa kanál v cíli vykreslování, nemůžete jednoduše přepnout na formát B5G6R5.  
  
## <a name="example"></a>Příklad  
 Variantu **formátu cíle vykreslování 16bpp** lze reprodukovat pro cíle vykreslování vytvořené pomocí `CreateTexture2D` kódu takto:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
