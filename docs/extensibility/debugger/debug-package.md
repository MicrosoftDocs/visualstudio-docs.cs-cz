---
title: Ladicí balíček | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739021"
---
# <a name="debug-package"></a>Ladicí balíček
Ladicí balíček běží v prostředí Visual Studio a zpracovává všechny ui. Spotřebovává rozhraní pro ladění sady Visual Studio a komunikuje se správcem ladění relace (SDM).

 Break události odeslané prostřednictvím SDM přepnout ladicí program z režimu spuštění do režimu přerušení a změnit fokus na program, kde došlo k přerušení. Balíček ladění sleduje rámec zásobníku a podproces z informací odeslaných události.

 Ladicí balíček nemá žádné závislosti prostředí jazyka nebo běhu. Není nutné implementovat nebo upravit ladicí balíček.

 Ladicí balíček je implementován *souborem vsdebug.dll*.

## <a name="see-also"></a>Viz také
- [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)
- [Stohovat rámce](../../extensibility/debugger/stack-frames.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
