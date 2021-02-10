---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69fbdef70fc9c95ef571ce0ce796199292417ca0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933554"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Představuje pozici ve zdrojovém souboru jako posun znaku.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementováno rozhraním IDE a spotřebované moduly ladění.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugDocumentPositionOffset2` .

|Metoda|Popis|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Načte rozsah pro aktuální pozici dokumentu.|

## <a name="remarks"></a>Poznámky
 Vrátí se stejné informace jako [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , ale v `char` posunech od začátku dokumentu. To představuje dokument podobný tomu, jako by existoval na disku, tj. jednorozměrné pole znaků namísto informace o řádku a sloupci, které se obvykle vracejí.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
