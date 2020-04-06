---
title: IDebugProgramEx2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722331"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Toto rozhraní umožňuje správce ladění relace (SDM) připojit k programu a získat uzel programu přidružené k programu.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) s cílem umožnit SDM připojit k programu a zároveň umožňuje dodavateli portu sledovat všechny relace připojené k programu. Vlastní port dodavatel můžete implementovat toto rozhraní, pokud se rozhodne.

## <a name="notes-for-callers"></a>Poznámky pro volající
 SDM volá [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` na rozhraní získat toto rozhraní ke sledování relací, které byly připojeny k programům.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProgramEx2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Připojit](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Připojí program k relaci.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Získá uzel programu přidružený k programu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je soukromé mezi sdm a programem.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
