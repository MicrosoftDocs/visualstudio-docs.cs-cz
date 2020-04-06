---
title: IDebugArrayObject::GetElement | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736180"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Získá prvek pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
[v] Index prvku.

`ppElement`\
[out] Vrátí rozhraní [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) které představuje prvek.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda vidí všechny prvky objektu pole jako jednorozměrné pole, i když je objekt pole vícerozměrný. Například vzhledem `myarray[3][2][6]` k `dwIndex` poli a parametru 20 by `myarray[1][1][2]`tato metoda `dwIndex` vrátila prvek z , `myarray[1][1][3]`a parametr 21 by vrátil prvek z . Pomocí metody [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) určete celkový počet prvků v poli.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
