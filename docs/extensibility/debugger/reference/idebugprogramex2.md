---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f206de825d021d8daa2977a839f96fabd5e9db7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898864"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Toto rozhraní umožňuje, aby se správce ladění relace (SDM) připojil k programu a získal uzel programu přidružený k programu.

## <a name="syntax"></a>Syntax

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní na stejném objektu jako rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , aby se model SDM mohl připojit k programu, a současně umožňuje poskytovateli portu sledovat všechny relace připojené k programu. Vlastní dodavatel portu může implementovat toto rozhraní, pokud se rozhodne.

## <a name="notes-for-callers"></a>Poznámky pro volající
 SDM zavolá [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgram2` rozhraní, aby získalo toto rozhraní ke sledování relací, které jsou připojené k programům.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProgramEx2` .

|Metoda|Popis|
|------------|-----------------|
|[Připojit](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Připojí program k relaci.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Získá uzel programu přidružený k programu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je v rámci modelu SDM a programu privátní.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
