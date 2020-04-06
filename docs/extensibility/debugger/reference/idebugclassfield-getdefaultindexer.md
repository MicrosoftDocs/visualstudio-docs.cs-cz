---
title: IDebugClassField::GetDefaultIndexer | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734418"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Získá název výchozí indexeru.

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
`pbstrIndexer`[out] Vrátí řetězec obsahující název výchozího indexeru.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistuje žádný výchozí indexer. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Výchozí indexer třídy je vlastnost, která `Default` je označena jako vlastnost pro přístupy pole. To je [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]specifické pro . Zde je příklad výchozí indexer [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] deklarované v a jak se používá.

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
