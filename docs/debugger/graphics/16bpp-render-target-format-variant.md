---
title: Varianta cílového formátu 16bpp vykreslování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188595"
---
# <a name="16-bpp-render-target-format-variant"></a>16 BPP cílů vykreslování cílového formátu
Nastaví formát pixelu na DXGI_FORMAT_B5G6R5_UNORM pro všechny cíle vykreslování a zpětnou vyrovnávací paměť.

## <a name="interpretation"></a>Interpretace
 Cílová nebo zadní vyrovnávací paměť vykreslování obvykle používá formát 32 bpp (32 bitů na pixel), jako je například B8G8R8A8_UNORM. 32 – formáty BPP mohou spotřebovat velké množství šířky pásma paměti. Vzhledem k tomu, že formát B5G6R5_UNORM má 16 BPP formát o velikosti 32 – bpp, může to snížit tlak na šířku pásma paměti, ale s náklady na zmenšenou přesnost barev.

 Pokud tato varianta znázorňuje velký nárůst výkonu, nejspíš to znamená, že vaše aplikace spotřebovává příliš velkou šířku pásma paměti. Můžete získat výrazné zlepšení výkonu, zejména v případě, že profilované orámování mělo značné množství překreslování nebo alfa míchání.

BPP cílový formát vykreslování může snížit pásmo paměti s využitím, když má aplikace následující podmínky:
- Nepožaduje barevnou reprodukci barev s vysokou věrností.
- Nevyžaduje kanál alfa.
- Často mají hladké přechody (které jsou náchylné k rozřazení artefaktů pod zmenšenou přesností barev).

Mezi další strategie pro omezení šířky pásma paměti patří:
- Snižte množství překreslování nebo alfa míchání.
- Snižte rozměry vyrovnávací paměti rámce.
- Snižte rozměry prostředků textury.
- Snižte komprimaci prostředků textury.

V obvyklých případech je nutné zvážit kompromisy v kvalitě obrazu, které jsou součástí kterékoli z těchto optimalizací.

Aplikace, které jsou součástí řetězce přepnutí, mají formát back-buffer (DXGI_FORMAT_B5G6R5_UNORM), který nepodporuje 16 BPP. Tyto swapové řetězy se vytvářejí pomocí `D3D11CreateDeviceAndSwapChain` nebo `IDXGIFactory::CreateSwapChain`. Chcete-li toto omezení obejít, proveďte následující kroky:
1. Vytvoření B5G6R5_UNORM formátu cíle vykreslování pomocí `CreateTexture2D` a vykreslení do tohoto cíle.
2. Zkopírujte cíl vykreslování do vyrovnávací paměti odkládacího řetězce, a to tak, že nakreslíte celou obrazovku s cílem vykreslování jako zdrojovou texturou.
3. Volání je k dispozici v řetězu přepnutí.

   Pokud tato strategie šetří větší šířku pásma, než je spotřebované kopírováním cíle vykreslování do přístupné paměti swap-Chain, zlepší se výkon vykreslování.

   Architektury GPU, které používají dlaždici vykreslování, můžou zobrazit významné výhody výkonu pomocí 16 BPP formátu snímků. Toto zlepšení je způsobeno tím, že větší část vyrovnávací paměti rámce se může vejít do místní mezipaměti vyrovnávací paměti rámců v rámci každé dlaždice. V procesorech GPU v mobilních sluchátkech a tabletových počítačích se někdy nacházejí vedle architektury vykreslování. zřídka se vyskytují mimo tento mezery.

## <a name="remarks"></a>Poznámky
 Formát cíle vykreslování je resetován na DXGI_FORMAT_B5G6R5_UNORM při každém volání `ID3D11Device::CreateTexture2D`, které vytvoří cíl vykreslování. Konkrétně je formát přepsán, pokud D3D11_TEXTURE2D_DESC objekt předaný v pDesc popisuje cíl vykreslování; To je:

- Člen BindFlags má nastaven příznak D3D11_BIND_REDNER_TARGET.

- Člen BindFlags má nezaškrtnutý příznak D3D11_BIND_DEPTH_STENCIL.

- Člen použití je nastaven na D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Omezení a omezení
 Vzhledem k tomu, že formát B5G6R5 nemá alfa kanál, neuchová se v této variantě obsah alfa. Pokud vykreslování vaší aplikace vyžaduje alfa kanál v cíli vykreslování, nemůžete jednoduše přepnout na formát B5G6R5.

## <a name="example"></a>Příklad
 Variantu **cílového formátu BPP vykreslování** lze reprodukovat pro cíle vykreslování vytvořené pomocí `CreateTexture2D` pomocí kódu takto:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
