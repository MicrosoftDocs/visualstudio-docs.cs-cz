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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41d004a9b226646dd1196f1debc244cdf11efe32
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092576"
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
