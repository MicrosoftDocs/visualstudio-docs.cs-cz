---
title: IDebugProcess3::Pokračovat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723780"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Pokračuje ve spuštění tohoto procesu z zastaveného stavu. Jakýkoli předchozí stav spuštění (například krok) je zachována a proces spustí znovu.

> [!NOTE]
> Tato metoda by měla být použita namísto [Pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
[v] [Objekt IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující vlákno, které má pokračovat.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána na tento proces bez ohledu na to, kolik procesů jsou laděny nebo který proces generoval zastavení události. Implementace musí zachovat předchozí stav spuštění (například krok) a pokračovat v provádění, jako by nikdy zastavena před dokončením jeho předchozí spuštění. To znamená, že pokud vlákno v tomto procesu provádělo operaci krok přes `Continue` a bylo zastaveno, protože byl zastaven jiný proces a poté byl volán, zadaný podproces musí dokončit původní operaci krok přes.

 **Upozornění** Neodesílejte událost zastavení nebo okamžitou (synchronní) událost na [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto hovoru; jinak může zavěsit ladicí program.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
