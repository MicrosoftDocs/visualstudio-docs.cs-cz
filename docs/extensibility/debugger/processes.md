---
title: Procesy | Microsoft Docs
description: Tento článek popisuje definici a roli procesu v architektuře ladicího programu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901250"
---
# <a name="processes"></a>Procesy
V architektuře ladicího programu *proces*:

- Je kontejner pro sadu programů. Je velmi obdobou procesu Windows, což je kontejner pro sadu vláken.

- Může se identifikovat podle názvu, identifikátoru nebo fyzického identifikátoru.

- Může zobrazit výčet všech spuštěných programů (a jejich vláken).

- Může popsat sám sebe, port, na který běží, a počítač, který ho obsahuje.

- Může vytvořit jeden nebo více programů, ukončit kterýkoli z programů, které vytvoří, nebo způsobit zastavení programu.

- Je reprezentováno [rozhraním IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) které se vytvoří při spuštění procesu. Proces spustí buď správce ladění relací (SDM), nebo [launchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  Ladicí balíček může k procesu připojit ladicí modul (DE) voláním attach [,](../../extensibility/debugger/reference/idebugprocess2-attach.md)což znamená, že se DE připojí ke všem možným programům spuštěných v procesu, který dokáže zpracovat. Pokud se například funkce COMMON Language Runtime DE připojí k procesu, připojí se pouze k programům, ve které běží spravovaný kód.

## <a name="see-also"></a>Viz také
- [Programy](../../extensibility/debugger/programs.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [Ladění balíčku](../../extensibility/debugger/debug-package.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md)
