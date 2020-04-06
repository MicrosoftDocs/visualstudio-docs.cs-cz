---
title: IDebugReference2::GetSize | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7ea57467c6bcc716226ac7075976a0fb9daf5f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720375"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Získá velikost v bajtů, hodnoty odkazu. Vyhrazeno pro budoucí použití.

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
[out] Vrátí velikost hodnoty odkazu v bajtech.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
