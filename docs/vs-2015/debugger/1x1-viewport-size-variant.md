---
title: Varianta velikosti zobrazení 1x1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74e3bc706cb2df12aacddf9fbb77dec598bfc17a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157557"
---
# <a name="1x1-viewport-size-variant"></a>Varianta velikosti oblasti zobrazení 1x1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zmenší rozměry zobrazení na všech cílech vykreslování na 1x1 pixelů.  
  
## <a name="interpretation"></a>Interpretace  
 Menší zobrazení zmenší počet pixelů, které musí být vystínované, ale nesníží počet vrcholů, které se musí zpracovat. Nastavení rozměrů zobrazení na 1x1 pixelů efektivně eliminují stínování v pixelech z vaší aplikace.  
  
 Pokud tato varianta znázorňuje velký nárůst výkonu, může to znamenat, že vaše aplikace spotřebovává příliš mnoho fillrate. To může znamenat, že zvolené rozlišení je pro cílovou platformu příliš vysoké nebo že vaše aplikace stráví významnou časovou přesností v pixelech, které jsou později přepsány (překreslit). Výsledkem tohoto výsledku je, aby se snížila velikost framebuffer nebo zmenšení množství překreslování, což vylepšuje výkon vaší aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Rozměry zobrazení jsou obnoveny na 1x1 pixelů po každém volání `ID3D11DeviceContext::OMSetRenderTargets` nebo `ID3D11DeviceContext::RSSetViewports` .  
  
## <a name="example"></a>Příklad  
 Tuto variantu lze reprodukovat pomocí kódu, který by vypadal takto:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
