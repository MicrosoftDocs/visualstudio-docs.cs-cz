---
title: IDebugClassField::EnumBaseClasses | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734471"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Vytvoří čítač výčtu pro základní třídy této třídy.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\

[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam základních tříd. Vrátí hodnotu null, pokud neexistují žádné základní třídy.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK, vrátí S_SH_NO_BASE_CLASSES `ppEnum` pokud neexistují žádné základní třídy (a parametr je nastaven na hodnotu null); v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Základní třídy v objektu čítače výčtu jsou určeny v pořadí nejbezprostřednější (nebo nejvíce odvozené) základní třídy na nejodlehlejší základní třídy. Například vzhledem k c++ třídy:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Výčet vrátí základní třídy v `Level2`pořadí `Level1` `Root`, . .

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
