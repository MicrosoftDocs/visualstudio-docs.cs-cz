---
description: Toto rozhraní představuje ladicí stroj (DE).
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066149"
---
# <a name="idebugengine2"></a>IDebugEngine2
Toto rozhraní představuje ladicí stroj (DE). Používá se ke správě různých aspektů relace ladění, od vytvoření zarážek k nastavení a mazání výjimek.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí vlastního DE pro správu ladění programů. Toto rozhraní musí být implementováno pomocí DE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se volá správcem ladění relace (SDM) za účelem správy relace ladění, včetně správy výjimek, vytváření zarážek a reagování na synchronní události odesílané DE.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugEngine2` .

|Metoda|Popis|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Vytvoří enumerátor pro všechny programy, které jsou laděny pomocí DE.|
|[Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Připojí k programu DE.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Vytvoří nevyřízenou zarážku ve DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Určuje, jak by měl DE zpracovat danou výjimku.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Odstraní určenou výjimku, takže již není zpracována ladicím modulem.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Odebere seznam výjimek, které rozhraní IDE nastavilo pro konkrétní architekturu nebo jazyk run-time.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Získá identifikátor GUID DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informuje o tom, že zadaný program byl neobvyklým ukončen a že DE by měl vyčistit všechny odkazy na program a odeslat událost zničení programu.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Volá se serverem SDM k označení toho, že byla přijata a zpracována synchronní událost ladění, která byla dříve odeslána nástrojem DE do modelu SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Nastaví národní prostředí DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Nastaví kořen registru, který je aktuálně používán nástrojem DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Nastaví metriku.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Požaduje, aby všechny programy laděné tímto DE zastavily provedení při příštím pokusu o spuštění některého z jeho vláken.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
