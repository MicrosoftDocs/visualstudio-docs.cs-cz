---
title: Ladit balíček | Microsoft Docs
description: Přečtěte si, jak balíček ladění běží v prostředí Visual Studio a zpracovává uživatelské rozhraní tím, že spotřebovává rozhraní pro ladění a komunikuje se správcem ladění relace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067904"
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
