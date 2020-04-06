---
title: IDebugProgramEx2::Připojit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722390"
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
[v] Objekt [IDebugCallBackback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) který představuje funkci zpětného volání, do které připojený ladicí modul odesílá události.

`dwReason`\
[v] Hodnota z [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) výčtu, který popisuje důvod operace připojení.

`pSession`\
[v] Hodnota, která jednoznačně identifikuje relaci, která se připojuje k programu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Tato metoda `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` by měla vrátit, pokud je program již připojen.

## <a name="remarks"></a>Poznámky
 Port, který obsahuje program, může `pSession` použít hodnotu v aplikace k určení, která relace se pokouší připojit k programu. Například pokud port umožňuje pouze jednu relaci ladění připojit k procesu v době, port můžete určit, zda je stejná relace již připojena k jiným programům v procesu.

> [!NOTE]
> Předané rozhraní `pSession` má být považováno pouze za soubor cookie, což je hodnota, která jednoznačně identifikuje správce ladění relace připojující se k tomuto programu; žádná z metod na dodaném rozhraní není funkční.

## <a name="see-also"></a>Viz také
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
