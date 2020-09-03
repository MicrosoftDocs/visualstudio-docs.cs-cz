---
title: Připojení ke spuštěným procesům pomocí ladicího programu | Microsoft Docs
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
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918948"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ke spuštěným procesům pomocí ladicího programu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Po spuštění procesu klikněte na tlačítko **ladit/připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL + ALT + P**) a otevřete tak dialogové okno **připojit k procesu** .

Tuto možnost můžete použít k ladění aplikací, které jsou spuštěny v místním nebo vzdáleném počítači, ladění více procesů současně nebo ladění aplikace, která nebyla vytvořena v aplikaci Visual Studio. Je často užitečné, pokud chcete ladit aplikaci, ale z jakéhokoli důvodu jste nespouštěli aplikaci ze sady Visual Studio pomocí připojeného ladicího programu. Například pokud aplikaci spouštíte bez ladicího programu a narazíte na výjimku, pak se můžete připojit k procesu, ve kterém je spuštěna aplikace, a zahájit tak ladění.

> [!TIP]
> Nejste si jisti, jestli pro svůj scénář ladění potřebujete použít **připojit k procesu** ? Viz [běžné scénáře ladění](#BKMK_Scenarios). Pokud chcete ladit aplikace ASP.NET nasazené do služby IIS, přečtěte si téma [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Připojit ke spuštěnému procesu v místním počítači
 Aby bylo možné se připojit k procesu, je nutné znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesů).

1. V aplikaci Visual Studio vyberte možnost **ladit/připojit k procesu** (nebo stiskněte klávesy **CTRL + ALT + P**).

