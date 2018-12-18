---
title: IDebugEngine2::Attach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4de13e9763cfed74c2b7dbbbb58ac80610501ace
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926082"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Připojí ladicí stroj (DE) pro program nebo programy. Když DE je spuštěné v rámci procesu SDM volány správce ladění relace (SDM).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProgram`  
 [in] Pole [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objekty, které představují programy k bude připojený. Jedná se o programy portu.  
  
 `rgpProgramNodes`  
 [in] Pole [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objekty, které představují program uzlů, jeden pro každou aplikaci. Uzly programů v tomto poli představují stejné programy jako v `pProgram`. Uzly programů jsou uvedeny tak, aby DE můžete identifikovat programy se připojit k.  
  
 `celtPrograms`  
 [in] Počet aplikací a program uzlech v `pProgram` a `rgpProgramNodes` pole.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objekt, který se má použít k odesílání událostí ladění na SDM.  
  
 `dwReason`  
 [in] Hodnota z [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) výčet, který je obsažený důvod připojení těchto programů. Další informace najdete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Existují tři důvody pro připojení k programu, následujícím způsobem:  
  
- `ATTACH_REASON_LAUNCH` Označuje, že je DE je připojení k programu, protože uživatel spustí proces, který jej obsahuje.  
  
- `ATTACH_REASON_USER` Označuje, že uživatel explicitně požaduje DE se připojit k programu (nebo proces, který obsahuje program).  
  
- `ATTACH_REASON_AUTO` Označuje, že je DE je připojení ke konkrétní programu, protože ji už ladí další programy v určitém procesu. To se také nazývá Automatické připojení.  
  
  Pokud tato metoda je volána, DE není potřeba tyto události odesílat v pořadí:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (pokud ho už se neodeslala pro konkrétní instanci ladicí stroj)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Kromě toho, pokud je důvodem připojení `ATTACH_REASON_LAUNCH`, DE musí odeslat [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) událostí.  
  
   Jednou získá DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objektu odpovídající program laděn, je možné zadávat dotazy pro všechny privátní rozhraní.  
  
   Před voláním metody program uzlu v poli uvedena v každém `pProgram` nebo `rgpProgramNodes`, zosobnění, pokud je to nutné, by měla být povolená na `IDebugProgram2` rozhraní, které představuje uzel programu. Za normálních okolností však tento krok není nezbytný. Další informace najdete v tématu [problémy se zabezpečením](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)