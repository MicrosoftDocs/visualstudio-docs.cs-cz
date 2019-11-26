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

Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Po spuštění procesu klikněte na tlačítko **ladit/připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL + ALT + P**) a otevřete tak dialogové okno **připojit k procesu** .

Tato funkce slouží k ladění aplikací, které běží na místním nebo vzdáleném počítači ladění více procesů současně nebo ladění aplikace, který nebyl vytvořen v sadě Visual Studio. Často je užitečné, pokud chcete ladit aplikaci, ale (z jakéhokoli důvodu) nebyla spuštěna aplikace ze sady Visual Studio s připojeným ladícím nástrojem. Například pokud jsou spuštěné aplikaci bez ladicího programu a k výjimce, může pak připojíte k procesu spuštění aplikace a zahájit ladění.

> [!TIP]
> Nejste si jisti, jestli pro svůj scénář ladění potřebujete použít **připojit k procesu** ? Viz [běžné scénáře ladění](#BKMK_Scenarios). Pokud chcete ladit aplikace ASP.NET nasazené do služby IIS, přečtěte si téma [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a>Připojit ke spuštěnému procesu v místním počítači
 Aby bylo možné se připojit k procesu, je nutné znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesů).

1. V aplikaci Visual Studio vyberte možnost **ladit/připojit k procesu** (nebo stiskněte klávesy **CTRL + ALT + P**).

