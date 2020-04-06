---
title: IDebugThread2::EnumFrameInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718857"
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
[v] Kombinace příznaků z [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) výčtu, který určuje, která pole [frameINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury mají být vyplněny. Zadejte `FIF_FUNCNAME_FORMAT` příznak pro formátování názvu funkce do jednoho řetězce.

`nRadix`\
[v] Radix používá ve formátování číselných informací v čítači výčtu.

`ppEnum`\
[out] Vrátí objekt [IEnumDebugFrameInfo2,](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) který obsahuje seznam struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) popisujících rámec zásobníku.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Rámce vlákna jsou uvedeny v pořadí, přičemž aktuální snímek je uveden jako první a nejstarší snímek vyčíslený jako poslední.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
