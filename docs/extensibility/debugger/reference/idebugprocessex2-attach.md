---
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
ms.openlocfilehash: a9b9e2fa8f636581572b97da58fb9ddefeafd375
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892538"
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
