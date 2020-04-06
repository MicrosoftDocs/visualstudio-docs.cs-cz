---
title: IEEDataStorage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718185"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Toto rozhraní představuje pole bajtů.

## <a name="syntax"></a>Syntaxe

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu (EE) implementuje toto rozhraní představují pole bajtů (používá typ vizualizéry načíst a změnit data prostřednictvím rozhraní [IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) EE obvykle implementuje toto rozhraní pro podporu vizualizérů externího typu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Všechny metody `IPropertyProxyEESide` na rozhraní vrátí toto rozhraní. Volání [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) získat rozhraní [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Volání [QueryInterface](/cpp/atl/queryinterface) v rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) získat rozhraní [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Rozhraní `IEEDataStorage` implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Načte zadaný počet bajtů dat do zadané vyrovnávací paměti.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Načte počet dostupných bajtů dat.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní používá typ vizualizéru pro přístup k datům uchovávaných určitým objektem. Data jsou považována za pole bajtů, což umožňuje vizualizéru typu manipulovat s ním jakýmkoli způsobem je nutné prezentovat uživateli.

 Vlastní prohlížeč můžete také použít toto rozhraní, pokud je to žádoucí, i když více typicky, vlastní prohlížeč by použít vlastní rozhraní, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) nebo [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pro data orientovaná na řetězec).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
