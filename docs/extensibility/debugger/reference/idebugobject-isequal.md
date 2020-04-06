---
title: IDebugObject::IsEqual | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726500"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Porovná objekt s tímto objektem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parametry
`pObject`\
[v] Objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující objekt, se který má být porovnán.

`pfIsEqual`\
[out] Vrátí hodnotu`TRUE`nenulová ( ), pokud jsou hodnoty objektů stejné; v opačném případě`FALSE`vrátí hodnotu nula ( ).

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda může obvykle porovnat adresy hodnot reprezentované parametrem `pObject` a tento objekt [IDebugObject;](../../../extensibility/debugger/reference/idebugobject.md) Pokud jsou adresy stejné, pak objekty lze považovat za rovné.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
