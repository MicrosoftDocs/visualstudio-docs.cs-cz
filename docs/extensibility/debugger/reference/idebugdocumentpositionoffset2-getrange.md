---
title: IDebugDocumentPositionOffset2::GetRange | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731623"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Načte rozsah pro aktuální pozici dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametry
`pdwBegOffset`\
[dovnitř, ven] Posun pro počáteční pozici rozsahu. Pokud tyto informace nejsou potřeba, nastavte tento parametr na hodnotu null.

`pdwEndOffset`\
[dovnitř, ven] Posun pro koncovou pozici rozsahu. Pokud tyto informace nejsou potřeba, nastavte tento parametr na hodnotu null.

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
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
