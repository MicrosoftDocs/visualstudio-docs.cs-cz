---
title: Ladit balíček | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181301"
---
# <a name="debug-package"></a>Ladění balíčku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí balíček běží v prostředí Visual Studio a zpracovává všechna rozhraní. Spotřebovává rozhraní pro ladění sady Visual Studio a komunikuje se správcem ladění relace (SDM).  
  
 Přerušit události odesílané přes model SDM přepněte ladicí program z režimu spuštění do režimu přerušení a změňte fokus na program, kde došlo k přerušení. Balíček pro ladění sleduje rámec zásobníku a vlákno z informací, které jsou do něj odesílány událostmi.  
  
 Ladicí balíček nemá žádné závislosti jazyka nebo prostředí run-time. Není nutné implementovat ani upravovat balíček ladění.  
  
 Balíček pro ladění je implementován pomocí vsdebug.dll.  
  
## <a name="see-also"></a>Viz také  
 [Správce ladění relace](../../extensibility/debugger/session-debug-manager.md)   
 [Rámce zásobníku](../../extensibility/debugger/stack-frames.md)   
 [Vláken](../../extensibility/debugger/threads.md)   
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
