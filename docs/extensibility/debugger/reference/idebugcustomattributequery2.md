---
title: IDebugCustomAttributeQuery2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732485"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Určuje existenci vlastního atributu pro toto pole a pokud existuje, vrátí informace o atributu.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní na stejném objektu, který implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pro podporu vlastníatributy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface) získáte toto rozhraní z rozhraní [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou uvedeny metody rozhraní **IDebugCustomAttributeQuery.**

|Metoda|Popis|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Určuje, zda vlastní atribut existuje podle názvu.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Získá informace o atributu pro daný vlastní atribut.|

 Kromě metod **IDebugCustomAttributeQuery** `IDebugCustomAttributeQuery2` implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Získá čítač výčtu pro všechny vlastní atributy připojené k tomuto poli.|

## <a name="remarks"></a>Poznámky
 [Metoda IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) může vrátit čítač výčtu pro všechny vlastní atributy definované pro toto pole.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
