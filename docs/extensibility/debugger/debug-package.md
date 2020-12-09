---
title: Ladit balíček | Microsoft Docs
description: Přečtěte si, jak balíček ladění běží v prostředí Visual Studio a zpracovává uživatelské rozhraní tím, že spotřebovává rozhraní pro ladění a komunikuje se správcem ladění relace.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914124"
---
# <a name="debug-package"></a>Ladit balíček
Ladicí balíček běží v prostředí Visual Studio a zpracovává všechna rozhraní. Spotřebovává rozhraní pro ladění sady Visual Studio a komunikuje se správcem ladění relace (SDM).

 Přerušit události odesílané přes model SDM přepněte ladicí program z režimu spuštění do režimu přerušení a změňte fokus na program, kde došlo k přerušení. Balíček pro ladění sleduje rámec zásobníku a vlákno z informací, které jsou do něj odesílány událostmi.

 Ladicí balíček nemá žádné závislosti jazyka nebo prostředí run-time. Není nutné implementovat ani upravovat balíček ladění.

 Balíček pro ladění je implementován pomocí *vsdebug.dll*.

## <a name="see-also"></a>Viz také
- [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)
- [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
