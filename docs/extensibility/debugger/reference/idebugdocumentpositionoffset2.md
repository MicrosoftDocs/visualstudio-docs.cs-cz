---
description: Představuje pozici ve zdrojovém souboru jako posun znaku.
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01815a7dcae5a469db20b9288918b4e2aaf9ffed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066318"
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
