---
title: Posílání událostí po spuštění | Microsoft Docs
description: Přečtěte si o řadě spouštěcích událostí, které ladicí stroj odešle do ladicí relace poté, co je ladicí stroj připojen k programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 227d863df1e3318d2df6be6a24aaf05b5033e92d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070394"
---
# <a name="send-startup-events-after-a-launch"></a>Po spuštění Odeslat události po spuštění
Jakmile je ladicí stroj (DE) připojen k programu, pošle řada událostí po spuštění zpět do ladicí relace.

 Události spuštění odeslané zpět do ladicí relace zahrnují:

- Událost vytvoření motoru.

- Událost vytvoření programu

- Události vytvoření vlákna a načtení modulu.

- Událost dokončení zátěže, která je odeslána, když je kód načten a připraven ke spuštění, ale před spuštěním jakéhokoli kódu.

  > [!NOTE]
  > Po pokračování této události jsou inicializovány globální proměnné a spuštěny rutiny spuštění.

- Je možné provést jiné události vytvoření vlákna a načtení modulu.

- Událost vstupního bodu, která signalizuje, že program dosáhl svého hlavního vstupního bodu, jako je například **Main** nebo `WinMain` . Tato událost se obvykle neposílá, pokud se DE připojí k programu, který je už spuštěný.

  Prostřednictvím kódu programu DE First pošle Správce ladění relace (SDM) rozhraní [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , které představuje událost vytvoření modulu, následovanou [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), která představuje událost vytvoření programu.

  Tyto události jsou obvykle následovány jednou nebo více událostmi vytvoření vlákna [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a událostmi načtení modulu [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Když je kód načten a připraven ke spuštění, ale před spuštěním jakéhokoli kódu, DE pošle událost SDM, která [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) načtení dokončí. Nakonec, pokud program ještě není spuštěný, nástroj DE pošle událost vstupního bodu [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , která signalizuje, že program dosáhl svého hlavního vstupního bodu a je připravený na ladění.

## <a name="see-also"></a>Viz také
- [Řízení provádění](../../extensibility/debugger/control-of-execution.md)
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
