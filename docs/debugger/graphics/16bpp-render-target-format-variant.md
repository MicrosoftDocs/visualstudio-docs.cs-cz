---
title: Varianta 16bpp formátu cíle vykreslování | Microsoft Docs
description: Použijte variantu cílového formátu vykreslení 16 bitů na pixel (bpp) nastavením formátu pixelů na DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a vyrovnávací paměť zpět.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96f202663b1b325f7a4ac86876abc94563a02fb2
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232866"
---
# <a name="16-bpp-render-target-format-variant"></a>Varianta cílového formátu vykreslování 16 bpp
Nastaví formát pixelů na DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a vyrovnávací paměti zpět.

## <a name="interpretation"></a>Interpretace
 Cíl vykreslování nebo zpětná vyrovnávací paměť obvykle používají formát 32 bpp (32 bitů na pixel), například B8G8R8A8_UNORM. Formáty 32 bpp mohou spotřebovávat velkou šířku pásma paměti. Vzhledem k tomu, že formát B5G6R5_UNORM je formát 16 bpp, který má poloviční velikost než formáty 32 bpp, může jeho použití snížit tlak na šířku pásma paměti, ale za cenu nižší věrnosti barev.

 Pokud tato varianta vykazuje velké zvýšení výkonu, pravděpodobně to značí, že vaše aplikace spotřebovává příliš velkou šířku pásma paměti. Můžete výrazně zlepšit výkon, zejména v případě, že profilovaný rámec měl značné množství překreslení nebo alfa blendingu.

Cílový formát vykreslování 16 bpp může snížit využití pásma paměti, pokud má vaše aplikace následující podmínky:
- Nevyžaduje vysoce věrnou reprodukci barev.
- Nevyžaduje alfa kanál.
- Často nemá hladké přechody (které jsou náchylné k pruhování artefaktů pod omezenou věrností barev).

Mezi další strategie, jak snížit šířku pásma paměti, patří:
- Zmenšete množství překreslování nebo alfa blendingu.
- Zmenšete rozměry vyrovnávací paměti rámců.
- Zmenšete rozměry prostředků textury.
- Snižte kompresi prostředků textury.

Jako obvykle je třeba vzít v úvahu obchody s kvalitou obrázků, které jsou součástí jakékoli z těchto optimalizací.

Aplikace, které jsou součástí řetězce prohození, mají formát vyrovnávací paměti zpět (DXGI_FORMAT_B5G6R5_UNORM), který nepodporuje 16 bpp. Tyto řetězce prohození se vytvářejí pomocí `D3D11CreateDeviceAndSwapChain` nebo `IDXGIFactory::CreateSwapChain` . Pokud chcete toto omezení obejít, proveďte následující kroky:
1. Vytvořte cíl B5G6R5_UNORM vykreslování pomocí a `CreateTexture2D` vykreslení na tomto cíli.
2. Zkopírujte cíl vykreslování do backbufferu řetězce prohození tím, že jako zdrojovou texturu nakreslíte čtyřúhelník na celé obrazovce s cílem vykreslování.
3. Volejte Present on your swap chain (Přítomno v řetězci prohození).

   Pokud tato strategie šetří větší šířku pásma, než se využívá zkopírováním cíle vykreslování do backbufferu řetězce prohození, zlepší se výkon vykreslování.

   Architektury GPU, které používají techniky vykreslování s dlaždicemi, vidíte významné výhody výkonu s využitím formátu vyrovnávací paměti rámce 16 bpp. Toto vylepšení je proto, že větší část vyrovnávací paměti rámce se vejde do místní mezipaměti vyrovnávací paměti rámce každé dlaždice. Architektury vykreslování s dlaždicemi se někdy nacházejí v GPU v mobilních handsetech a tabletech. Jen zřídka se vyskytují mimo tento výklenek.

## <a name="remarks"></a>Poznámky
 Cílový formát vykreslování se resetuje tak, DXGI_FORMAT_B5G6R5_UNORM při každém volání metody `ID3D11Device::CreateTexture2D` , které vytvoří cíl vykreslení. Konkrétně je formát přepsán, když D3D11_TEXTURE2D_DESC objekt předaný v pDesc popisuje cíl vykreslení. To je:

- Člen BindFlags má D3D11_BIND_REDNER_TARGET příznak.

- Člen BindFlags má příznak D3D11_BIND_DEPTH_STENCIL zrušen.

- Člen Využití je nastavený na D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Omezení a limity
 Vzhledem k tomu, že formát B5G6R5 nemá alfa kanál, tato varianta nezachová alfa obsah. Pokud vykreslování vaší aplikace vyžaduje alfa kanál v cíli vykreslování, nemůžete přepnout na formát B5G6R5.

## <a name="example"></a>Příklad
 Variantu cílového formátu **vykreslování 16 bpp** je možné reprodukovat pro cíle vykreslování vytvořené pomocí `CreateTexture2D` následujícího kódu:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
