---
title: iPropertyProxyeeside::CreateReplacementObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715040"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Vytvoří kopii datového objektu specifického pro vyhodnocení výrazu (EE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataIn`\
[v] Objekt [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) který uchovává data, která mají být zkopírována.

`dataOut`\
[out] Vrátí nový `IEEDataStorage` objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je dána [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objekt představující pole bajtů. Tento příchozí datový objekt obvykle není implementován EE. Objekt vrácený touto metodou je však vždy implementován EE, `IEEDataStorage` který umožňuje EE implementovat rozhraní na jakékoli třídy je žádoucí.

 Všimněte si, že data `IEEDataStorage` dodaná příchozíobjekt musí `IEEDataStorage` být stejná data v odchozí objekt.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
