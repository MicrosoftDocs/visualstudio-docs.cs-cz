---
description: Vrátí rozhraní, které představuje spravovaný objekt.
title: 'IDebugManagedObject:: GetManagedObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1aea4f233160f9bdcc5c18c1dda16b4e3f361540
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076937"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Vrátí rozhraní, které představuje spravovaný objekt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parametry
`ppManagedObject`\
mimo Vrátí rozhraní, které představuje spravovaný objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Rozhraní vrácené z této metody lze dotazovat pro jakékoli rozhraní implementované spravovanou třídou a umožnit volání jeho metod.

## <a name="see-also"></a>Viz také
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
