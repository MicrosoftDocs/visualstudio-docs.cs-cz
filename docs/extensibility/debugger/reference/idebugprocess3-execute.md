---
title: IDebugProcess3::Execute | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723681"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Pokračuje ve spuštění tohoto procesu z zastaveného stavu. Jakýkoli předchozí stav spuštění (například krok) je vymazána a proces spustí znovu.

> [!NOTE]
> Tato metoda by měla být použita namísto [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`\
[v] Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující vlákno ke spuštění.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když uživatel spustí spuštění z zastaveného stavu v jiném procesu vlákna, tato metoda je volána na tento proces. Tato metoda je také volána, když uživatel vybere příkaz **Start** z nabídky **Ladění** v rozhraní IDE. Implementace této metody může být stejně jednoduché jako volání [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metoda v aktuálním vlákně v procesu.

> [!WARNING]
> Neodesílejte událost zastavení nebo okamžitou (synchronní) událost na [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto hovoru; jinak může zavěsit ladicí program.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
