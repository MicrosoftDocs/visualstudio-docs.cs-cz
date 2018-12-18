---
title: IDebugApplication110::AsynchronousCallInMainThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 236a6585d5d5844f282d8ecf5820ac8fdfb49648
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793875"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Provede asynchronní volání na hlavní vlákno.  
  
> [!IMPORTANT]
>  [Idebugapplication110 – rozhraní](../../winscript/reference/idebugapplication110-interface.md) je implementovaná pomocí PDM v11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
 [Idebugthreadcall – rozhraní](../../winscript/reference/idebugthreadcall-interface.md) objekt, který chcete volat.  
  
 `dwParam1`  
 První parametr volání.  
  
 `dwParam1`  
 První parametr volání.  
  
 `dwParam2`  
 Druhý parametr volání.  
  
 `dwParam3`  
 Třetí parametr volání.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplication110 – rozhraní](../../winscript/reference/idebugapplication110-interface.md)