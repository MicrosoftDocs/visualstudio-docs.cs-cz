---
description: Porovná kontext tohoto dokumentu s daným polem kontextů dokumentů.
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a18a689a187e802b92485f092b10b7323d0f97c8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173014"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porovná kontext tohoto dokumentu s daným polem kontextů dokumentů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parametry
`compare`\
pro Hodnota z výčtu [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) , která určuje typ porovnání.

`rgpDocContextSet`\
pro Pole objektů [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , které reprezentují kontexty dokumentů, které jsou v porovnání s.

`dwDocContextSetLen`\
pro Délka pole kontextů dokumentu k porovnání

`pdwDocContext`\
mimo Vrátí index do `rgpDocContextSet` pole prvního kontextu dokumentu, který splňuje porovnání.

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK` , zda byla nalezena shoda. Vrátí `S_FALSE` , pokud nebyla nalezena žádná shoda. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Objekty [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , které jsou předány v poli, musí být implementovány stejným ladicím strojem, který implementuje objekt, na kterém je `IDebugDocumentContext2` volána; v opačném případě porovnání není platné.

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
