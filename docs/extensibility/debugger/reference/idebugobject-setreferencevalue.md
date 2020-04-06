---
title: IDebugObject::SetReferenceValue | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726375"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Nastaví referenční hodnotu tohoto objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parametry
`pObject`\
[v] Objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující novou referenční hodnotu.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda umožňuje tento [objekt IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) odkaz na hodnotu objektu uvedené v parametru, `pObject` zahodit všechny předchozí odkaz. Všimněte `IDebugObject` si, že tento objekt již musí být typ odkazu.

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
