---
description: Získá rozsah zdrojového kódu tohoto kontextu dokumentu.
title: 'IDebugDocumentContext2:: GetSourceRange – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d02dfbd93002bedadd4c82168d498f89050ddc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162898"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Získá rozsah zdrojového kódu tohoto kontextu dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametry
`pBegPosition`\
[in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní počáteční pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

`pEndPosition`\
[in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní koncovou pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zdrojový rozsah je celý rozsah zdrojového kódu, od aktuálního příkazu až po předchozí příkaz, který přispěl kódu. Zdrojový rozsah se obvykle používá pro kombinování zdrojových příkazů, včetně komentářů, s kódem v okně zpětný překlad.

 Chcete-li získat rozsah pro pouze příkazy kódu obsažené v tomto kontextu dokumentu, zavolejte metodu [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
