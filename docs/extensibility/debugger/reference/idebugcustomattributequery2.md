---
description: Určuje existenci vlastního atributu pro toto pole a v případě, že existuje, vrátí informace o atributu.
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00f7e23b280ef92e9883f68f203bd790f5e4d815
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077561"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Určuje existenci vlastního atributu pro toto pole a v případě, že existuje, vrátí informace o atributu.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní u stejného objektu, který implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , aby podporovaly vlastní atributy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 K získání tohoto rozhraní z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) použijte [QueryInterface](/cpp/atl/queryinterface) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody rozhraní **IDebugCustomAttributeQuery** .

|Metoda|Popis|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Určuje, zda vlastní atribut existuje podle názvu.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Získá informace o atributu pro daný vlastní atribut.|

 Kromě metod **IDebugCustomAttributeQuery** `IDebugCustomAttributeQuery2` implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Získá enumerátor pro všechny vlastní atributy připojené k tomuto poli.|

## <a name="remarks"></a>Poznámky
 Metoda [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) může vracet enumerátor pro všechny vlastní atributy definované pro toto pole.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
