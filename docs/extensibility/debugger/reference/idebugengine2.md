---
title: IDebugEngine2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730859"
---
# <a name="idebugengine2"></a>IDebugEngine2
Toto rozhraní představuje ladicí modul (DE). Používá se ke správě různých aspektů relace ladění, od vytváření zarážek až po nastavení a vymazání výjimek.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastní DE pro správu ladění programů. Toto rozhraní musí být implementováno DE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je voláno správcem ladění relace (SDM) ke správě relace ladění, včetně správy výjimek, vytváření zarážek a reakce na synchronní události odeslané de.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEngine2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Vytvoří čítač výčtu pro všechny programy, které jsou laděny DE.|
|[Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Připojí de k programu.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Vytvoří čekající zarážka v DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Určuje, jak má DE zpracovat danou výjimku.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Odebere zadanou výjimku, takže již není zpracována ladicím strojem.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Odebere seznam výjimek, které rozhraní IDE nastavilo pro konkrétní architekturu nebo jazyk za běhu.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Získá identifikátor GUID DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informuje DE, že zadaný program byl atypically ukončen a že DE by měl vyčistit všechny odkazy na program a odeslat událost zničení programu.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Volal SDM k označení, že synchronní ladicí událost, dříve odeslaná DE sSDM, byla přijata a zpracována.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Nastaví národní prostředí DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Nastaví kořenový adresář registru, který de aktuálně používá.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Nastaví metriku.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Požaduje, aby všechny programy, které jsou laděny tímto DE zastavit spuštění při příštím pokusu o spuštění jednoho z jejich vláken.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
