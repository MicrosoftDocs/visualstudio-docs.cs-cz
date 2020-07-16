---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6a70a96014ebf18984c75df60cfeb75ba0d0577
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387236"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Provede krok.

> [!NOTE]
> Tato metoda je zastaralá. Místo toho použijte metodu [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parametry
`pThread`\
pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje nejladěné vlákno.

`sk`\
pro Hodnota z výčtu [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) , která určuje druh kroku.

`step`\
pro Hodnota z výčtu [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) , která určuje jednotku kroku (například podle příkazu nebo instrukce).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V případě, že dojde ke synchronizaci vlákna nebo komunikaci mezi vlákny, by se měly spouštět další vlákna v programu při krokování určitého vlákna.

> [!WARNING]
> Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
