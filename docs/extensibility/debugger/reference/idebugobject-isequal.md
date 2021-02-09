---
title: 'IDebugObject:: Equals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 406e93456f1bd6d92a42f1584d19aeb52dd5ff93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846774"
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
pro Objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující objekt, na který se má porovnat.

`pfIsEqual`\
mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud jsou hodnoty objektů stejné. v opačném případě vrátí hodnotu nula ( `FALSE` ).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda obvykle může porovnat adresy hodnot reprezentovaných `pObject` parametrem a tímto objektem [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; Pokud jsou adresy stejné, lze objekty považovat za stejné.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
