---
title: IDebugContainerField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733214"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Toto rozhraní představuje symbol nebo typ, který je kontejnerem pro jiné symboly nebo typy.

## <a name="syntax"></a>Syntaxe

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní na stejném objektu, který implementuje rozhraní [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Toto rozhraní je také základní třídy pro všechna rozhraní, které představují kontejnery.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Mnoho metod na mnoha rozhraních vrátí toto rozhraní. Protože se jedná o základní třídu pro všechny kontejnery, lze získat specializovanější rozhraní z tohoto rozhraní pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface). Mezi taková rozhraní patří [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)a [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Vytvoří čítač výčtu pro pole kontejneru.|

## <a name="remarks"></a>Poznámky
 Pole (kontejnery pro proměnné), třídy (kontejnery pro metody a proměnné) a metody (kontejnery pro parametry a místní proměnné) jsou všechny příklady kontejnerů.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
