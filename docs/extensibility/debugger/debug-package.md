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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e5296a77e835ab291bce7a77e3f0cb09eb6bcf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840844"
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
