---
title: IEnumDebugCustomAttributes | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717129"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Vyjmenovává vlastní atributy.

## <a name="syntax"></a>Syntaxe

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní pro podporu vlastních atributů (prostřednictvím rozhraní [IDebugCustomAttribute).](../../../extensibility/debugger/reference/idebugcustomattribute.md)

## <a name="notes-for-callers"></a>Poznámky pro volající
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugCustomAttributes`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Načte zadaný počet vlastních atributů v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Přeskočí zadaný počet vlastních atributů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Získá počet vlastních atributů v čítači výčtu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
