---
title: 'Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5ff383b279bbdac85ce85de6e65b857cec6a8e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737480"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.
Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:

 Microsoft Visual Studio Sledování vzdáleného ladění na vzdáleném počítači je spuštěný jako jiný uživatel.

## <a name="cause"></a>příčina
 Tato zpráva se zobrazí, když ladíte v režimu bez ověřování a uživatel, který spustil msvsmon, není uživatel, který používá Visual Studio.

## <a name="solution"></a>Řešení
 Nejbezpečnější a nejlepší řešení je spustit Sledování vzdáleného ladění (Msvsmon. exe) pod stejným uživatelským účtem jako Visual Studio. Pokud to nemůžete udělat, můžete spustit Sledování vzdáleného ladění pod druhým účtem s možností **Povolit libovolný uživatel k ladění** vybraný v dialogovém okně **Možnosti** sledování vzdáleného ladění.

> [!CAUTION]
> Udělení oprávnění ostatním uživatelům pro připojení umožňuje nechtěnému připojení k nesprávnému relaci vzdáleného ladění. Ladění v režimu **bez ověřování** není nikdy zabezpečené a mělo by se používat opatrně.

## <a name="see-also"></a>Viz také:
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)