---
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
ms.openlocfilehash: 205a32c0c7c6bb10b8b0a58e62f5d6ba5cdca91f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941697"
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
