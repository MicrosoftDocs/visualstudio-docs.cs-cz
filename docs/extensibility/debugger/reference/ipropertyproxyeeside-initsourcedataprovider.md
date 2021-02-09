---
title: 'IPropertyProxyEESide:: InitSourceDataProvider | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60de888e3aa3f26bc094440fb07a67e49b62e73b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895983"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inicializuje zdrojová data pro tento objekt a vrátí objekt obsahující počáteční data.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataOut`\
mimo Vrátí objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je nutná k inicializaci objektu, aby mohla vracet rozhraní [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) v datech objektu. To umožňuje zobrazení dat objektu a, pokud je povoleno, změněno pomocí Vizualizér typu.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
