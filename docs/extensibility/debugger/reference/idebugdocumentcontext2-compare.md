---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731890"
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
