---
title: IDebugCanStopEvent2::CanStop | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734588"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Upozorní ladicí modul (DE), zda se má zastavit v aktuálním umístění kódu nebo pokračovat v provádění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parametry
`fCanStop`\
[v] Nenulová`TRUE`( ), pokud by se DE zastavila v aktuálním umístění kódu; jinak nula`FALSE`( ).

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Příjemce této události obvykle volá [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metoda k určení důvodu DE chce zastavit `IDebugCanStopEvent2::CanStop` a potom volá metodu s příslušnou odpověď.

 Pokud DE zastaví, odešle událost, která popisuje důvod pro zastavení. Obvykle jsou odeslány dvě události, přerušení uživatele nebo signálu reprezentované rozhraním [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) a událost zarážky reprezentovaná rozhraním [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

## <a name="see-also"></a>Viz také
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
