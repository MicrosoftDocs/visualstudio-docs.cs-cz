---
description: 'IDebugProgram2:: Continue pokračuje v běhu tohoto programu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) se zachová a program se spustí znovu.'
title: 'IDebugProgram2:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60f3cb4764a53d359e971020df8261d064c62e81
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076118"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Pokračuje v běhu tohoto programu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) se zachová a program se spustí znovu.

> [!NOTE]
> Tato metoda je zastaralá. Místo toho použijte metodu [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .

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
`pThread` pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána u tohoto programu bez ohledu na to, kolik programů je právě laděno nebo který program vygeneroval událost zastavení. Implementace musí uchovávat předchozí stav spuštění (například krok) a pokračovat v provádění, jako by se ještě nezastavila před dokončením předchozího spuštění. To znamená, že pokud vlákno v tomto programu provádělo operaci převzetím krok za běhu a zastavilo se, protože se zastavil nějaký jiný program a tato metoda se zavolala, program musí dokončit původní operaci převzetí služeb při selhání.

> [!WARNING]
> Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
