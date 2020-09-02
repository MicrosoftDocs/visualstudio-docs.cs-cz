---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714863"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Toto rozhraní poskytuje metody pro zobrazení dat u přidruženého objektu. Toto rozhraní je součástí podpory pro typy vizualizací.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní pro podporu typů vizualizací.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pro získání tohoto rozhraní volejte [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) . Chcete-li získat rozhraní [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) , zavolejte na rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) [QueryInterface](/cpp/atl/queryinterface) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializuje zprostředkovatele zdroje dat tak, aby bylo možné přistupovat k datům objektu.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Načte informace o sestavení objektu.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Získá počáteční data pro objekt.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Vytvoří kopii existujícího úložiště dat.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Vytvoří odkaz na existující úložiště dat.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Načte informace o konkrétním sestavení v kontextu sestavení obsahujícího tento objekt.|

## <a name="remarks"></a>Poznámky
 Vizualizér typů používá toto rozhraní pro přístup k hodnotám přidruženým k objektu, ke kterému je toto rozhraní součástí. Data jsou přístupná prostřednictvím rozhraní [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , které poskytuje zobrazení dat jen pro čtení.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
