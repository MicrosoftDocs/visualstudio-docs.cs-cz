---
title: IDebugCodeContext2::GetDocumentContext | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734346"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Získá kontext dokumentu, který odpovídá tomuto kontextu kódu. Kontext dokumentu představuje pozici ve zdrojovém souboru, která odpovídá zdrojovému kódu, který generoval tuto instrukci.

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
[out] Vrátí objekt [IDebugDocumentContext2,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) který odpovídá kontextu kódu. Pokud `S_OK` je vrácena, ths`null`by měla být non- .

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Ladicí modul by měl vrátit `E_FAIL` kód `out` selhání, například když je `null` parametr například když kontext kódu nemá žádnou přidruženou zdrojovou pozici.

## <a name="remarks"></a>Poznámky
 Obecně kontextu dokumentu lze považovat za pozici ve zdrojovém souboru, zatímco kontext kódu je pozice instrukce kódu v proudu spuštění.

## <a name="see-also"></a>Viz také
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
