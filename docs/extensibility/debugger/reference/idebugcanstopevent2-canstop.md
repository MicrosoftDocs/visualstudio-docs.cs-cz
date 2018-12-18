---
title: IDebugCanStopEvent2::CanStop | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 545d1ea57c207429b7aeb999384b6d5ffbb6c723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861667"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Upozorní ladicího stroje (DE), jestli se mají zastavit na aktuální umístění v kódu nebo jenom pokračovat v provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fCanStop`  
 [in] Nenulová (`TRUE`), pokud by se měla zastavit DE do aktuálního umístění kódu; v opačném případě hodnotu (`FALSE`).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Příjemce této události obvykle volá [getreason –](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodu a zjistěte jeho důvod DE chce zastavit a pak zavolá `IDebugCanStopEvent2::CanStop` metodu s odpovídající odpověď.  
  
 Pokud je DE zastaví, odešle událost, která popisuje důvody, proč zastavení. Obvykle existují dvě události, které jsou odeslány, uživatele nebo signál přerušení reprezentována [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) rozhraní a reprezentována událost zarážky [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)