---
title: 'IDebugBoundBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ac19bfe2109d7885265342ccc5ef4d358727d49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156198"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Nastaví nebo změní podmínku přidruženou k této vázané zarážce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bpCondition`  
 pro Hodnota z výčtu [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , která popisuje podmínku.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí, `E_BP_DELETED` zda je stav objektu vázaného bodu přerušení nastaven na hodnotu `BPS_DELETED` (součást výčtu [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).  
  
## <a name="remarks"></a>Poznámky  
 Veškerá podmínka, která byla dříve přidružena k této zarážce, bude ztracena.  
  
## <a name="see-also"></a>Viz také  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
