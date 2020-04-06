---
title: iPropertyProxyeeSide::InplaceUpdateObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714896"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje data objektu pomocí daného datového objektu a vrátí nový datový objekt představující nová data objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataIn`\
[v] Objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obsahující nová data.

`dataOut`\
[out] Vrátí nový `IEEDataStorage` objekt obsahující nahrazená data.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda ve skutečnosti aktualizuje data objektu. Data v vráceném objektu [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nemusí být stejná jako `IEEDataStorage` data v příchozím objektu, ale vrácený objekt musí odrážet aktuální hodnotu vlastnosti.

 Objekt příchozích dat obvykle není implementován EE. Objekt vrácený touto metodou je však vždy implementován EE, `IEEDataStorage` který umožňuje EE implementovat rozhraní na jakékoli třídy je žádoucí.

 Metoda [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) vytvoří datový objekt na základě příchozího datového objektu, ale neovlivní původní data vlastnosti.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
