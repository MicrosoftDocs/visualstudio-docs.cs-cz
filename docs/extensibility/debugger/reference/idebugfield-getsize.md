---
title: 'IDebugField:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6330179f1bbfffcb1f590dfc09ae0c06385f12e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869853"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Tato metoda získá velikost pole v bajtech.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametry
`pdwSize`\
mimo Vrátí velikost.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Všechna pole mají typ a všechny typy mají velikost. Například pole s typem bajt má velikost 1 bajt.

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
