---
title: Sledování vzdáleného ladění sady Microsoft Visual Studio je na vzdáleném počítači spuštěné pod jiným uživatelským účtem.
titleSuffix: ''
description: Tato zpráva se zobrazí, když ladíte v režimu bez ověřování a uživatel, který spustil msvsmon, není uživatel, který používá Visual Studio.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cee8ea9442ab88c280a11a0b73d74cac6888e9f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146701"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Chyba: Microsoft Visual Studio Remote Debugging Monitor na vzdáleném počítači běží jako jiný uživatel.
Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:

 Microsoft Visual Studio Sledování vzdáleného ladění na vzdáleném počítači je spuštěný jako jiný uživatel.

## <a name="cause"></a>Příčina
 Tato zpráva se zobrazí, když ladíte v režimu bez ověřování a uživatel, který spustil msvsmon, není uživatel, který používá Visual Studio.

## <a name="solution"></a>Řešení
 Nejbezpečnější a nejlepší řešení je spustit Sledování vzdáleného ladění (msvsmon.exe) pod stejným uživatelským účtem jako Visual Studio. Pokud to nemůžete udělat, můžete spustit Sledování vzdáleného ladění pod druhým účtem s možností **Povolit libovolný uživatel k ladění** vybraný v dialogovém okně **Možnosti** sledování vzdáleného ladění.

> [!CAUTION]
> Udělení oprávnění ostatním uživatelům pro připojení umožňuje nechtěnému připojení k nesprávnému relaci vzdáleného ladění. Ladění v režimu **bez ověřování** není nikdy zabezpečené a mělo by se používat opatrně.

## <a name="see-also"></a>Viz také
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
