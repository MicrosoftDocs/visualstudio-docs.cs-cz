---
description: Načte informace o tomto modulu.
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a31c6e40f18e3b405449179e3e5a3ea1a42acc6f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150560"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Načte informace o tomto modulu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
pro Kombinace příznaků z výčtu [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) , které určují, která pole mají `pInfo` být vyplněna.

`pInfo`\
[in, out] Struktura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , která je vyplněna popisem modulu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Struktura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) obsahuje název modulu, který se zobrazí v okně **moduly** .

## <a name="see-also"></a>Viz také
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
