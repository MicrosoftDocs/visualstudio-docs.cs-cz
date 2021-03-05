---
description: Tato metoda vrací hodnotu přidruženou k názvu konstanty výčtu.
title: 'IDebugEnumField:: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a4ab2950667ba9268335f2e0dbca1c0ce5183bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153297"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Tato metoda vrací hodnotu přidruženou k názvu konstanty výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
pro Řetězec určující název, pro který má být získána hodnota. Všimněte si, že pro C++ je to řetězec s velkým znakem.

`pValue`\
mimo Vrátí přidruženou číselnou hodnotu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` , pokud název není součástí výčtu nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda rozlišuje velká a malá písmena. Pokud je vyžadováno vyhledávání bez rozlišování velkých a malých písmen (například v jazyce, jako je například Visual Basic kde nerozlišují názvy malých a velkých písmen), použijte [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Viz také
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
