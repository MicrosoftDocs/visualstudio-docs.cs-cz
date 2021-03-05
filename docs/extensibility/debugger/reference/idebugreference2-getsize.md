---
description: Získá velikost hodnoty reference v bajtech.
title: 'IDebugReference2:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e653a88adcf6388ab31d7ba5ae2cf526c5c84bae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165966"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Získá velikost hodnoty reference v bajtech. Vyhrazeno pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametry
`pdwSize`\
mimo Vrátí velikost hodnoty reference v bajtech.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
