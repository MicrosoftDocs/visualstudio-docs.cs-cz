---
description: Určuje, zda je pozice dokumentu obsažena v daném dokumentu.
title: 'IDebugDocumentPosition2:: IsPositionInDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4800f3735e2d015e3638a642e8c0d54829ddd4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154285"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Určuje, zda je pozice dokumentu obsažena v daném dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

## <a name="parameters"></a>Parametry
`pDoc`\
pro Objekt [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , který představuje kandidáta na dokument.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá hlavně při nastavení zarážek v rozhraních [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) . Při načítání dokumentů je volána pozice zarážky k určení, zda dokument obsahuje tuto pozici.

## <a name="see-also"></a>Viz také
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
