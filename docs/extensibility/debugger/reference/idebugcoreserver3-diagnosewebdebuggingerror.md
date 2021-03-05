---
description: Pokusí se zjistit, proč se automatické připojení nezdařilo.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95e54add3616fa0ec97f4114b4cd628213e752f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154688"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Pokusí se zjistit, proč se automatické připojení nezdařilo.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametry
`pszUrl`\
pro Momentálně se nepoužívá; hodnota by měla být vždy nastavená na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Níže jsou uvedené další typické návratové kódy:

|Kód|Popis|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Nejde určit, proč se vzdálenému serveru nepovedlo spustit ladění.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Nelze ladit na vzdáleném serveru, pravděpodobně z důvodu nedostatečných oprávnění, nebo protože operace ladění není povolena.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Webový server byl uzamčen a blokuje příkaz DEBUG, který je požadován pro povolení ladění.|

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
