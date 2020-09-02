---
title: Varianty filtru textury Point/varianty/trilineárního/anisotropního
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 314ec61da7ed61cc8bdd573e201d98a53862a32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262922"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Varianty bodového, bilineárního, trilineárního a anisotropního filtrování textur
Přepíše režim filtrování na příslušných vzorkovačích textury.

## <a name="interpretation"></a>Interpretace
 Různé metody vzorkování textury mají různé náklady na výkon a kvalitu obrazu. V rámci zvýšení nákladů a zvyšování vizuální kvality – režimy filtru jsou:

1. Filtrování bodů (nejlevnější, nejhorší vizuální kvalita)

2. Varianty filtrování

3. Trilineárního filtrování

4. Anisotropního filtrování (nejdražší, nejlepší vizuální kvalita)

   Pokud jsou náklady na výkon jednotlivých variant významné nebo se zvyšují s větším množstvím způsobů filtrování, můžete zvážit její náklady na zvýšení kvality obrazu. Na základě vašeho posouzení můžete akceptovat dodatečné náklady na výkon, abyste zvýšili kvalitu vizuálů, nebo můžete přijmout sníženou vizuální kvalitu, abyste dosáhli vyšší frekvence snímkování nebo mohli získat výkon, který můžete použít jiným způsobem.

   Pokud zjistíte, že náklady na výkon jsou zanedbatelné nebo stabilní bez ohledu na režim filtrování – například když GPU, na kterou cílíte, má větší míru propustnosti shaderu a šířku pásma paměti, zvažte použití filtrování anisotropního, abyste dosáhli nejlepší kvality obrazu ve vaší aplikaci.

## <a name="remarks"></a>Poznámky
 Tyto varianty přepíšou stavy vzorkovače při voláních, `ID3D11DeviceContext::PSSetSamplers` ve kterých je režim filtru vzorkovače poskytnutý aplikací jedním z těchto:

- `D3D11_FILTER_MIN_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`

- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`

- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`

- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`

- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`

- `D3D11_FILTER_ANISOTROPIC`

  V variantě filtrování objektu s **texturou** , je režim filtru poskytnutý aplikací nahrazen. `D3D11_FILTER_MIN_MAG_MIP_POINT` v variantě filtru **varianty Texture** je nahrazeno `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` a v variantě **filtru trilineárního textur** je nahrazen `D3D11_FILTER_MIN_MAG_MIP_LINEAR` .

  V variantě **filtrování Anisotropního textury** je režim filtrování poskytovaný aplikací nahrazen hodnotou `D3D11_FILTER_ANISOTROPIC` a maximální Anisotropy je nastaven na 16.

## <a name="restrictions-and-limitations"></a>Omezení a omezení
 V rozhraní Direct3D úroveň funkce 9,1 určuje maximální anisotropy hodnotu 2x. Vzhledem k tomu, že se varianta **Anisotropního textur filtrování** pokusí použít výhradně 16x anisotropy, přehrávání se nezdařilo, když je analýza snímků spuštěna na zařízení 9,1 na úrovni funkce. Mezi moderní zařízení ovlivněná tímto omezením patří zařízení s platformou RT a Surface 2 pro tablety na bázi ARM. Starší grafické procesory, které by se mohly v některých počítačích pořád najít, můžou mít vliv i na zastaralé a pořád stále neobvyklá.

## <a name="example"></a>Příklad
 Variantu **filtrování pro texturu bodu** je možné reprodukovat pomocí kódu, jako je tato:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Příklad
 Variantu **filtrování textury varianty** je možné reprodukovat pomocí kódu podobného následujícímu:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Příklad
 Variantu **filtrování textury trilineárního** je možné reprodukovat pomocí kódu podobného následujícímu:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```

## <a name="example"></a>Příklad
 Variantu **filtrování textury anisotropního** je možné reprodukovat pomocí kódu podobného následujícímu:

```cpp
D3D11_SAMPLER_DESC sampler_description;

// ... other sampler description setup ...

sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;
sampler_description.MaxAnisotropy = 16;

d3d_device->CreateSamplerState(&sampler_desc, &sampler);
d3d_context->PSSetSamplers(0, 1, &sampler
```
