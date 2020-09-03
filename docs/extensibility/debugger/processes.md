---
title: Procesy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738244"
---
# <a name="processes"></a>Procesy
V architektuře ladicího programu *proces*:

- Je kontejner pro sadu programů. Je úzce obdobou procesu systému Windows, který je kontejnerem pro sadu vláken.

- Může identifikovat sám podle názvu, identifikátoru nebo fyzického identifikátoru.

- Může vytvořit výčet všech spuštěných programů (a jejich podprocesů).

- Může označovat sám sebe, port, na kterém je spuštěný, a počítač, který ho obsahuje.

- Může vytvořit jeden nebo více programů, ukončit všechny programy, které vytvoří, nebo způsobit zastavení programu.

- Je reprezentován rozhraním [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , které se vytvoří při spuštění procesu. Proces se spustí buď pomocí Správce ladění relace (SDM), nebo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Ladicí balíček může připojit ladicí stroj (DE) k procesu voláním metody [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), což znamená, že příkaz de se připojí ke všem možným programům spuštěným v procesu, který dokáže zpracovat. Například pokud se modul CLR (Common Language Runtime) DE připojí k procesu, připojí se pouze k programům, na kterých je spuštěn spravovaný kód.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Ladit balíček](../../extensibility/debugger/debug-package.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md)
