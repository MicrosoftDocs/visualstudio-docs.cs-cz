---
description: Tato metoda získá informace o poli.
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c681fef38377f0ce8e74b45dba065b5eae39462c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151932"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Tato metoda získá informace o poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
pro Kombinace [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) konstant, které vyberou informace, které se mají zobrazit Pokud pole představuje symbol, obvykle se jedná o název a typ symbolu.

`pFieldInfo`\
mimo Vrátí informace v zadané struktuře [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
