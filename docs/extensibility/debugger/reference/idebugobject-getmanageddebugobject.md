---
title: IDebugObject::GetManagedDebugObject | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726686"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Vytvoří kopii spravovaného objektu v adresním prostoru ladicího modulu.

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
[out] Vrátí objekt [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) představující nově vytvořený spravovaný objekt.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby. Vrátí E_FAIL pokud tato [objekt IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nepředstavuje instanci spravované třídy hodnoty.

## <a name="remarks"></a>Poznámky
 Tento objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) musí představovat instanci `System.Decimal` spravované třídy hodnoty, například instanci. Tím, že místní kopie, režie volání [Vyhodnotit](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) je eliminován.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
