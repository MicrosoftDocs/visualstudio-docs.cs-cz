---
title: IDebugProgram2::Pokračovat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723076"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Pokračuje ve spouštění tohoto programu ze zastaveného stavu. Jakýkoli předchozí stav spuštění (například krok) je zachován a program se spustí znovu.

> [!NOTE]
> Tato metoda je zastaralé. Místo toho použijte metodu [Continue.](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`[v] [Objekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje vlákno.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána v tomto programu bez ohledu na to, kolik programů je odladěno nebo který program vygeneroval událost zastavení. Implementace musí zachovat předchozí stav spuštění (například krok) a pokračovat v provádění, jako by nikdy zastavena před dokončením jeho předchozí spuštění. To znamená, že pokud vlákno v tomto programu provádělo operaci krok přes a bylo zastaveno, protože byl zastaven jiný program a pak byla tato metoda volána, musí program dokončit původní operaci krok přes.

> [!WARNING]
> Neodesílejte událost zastavení nebo okamžitou (synchronní) událost na [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto hovoru; jinak může zavěsit ladicí program.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