2. V dialogovém okně **připojit k procesu** vyhledejte v seznamu **procesy k dispozici** program, který chcete připojit.

     Chcete-li rychle vybrat požadovaný proces, zadejte první písmeno názvu procesu. Pokud název procesu neznáte, přečtěte si téma [běžné scénáře ladění](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Pokud je proces spuštěn pod jiným uživatelským účtem, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .

3. V poli **připojit k** ověřte, zda je uveden typ kódu, který budete ladit. Výchozí **Automatické** nastavení se pokusí určit typ kódu, který chcete ladit. Pokud chcete nastavit typ kódu ručně, udělejte toto:

    1. V poli **připojit k** klikněte na **Vybrat**.

    2. V dialogovém okně **Vybrat typ kódu** klikněte na možnost **ladit tyto typy kódu** a vyberte typy pro ladění.

    3. Klikněte na **OK**.

4. Klikněte na **připojit**.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojit k procesu ve vzdáleném počítači
 Aby bylo možné se připojit k procesu, je nutné znát název procesu (viz [běžné scénáře ladění](#BKMK_Scenarios) pro několik běžných názvů procesů). Další kompletní pokyny pro aplikace ASP.NET nasazené do služby IIS najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). U ostatních aplikací může být možné najít název procesu ve Správci úloh.

 Při použití dialogového okna **připojit k procesu** můžete vybrat jiný počítač, který byl nastaven pro vzdálené ladění. Další informace najdete v tématu [vzdálené ladění](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Pokud jste vybrali vzdálený počítač, můžete zobrazit seznam dostupných procesů spuštěných na tomto počítači a připojit se k jednomu nebo více procesům pro ladění.

 **Výběr vzdáleného počítače:**

1. V aplikaci Visual Studio vyberte možnost **ladit/připojit k procesu** (nebo stiskněte klávesy **CTRL + ALT + P**).

2. V dialogovém okně **připojit k procesu** vyberte příslušný typ připojení ze seznamu **přenosů** . **Výchozím** nastavením je správné nastavení ve většině případů.

   Nastavení **přenosu** přetrvá mezi relacemi ladění.

3. Pomocí seznamu **kvalifikátor** můžete vybrat název vzdáleného počítače jedním z následujících způsobů:

   1. Zadejte název do pole seznam **kvalifikátoru** .

      > [!NOTE]
      > Pokud se v pozdějších krocích nemůžete připojit pomocí názvu vzdáleného počítače, použijte IP adresu. (Číslo portu se může po výběru procesu automaticky zobrazit. Můžete ho zadat také ručně. Na obrázku níže je 4020 výchozí port pro vzdálený ladicí program.)

   2. Klikněte na šipku rozevíracího seznamu připojená k seznamu **kvalifikátoru** a v rozevíracím seznamu vyberte název počítače.

   3. Kliknutím na tlačítko **Najít** vedle seznamu **kvalifikátor** otevřete dialogové okno **Vybrat připojení vzdáleného ladicího programu** . Dialogové okno **Vybrat připojení vzdáleného ladicího programu** obsahuje seznam všech zařízení, která jsou na vaší místní podsíti, a všechna zařízení, která jsou přímo připojena k počítači pomocí kabelu Ethernet. Klikněte na požadovaný počítač nebo požadované zařízení a pak klikněte na **Vybrat**.

      Nastavení **kvalifikátoru** přetrvává mezi relacemi ladění pouze v případě, že u tohoto kvalifikátoru dojde k úspěšnému připojení ladění.

4. Klikněte na **Aktualizovat**.

     Seznam **procesy k dispozici** se zobrazí automaticky při otevření dialogového okna **procesy** . Procesy mohou začínat a zastavovat na pozadí, když je dialogové okno otevřeno. Obsah však není vždy aktuální. Seznam můžete kdykoli aktualizovat, aby se zobrazil aktuální seznam procesů kliknutím na **aktualizovat**.

5. V dialogovém okně **připojit k procesu** vyhledejte v seznamu **procesy k dispozici** program, který chcete připojit.

    Pokud je proces spuštěn pod jiným uživatelským účtem, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .

6. Klikněte na **připojit**.

## <a name="additional-info"></a>Další informace

Můžete být připojeni k více programům při ladění, ale pouze jeden program je v ladicím programu aktivní. Aktivní program můžete nastavit na panelu nástrojů **umístění ladění** nebo v okně **procesy** . Další informace naleznete v tématu [How to: set a Current program](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Pokud se pokusíte připojit k procesu vlastněné nedůvěryhodným uživatelským účtem, zobrazí se potvrzení dialogového okna Upozornění zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

V některých případech se při ladění v relaci vzdálené plochy (Terminálové služby) nezobrazí seznam **procesy k** dispozici všechny dostupné procesy. Pokud používáte aplikaci Visual Studio jako uživatel s omezeným uživatelským účtem, seznam **procesy k dispozici** nebude zobrazovat procesy spuštěné v relaci 0, která se používá pro služby a jiné serverové procesy, včetně w3wp.exe. Problém můžete vyřešit tak, že spustíte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] účet správce nebo spustíte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z konzoly serveru místo relace Terminálové služby. Pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu spuštěním `vsjitdebugger.exe -p` příkazu *ProcessID* z příkazového řádku Windows. ID procesu můžete určit pomocí tlist.exe. Chcete-li získat tlist.exe, Stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na adrese  [WDK a programu WinDbg ke stažení](/windows-hardware/drivers/dashboard/).

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Běžné scénáře ladění

Abychom vám pomohli zjistit, jestli potřebujete použít **připojit k procesu** a jaký proces se má připojit, zobrazí se tady několik běžných scénářů ladění (seznam není vyčerpávající). Tam, kde jsou k dispozici další pokyny, poskytujeme odkazy.

U některých typů aplikací (jako jsou aplikace pro Windows Store) se přímo nepřipojují k názvu procesu, ale místo toho použijte možnost **ladění nainstalovaného balíčku aplikace** (viz tabulka).

> [!NOTE]
> Informace o základním ladění v aplikaci Visual Studio naleznete v tématu [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Ladění spravované nebo nativní aplikace na místním počítači|Použít připojit k procesu nebo [standardnímu ladění](../debugger/getting-started-with-the-debugger.md)|*AppName*. exe|Pro rychlý přístup k dialogovému oknu použijte **kombinaci kláves CTRL + ALT + P** a zadejte první písmeno názvu procesu.|
|Ladění aplikací ASP.NET na místním počítači po spuštění aplikace bez ladicího programu|Použít připojit k procesu|iiexpress.exe|To může být užitečné při rychlejším načítání aplikace, například (například) při profilaci. |
|Vzdálené ladění ASP.NET 4 nebo 4,5 na serveru služby IIS|Použití vzdálených nástrojů a připojení k procesu|w3wp.exe|Viz [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Vzdálené ladění ASP.NET Core na serveru služby IIS|Použití vzdálených nástrojů a připojení k procesu|dnx.exe|Nasazení aplikací najdete v tématu [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pro ladění se podívejte [na téma vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Ladění dalších podporovaných typů aplikací v procesu serveru|Použití nástrojů Remote Tools (Pokud je server vzdálený) a připojení k procesu|iexplore.exe nebo jiné procesy|V případě potřeby použijte Správce úloh, který vám usnadní identifikaci tohoto procesu. Viz téma [vzdálené ladění](../debugger/remote-debugging.md) a pozdější části v tomto tématu.|
|Vzdálené ladění desktopové aplikace pro Windows|Remote Tools a F5|–| Viz [vzdálené ladění](../debugger/remote-debugging.md)|
|Vzdálené ladění aplikace pro Windows Universal (UWP), OneCore, HoloLens nebo IoT|Ladit nainstalovaný balíček aplikace|–|Použít **ladění/jiné cíle ladění/ladit nainstalovaný balíček aplikace** místo příkazu **připojit k procesu**|
|Ladění aplikace pro Windows Universal (UWP), OneCore, HoloLens nebo IoT, kterou jste nespustili v aplikaci Visual Studio|Ladit nainstalovaný balíček aplikace|–|Použít **ladění/jiné cíle ladění/ladit nainstalovaný balíček aplikace** místo příkazu **připojit k procesu**|

> [!WARNING]
> Chcete-li se připojit k univerzální aplikaci pro Windows, která je napsána v jazyce JavaScript, je nutné nejprve povolit ladění aplikace. Viz část [připojení ladicího programu](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) na stránce Windows Dev Center.

> [!NOTE]
> Aby ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute` . To můžete do kódu přidat automaticky tak, že propojíte s možností linkeru [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .

## <a name="what-debugger-features-can-i-use"></a>Jaké funkce ladicího programu můžu použít?

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážky se zarážkami) při připojení k procesu, spustitelný soubor musí přesně odpovídat vašemu místnímu zdroji a symbolům (to znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (. pbd)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Ve výchozím nastavení to vyžaduje sestavení ladění.

Pro scénáře vzdáleného ladění musíte mít zdrojový kód (nebo kopii zdrojového kódu), který je již otevřen v aplikaci Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako na místním počítači.

V některých místních scénářích ladění můžete ladit v aplikaci Visual Studio bez přístupu ke zdroji, pokud jsou v aplikaci k dispozici správné soubory symbolů (ve výchozím nastavení to vyžaduje ladění sestavení). Další informace naleznete v tématu [Určení symbolů a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Řešení chyb připojení
 Pokud se ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu, ke kterým se může ladicí program připojit, jsou zobrazeny a vybrány v dialogovém okně **Vybrat typ kódu** .

 V některých případech se ladicí program může úspěšně připojit k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, který je spuštěn ve vzdáleném počítači. Vzdálený počítač může mít nainstalované komponenty pro vzdálené ladění pro některé typy kódu, ale ne pro jiné. Tato situace může nastat i v případě, že se pokusíte připojit ke dvěma nebo více procesům pro přímé ladění databáze. Ladění SQL podporuje připojení pouze k jednomu procesu.

 Pokud se ladicí program může připojit k některému, ale ne všem typům kódu, zobrazí se zpráva s identifikací, které typy se nepodařilo připojit.

 Pokud se ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete pokračovat v ladění procesu. Budete moct ladit jenom typy kódu, které se úspěšně připojily. Předchozí příklad zprávy ukazuje, že se nepodařilo připojit typ kódu skriptu. Proto nebudete moct ladit kód skriptu v rámci procesu. Kód skriptu v procesu by se pořád spouštěl, ale nebudete moct nastavovat zarážky, zobrazovat data ani provádět jiné operace ladění ve skriptu.

 Pokud chcete konkrétnější informace o tom, proč se ladicímu programu nepodařilo připojit k typu kódu, můžete se pokusit znovu připojit pouze k tomuto typu kódu.

 **Získat konkrétní informace o tom, proč se typ kódu nepodařilo připojit**

1. Odpojte se od procesu. V nabídce **ladění** klikněte na **Odpojit vše**.

2. Znovu se připojte k procesu a vyberte pouze jeden typ kódu.

   1. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** .

   2. Klikněte na **Vybrat**.

   3. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Vymažte jakýkoli jiný kód.

   4. Klikněte na **OK**. Dialogové okno **Vybrat typ kódu** se zavře.

   5. V dialogovém okně **připojit k procesu** klikněte na **připojit**.

      Tentokrát se připojení zcela nezdaří a zobrazí se konkrétní chybová zpráva.

## <a name="see-also"></a>Viz také
 [Ladění více procesů](../debugger/debug-multiple-processes.md) [za běhu ladění](../debugger/just-in-time-debugging-in-visual-studio.md) [vzdáleného ladění](../debugger/remote-debugging.md)
