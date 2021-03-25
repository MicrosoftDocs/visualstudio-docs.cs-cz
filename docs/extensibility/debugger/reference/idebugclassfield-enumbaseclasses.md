---
description: Vytvoří enumerátor pro základní třídy této třídy.
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ba31ead00ad2312b66273a2ddfaeebd252e0981
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084984"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Vytvoří enumerátor pro základní třídy této třídy.

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

mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam základních tříd. Vrátí hodnotu null, pokud nejsou žádné základní třídy.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK, vrátí S_SH_NO_BASE_CLASSES, pokud nejsou žádné třídy Base (a `ppEnum` parametr je nastaven na hodnotu null). v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Základní třídy v objektu Enumerator jsou určeny v pořadí nejokamžitější (nebo nejvíce odvozené) základní třídy na nejvyšší vzdálenou základní třídu. Například s ohledem na třídy jazyka C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Výčet vrátí základní třídy v pořadí `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
