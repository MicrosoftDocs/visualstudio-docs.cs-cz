---
description: Získá typ prvku v poli.
title: 'IDebugArrayField:: GetElementType – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4c6e5eb14d3fa320cb8b86c20c6d336466c42cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058960"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Získá typ prvku v poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametry
`ppType`\
mimo Vrátí objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který popisuje typ elementu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Objekt [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) předpokládá, že všechny prvky pole jsou stejného typu.

## <a name="see-also"></a>Viz také
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
