---
title: 'IDebugProgramEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30818627f8ebc293e444b43adb0590db077da4a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898833"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Připojte relaci k programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který představuje funkci zpětného volání, do které připojený ladicí stroj odesílá události.

`dwReason`\
pro Hodnota z výčtu [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , která popisuje důvod operace připojení.

`pSession`\
pro Hodnota, která jednoznačně identifikuje relaci, která je připojena k programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby. Tato metoda by měla vracet `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` , pokud je program již připojen.

## <a name="remarks"></a>Poznámky
 Port, který obsahuje program, může použít hodnotu v `pSession` k určení relace, která se pokouší o připojení k programu. Pokud například port umožňuje připojit pouze jednu relaci ladění k procesu najednou, port může určit, zda je stejná relace již připojena k ostatním programům v procesu.

> [!NOTE]
> Předané rozhraní `pSession` je považováno za soubor cookie, což je hodnota, která jednoznačně identifikuje Správce ladění relací, který se připojuje k tomuto programu; žádná z metod v zadaném rozhraní není funkční.

## <a name="see-also"></a>Viz také
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
