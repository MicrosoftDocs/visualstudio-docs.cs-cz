---
description: Načte seznam rámců zásobníku pro toto vlákno.
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9ad740de00338596de622cbce1028768ddda638
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149337"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Načte seznam rámců zásobníku pro toto vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFieldSpec`\
pro Kombinace příznaků z výčtu [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , která určuje, která pole struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) mají být vyplněna. Zadejte `FIF_FUNCNAME_FORMAT` příznak pro formátování názvu funkce do jednoho řetězce.

`nRadix`\
pro Číselná soustava používaná při formátování číselných informací v enumerátoru.

`ppEnum`\
mimo Vrátí objekt [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , který obsahuje seznam struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) popisujících rámec zásobníku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Snímky vlákna jsou vyčísleny v pořadí s aktuálním výčtem, který je nejprve vyhodnocen a nejstarší snímek byl vyhodnocen jako poslední.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
