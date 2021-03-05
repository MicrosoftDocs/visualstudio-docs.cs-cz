---
description: Získá informace o jazyce pro tento kontext kódu.
title: 'IDebugCodeContext2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dccf0c34b6483ad85cc7bfd9cff7078cc20524f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164120"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Získá informace o jazyce pro tento kontext kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parametry
`pbstrLanguage`\
[in, out] Vrátí řetězec, který obsahuje název jazyka, například "C++".

`pguidLanguage`\
[in, out] Vrátí identifikátor GUID pro jazyk kontextu kódu, například `guidCPPLang` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nejméně jeden z parametrů musí vracet hodnotu, která není null.

## <a name="see-also"></a>Viz také
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
