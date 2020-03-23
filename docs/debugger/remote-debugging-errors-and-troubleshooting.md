---
title: Vzdálené ladění chyb y a řešení potíží | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302089"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Chyby a řešení potíží se vzdáleným laděním

Při pokusu o vzdálené ladění se můžete sejít s následujícími chybami.

- [Chyba: Automatické krokování s vnořením do serveru se nezdařilo.](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Chyba: Zdá se, že sledování vzdáleného ladění sady Microsoft Visual Studio (MSVSMON.EXE) na vzdáleném počítači neběží.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Nelze se připojit k monitoru vzdáleného ladění sady Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Chyba: Vzdálený počítač se nezobrazuje v dialogovém okně Vzdálená připojení](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Spuštění vzdáleného ladicího programu jako správce

Pokud nespustíte vzdálený ladicí program jako správce, můžete narazit na problémy. Může se například zobrazit následující chyba: "Vzdálený ladicí program Visual Studio (MSVSMON. EXE) nemá dostatečná oprávnění k ladění tohoto procesu." Pokud používáte vzdálený ladicí program jako aplikaci (nikoli službu), může se zobrazit [chyba jiného uživatelského účtu.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Při spuštění vzdáleného ladicího programu jako služby

Při spuštění vzdáleného ladicího programu jako služby s, doporučujeme spustit jako správce z několika důvodů:

- Služba vzdáleného ladicího programu umožňuje pouze připojení od správců, takže neexistují **žádná** nová bezpečnostní rizika zavedená spuštěním jako správce.

- Může zabránit chybám, které narůstají, když má uživatel sady Visual Studio více práv k ladění procesu než samotný vzdálený ladicí program.

- Pro zjednodušení nastavení a konfigurace vzdáleného ladicího programu.

I když je možné ladit bez spuštění vzdáleného ladicího programu jako správce, existuje několik požadavků, aby tato práce fungovala správně a často vyžadují pokročilejší kroky konfigurace služby.

- Účet, který používáte ve vzdáleném počítači, musí mít **oprávnění k přihlášení jako oprávnění služby.** Podívejte se na kroky v části "Chcete-li přidat přihlášení jako službu" v článku nelze [připojit zpět](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) chyby.

- Účet musí mít práva k ladění cílového procesu. Chcete-li získat tato práva, musíte spustit vzdálený ladicí program pod stejným účtem jako proces, který má být laděn. (Jednodušší alternativou je spuštění služby jako správce.) 

- Účet musí být schopen se připojit zpět (to znamená, ověřit s) počítač sady Visual Studio v síti. V doméně je snadnější se připojit zpět, pokud je vzdálený ladicí program spuštěn pod integrovanými účty místního systému nebo síťové služby nebo v účtu domény. Předdefinované účty mají zvýšená oprávnění zabezpečení, která mohou představovat bezpečnostní riziko.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Při spuštění vzdáleného ladicího programu jako aplikace (normální režim)

Pokud se pokoušíte připojit k vlastnímu procesu bez vyšších oprávnění (například normální aplikaci), nezáleží na tom, zda používáte vzdálený ladicí program jako správce.

Chcete spustit vzdálený ladicí program jako správce v několika scénářích:

- Chcete se připojit k procesům spuštěných jako jiný uživatel (například při ladění iIS) nebo

- Pokoušíte se spustit jiný proces a proces, který chcete spustit, je správce.

Pokud chcete spustit procesy, **nechcete** spustit jako správce a proces, který chcete spustit, by **neměl** být správcem.

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)