---
title: Varianta velikosti zobrazení 1x1 | Microsoft Docs
description: Použijte variantu velikosti zobrazení 1x1 a snižte rozměry zobrazení na všech cílech vykreslování na 1x1 pixelů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb8d00d68a61fd2e97740ee46f92433ea34abb65
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232840"
---
# <a name="1x1-viewport-size-variant"></a>Varianta velikosti oblasti zobrazení 1x1
Zmenší rozměry zobrazení na všech cílech vykreslování na 1x1 pixelů.

## <a name="interpretation"></a>Interpretace
 Menší zobrazení zmenší počet pixelů, které je třeba stínovat. Menší zobrazení ale neomezuje počet vrcholů, které je třeba zpracovat. Nastavení rozměrů zobrazení na 1x1 pixelů efektivně eliminují stínování v pixelech z vaší aplikace.

 Pokud tato varianta znázorňuje velký nárůst výkonu, může to znamenat, že vaše aplikace spotřebovává příliš velkou rychlost plnění. Kromě toho je možné, že vaše řešení může být pro cílovou platformu příliš vysoké, nebo vaše aplikace by mohla strávit značnou časovou přesnost v pixelech, které jsou později přepsány, a to také jako *překreslování*. Menší vyrovnávací paměť snímků nebo snížení množství překreslování zvýší výkon vaší aplikace.

## <a name="remarks"></a>Poznámky
 Rozměry zobrazení jsou obnoveny na 1x1 pixelů po každém volání `ID3D11DeviceContext::OMSetRenderTargets` nebo `ID3D11DeviceContext::RSSetViewports` .

## <a name="example"></a>Příklad
 Tuto variantu lze reprodukovat pomocí následujícího kódu:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
