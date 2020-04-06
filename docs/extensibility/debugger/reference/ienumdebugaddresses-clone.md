---
title: IEnumDebugAddresses::Klonování | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f163f2733f237b30b668c2c46473e152718dd6fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717711"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Tato metoda vrátí kopii aktuálnívýčty jako samostatný objekt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugAddresses** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugAddresses ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Vrátí kopii tohoto výčtu jako samostatný objekt.

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kopie výčtu má stejný stav jako originál v době, kdy je tato metoda volána. Stavy kopie a originálu jsou však samostatné a lze je změnit jednotlivě.

## <a name="see-also"></a>Viz také
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
