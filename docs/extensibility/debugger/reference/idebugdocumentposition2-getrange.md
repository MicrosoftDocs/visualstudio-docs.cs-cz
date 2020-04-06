---
title: IDebugDocumentPosition2::GetRange | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731673"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Získá rozsah pro tuto pozici dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
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
 Rozsah zadaný v pozici dokumentu pro zarážky umístění používá ladicí modul (DE) k hledání příkazu, který ve skutečnosti přispívá kódem. Zvažte například následující kód:

```
Line 5: // comment
Line 6: x = 1;
```

 Řádek 5 nepřispívá k ladění programu žádný kód. Pokud ladicí program, který nastaví zarážku na řádku 5, chce, aby DE prohledává určitou částku pro první řádek, který přispívá kódem, ladicí program by určil oblast, která obsahuje další řádky kandidáta, kde může být zarážka správně umístěna. De by pak hledat vpřed prostřednictvím těchto řádků, dokud nenajde řádek, který by mohl přijmout zarážku.

## <a name="see-also"></a>Viz také
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
