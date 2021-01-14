---
title: Chyby vzdáleného ladění a řešení potíží | Microsoft Docs
description: Umožňuje zobrazit odkazy na běžné chyby vzdáleného ladění v aplikaci Visual Studio. Přečtěte si, jak spustit vzdálený ladicí program jako správce.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0260f939c8f6b7e5bed77ec42a4720adf0a4c720
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205655"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Chyby a řešení potíží se vzdáleným laděním

Při pokusu o ladění vzdáleně může docházet k následujícím chybám.

- [Chyba: Automatické krokování s vnořením do serveru se nezdařilo.](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Chyba: Zdá se, že sledování vzdáleného ladění sady Microsoft Visual Studio (MSVSMON.EXE) na vzdáleném počítači neběží.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Nelze se připojit k Microsoft Visual Studio Sledování vzdáleného ladění](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Chyba: Vzdálený počítač se nezobrazuje v dialogovém okně Vzdálená připojení](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Spuštění vzdáleného ladicího programu jako správce

Pokud nespustíte vzdálený ladicí program jako správce, může dojít k problémům. Například se může zobrazit následující chyba: "Visual Studio Remote Debugger (MSVSMON.EXE) má nedostatečná oprávnění pro ladění tohoto procesu." Pokud používáte vzdálený ladicí program jako aplikaci (nikoli službu), může se zobrazit chyba [různých uživatelských účtů](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Při spuštění vzdáleného ladícího programu jako služby

Když spouštíte vzdálený ladicí program jako službu s, doporučujeme spustit ho jako správce z několika důvodů:

- Služba vzdáleného ladicího programu umožňuje pouze připojení správců, takže neexistují **žádná** nová bezpečnostní rizika, která by mohla spustit jako správce.

- Může zabránit chybám, které mají za následek, když má uživatel aplikace Visual Studio více práv na ladění procesu, než samotný vzdálený ladicí program.

- Pro zjednodušení nastavení a konfigurace vzdáleného ladicího programu.

I když je možné ladit bez spuštění vzdáleného ladícího programu jako správce, existuje několik požadavků na to, aby tato práce fungovala správně a často vyžadovaly pokročilejší kroky konfigurace služby.

- Účet, který používáte ve vzdáleném počítači, musí mít oprávnění **Přihlásit se jako služba** . Projděte si postup v části "přidání přihlášení jako služby" v článku [nelze se připojit](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) k chybě.

- Účet musí mít oprávnění k ladění cílového procesu. Chcete-li získat tato práva, je nutné spustit vzdálený ladicí program pod stejným účtem jako proces, který se má ladit. (Jednodušší alternativou je spuštění služby jako správce.) 

- Účet musí být schopný připojit se k počítači sady Visual Studio přes síť (tj. ověřování pomocí). V doméně se můžete snadno připojit zpátky, pokud je vzdálený ladicí program spuštěný pod integrovaným účtem místního systému nebo síťové služby nebo účtem domény. Předdefinované účty mají zvýšená oprávnění zabezpečení, která mohou představovat bezpečnostní riziko.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Při spuštění vzdáleného ladícího programu jako aplikace (normální režim)

Pokud se pokoušíte připojit k vlastnímu procesu bez zvýšené úrovně oprávnění (například k normální aplikaci), nezáleží na tom, jestli spouštíte vzdálený ladicí program jako správce.

Chcete spustit vzdálený ladicí program jako správce v několika scénářích:

- Chcete se připojit k procesům spuštěným jako jiný uživatel (například při ladění služby IIS) nebo

- Pokoušíte se spustit jiný proces a proces, který chcete spustit, je správce.

Nechcete spustit jako správce, pokud chcete spouštět procesy a proces, který chcete spustit, **by neměl být** správcem. 

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)