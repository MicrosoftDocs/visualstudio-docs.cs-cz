---
description: Toto rozhraní vyčísluje DEBUG_REFERENCE_INFO struktury.
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89dd664d7b54ce451c2d3a303b3da1c7ad2b13e8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224171"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Toto rozhraní vyčísluje [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.

## <a name="syntax"></a>Syntax

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory odkazů na objekty v paměti. Toto rozhraní je nutné implementovat pouze v případě, že jsou podporovány odkazy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) k získání tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugReferenceInfo2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Načte zadaný počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Přeskočí zadaný počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Získá počet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Odkaz je v podstatě typ a adresa, zatímco vlastnost je název, typ a adresa. Odkaz přetrvává, dokud objekt, na který odkazuje, v paměti. Další podrobnosti najdete v tématu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
