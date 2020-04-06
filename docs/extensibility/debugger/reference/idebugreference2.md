---
title: IDebugReference2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720259"
---
# <a name="idebugreference2"></a>IDebugReference2
Toto rozhraní představuje odkaz na vlastnost rámce zásobníku nebo jinou vlastnost.

> [!NOTE]
> `IDebugReference2`je vyhrazena pro budoucí použití a `E_NOTIMPL`všechny jeho metody by se měly vrátit .

## <a name="syntax"></a>Syntaxe

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní představují odkaz na určitý druh hodnoty. Hodnota může být například číselná hodnota v důsledku vyhodnocení výrazu, kontext paměti používaný pro zobrazení paměti nebo seznam registrů a jejich hodnot.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) získat toto rozhraní. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) a [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) také vrátit toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugReference2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Získá [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strukturu, která popisuje tento odkaz.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Nastaví hodnotu tohoto odkazu z řetězce.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Nastaví hodnotu tohoto odkazu z jiného odkazu.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Vyjmenovává podřízené položky tohoto odkazu.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Získá nadřazený tento odkaz.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Získá nejvíce odvozený odkaz tohoto odkazu.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Získá bajtů paměti, na které odkazuje tento odkaz.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Získá kontext paměti pro tento odkaz.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Získá velikost v bajtů tohoto odkazu.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Nastaví tento typ odkazu.|
|[Porovnání](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porovná tento odkaz s jiným.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Toto použití "vlastnost" by neměla být zaměňována `IDebugReference2` s tím smyslu členské proměnné třídy, i když může představovat takovou entitu.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představuje vlastnost, `IDebugReference2` zatímco představuje odkaz na vlastnost, obvykle odkaz na objekt v programu, který je laděn.

 Hlavní rozdíl mezi vlastností a odkazem spoáž, že vlastnost odkazuje na pojmenovanou instanci objektu, zatímco odkaz odkazuje na nepojmenovanou instanci. Vlastnost může například odkazovat na objekt v haldě programu podle `"a.b"`. Jiná vlastnost může odkazovat `"c.d"`na stejný objekt jako . Způsob odkazování na tuto vlastnost `"a.b"` `"c.d"` vyžaduje, nebo být v oboru. Odkaz na stejný objekt je bezejmenný; objekt může být odkazováno tak dlouho, dokud je platná paměť pro tento objekt.

 Rozhraní `IDebugProperty2` si lze myslet jako hodnotu s názvem, typem a adresou. Na `IDebugReference2`druhou stranu , lze si myslet, že jako typ a adresu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
