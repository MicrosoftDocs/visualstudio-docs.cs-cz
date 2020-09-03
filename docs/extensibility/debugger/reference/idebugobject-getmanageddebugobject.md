---
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726686"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Vytvoří kopii spravovaného objektu v adresním prostoru ladicího stroje.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
mimo Vrátí objekt [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) představující nově vytvořený spravovaný objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby. Vrátí E_FAIL, pokud tento [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nepředstavuje instanci třídy spravované hodnoty.

## <a name="remarks"></a>Poznámky
 Tento objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) musí představovat instanci třídy spravované hodnoty, jako je například `System.Decimal` instance. Když máte místní kopii, režie [vyhodnocování](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) volání se eliminuje.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
