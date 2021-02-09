---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edff2cad101a6a6f0f19a4b384b8f2398b98b2e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883737"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Toto rozhraní vytváří výčet dodavatelů portů.

## <a name="syntax"></a>Syntax

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní tak, aby představovalo seznam dodavatelů portů.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Zavolejte [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) a získejte seznam dodavatelů portů.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugPortSuppliers2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Načte zadaný počet dodavatelů portů v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Přeskočí zadaný počet dodavatelů portů v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Získá počet dodavatelů portů v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Ladicí modul obecně nemusí toto rozhraní získat.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
