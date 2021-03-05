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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9624a04ae70c8d29abd9b8af5b597b583efb7834
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143841"
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
