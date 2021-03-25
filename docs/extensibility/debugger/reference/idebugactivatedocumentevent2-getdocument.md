---
description: Načte dokument, který se má aktivovat.
title: 'IDebugActivateDocumentEvent2:: GetDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocument
helpviewer_keywords:
- GetDocument method
- IDebugActivateDocumentEvent2::GetDocument method
ms.assetid: b3c32f1b-f3de-409d-920d-ba7b3fa84fcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68d75fc184dbe774c4115451c504244c2e79a4f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059207"
---
# <a name="idebugactivatedocumentevent2getdocument"></a>IDebugActivateDocumentEvent2::GetDocument
Načte dokument, který se má aktivovat.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDocument ( 
   IDebugDocument2** ppDoc
);
```

```csharp
int GetDocument ( 
   out IDebugDocument2 ppDoc
);
```

## <a name="parameters"></a>Parametry
`ppDoc`\
mimo Vrátí objekt [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , který představuje dokument, který se má aktivovat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
