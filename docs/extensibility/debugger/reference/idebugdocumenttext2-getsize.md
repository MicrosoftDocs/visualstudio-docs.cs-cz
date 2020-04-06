---
title: IDebugDocumentText2::GetSize | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731588"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Načte velikost textu na tomto místě v dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parametry
`pcNumLines`\
[out] Vrátí počet řádků textu.

`pcNumChars`\
[out] Vrátí počet znaků textu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky

 [Pouze C++] Pokud určitá hodnota není žádoucí, předajte hodnotu NULL pro parametr.

 [Pouze C#] Musí být zadány oba parametry.

## <a name="see-also"></a>Viz také
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
