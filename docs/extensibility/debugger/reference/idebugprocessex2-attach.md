---
description: Tato metoda informuje o procesu, že relace právě ladí proces.
title: 'IDebugProcessEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149740"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Tato metoda informuje o procesu, že relace právě ladí proces.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametry
`pSession`\
pro Hodnota, která jednoznačně identifikuje relaci, která se připojuje k tomuto procesu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Předané rozhraní `pSession` je považováno za soubor cookie, což je hodnota, která jednoznačně identifikuje Správce ladění relací, který se připojuje k tomuto procesu; žádná z metod v zadaném rozhraní není funkční.

## <a name="see-also"></a>Viz také
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
