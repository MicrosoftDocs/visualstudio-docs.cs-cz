---
title: IEnumDebugPropertyInfo2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715357"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Toto rozhraní vyjmenovává [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představují informace pro konkrétní vlastnost.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) získat toto rozhraní představující podřízené objekty určité vlastnosti. Volání [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) získat toto rozhraní představující vlastnosti konkrétní hosto.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugPropertyInfo2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Načte zadaný počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Přeskočí zadaný počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Získá počet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Obecně platí, že vlastnost je hierarchie informací, které mohou obsahovat název, hodnotu, adresu a typ, stejně jako všechny další informace vhodné pro přidružený objekt vlastnosti nebo rámec zásobníku. Viz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) další podrobnosti.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
