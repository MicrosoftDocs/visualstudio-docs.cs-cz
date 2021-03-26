---
description: Vytvoří výčet vlastních atributů.
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8decd8d244ad4b55d2bba7381e247535faad9b22
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081071"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Vytvoří výčet vlastních atributů.

## <a name="syntax"></a>Syntax

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní pro podporu vlastních atributů (přes rozhraní [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) ).

## <a name="notes-for-callers"></a>Poznámky pro volající
- [EnumCustomAttributes –](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugCustomAttributes` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Načte zadaný počet vlastních atributů v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Přeskočí zadaný počet vlastních atributů v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Získá počet vlastních atributů v enumerátoru.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
