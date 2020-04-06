---
title: IDebugProgram2::Spustit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722983"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Pokračuje ve spouštění tohoto programu ze zastaveného stavu. Všechny předchozí spuštění stavu (například krok) je vymazána a program spustí provádění znovu.

> [!NOTE]
> Tato metoda je zastaralé. Místo toho použijte metodu [Execute.](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když uživatel spustí spuštění z zastaveného stavu v vlákně jiného programu, je tato metoda volána v tomto programu. Tato metoda je také volána, když uživatel vybere příkaz **Start** z nabídky **Ladění** v rozhraní IDE. Implementace této metody může být stejně jednoduché jako volání [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metoda v aktuálním vlákně v programu.

> [!WARNING]
> Neodesílejte událost zastavení nebo okamžitou (synchronní) událost na [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto hovoru; jinak může zavěsit ladicí program.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
