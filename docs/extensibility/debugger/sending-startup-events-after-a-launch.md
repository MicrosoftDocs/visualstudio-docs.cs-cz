---
title: Odesílání událostí spuštění po spuštění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713016"
---
# <a name="send-startup-events-after-a-launch"></a>Odeslání událostí spuštění po spuštění
Jakmile je ladicí modul (DE) připojen k programu, odešle řadu událostí spuštění zpět do relace ladění.

 Události při spuštění odeslané zpět do relace ladění zahrnují:

- Událost vytvoření motoru.

- Událost vytvoření programu.

- Vytváření vláken a události načítání modulu.

- Načtení dokončení události, odeslané při načtení kódu a připraven ke spuštění, ale před spuštěním libovolného kódu.

  > [!NOTE]
  > Při pokračování této události jsou inicializovány globální proměnné a spuštěny spouštěcí rutiny.

- Možné další vytváření podprocesů a události načítání modulu.

- Událost vstupního bodu, která signalizuje, že program dosáhl svého `WinMain`hlavního vstupního bodu, **například Main** nebo . Tato událost není obvykle odeslána, pokud de připojí k programu, který je již spuštěn.

  Programově DE nejprve odešle správce ladění relace (SDM) rozhraní [IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) které představuje událost vytvoření motoru následovanou [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), která představuje událost vytvoření programu.

  Tyto události jsou obvykle následuje jeden nebo více událostí vytvoření vlákna [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) události načtení modulu.

  Když je kód načten a připraven ke spuštění, ale před spuštěním libovolného kódu de odešle SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) načíst úplnou událost. Nakonec pokud program ještě není spuštěn, DE odešle událost vstupního bodu [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) která signalizuje, že program dosáhl svého hlavního vstupního bodu a je připraven k ladění.

## <a name="see-also"></a>Viz také
- [Řízení provádění](../../extensibility/debugger/control-of-execution.md)
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
