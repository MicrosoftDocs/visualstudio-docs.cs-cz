---
description: Tato metoda získá název konstanty výčtu dané hodnoty.
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8601be6a1c87fcad10c6e5260e791fcf2ce42f01
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153336"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Tato metoda získá název konstanty výčtu dané hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parametry
`value`\
pro Hodnota, pro kterou má být získán název konstanty výčtu.

`pbstrValue`\
mimo Vrátí název konstanty výčtu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí hodnotu `S_OK` ; jinak vrátí, `S_FALSE` zda nemá žádná přidružená název, nebo vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud je k stejné hodnotě přidruženo více než jeden název, bude vráceno křestní jméno definované ve výčtu.

## <a name="see-also"></a>Viz také
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
