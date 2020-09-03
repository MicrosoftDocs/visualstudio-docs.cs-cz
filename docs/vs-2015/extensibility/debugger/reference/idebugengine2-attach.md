---
title: 'IDebugEngine2:: Attach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a82d26fbfd6fe08f4976aaa7643bcaa95008032f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196047"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Připojí ladicí stroj (DE) k programu nebo programům. Volá se správcem ladění relace (SDM), když DE běží v procesu do modelu SDM.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProgram`  
 pro Pole objektů [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , které reprezentují programy, ke kterým mají být připojeny. Jedná se o programy portů.  
  
 `rgpProgramNodes`  
 pro Pole objektů [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , které reprezentují uzly programu, jeden pro každý program. Uzly programu v tomto poli reprezentují stejné programy jako v `pProgram` . Jsou uvedené uzly programu, aby DE mohl identifikovat programy, ke kterým se má připojit.  
  
 `celtPrograms`  
 pro Počet programů nebo uzlů programu v `pProgram` `rgpProgramNodes` polích a.  
  
 `pCallback`  
 pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který se má použít k odeslání událostí ladění do SDM.  
  
 `dwReason`  
 pro Hodnota z výčtu [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , která určuje důvod připojení těchto programů. Další informace najdete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Existují tři důvody pro připojení k programu, a to následujícím způsobem:  
  
- `ATTACH_REASON_LAUNCH` označuje, že se má k programu připojit DE, protože uživatel spustil proces, který ho obsahuje.  
  
- `ATTACH_REASON_USER` indikuje, že uživatel explicitně požádal o připojení k programu (nebo k procesu, který obsahuje program).  
  
- `ATTACH_REASON_AUTO` Určuje, že se má ke konkrétnímu programu připojit DE, protože už ladí jiné programy v určitém procesu. Tato metoda se označuje také jako automatické připojení.  
  
  Při volání této metody potřebuje DE odeslat tyto události v sekvenci:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (Pokud ještě nebyla odeslána pro konkrétní instanci ladicího stroje)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Kromě toho, pokud je důvodem pro připojení `ATTACH_REASON_LAUNCH` , de potřebuje odeslat událost [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .  
  
   Jakmile DE Získá objekt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , který odpovídá laděnému programu, může se dotazovat na jakékoli privátní rozhraní.  
  
   Před voláním metod uzlu programu v poli, které je zadáno v `pProgram` nebo `rgpProgramNodes` , by mělo být povoleno zosobnění v případě potřeby v `IDebugProgram2` rozhraní, které představuje uzel programu. Obvykle ale tento krok není nezbytný. Další informace najdete v tématu [problémy se zabezpečením](../../../extensibility/debugger/security-issues.md).  
  
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