2. V dialogovém okně **připojit k procesu** vyhledejte v seznamu **procesy k dispozici** program, který chcete připojit.

     Chcete-li rychle vyberte proces, který chcete, zadejte první písmeno názvu procesu. Pokud název procesu neznáte, přečtěte si téma [běžné scénáře ladění](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Pokud je proces spuštěn pod jiným uživatelským účtem, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .

3. V poli **připojit k** ověřte, zda je uveden typ kódu, který budete ladit. Výchozí **Automatické** nastavení se pokusí určit typ kódu, který chcete ladit. Chcete-li nastavit typ kódu ručně, postupujte následovně

    1. V poli **připojit k** klikněte na **Vybrat**.

    2. V dialogovém okně **Vybrat typ kódu** klikněte na možnost **ladit tyto typy kódu** a vyberte typy pro ladění.

    3. Klikněte na tlačítko **OK**.

4. Klikněte na **připojit**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Připojit k procesu ve vzdáleném počítači
 Aby bylo možné se připojit k procesu, je nutné znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesů). Další kompletní pokyny pro aplikace ASP.NET nasazené do služby IIS najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Pro jiné aplikace budete moci najít název procesu, ve Správci úloh.

 Při použití dialogového okna **připojit k procesu** můžete vybrat jiný počítač, který byl nastaven pro vzdálené ladění. Další informace najdete v tématu [vzdálené ladění](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Po výběru vzdáleného počítače, můžete zobrazit seznam dostupných procesů spuštěných na tomto počítači a připojit k jednomu nebo více procesům pro ladění.

 **Výběr vzdáleného počítače:**

1. V aplikaci Visual Studio vyberte možnost **ladit/připojit k procesu** (nebo stiskněte klávesy **CTRL + ALT + P**).

2. V dialogovém okně **připojit k procesu** vyberte příslušný typ připojení ze seznamu **přenosů** . **Výchozím** nastavením je správné nastavení ve většině případů.

   Nastavení **přenosu** přetrvá mezi relacemi ladění.

3. Pomocí seznamu **kvalifikátor** můžete vybrat název vzdáleného počítače jedním z následujících způsobů:

   1. Zadejte název do pole seznam **kvalifikátoru** .

      > [!NOTE]
      > Pokud se v pozdějších krocích nemůžete připojit pomocí názvu vzdáleného počítače, použijte IP adresu. (Číslo portu může automaticky zobrazit po výběru procesu. Můžete také zadat ho ručně. Na následující ilustraci 4020 je výchozí port pro vzdálené ladění.)

   2. Klikněte na šipku rozevíracího seznamu připojená k seznamu **kvalifikátoru** a v rozevíracím seznamu vyberte název počítače.

   3. Kliknutím na tlačítko **Najít** vedle seznamu **kvalifikátor** otevřete dialogové okno **Vybrat připojení vzdáleného ladicího programu** . Dialogové okno **Vybrat připojení vzdáleného ladicího programu** obsahuje seznam všech zařízení, která jsou na vaší místní podsíti, a všechna zařízení, která jsou přímo připojena k počítači pomocí kabelu Ethernet. Klikněte na požadovaný počítač nebo požadované zařízení a pak klikněte na **Vybrat**.

      Nastavení **kvalifikátoru** přetrvává mezi relacemi ladění pouze v případě, že u tohoto kvalifikátoru dojde k úspěšnému připojení ladění.

4. Klikněte na tlačítko **aktualizovat**.

     Seznam **procesy k dispozici** se zobrazí automaticky při otevření dialogového okna **procesy** . Procesy můžete spouštět a zastavovat na pozadí při otevřeném dialogovém okně. Nicméně obsah nejsou vždy aktuální. Seznam můžete kdykoli aktualizovat, aby se zobrazil aktuální seznam procesů kliknutím na **aktualizovat**.

5. V dialogovém okně **připojit k procesu** vyhledejte v seznamu **procesy k dispozici** program, který chcete připojit.

    Pokud je proces spuštěn pod jiným uživatelským účtem, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .

6. Klikněte na **připojit**.

## <a name="additional-info"></a>Další informace

Můžete být připojení k více programům při ladění, ale pouze jeden program je v každém okamžiku aktivní v ladicím programu. Aktivní program můžete nastavit na panelu nástrojů **umístění ladění** nebo v okně **procesy** . Další informace naleznete v tématu [How to: set a Current program](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Pokud se pokusíte připojit k procesu vlastněnému nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

V některých případech se při ladění v relaci vzdálené plochy (Terminálové služby) nezobrazí seznam **procesy k** dispozici všechny dostupné procesy. Pokud používáte aplikaci Visual Studio jako uživatel s omezeným uživatelským účtem, seznam **procesy k dispozici** nebude zobrazovat procesy spuštěné v relaci 0, která se používá pro služby a jiné serverové procesy, včetně W3wp. exe. Problém můžete vyřešit tak, že spustíte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v rámci účtu správce nebo spuštěním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z konzoly serveru namísto relace Terminálové služby. Pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu spuštěním `vsjitdebugger.exe -p` *ProcessID* z příkazového řádku Windows. Můžete určit id procesu pomocí tlist.exe. Chcete-li získat Tlist. exe, Stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na webu [WDK a programu WinDbg ke stažení](https://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a>Běžné scénáře ladění

Abychom vám pomohli zjistit, jestli potřebujete použít **připojit k procesu** a jaký proces se má připojit, zobrazí se tady několik běžných scénářů ladění (seznam není vyčerpávající). Je-li další pokyny jsou k dispozici, zajišťuje odkazy.

U některých typů aplikací (jako jsou aplikace pro Windows Store) se přímo nepřipojují k názvu procesu, ale místo toho použijte možnost **ladění nainstalovaného balíčku aplikace** (viz tabulka).

> [!NOTE]
> Informace o základním ladění v aplikaci Visual Studio naleznete v tématu [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Ladění spravované nebo nativní aplikace v místním počítači|Použít připojit k procesu nebo [standardnímu ladění](../debugger/getting-started-with-the-debugger.md)|*AppName*. exe|Pro rychlý přístup k dialogovému oknu použijte **kombinaci kláves CTRL + ALT + P** a zadejte první písmeno názvu procesu.|
|Ladění aplikací ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použití se připojit k procesu|iiexpress.exe|To může být užitečné k vytvoření aplikace načíst rychleji, například (třeba) při profilování. |
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Pomocí nástrojů pro vzdálenou a připojit k procesu|W3wp.exe|Viz [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Vzdálené ladění ASP.NET Core na server služby IIS|Pomocí nástrojů pro vzdálenou a připojit k procesu|dnx.exe|Nasazení aplikací najdete v tématu [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pro ladění se podívejte [na téma vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Ladit další typy aplikací podporované v procesu serveru|Pomocí nástrojů pro vzdálenou (Pokud je vzdálený server) a připojit k procesu|Iexplore.exe nebo jiných procesů|V případě potřeby použijte k identifikaci procesu Správce úloh. Viz téma [vzdálené ladění](../debugger/remote-debugging.md) a pozdější části v tomto tématu.|
|Vzdálené ladění aplikace klasické pracovní plochy Windows|Remote Tools a F5|Není k dispozici| Viz [vzdálené ladění](../debugger/remote-debugging.md)|
|Vzdálené ladění Universal Windows (UPW), OneCore, HoloLens a IoT aplikací|Ladit nainstalovaný balíček aplikace|Není k dispozici|Použít **ladění/jiné cíle ladění/ladit nainstalovaný balíček aplikace** místo příkazu **připojit k procesu**|
|Ladění aplikace Universal Windows (UPW), OneCore, HoloLens a IoT, které se nepovedlo spustit ze sady Visual Studio|Ladit nainstalovaný balíček aplikace|Není k dispozici|Použít **ladění/jiné cíle ladění/ladit nainstalovaný balíček aplikace** místo příkazu **připojit k procesu**|

> [!WARNING]
> Připojit k Windows univerzální aplikace, která je napsána v jazyce JavaScript, je nutné nejprve povolit ladění pro aplikace. Viz část [připojení ladicího programu](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) na stránce Windows Dev Center.

> [!NOTE]
> Aby se ladicí program připojil k kódu napsanému v C++, musí kód vygenerovat `DebuggableAttribute`. To můžete do kódu přidat automaticky tak, že propojíte s možností linkeru [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .

## <a name="what-debugger-features-can-i-use"></a>Jaké funkce ladicího programu můžete použít?

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážky se zarážkami) při připojení k procesu, spustitelný soubor musí přesně odpovídat vašemu místnímu zdroji a symbolům (to znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (. pbd)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění.

Pro scénáře vzdálené ladění musí mít zdrojový kód (nebo kopii zdrojového kódu) otevřen v sadě Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako v místním počítači.

V některých místní ladění scénářích můžete ladit v sadě Visual Studio bez přístupu ke zdroji Pokud jsou k dispozici v aplikaci správný symbol soubory (ve výchozím nastavení, vyžaduje sestavení pro ladění). Další informace naleznete v tématu [Určení symbolů a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a>Řešení chyb připojení
 Pokud ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu, ke kterým se může ladicí program připojit, jsou zobrazeny a vybrány v dialogovém okně **Vybrat typ kódu** .

 V některých případech můžete úspěšně připojit ladicí program k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, která běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované pro některé typy kódu, ale nikoli pro jiné komponenty vzdáleného ladění. Může dojít také při pokusu o připojení ke dvěma nebo více procesům pro přímé ladění databáze. SQL ladění podporuje připojení pouze jednoho procesu.

 Pokud ladicí program je možné se připojit k některým, ale ne všechny typy kódu, zobrazí se zpráva označující, ke kterým typům se nepodařilo připojit.

 Pokud ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete přejít k ladění procesu. Budete moci ladit pouze typy kódu, které byly úspěšně připojeny. Předchozí příklad zprávy ukazuje, že typ kódu skriptu se nepovedlo připojit. Proto nebude moci ladit kód skriptu v rámci procesu. Kód skriptu v procesu by stále běžel, ale nebude moct nastavit zarážky, zobrazit data ani provádět jiné operace ladění ve skriptu.

 Pokud potřebujete konkrétnější informace o Proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze tomuto typu kódu.

 **Získat konkrétní informace o tom, proč se typ kódu nepodařilo připojit**

1. Odpojte od procesu. V nabídce **ladění** klikněte na **Odpojit vše**.

2. Znovu připojte k procesu, vyberte pouze jeden typ kódu.

   1. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** .

   2. Klikněte na **Vybrat**.

   3. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Vymazání veškerého dalšího kódu.

   4. Klikněte na tlačítko **OK**. Dialogové okno **Vybrat typ kódu** se zavře.

   5. V dialogovém okně **připojit k procesu** klikněte na **připojit**.

      Tentokrát připojení zcela selže a dostanete konkrétní chybovou zprávu.

## <a name="see-also"></a>Viz také
 [Ladění více procesů](../debugger/debug-multiple-processes.md) [za běhu ladění](../debugger/just-in-time-debugging-in-visual-studio.md) [vzdáleného ladění](../debugger/remote-debugging.md)
