---
title: BeginCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b16fdc4d0a12d7082400e697ca44a7ca4c549f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431794"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zahájí interval zachycení, který skončí `EndCapture` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Poznámky  
 Interval zachycení obvykle pokrývá podmnožinu jednoho rámce, například pokud chcete zachytit informace grafiky pouze o určitém typu volání draw. Pokud interval zachycení zahrnuje volání k dispozici, jsou zachyceny dva snímky informací o grafice. První rámec zahrnuje interval mezi voláním `BeginCapture` a voláním, které je k dispozici. druhý rámec zahrnuje interval mezi první událostí Direct3D po volání k přítomnosti a volání `EndCapture` .  
  
 Chcete-li zachytit interval, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že je [Init](../debugger/init.md) nutné se `VsgDbg` před voláním nebo pomocí volání metody init přes instanci třídy `BeginCapture` `EndCapture` .  
  
## <a name="see-also"></a>Viz také  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
