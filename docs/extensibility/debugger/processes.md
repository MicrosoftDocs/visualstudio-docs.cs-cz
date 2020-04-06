---
title: Procesy | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738244"
---
# <a name="processes"></a>Procesy
V architektuře ladicího programu *proces*:

- Je kontejner pro sadu programů. Je úzce podobný procesu systému Windows, což je kontejner pro sadu vláken.

- Dokáže se identifikovat podle názvu, identifikátoru nebo fyzického identifikátoru.

- Můžete vytvořit výčet všech spuštěných programů (a jejich vláken).

- Může popsat sám, port, který je spuštěn v a počítač, který jej obsahuje.

- Může vytvořit jeden nebo více programů, ukončit některý z vytvářených programů nebo způsobit ukončení programu.

- Je reprezentován [rozhraní MDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) který je vytvořen při spuštění procesu. Proces je spuštěn správcem ladění relace (SDM) nebo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Ladicí balíček můžete připojit ladicí modul (DE) k procesu voláním [Připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md), což znamená, že DE připojí ke všem možným programům spuštěným v procesu, který může zpracovat. Například pokud se k procesu připojí běžný jazyk runtime DE, připojí se pouze k programům, které spouštějí spravovaný kód.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [Ladicí balíček](../../extensibility/debugger/debug-package.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md)
