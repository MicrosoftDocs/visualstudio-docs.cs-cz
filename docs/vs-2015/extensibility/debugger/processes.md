---
title: Procesy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153671"
---
# <a name="processes"></a>Procesy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V rámci architektury ladicího programu **proces**:  
  
- Je kontejner pro sadu programů. Je úzce obdobou procesu systému Windows, který je kontejnerem pro sadu vláken.  
  
- Může identifikovat sám podle názvu, identifikátoru nebo fyzického identifikátoru.  
  
- Může vytvořit výčet všech spuštěných programů (a jejich podprocesů).  
  
- Může označovat sám sebe, port, na kterém je spuštěný, a počítač, který ho obsahuje.  
  
- Může vytvořit jeden nebo více programů, ukončit všechny programy, které vytvoří, nebo způsobit zastavení programu.  
  
- Je reprezentován rozhraním [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , které se vytvoří při spuštění procesu. Proces se spustí buď pomocí Správce ladění relace (SDM), nebo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  Ladicí balíček může k procesu připojit modul ladění (DE) voláním příkazu [připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md). To znamená, že DE připojí ke všem možným programům spuštěným v procesu, který dokáže zpracovat. Například pokud se modul CLR (Common Language Runtime) DE připojí k procesu, připojí se pouze k programům, na kterých je spuštěn spravovaný kód.  
  
## <a name="see-also"></a>Viz také  
 [Spuštěn](../../extensibility/debugger/programs.md)   
 [Vláken](../../extensibility/debugger/threads.md)   
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)   
 [Ladit balíček](../../extensibility/debugger/debug-package.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Připojit](../../extensibility/debugger/reference/idebugprocess2-attach.md)
