---
title: IDebugCanStopEvent2::GetReason | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d32f8be53d88b8268fdbbc82e6d774bffe3d7c3a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898411"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Získá důvod, proč chce zastavit ladicí stroj (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcr`  
 [out] Vrátí hodnotu z [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) výčet, který je popsaný i důvod pro tuto událost.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je obvykle volána před provedením [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metodu, volající můžete určit, jestli se má předat nenulovou (`TRUE`) k `IDebugCanStopEvent2::CanStop` metody.  
  
 Může být důvodem zastavení `CANSTOP_ENTRYPOINT`, což znamená, že je DE dosáhla vstupní bod, nebo `CANSTOP_STEPIN`, což znamená, že je DE vstoupí do funkce.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)