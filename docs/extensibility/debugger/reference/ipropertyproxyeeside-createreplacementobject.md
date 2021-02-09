---
title: 'IPropertyProxyEESide:: funkce CreateReplacementObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30e2b8037059824bd514024e6fb86561406895c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852827"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Vytvoří kopii datového objektu specifickou pro vyhodnocení výrazu (EE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataIn`\
pro Objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , který uchovává data ke zkopírování.

`dataOut`\
mimo Vrátí nový `IEEDataStorage` objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Této metodě je udělen objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) představující pole bajtů. Tento příchozí datový objekt není obvykle implementován pomocí et. Objekt vrácený touto metodou je však vždy implementován pomocí et, což umožňuje, aby rozhraní EE implementovalo `IEEDataStorage` rozhraní pro jakoukoliv třídu.

 Všimněte si, že data zadaná příchozím `IEEDataStorage` objektem musí být stejná data v odchozím `IEEDataStorage` objektu.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
