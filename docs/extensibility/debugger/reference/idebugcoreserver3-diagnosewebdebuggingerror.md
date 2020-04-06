---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732949"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Pokusy o určení, proč se automatické připojení nezdařilo.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametry
`pszUrl`\
[v] Není v současné době používáno; by měla být vždy nastavena na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Následují další typické návratové kódy:

|kód|Popis|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Nelze určit, proč se vzdálenému serveru nepodařilo spustit ladění.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Nelze ladit na vzdáleném serveru, pravděpodobně z důvodu nedostatečných oprávnění nebo protože sloveso LADĚNÍ není povoleno.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Webový server byl uzamčen a blokuje sloveso LADĚNÍ, které je nutné k povolení ladění.|

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
