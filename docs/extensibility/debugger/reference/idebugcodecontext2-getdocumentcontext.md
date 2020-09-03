---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734346"
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
