---
description: Získá kontext dokumentu, který odpovídá tomuto kontextu kódu.
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b67e76c8cc8719c77c88c8b93ca667c3a025a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164159"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Získá kontext dokumentu, který odpovídá tomuto kontextu kódu. Kontext dokumentu představuje pozici ve zdrojovém souboru, která odpovídá zdrojovému kódu, který tuto instrukci vygeneroval.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parametry
`ppSrcCxt`\
mimo Vrátí objekt [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , který odpovídá kontextu kódu. Pokud `S_OK` se vrátí, tuto by měl být jiný než `null` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Ladicí stroj by měl vrátit kód chyby, například `E_FAIL` Pokud je parametr, například když `out` `null` má kontext kódu přidruženu zdrojovou pozici.

## <a name="remarks"></a>Poznámky
 Obecně lze kontext dokumentu představit jako pozici ve zdrojovém souboru, zatímco kontext kódu je pozice instrukce kódu ve spouštěcím proudu.

## <a name="see-also"></a>Viz také
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
