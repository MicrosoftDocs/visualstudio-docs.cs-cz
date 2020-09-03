---
title: 'IDebugCanStopEvent2:: getdůvod | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734532"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Získá důvod, proč se chce ladicí stroj (DE) zastavit.

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
mimo Vrací hodnotu z výčtu [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) , který popisuje důvod pro tuto událost.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je obvykle volána před metodou [po spuštění](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) , aby volající mohl určit, zda má být metodě předána nenulová hodnota ( `TRUE` ) `IDebugCanStopEvent2::CanStop` .

 Důvod zastavení může být buď `CANSTOP_ENTRYPOINT` , což znamená, že de dosáhla vstupní bod, nebo `CANSTOP_STEPIN` , což znamená, že se de dostala do funkce.

## <a name="see-also"></a>Viz také
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
