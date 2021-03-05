---
description: Načte velikost textu na této pozici v dokumentu.
title: 'IDebugDocumentText2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91dd1b2a510589ab048bd1bd290b0ab4aabe571b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167305"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Načte velikost textu na této pozici v dokumentu.

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
mimo Vrátí počet řádků textu.

`pcNumChars`\
mimo Vrátí počet znaků textu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky

 [Pouze C++] Pokud určitou hodnotu nepožadujete, předejte pro parametr hodnotu NULL.

 [Pouze C#] Musí být zadány oba parametry.

## <a name="see-also"></a>Viz také
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
