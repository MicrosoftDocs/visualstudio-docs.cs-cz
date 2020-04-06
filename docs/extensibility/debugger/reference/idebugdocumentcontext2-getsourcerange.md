---
title: IDebugDocumentContext2::GetSourceRange | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731797"
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
[dovnitř, ven] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, která je vyplněna počáteční polohou. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

`pEndPosition`\
[dovnitř, ven] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, která je vyplněna koncovou polohou. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zdrojový rozsah je celý rozsah zdrojového kódu, od aktuálního příkazu zpět až po předchozí příkaz, který přispěl kódem. Zdrojová oblast se obvykle používá pro míchání zdrojových příkazů, včetně poznámek, s kódem v okně demontáže.

 Chcete-li získat rozsah pouze příkazy kódu obsažené v tomto kontextu dokumentu, volání [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) metoda.

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
