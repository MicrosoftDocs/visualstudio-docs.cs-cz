---
title: 'IDebugArrayObject:: GetRank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c645683cf1f842afdecba3c3dee8942a3fd6971a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736188"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Získá pořadí pole, tj. počet rozměrů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametry
`pdwRank`\
mimo Vrátí pořadí.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Použijte metodu [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) pro načtení velikosti každé dimenze objektu Array.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
