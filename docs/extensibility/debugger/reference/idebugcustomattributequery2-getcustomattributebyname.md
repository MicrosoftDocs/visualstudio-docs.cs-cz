---
description: Získá vlastní bajty atributů podle názvu vlastního atributu.
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd8b1793bad585dd808ebd812b610cd68aabc129
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077600"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Získá vlastní bajty atributů podle názvu vlastního atributu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parametry
`pszCustomAttributeName`\
pro Řetězec obsahující název vlastního atributu, který má být hledán.

`ppBlob`\
[in, out] Pole, které je vyplněno s vlastními bajty atributů.

`pdwLen`\
[in, out] Určuje maximální počet bajtů, které mají být v `ppBlob` poli vráceny, a vrátí počet bajtů, které jsou ve skutečnosti zapsány do pole.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud vlastní atribut neexistuje. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nastavte `ppBlob` parametr na hodnotu null, která vrátí počet dostupných bajtů atributů. Pak přidělte pole a předejte ho do pole pro `ppBlob` parametr.

 Bajty atributů reprezentují nezpracovaná data vlastního atributu.

 Pokud `ppBlob` `pdwLen` jsou parametry a nastaveny na hodnotu null, lze tuto metodu použít k určení, zda vlastní atribut existuje pouze. Jednodušší alternativa je však volat metodu [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>Viz také
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
