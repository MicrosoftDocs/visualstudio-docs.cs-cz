---
title: Připojení ke spuštěným procesům pomocí ladicího programu | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299513"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ke spuštěným procesům pomocí ladicího programu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Jakmile je proces spuštěn, klikněte na tlačítko **ladění / připojit k procesu** (nebo stiskněte klávesu **CTRL + ALT + P**) otevřete **připojit k procesu** dialogové okno.

Tato funkce slouží k ladění aplikací, které běží na místním nebo vzdáleném počítači ladění více procesů současně nebo ladění aplikace, který nebyl vytvořen v sadě Visual Studio. Často je užitečné, pokud chcete ladit aplikaci, ale (z jakéhokoli důvodu) nebyla spuštěna aplikace ze sady Visual Studio s připojeným ladícím nástrojem. Například pokud jsou spuštěné aplikaci bez ladicího programu a k výjimce, může pak připojíte k procesu spuštění aplikace a zahájit ladění.

> [!TIP]
> Nejste si jistí, jestli se budete muset použít **připojit k procesu** pro váš scénář ladění? Zobrazit [běžné scénáře ladění](#BKMK_Scenarios). Pokud chcete ladění aplikací ASP.NET, které jsou nasazené do služby IIS, přečtěte si téma [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Připojit ke spuštěnému procesu v místním počítači
 Aby bylo možné připojit k procesu, musíte znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesu).

1. V sadě Visual Studio, vyberte **ladění / připojit k procesu** (nebo stiskněte klávesu **CTRL + ALT + P**).

