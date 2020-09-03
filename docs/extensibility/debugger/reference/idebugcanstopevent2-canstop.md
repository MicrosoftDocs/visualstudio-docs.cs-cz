---
title: 'IDebugCanStopEvent2:: po spuštění | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734588"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Upozorní modul ladění (DE) na to, jestli se má zastavit v aktuálním umístění kódu, nebo jenom pokračovat v provádění.

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
pro Non-Zero ( `TRUE` ), pokud by měl příkaz de zastavit v aktuálním umístění kódu; v opačném případě nula ( `FALSE` ).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Příjemce této události obvykle volá metodu [getdůvod](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) k určení příčiny, proč de chce zastavit, a pak zavolá `IDebugCanStopEvent2::CanStop` metodu s příslušnou odpovědí.

 Pokud se operace DE zastaví, pošle událost, která popisuje důvod zastavení. K dispozici jsou obvykle dvě události, které jsou odeslány, uživatel nebo přerušení signálu reprezentované rozhraním [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) a událost zarážky reprezentované rozhraním [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>Viz také
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
