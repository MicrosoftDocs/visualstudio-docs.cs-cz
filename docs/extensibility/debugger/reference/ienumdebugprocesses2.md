---
description: Toto rozhraní vytváří výčet procesů spuštěných na portu ladění.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75778ea0f02c0e7dcca1f7d2eb0ea8ace82c9b9c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224379"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Toto rozhraní vytváří výčet procesů spuštěných na portu ladění.

## <a name="syntax"></a>Syntax

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní, aby poskytoval seznam procesů spuštěných na portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumProcesses –](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) k získání tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugProcesses2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Načte zadaný počet procesů ve výčtové sekvenci.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Přeskočí zadaný počet procesů ve výčtové sekvenci.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Získá počet procesů v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní k naplnění okna **procesy** .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
