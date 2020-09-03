---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161636"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zachycuje zbytek aktuálního rámce do souboru protokolu grafiky.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud v současné době probíhá jiné zachycení – například zachytávání, který byl spuštěn `BeginCapture` funkcí, pak toto zachycení je dokončeno a zaznamenáno do protokolu grafiky jako samostatný rámec. Ihned poté Diagnostika grafiky zahájí zachycení zbývajícího aktuálního rámce, který je také zaznamenán jako samostatný rámec. Konec aktuálního rámce je označen voláním k dispozici.  
  
 Chcete-li zachytit snímek, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že před voláním je nutné se před voláním volat [init](../debugger/init.md) pomocí instance `VsgDbg` třídy `CaptureCurrentFrame` .  
  
## <a name="see-also"></a>Viz také  
 [For](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
