---
title: IDebugCanStopEvent2::GetReason | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734532"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Získá důvod, proč ladicí modul (DE) chce zastavit.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Parametry
`pcr`\
[out] Vrátí hodnotu z [výčtu CANSTOP_REASON,](../../../extensibility/debugger/reference/canstop-reason.md) který popisuje důvod této události.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je obvykle volána před [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metoda, takže volající`TRUE`může určit, zda předat nenulovou ( ) `IDebugCanStopEvent2::CanStop` metody.

 Důvodem pro zastavení `CANSTOP_ENTRYPOINT`může být buď , což znamená, `CANSTOP_STEPIN`že DE dosáhl vstupníbod, nebo , což znamená, že DE vstoupil do funkce.

## <a name="see-also"></a>Viz také
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
