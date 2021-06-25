---
title: Ladění balíčků | Microsoft Docs
description: Zjistěte, jak se ladicí balíček spouští v Visual Studio prostředí a zpracovává uživatelské rozhraní tím, že používá rozhraní ladění a komunikuje se správcem ladění relací.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905667"
---
# <a name="debug-package"></a>Ladění balíčku
Balíček pro ladění se spouští v Visual Studio prostředí a zpracovává veškeré uživatelské rozhraní. Využívá rozhraní Visual Studio ladění a komunikuje se správcem ladění relací (SDM).

 Události odeslané přes SDM přepněte ladicí program z režimu spuštění do režimu přerušení a změňte fokus na program, ve kterém došlo k přerušení. Ladicí balíček sleduje rámec zásobníku a vlákno z informací, které do něj byly odeslány událostmi.

 Ladicí balíček nemá žádné závislosti jazyka nebo prostředí za běhu. Není nutné implementovat ani upravovat ladicí balíček.

 Balíček pro ladění je implementován *vsdebug.dll*.

## <a name="see-also"></a>Viz také
- [Správce ladění relací](../../extensibility/debugger/session-debug-manager.md)
- [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)
- [Vlákna](../../extensibility/debugger/threads.md)
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
