---
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730251"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Tato metoda používá hledání bez rozlišování velkých a malých písmen k vrácení hodnoty přidružené k názvu konstanty výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
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
 V této metodě se nerozlišují malá a velká písmena. Pokud je potřeba vyhledávání citlivé na velká a malá písmena (například v jazyce C++, kde se v názvech rozlišují malá a velká písmena), použijte [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Viz také
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
