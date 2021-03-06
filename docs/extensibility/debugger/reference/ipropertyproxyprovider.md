---
description: Toto rozhraní poskytuje proxy rozhraní pro zobrazení a změnu dat objektu.
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d8d92f6d616d86b82a9f4efa443f459a082256e
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225536"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Toto rozhraní poskytuje proxy rozhraní pro zobrazení a změnu dat objektu.

## <a name="syntax"></a>Syntax

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu (EE) implementuje toto rozhraní u stejného objektu, který implementuje rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , jako součást podpory typu vizualizuje v EE.

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugProperty3` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 `IPropertyProxyProvider`Rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Načte proxy rozhraní vlastnosti pro zobrazení dat v objektu.|

## <a name="remarks"></a>Poznámky
 I když EE implementuje toto rozhraní, implementace [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) je obvykle zpracována [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Podrobnosti o získání rozhraní IEEVisualizerService naleznete v tématu [vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)
