---
title: Varianta velikosti oblasti zobrazení 1 x 1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168b358bf58dcb2c91814f5460b203873255e275
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433242"
---
# <a name="1x1-viewport-size-variant"></a>Varianta velikosti oblasti zobrazení 1x1
Snižuje rozměry zobrazení na všechny cíle vykreslení na 1 × 1 pixelů.  
  
## <a name="interpretation"></a>interpretace  
 Menší zobrazení snižuje počet pixelů, které mají na odstín. Ale není menší zobrazení snížit počet vrcholy, které budete muset proces. Nastavení rozměry zobrazení 1 x 1 pixelů efektivně eliminuje pixel stínování z vaší aplikace.  
  
 Pokud se tato varianta zobrazí zisk náročné na výkon, může to znamenat, že vaše aplikace spotřebovává příliš mnoho míra naplnění. Kromě toho vaše řešení může být příliš vysoká. pro cílovou platformu nebo vaše aplikace může trávit spoustu času stínování pixelů, které jsou přepsány později, jsou označovány také jako *overdraw*. Menší vyrovnávací paměť snímku nebo snížit množství overdraw zlepší výkon vaší aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Rozměry zobrazení se resetují na pixelech 1 × 1 po každém volání do `ID3D11DeviceContext::OMSetRenderTargets` nebo `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Příklad  
 Tato varianta možné reprodukovat následujícím kódem:  
  
```cpp
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
