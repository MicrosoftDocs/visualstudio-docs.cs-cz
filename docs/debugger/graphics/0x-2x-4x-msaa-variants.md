---
title: 0x-2x-4x MSAA – varianty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 707d63d3ae5fb487f6232321a1d9d3128d379e06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816531"
---
# <a name="0x2x4x-msaa-variants"></a>Varianty 0x/2x/4x MSAA
Přepíše nastavení rozhraní MSAA (multi-Sample anti-aliasing) na všech cílech vykreslování a prohozených řetězcích.

## <a name="interpretation"></a>Interpretace
 Vyhlazení s více ukázkami zvyšuje vizuální kvalitu tím, že pobírá vzorky ve více umístěních v jednotlivých pixelech. větší úrovně rozhraní MSAA využívají další ukázky a bez rozhraní MSAA, z středu se dá vzít jenom jedna ukázka. Povolení rozhraní MSAA ve vaší aplikaci má obvykle mírné, ale nepatrné náklady při vykreslování, ale v určitých úlohách nebo na určitých Gpuch může být to skoro bez dopadu.

 Pokud už vaše aplikace má povolenou MSAA, pak menší varianty rozhraní MSAA označují relativní náklady na výkon, ke kterým dojde v existujícím rozhraní MSAA vyšší úrovně. Konkrétně 0x MSAA variant indikuje relativní výkon vaší aplikace bez rozhraní MSAA.

 Pokud vaše aplikace ještě nemá povolenou MSAA, pak dvojnásobné varianty MSAA a 4x MSAA označují relativní náklady na výkon při jejich povolování ve vaší aplikaci. Pokud jsou náklady přijatelné, zvažte možnost Povolit MSAA pro vylepšení kvality obrazu vaší aplikace.

> [!NOTE]
> Hardware nemusí plně podporovat rozhraní MSAA pro všechny formáty. Pokud některá z těchto variant narazí na omezení hardwaru, které nelze vyřešit, je jeho sloupec v tabulce souhrn výkonu prázdný a je vytvořena chybová zpráva.

## <a name="remarks"></a>Poznámky
 Tyto varianty přepíšou počet vzorků a argumenty kvality vzorků pro volání `ID3DDevice::CreateTexture2D` , která cílí na vytvoření vykreslování. Konkrétně tyto parametry jsou přepsány, pokud:

- `D3D11_TEXTURE2D_DESC`Předaný objekt `pDesc` popisuje cíl vykreslování; to je:

  - Člen BindFlags má buď příznak D3D11_BIND_TARGET, nebo nastaven příznak D3D11_BIND_DEPTH_STENCIL.

  - Člen použití je nastaven na D3D11_USAGE_DEFAULT.

  - Člen CPUAccessFlags je nastaven na hodnotu 0.

  - Člen MipLevels je nastaven na hodnotu 1.

- Zařízení podporuje požadovaný počet vzorků (0, 2 nebo 4) a kvalitu vzorku (0) pro požadovaný formát cíle vykreslování (D3D11_TEXTURE2D_DESC:: Format member), jak je určeno `ID3D11Device::CheckMultisampleQualityLevels` .

  Pokud má člen D3D11_TEXTURE2D_DESC:: BindFlags nastavené příznaky D3D_BIND_SHADER_RESOURCE nebo D3D11_BIND_UNORDERED_ACCESS, vytvoří se dvě verze textury; první má tyto příznaky nesmazatelné pro použití jako cíl vykreslování a druhá je textura bez rozhraní MSAA, která má tyto příznaky ponechány beze změny, aby fungovaly jako vyrovnávací paměť pro řešení první verze. To je nezbytné, protože použití textury rozhraní MSAA jako prostředku shaderu nebo pro neuspořádaný přístup je pravděpodobně neplatné – například shader, který na něm pracuje, vygeneruje nesprávné výsledky, protože by očekával texturu, která není MSAA. Pokud varianta vytvořila sekundární texturu bez rozhraní MSAA, pak pokaždé, když se v kontextu zařízení nerozhodne cíl vykreslování rozhraní MSAA, jeho obsah se přeloží na texturu, která není MSAA. Stejně tak, pokaždé, když by měl být cíl vykreslování rozhraní MSAA svázán jako prostředek shaderu, nebo se používá v zobrazení neuspořádaného přístupu, vyřešená textura bez rozhraní MSAA je namísto ní svázána.

  Tyto varianty také přepíší nastavení rozhraní MSAA na všech prohozených řetězcích vytvořených pomocí `IDXGIFactory::CreateSwapChain` , `IDXGIFactory2::CreateSwapChainForHwnd` ,, `IDXGIFactory2::CreateSwapChainForCoreWindow` `IDXGIFactory2::CreateSwapChainForComposition` a `ID3D11CreateDeviceAndSwapChain` .

  Čistým účinkem těchto změn je, že všechny vykreslování jsou provedeny v cíli vykreslování sady MSAA, ale pokud vaše aplikace používá jeden z těchto cílů vykreslování nebo vyrovnávací paměti pro odkládací řetěz jako zobrazení prostředků shaderu nebo neuspořádané zobrazení přístupu, jsou data z vyřešené kopie, která není v rozhraní MSAA, vyvzorkovaná.

## <a name="restrictions-and-limitations"></a>Omezení a omezení
 V Direct3D11 jsou textury MSAA více omezené než rozhraní MSAA. Například nemůžete volat `ID3D11DeviceContext::UpdateSubresource` texturu MSAA a volání `ID3D11DeviceContext::CopySubresourceRegion` selžou, pokud se počet vzorků a kvalita vzorku zdrojového prostředku a cílového prostředku neshodují, což může nastat, pokud tato varianta přepisuje nastavení rozhraní MSAA jednoho prostředku, ale ne druhý.

 Když přehrávání detekuje tyto druhy konfliktů, je vhodné replikovat zamýšlené chování, ale nemusí být možné přesně porovnat jeho výsledky. I když je to Neběžné, aby to ovlivnilo výkon těchto variant způsobem, který nepředstavuje jejich dopad, je možné – například když je řízení toku v pixel shaderu určeno přesným obsahem textury, protože replikovaná textura nemusí mít stejný obsah.

## <a name="example"></a>Příklad
 Tyto varianty je možné reprodukovat pro cíle vykreslování vytvořené pomocí pomocí `ID3D11Device::CreateTexture2D` kódu, který by vypadal takto:

```cpp
D3D11_TEXTURE2D_DESC target_description;
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
target_description.SampleDesc.Quality = 0;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```

## <a name="example"></a>Příklad
 Nebo pro swapové řetězy vytvořené pomocí IDXGISwapChain:: CreateSwapChain nebo D3D11CreateDeviceAndSwapChain pomocí kódu takto:

```cpp
DXGI_SWAP_CHAIN_DESC chain_description;
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead
chain_description.SampleDesc.Quality = 0;

// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.
```
