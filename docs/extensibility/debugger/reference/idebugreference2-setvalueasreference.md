---
description: Nastaví hodnotu odkazu z jiného odkazu.
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84117f4a9eb925b442be86a73736479a05818ca1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165940"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Nastaví hodnotu odkazu z jiného odkazu. Vyhrazeno pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametry
`rgpArgs`\
pro Pole objektů [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , které slouží k určení způsobu nastavení referenční hodnoty.

`dwArgCount`\
pro Počet odkazů v poli.

`pValue`\
pro Objekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , ze kterého se má nastavit hodnota vlastnosti

`dwTimeout`\
pro Maximální doba (v milisekundách), po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
