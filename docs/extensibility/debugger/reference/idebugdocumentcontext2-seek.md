---
description: Přesune kontext dokumentu podle zadaného počtu příkazů nebo řádků.
title: 'IDebugDocumentContext2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a70b8fac8e084a78b1a29ae941f1d03d6552f860
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162846"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Přesune kontext dokumentu podle zadaného počtu příkazů nebo řádků.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametry
`nCount`\
pro Počet příkazů nebo řádků, které se mají přesunout dopředu v závislosti na kontextu dokumentu.

`ppDocContext`\
mimo Vrátí nový objekt [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) s novou pozicí.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
