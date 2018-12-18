---
title: 'Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cb477cf852d0e07bf14f344b3dc27b20a56de59
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067730"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.
Při pokusu o provádět vzdálené ladění, může zobrazit následující chybová zpráva:  
  
 Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.  
  
## <a name="cause"></a>příčina  
 Tato zpráva se zobrazí při ladění v módu bez ověřování a uživatel, který spuštění msvsmon není uživatel, který se systémem Visual Studio.  
  
## <a name="solution"></a>Řešení  
 Nejbezpečnější a nejlepší řešení je pro spuštění sledování vzdáleného ladění (msvsmon.exe) pod stejným uživatelským účtem jako Visual Studio. Pokud nemůžete udělat, můžete pod jiným účtem se spustit sledování vzdáleného ladění **dovolit ladění jakémukoliv uživateli** možnosti vybrané v sledování vzdáleného ladění **možnosti** dialogové okno.  
  
> [!CAUTION]
>  Udělení oprávnění pro připojení jiných uživatelů umožňuje možnost nechtěným připojením k nesprávné relace vzdáleného ladění. Ladění v **bez ověřování** režimu se nikdy zabezpečené a by měl třeba používat opatrně.
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění chyby a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)