2. V **připojit k procesu** dialogovém okně vyhledejte program, který chcete připojit z **procesy k dispozici** seznamu.

     Chcete-li rychle vyberte proces, který chcete, zadejte první písmeno názvu procesu. Pokud neznáte název procesu, přečtěte si téma [běžné scénáře ladění](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Pokud je proces spuštěn pod účtem jiného uživatele, vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.

3. V **připojit k** pole, ujistěte se, zda je uveden typ kódu, který budete ladit. Výchozí hodnota **automatické** nastavení snaží se určit, jaký typ kódu, který chcete ladit. Chcete-li nastavit typ kódu ručně, postupujte následovně

    1. V **připojit k** klikněte **vyberte**.

    2. V **vybrat typ kódu** dialogové okno, klikněte na tlačítko **ladit tyto typy kódu** a vyberte typy k ladění.

    3. Klikněte na tlačítko **OK**.

4. Klikněte na tlačítko **připojit**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojit k procesu ve vzdáleném počítači
 Aby bylo možné připojit k procesu, musíte znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesu). Kompletní pokyny pro aplikace v ASP.NET, které jsou nasazené do služby IIS najdete v tématu [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Pro jiné aplikace budete moci najít název procesu, ve Správci úloh.

 Při použití **připojit k procesu** dialogovém okně můžete vybrat jiný počítač, který je nastavený pro vzdálené ladění. Další informace najdete v tématu [vzdálené ladění](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Po výběru vzdáleného počítače, můžete zobrazit seznam dostupných procesů spuštěných na tomto počítači a připojit k jednomu nebo více procesům pro ladění.

 **Výběr vzdáleného počítače:**

1. V sadě Visual Studio, vyberte **ladění / připojit k procesu** (nebo stiskněte klávesu **CTRL + ALT + P**).

2. V **připojit k procesu** dialogovém okně vyberte příslušný typ připojení z **přenosu** seznamu. **Výchozí** je správné nastavení ve většině případů.

   **Přenosu** nastavení zůstává mezi relacemi ladění.

3. Použití **kvalifikátor** pole se seznamem zvolte název vzdáleného počítače pomocí jedné z následujících metod:

   1. Zadejte název do **kvalifikátor** pole se seznamem.

      > [!NOTE]
      > Pokud se v pozdějších krocích nemůžete připojit pomocí názvu vzdáleného počítače, použijte IP adresu. (Číslo portu může automaticky zobrazit po výběru procesu. Můžete také zadat ho ručně. Na následující ilustraci 4020 je výchozí port pro vzdálené ladění.)

   2. Klikněte na šipku rozevíracího seznamu, který je připojen k **kvalifikátor** a z rozevíracího seznamu vyberte název počítače.

   3. Klikněte na tlačítko **najít** vedle **kvalifikátor** seznamu a otevře **vyberte připojení vzdáleného ladicího programu** dialogové okno. **Vyberte připojení vzdáleného ladicího programu** dialogové okno obsahuje všechna zařízení, které jsou na vaší místní podsíti a zařízení, která je přímo připojeno k počítači pomocí kabelu Ethernet. Klikněte na počítač nebo zařízení a potom klikněte na tlačítko **vyberte**.

      **Kvalifikátor** nastavení zůstává mezi relacemi ladění pouze v případě, že dojde k úspěšnému připojení ladění u tohoto kvalifikátoru.

4. Klikněte na tlačítko **aktualizovat**.

     **Procesy k dispozici** seznam se automaticky zobrazí při otevření **procesy** dialogové okno. Procesy můžete spouštět a zastavovat na pozadí při otevřeném dialogovém okně. Nicméně obsah nejsou vždy aktuální. Můžete aktualizovat seznam kdykoli zobrazit aktuální seznam procesů kliknutím **aktualizovat**.

5. V **připojit k procesu** dialogovém okně vyhledejte program, který chcete připojit z **procesy k dispozici** seznamu.

    Pokud je proces spuštěn pod účtem jiného uživatele, vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.

6. Klikněte na tlačítko **připojit**.

## <a name="additional-info"></a>Další informace

Můžete být připojení k více programům při ladění, ale pouze jeden program je v každém okamžiku aktivní v ladicím programu. Můžete nastavit aktivní program **umístění ladění** nástrojů nebo **procesy** okna. Další informace najdete v tématu [postupy: nastavení aktuálního programu](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Pokud se pokusíte připojit k procesu vlastněnému nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

V některých případech při ladění v relaci vzdálené plochy (Terminálová služba) **procesy k dispozici** seznamu nezobrazí všechny procesy k dispozici. Pokud používáte Visual Studio jako uživatel, který má omezený uživatelský účet, **procesy k dispozici** seznamu nezobrazí procesy spuštěné v relaci 0, který se používá pro služby a ostatních serverové procesy, včetně w3wp.exe. Problém můžete vyřešit spuštěním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pod účtem správce nebo spuštěním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z konzoly serveru místo relace Terminálové služby. Pokud ani jeden z těchto řešení je možné, třetí možnost je připojit k procesu spuštěním `vsjitdebugger.exe -p` *ProcessId* z příkazového řádku Windows. Můžete určit id procesu pomocí tlist.exe. Chcete-li získat tlist.exe, stáhněte a nainstalujte ladění nástroje pro Windows, k dispozici na [soubory ke stažení sady WDK a WinDbg](https://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Běžné scénáře ladění

Abyste mohli snadno identifikovat, jestli je třeba použít **připojit k procesu** a jaký proces se připojit k, několik běžných scénářů ladění se tady zobrazí (seznam není vyčerpávající). Je-li další pokyny jsou k dispozici, zajišťuje odkazy.

Pro některé typy aplikací (např. aplikace pro Windows Store), nemusíte připojit přímo k názvu procesu, ale použít **ladit nainstalovaný balíček aplikace** místo něj parametr nabídky (viz tabulka).

> [!NOTE]
> Informace o základní ladění v sadě Visual Studio najdete v tématu [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Ladění spravované nebo nativní aplikace v místním počítači|Použití se připojit k procesu nebo [standardní ladění](../debugger/getting-started-with-the-debugger.md)|*AppName*.exe|Rychle se dostat k dialogových oken, použijte **CTRL + ALT + P** a pak zadejte první písmeno názvu procesu.|
|Ladění aplikací ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použití se připojit k procesu|iiexpress.exe|To může být užitečné k vytvoření aplikace načíst rychleji, například (třeba) při profilování. |
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Pomocí nástrojů pro vzdálenou a připojit k procesu|W3wp.exe|Zobrazit [vzdálené ladění ASP.NET ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Vzdálené ladění ASP.NET Core na server služby IIS|Pomocí nástrojů pro vzdálenou a připojit k procesu|dnx.exe|Nasazení aplikace, najdete v tématu [publikovat do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Ladění, naleznete v tématu [vzdálené ladění ASP.NET ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Ladit další typy aplikací podporované v procesu serveru|Pomocí nástrojů pro vzdálenou (Pokud je vzdálený server) a připojit k procesu|Iexplore.exe nebo jiných procesů|V případě potřeby použijte k identifikaci procesu Správce úloh. Zobrazit [vzdálené ladění](../debugger/remote-debugging.md) a pozdější části tohoto tématu|
|Vzdálené ladění aplikace klasické pracovní plochy Windows|Remote Tools a F5|Není k dispozici| Zobrazit [vzdálené ladění](../debugger/remote-debugging.md)|
|Vzdálené ladění Universal Windows (UPW), OneCore, HoloLens a IoT aplikací|Ladit nainstalovaný balíček aplikace|Není k dispozici|Použití **ladění / jiné cíle ladění / ladění balíčku nainstalované aplikace** místo **připojit k procesu**|
|Ladění aplikace Universal Windows (UPW), OneCore, HoloLens a IoT, které se nepovedlo spustit ze sady Visual Studio|Ladit nainstalovaný balíček aplikace|Není k dispozici|Použití **ladění / jiné cíle ladění / ladění balíčku nainstalované aplikace** místo **připojit k procesu**|

> [!WARNING]
> Připojit k Windows univerzální aplikace, která je napsána v jazyce JavaScript, je nutné nejprve povolit ladění pro aplikace. Zobrazit [připojit ladicí program](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) Windows Dev Center.

> [!NOTE]
> Ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute`. Můžete přidat to do kódu automaticky díky propojení s [/assemblydebug](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) – možnost linkeru.

## <a name="what-debugger-features-can-i-use"></a>Jaké funkce ladicího programu můžete použít?

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážek) při připojování k procesu, spustitelný soubor musí přesně odpovídat, místní zdroje a symbolů (to znamená, ladicí program musí být schopný načíst správný [(.pbd) soubory symbolů ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění.

Pro scénáře vzdálené ladění musí mít zdrojový kód (nebo kopii zdrojového kódu) otevřen v sadě Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako v místním počítači.

V některých místní ladění scénářích můžete ladit v sadě Visual Studio bez přístupu ke zdroji Pokud jsou k dispozici v aplikaci správný symbol soubory (ve výchozím nastavení, vyžaduje sestavení pro ladění). Další informace najdete v tématu [zadejte symbolů a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Řešení potíží s chybami připojení
 Pokud ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu k se může připojit ladicí program se zobrazí a jsou vybrány v **vybrat typ kódu** dialogové okno.

 V některých případech můžete úspěšně připojit ladicí program k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, která běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované pro některé typy kódu, ale nikoli pro jiné komponenty vzdáleného ladění. Může dojít také při pokusu o připojení ke dvěma nebo více procesům pro přímé ladění databáze. SQL ladění podporuje připojení pouze jednoho procesu.

 Pokud ladicí program je možné se připojit k některým, ale ne všechny typy kódu, zobrazí se zpráva označující, ke kterým typům se nepodařilo připojit.

 Pokud ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete přejít k ladění procesu. Budete moci ladit pouze typy kódu, které byly úspěšně připojeny. Předchozí příklad zprávy ukazuje, že typ kódu skriptu se nepovedlo připojit. Proto nebude moci ladit kód skriptu v rámci procesu. Kód skriptu v procesu by stále běžel, ale nebude moct nastavit zarážky, zobrazit data ani provádět jiné operace ladění ve skriptu.

 Pokud potřebujete konkrétnější informace o Proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze tomuto typu kódu.

 **Získání konkrétních informací o Proč se nepodařilo připojit typ kódu**

1. Odpojte od procesu. Na **ladění** nabídky, klikněte na tlačítko **Odpojit vše**.

2. Znovu připojte k procesu, vyberte pouze jeden typ kódu.

   1. V **připojit k procesu** dialogového okna, vyberte v procesu **procesy k dispozici** seznamu.

   2. Klikněte na tlačítko **vyberte**.

   3. V **vybrat typ kódu** dialogovém okně vyberte **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Vymazání veškerého dalšího kódu.

   4. Klikněte na tlačítko **OK**. **Vybrat typ kódu** zavře dialogové okno.

   5. V **připojit k procesu** dialogové okno, klikněte na tlačítko **připojit**.

      Tentokrát připojení zcela selže a dostanete konkrétní chybovou zprávu.

## <a name="see-also"></a>Viz také
 [Ladění více procesů](../debugger/debug-multiple-processes.md) [ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) [vzdálené ladění](../debugger/remote-debugging.md)
