---
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4a697a4677b6bedef376e602c4327dff66ead53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915413"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Pokračuje v běhu tohoto procesu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) je vymazán a proces se spustí znovu.

> [!NOTE]
> Tato metoda by se měla použít místo [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`\
pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující vlákno, které má být provedeno.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když uživatel spustí spuštění z zastaveného stavu v jiném vlákně procesu, je tato metoda volána v tomto procesu. Tato metoda je volána také v případě, že uživatel vybere příkaz **Start** z nabídky **ladění** v rozhraní IDE. Implementace této metody může být jednoduchá jako volání metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) v aktuálním vlákně v procesu.

> [!WARNING]
> Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
