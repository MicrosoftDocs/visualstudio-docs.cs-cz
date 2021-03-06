---
description: Toto rozhraní poskytuje podporu s více vlákny pro ladění.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e52ae6477b49325d4b8a4d81192fe2ecf736163
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092654"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Toto rozhraní poskytuje podporu s více vlákny pro ladění.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní pro podporu současného ladění více vláken. Toto rozhraní je implementováno na stejném objektu, který implementuje rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 K [](/cpp/atl/queryinterface) získání tohoto rozhraní z rozhraní použijte QueryInterface `IDebugProgram2` .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugEngineProgram2` .

|Metoda|Popis|
|------------|-----------------|
|[Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Zastaví všechna vlákna spuštěná v tomto programu.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Sleduje spuštění (nebo zastavit sledování spuštění), aby se v daném vlákně stalo.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Povolí (nebo zakáže) vyhodnocení výrazu v daném vlákně, a to i v případě, že je program zastavený.|

## <a name="remarks"></a>Poznámky
 Sada Visual Studio volá toto rozhraní v reakci na událost [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a nastaví "Sledujte krok vlákna na vlákno" a "Sledujte" vyhodnocování výrazů ve vlákně pro program. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) se volá vždycky, když se program zastaví. Tato metoda dává programu možnost ukončit všechna vlákna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
