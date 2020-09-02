---
title: 'Chyba: Microsoft Visual Studio Sledování vzdáleného ladění na vzdáleném počítači je spuštěný jako jiný uživatel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dffaafbca80828a7501f5f7d24e525225284f5a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697312"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:  
  
 Microsoft Visual Studio Sledování vzdáleného ladění na vzdáleném počítači je spuštěný jako jiný uživatel.  
  
## <a name="cause"></a>Příčina  
 Tato zpráva se zobrazí, když ladíte v režimu bez ověřování a uživatel, který spustil msvsmon, není uživatel, který používá Visual Studio.  
  
## <a name="solution"></a>Řešení  
 Nejbezpečnější a nejlepší řešení je spustit Sledování vzdáleného ladění (msvsmon.exe) pod stejným uživatelským účtem jako Visual Studio. Pokud to nemůžete udělat, můžete spustit Sledování vzdáleného ladění pod druhým účtem s možností **Povolit libovolný uživatel k ladění** vybraný v dialogovém okně **Možnosti** sledování vzdáleného ladění.  
  
> [!CAUTION]
> Udělení oprávnění ostatním uživatelům pro připojení umožňuje nechtěnému připojení k nesprávnému relaci vzdáleného ladění. Ladění v režimu **bez ověřování** není nikdy zabezpečené a mělo by se používat opatrně.  
  
 Další informace najdete v tématu [spuštění sledování vzdáleného ladění](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Viz také  
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
