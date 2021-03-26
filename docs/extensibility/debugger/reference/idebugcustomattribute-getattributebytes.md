---
description: Získá informace o atributu jako objekt BLOB bajtů.
title: 'IDebugCustomAttribute:: GetAttributeBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84d6e807e3be6d0fbdaa94834fbc8cad37f8e4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088078"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Získá informace o atributu jako objekt BLOB bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parametry
`ppBlob`\
[in, out] Pole, které je vyplněno bajty atributů.

`pdwLen`\
[in, out] Určuje maximální počet bajtů, které mají být v `ppBlob` poli vráceny, a vrátí počet bajtů, které jsou ve skutečnosti zapsány do pole.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nastavte `ppBlob` parametr na hodnotu null, která vrátí počet dostupných bajtů atributů. Pak přidělte pole a předejte ho do pole pro `ppBlob` parametr.

 Bajty atributů reprezentují nezpracovaná data vlastního atributu.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
