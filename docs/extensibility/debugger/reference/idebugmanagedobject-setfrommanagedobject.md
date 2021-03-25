---
description: Nastaví hodnotu instance objektu value class z instance třídy Value poskytnuté jako parametr.
title: 'IDebugManagedObject:: SetFromManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c00e61de35e0cc9c33845236d8103bcd16cebfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076846"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Nastaví hodnotu instance objektu value class z instance třídy Value poskytnuté jako parametr.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parametry
`pManagedObject`\
pro Rozhraní, které představuje spravovaný objekt, který obsahuje novou hodnotu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá ke změně spravovaného objektu, který je reprezentován objektem [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) .

## <a name="see-also"></a>Viz také
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
