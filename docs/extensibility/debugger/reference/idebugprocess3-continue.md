---
description: Pokračuje v běhu tohoto procesu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) se zachová a proces se začne znovu spouštět.
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e003193a189017b9aeacf6a983756d219b10195
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149769"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Pokračuje v běhu tohoto procesu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) se zachová a proces se začne znovu spouštět.

> [!NOTE]
> Tato metoda by se měla použít místo [pokračování](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující vlákno, které se má pokračovat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se volá na tomto procesu bez ohledu na to, kolik procesů je právě laděno nebo který proces vygeneroval událost zastavení. Implementace musí uchovávat předchozí stav spuštění (například krok) a pokračovat v provádění, jako by se ještě nezastavila před dokončením předchozího spuštění. To znamená, že pokud vlákno v tomto procesu provádělo operaci převzetí operacemi krok za sebou a zastavilo se, protože se zastavil nějaký jiný proces a potom `Continue` byl volán, zadané vlákno musí dokončit původní operaci převzetí služeb.

 **Upozornění** Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
