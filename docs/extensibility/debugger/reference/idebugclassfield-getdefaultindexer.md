---
title: 'IDebugClassField:: GetDefaultIndexer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57e00107374485043af370967794bdade1c213d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734418"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Získá název výchozího indexeru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parametry
`pbstrIndexer` mimo Vrátí řetězec obsahující název výchozího indexeru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud není k dispozici žádný výchozí indexer. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Výchozím indexerem třídy je vlastnost, která je označena jako `Default` vlastnost pro přístup k poli. To je specifické pro [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] . Zde je příklad výchozího indexeru deklarovaného v [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] a způsobu jeho použití.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
