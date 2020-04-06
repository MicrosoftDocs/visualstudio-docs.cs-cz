---
title: IDebugDocumentPositionOffset2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731600"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Představuje pozici ve zdrojovém souboru jako posun znaků.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementováno ide a spotřebované ladicí motory.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugDocumentPositionOffset2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Načte rozsah pro aktuální pozici dokumentu.|

## <a name="remarks"></a>Poznámky
 To vrátí stejné informace jako `char` [GetRange,](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ale v posuny od začátku dokumentu. To představuje dokument, jako by existoval na disku, to znamená jednorozměrné pole znaků, namísto řádku a sloupce informace, které jsou obvykle vráceny.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
