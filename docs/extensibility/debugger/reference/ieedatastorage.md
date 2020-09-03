---
title: IEEDataStorage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718185"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Toto rozhraní představuje pole bajtů.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu (EE) implementuje toto rozhraní tak, aby představovalo pole bajtů (používaného vizualizacemi typů pro načtení a změnu dat prostřednictvím rozhraní [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). EE obvykle implementuje toto rozhraní pro podporu vizualizací externích typů.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody na `IPropertyProxyEESide` rozhraní vrátí toto rozhraní. Zavolejte [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) a získejte rozhraní [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Chcete-li získat rozhraní [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) , zavolejte na rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) [QueryInterface](/cpp/atl/queryinterface) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 `IEEDataStorage`Rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Načte zadaný počet bajtů dat do zadané vyrovnávací paměti.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Načte počet dostupných datových bajtů.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní používá Vizualizér typů pro přístup k datům uchovávaným konkrétním objektem. Data se považují za pole bajtů, což umožňuje, aby Vizualizér typů mohl manipulovat bez ohledu na to, jak ho prezentuje uživateli.

 Vlastní prohlížeč může toto rozhraní použít i v případě potřeby, i když to více obvykle vlastní prohlížeč používá vlastní rozhraní, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) nebo [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (pro řetězcová data).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
