---
description: Aktualizuje data objektu daným datovým objektem a vrátí nový datový objekt reprezentující nová data objektu.
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fb6c098d26148db39493b25f199c6819fb81d27
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082410"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje data objektu daným datovým objektem a vrátí nový datový objekt reprezentující nová data objektu.

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
pro Objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obsahující nová data.

`dataOut`\
mimo Vrátí nový `IEEDataStorage` objekt obsahující nahrazená data.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda ve skutečnosti aktualizuje data objektu. Data v vráceném objektu [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nemusí být shodná s daty ve vstupním `IEEDataStorage` objektu, ale vrácený objekt musí odrážet aktuální hodnotu vlastnosti.

 Datový objekt příchozích dat není obvykle implementován pomocí et. Objekt vrácený touto metodou je však vždy implementován pomocí et, což umožňuje, aby rozhraní EE implementovalo `IEEDataStorage` rozhraní pro jakoukoliv třídu.

 Metoda [funkce CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) vytvoří datový objekt na základě příchozího datového objektu, ale nemá vliv na původní data vlastnosti.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
