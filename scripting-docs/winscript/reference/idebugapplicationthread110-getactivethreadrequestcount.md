---
title: 'Idebugapplicationthread110 –:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574480"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Vrátí počet požadavků na vlákno z mechanismů přepínání vláken PDM, které jsou právě zpracovávány. Toto číslo je obvykle 0 nebo 1. Číslo ale může být vyšší, pokud jedno volání vlákna spustí zpracování, ale aktivuje synchronní volání mimo vlákno nebo jinak pozastaví vlákno a umožní opětovné zpracování příchozích volání (například aktivací [iremotedebugapplicationevents – Událost rozhraní](../../winscript/reference/iremotedebugapplicationevents-interface.md) , která je vydána ve vlákně ladicího programu.  
  
> [!IMPORTANT]
> [Rozhraní idebugapplicationthread110 –](../../winscript/reference/idebugapplicationthread110-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puiThreadRequests`  
 mimo Počet požadavků na vlákno.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationThread110 – rozhraní](../../winscript/reference/idebugapplicationthread110-interface.md)