---
title: Připojení ke spuštěným procesům pomocí ladicího programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 04/08/2019
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
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257186"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům
Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Po spuštění procesu vyberte **ladit** > **připojit k procesu** nebo stiskněte **CTRL**+**ALT**+**P** v aplikaci Visual Studio a pomocí dialogu **připojit k** procesu připojte ladicí program k procesu.

Pomocí příkazu **připojit k procesu** můžete ladit spuštěné aplikace v místních nebo vzdálených počítačích, ladit současně více procesů, ladit aplikace, které nebyly vytvořeny v aplikaci Visual Studio, nebo ladit jakoukoli aplikaci, kterou jste nespustili ze sady Visual Studio, pomocí připojeného ladicího programu. Například pokud máte spuštěnou aplikaci bez ladicího programu a k výjimce, můžete potom připojit ladicí program k procesu spuštění aplikace a spusťte ladění.

> [!TIP]
> Nejste si jisti, jestli pro váš scénář ladění chcete použít **připojit k procesu** ? Viz [běžné scénáře ladění](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a>Připojte se k běžícímu procesu na místním počítači.

Chcete-li se rychle znovu připojit k procesu, který jste k dřív připojili, přečtěte si téma [opětovné připojení k procesu](#BKMK_reattach).

Postup ladění procesu ve vzdáleném počítači najdete v tématu [připojení k procesu ve vzdáleném počítači](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Chcete-li ladit proces .NET Core na kontejneru Docker pro Linux, přečtěte si téma [připojení k kontejneru Docker pro Linux](#BKMK_Docker_Attach).
::: moniker-end

**Připojení k procesu v místním počítači:**

1. V aplikaci Visual Studio vyberte možnost **ladění** > **připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL**+**ALT**+**P**) a otevřete tak dialogové okno **připojit k procesu** .

   **Typ připojení** by měl být nastaven na **výchozí**. **Cíl připojení** by měl být název místního počítače.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. V seznamu **procesy k dispozici** vyhledejte a vyberte proces nebo procesy, ke kterým se chcete připojit.

   - Chcete-li rychle vybrat proces, zadejte jeho název nebo první písmeno do pole **filtrovat procesy** .

   - Pokud název procesu neznáte, procházejte seznamem nebo si prohlédněte [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů.

   >[!TIP]
   >Procesy lze spustit a zastavit na pozadí, zatímco je otevřeno dialogové okno **připojit k procesu** , takže seznam spuštěných procesů nemusí být vždy aktuální. Můžete kdykoli vybrat možnost **aktualizovat** , aby se zobrazil aktuální seznam.

3. V poli **připojit k** ověřte, že je uveden typ kódu, který chcete ladit. Výchozí **Automatické** nastavení funguje pro většinu typů aplikací.

   Ručně vyberte typy kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu**.
   1. Vyberte typy kódu, který chcete ladit.
   1. Vyberte **OK**.

4. Vyberte **připojit**.

>[!NOTE]
>Můžete být připojení k několika aplikacím pro ladění, ale současně je aktivní v ladicím programu jenom jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studio **umístění** .

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Připojit k procesu ve vzdáleném počítači

Můžete také vybrat vzdálený počítač v dialogovém okně **připojit k procesu** , zobrazit seznam dostupných procesů spuštěných v tomto počítači a připojit se k jednomu nebo více procesům pro ladění. Na vzdáleném počítači musí být spuštěný vzdálený ladící program (*msvsmon. exe*). Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

Podrobnější pokyny pro ladění aplikací ASP.NET, které byly nasazeny do služby IIS, najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Chcete-li se připojit ke spuštěnému procesu na vzdáleném počítači:**

1. V aplikaci Visual Studio vyberte možnost **ladění** > **připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL**+**ALT**+**P**) a otevřete tak dialogové okno **připojit k procesu** .

2. Pro většinu případů by měl být **Typ připojení** **výchozí** . V poli **cíl připojení** vyberte vzdálený počítač pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **cíle připojení**a v rozevíracím seznamu vyberte název počítače.
   - Do pole **cíl připojení** zadejte název počítače a stiskněte klávesu **ENTER**.

     Ověřte, že Visual Studio přidá požadovaný port do názvu počítače, který se zobrazí ve formátu: **\<název vzdáleného počítače >:p** .

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022`). 4024 je výchozí port pro vzdálený ladicí program sady Visual Studio 2019 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022`). 4022 je výchozím portem pro vzdálený ladicí program sady Visual Studio 2017 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Zaškrtněte tlačítko **Najít** vedle pole **cíl připojení** a otevřete tak dialogové okno **Vzdálená připojení** . V dialogovém okně **Vzdálená připojení** jsou uvedena všechna zařízení, která jsou ve vaší místní podsíti nebo jsou přímo připojená k počítači. Možná budete muset na serveru [otevřít port UDP 3702](../debugger/remote-debugger-port-assignments.md) , abyste mohli zjišťovat vzdálená zařízení. Vyberte počítač nebo zařízení, které chcete, a potom klikněte na **Vybrat**.

   > [!NOTE]
   > Nastavení **typu připojení** trvá mezi relacemi ladění. Nastavení **cíl připojení** trvá mezi relacemi ladění pouze v případě, že u tohoto cíle došlo k úspěšnému připojení ladění.

3. Kliknutím na tlačítko **aktualizovat** naplňte seznam **procesy k dispozici** .

    >[!TIP]
    >Procesy lze spustit a zastavit na pozadí, zatímco je otevřeno dialogové okno **připojit k procesu** , takže seznam spuštěných procesů nemusí být vždy aktuální. Můžete kdykoli vybrat možnost **aktualizovat** , aby se zobrazil aktuální seznam.

4. V seznamu **procesy k dispozici** vyhledejte a vyberte proces nebo procesy, ke kterým se chcete připojit.

   - Chcete-li rychle vybrat proces, zadejte jeho název nebo první písmeno do pole **filtrovat procesy** .

   - Pokud název procesu neznáte, procházejte seznamem nebo si prohlédněte [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů.

   - Chcete-li najít procesy spuštěné v rámci všech uživatelských účtů, zaškrtněte políčko **Zobrazit procesy všech uživatelů** .

     >[!NOTE]
     >Pokud se pokusíte připojit k procesu vlastněnému nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. V poli **připojit k** ověřte, že je uveden typ kódu, který chcete ladit. Výchozí **Automatické** nastavení funguje pro většinu typů aplikací.

   Ručně vyberte typy kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu**.
   1. Vyberte typy kódu, který chcete ladit.
   1. Vyberte **OK**.

6. Vyberte **připojit**.

>[!NOTE]
>Můžete být připojení k několika aplikacím pro ladění, ale současně je aktivní v ladicím programu jenom jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studio **umístění** .

V některých případech se při ladění v relaci vzdálené plochy (Terminálové služby) nezobrazí seznam **procesy k** dispozici všechny dostupné procesy. Pokud používáte aplikaci Visual Studio jako uživatel s omezeným uživatelským účtem, seznam **procesy k dispozici** nebude zobrazovat procesy spuštěné v relaci 0. Relace 0 se používá pro služby a jiné serverové procesy, včetně *W3wp. exe*. Problém můžete vyřešit tak, že spustíte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v rámci účtu správce nebo spuštěním [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z konzoly serveru namísto relace Terminálové služby.

Pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu spuštěním `vsjitdebugger.exe -p <ProcessId>` z příkazového řádku Windows. Můžete určit ID procesu pomocí *Tlist. exe*. Chcete-li získat *Tlist. exe*, Stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na webu [WDK a programu WinDbg ke stažení](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Připojení k procesu .NET Core běžícímu na Linux pomocí SSH

Další informace najdete v tématu [vzdálené ladění .NET Core běžící na Linux pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="BKMK_Docker_Attach"></a>Připojení k procesu běžícímu na kontejneru Docker platformy Linux

Můžete připojit ladicí program sady Visual Studio k procesu běžícímu v kontejneru Docker platformy Linux .NET Core na místním nebo vzdáleném počítači pomocí dialogového okna **připojit k procesu** .

> [!IMPORTANT]
> Pokud chcete používat tuto funkci, musíte nainstalovat úlohu vývoje .NET Core pro různé platformy a mít místní přístup ke zdrojovému kódu.

**Připojení ke spuštěnému procesu v kontejneru Docker systému Linux:**

1. V aplikaci Visual Studio vyberte možnost **ladit > připojit k procesu (CTRL + ALT + P)** a otevřete dialogové okno **připojit k procesu** .

![Nabídka připojit k procesu](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Nastavte **Typ připojení** **Docker (kontejner Linux)** .
3. Vyberte **Najít...** a nastavte **cíl připojení** přes dialogové okno **Vybrat kontejner Docker** .

    Proces kontejneru Docker můžete ladit buď místně, nebo vzdáleně.
    
    **Postup při ladění procesu kontejneru Docker v místním prostředí:**
    1. Nastavte **hostitele Docker CLI** na **místní počítač**.
    1. Vyberte běžící kontejner, ze kterého se má připojit, a stiskněte **OK**.
    
    ![Vybrat nabídku kontejneru Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. pro vzdálené ladění procesu kontejneru Docker:**
    
    > [!NOTE] 
    > Existují dvě možnosti, jak se vzdáleně připojit ke spuštěnému procesu v kontejneru Docker. První možnost použití SSH je ideální, pokud na místním počítači nemáte nainstalované nástroje Docker.  Pokud máte nástroje Docker nainstalované místně a máte démona Docker, který je nakonfigurovaný tak, aby přijímal vzdálené požadavky, zkuste druhou možnost s použitím démona Docker.

    1. ***Připojení ke vzdálenému počítači přes SSH:***
        1. Vyberte **Přidat...** a připojte se ke vzdálenému systému.<br/>
        ![Připojit ke vzdálenému systému](../debugger/media/connect-remote-system.png "Připojit ke vzdálenému systému")
        1. Vyberte běžící kontejner, ke kterému se připojíte po úspěšném připojení k SSH nebo procesu démona, a pak stiskněte **OK**.

    
    1. ***Nastavení cíle ke vzdálenému kontejneru se spuštěným procesem prostřednictvím [démona Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Zadejte adresu démona (tj. přes TCP, IP adresu atd.) v části **hostitel Docker (volitelné)** a klikněte na odkaz aktualizovat.
        1. Vyberte běžící kontejner, ke kterému se připojíte po úspěšném připojení k procesu démona, a pak stiskněte **OK**.

4. Zvolte odpovídající proces kontejneru ze seznamu **dostupných procesů** a vyberte **připojit** k zahájení ladění procesu C# kontejneru v aplikaci Visual Studio!

    ![Nabídka připojit k Docker je dokončená](../debugger/media/docker-attach-complete.png "Nabídka připojit k Docker je dokončená")


::: moniker-end

## <a name="BKMK_reattach"></a>Opětovné připojení k procesu

Můžete se rychle znovu připojit k procesům, které jste dříve připojili k procesu, a to výběrem možnosti **ladit** > znovu **připojit k procesu** (**SHIFT**+**ALT**+**P**). Název procesu, když zvolíte tento příkaz, ladicí program se okamžitě pokusí připojit k naposledy procesy, které jste připojili při prvním pokusu odpovídat ID předchozího procesu a pokud se nezdaří, to provede spárováním odpovídajících na předchozí. Pokud se nenajde žádné shody nebo pokud má několik procesů stejný název, otevře se dialogové okno **připojit k procesu** , abyste mohli vybrat správný proces.

> [!NOTE]
> Příkaz znovu **připojit k procesu** je k dispozici od začátku v aplikaci Visual Studio 2017.

## <a name="BKMK_Scenarios"></a>Běžné scénáře ladění

V následující tabulce je uvedeno několik běžných scénářů ladění, které vám pomůžou určit, jestli se má použít **k procesu připojení** a jaký proces se má připojit, a to s odkazy na další pokyny, které jsou k dispozici. (Seznam není vyčerpávající.)

U některých typů aplikací, jako jsou aplikace pro univerzální aplikace pro Windows (UWP), se nepřipojujte přímo k názvu procesu, ale místo toho použijte možnost **ladit nainstalovaný balíček aplikace** v aplikaci Visual Studio (viz tabulka).

Aby se ladicí program připojil k kódu napsanému v C++, musí kód vygenerovat `DebuggableAttribute`. To můžete do kódu přidat automaticky tak, že propojíte s možností linkeru [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Pro ladění skriptů na straně klienta musí být ladění skriptů povoleno v prohlížeči. Pro ladění skriptu na straně klienta v Chrome vyberte možnost **Webová sada** jako typ kódu a v závislosti na typu vaší aplikace možná budete muset zavřít všechny instance Chromu a spustit prohlížeč v režimu ladění (typ `chrome.exe --remote-debugging-port=9222` z příkazového řádku).

Pokud chcete rychle vybrat běžící proces, ke kterému se chcete připojit, v aplikaci Visual Studio zadejte **Ctrl**+**ALT**+**P**a pak zadejte první písmeno názvu procesu.

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Použití vzdálených nástrojů a **připojení k procesu**|*W3wp.exe*|Viz [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Vzdálené ladění ASP.NET Core na server služby IIS|Použití vzdálených nástrojů a **připojení k procesu**|*dotnet. exe* nebo *APPNAME. exe*|Nasazení aplikací najdete v tématu [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pro ladění, viz [vzdálené ladění ASP.NET Core na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Ladění skriptů na straně klienta na místním serveru IIS, pro typy podporovaných aplikací |Použít **připojit k procesu**|*Chrome. exe*, *MicrosoftEdgeCP. exe*nebo *iexplore. exe*|Musí být povoleno ladění skriptu. Pro Chrome musíte také spustit Chrome v režimu ladění a vybrat **WebKit kód** v poli **připojit k** .|
|Ladění aplikací v jazyce C#, Visual Basic nebo C++ v místním počítači|Použít buď standardní ladění (**F5**), nebo **připojit k procesu**|*\<název_aplikace >. exe*|Ve většině scénářů použijte standardní ladění a **Nepřipojujte se k procesu**.|
|Vzdálené ladění aplikace klasické pracovní plochy Windows|Vzdálené nástroje|neuvedeno| Viz téma [vzdálené ladění C# a aplikace Visual Basic](../debugger/remote-debugging-csharp.md) nebo [vzdálené C++ ladění aplikace](../debugger/remote-debugging-cpp.md) .|
|Ladění .NET Core v systému Linux|Použít **připojit k procesu**|*dotnet. exe*|Pokud chcete použít SSH, přečtěte si téma [vzdálené ladění .NET Core běžící na Linux pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Ladění aplikace ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použít **připojit k procesu**|*iiexpress. exe*|To může být užitečné k vytvoření aplikace načíst rychleji, například (třeba) při profilování. |
|Ladit další typy aplikací podporované v procesu serveru|Pokud je server vzdálený, použijte nástroje Remote Tools a **Připojte se k procesu** .|*Chrome. exe*, *iexplore. exe*nebo jiné procesy|V případě potřeby použijte k identifikaci procesu Sledování prostředků. Viz téma [vzdálené ladění](../debugger/remote-debugging.md).|
|Vzdálené ladění aplikací pro univerzální aplikace Windows (UPW), OneCore, HoloLens a IoT aplikací|Ladit nainstalovaný balíček aplikace|neuvedeno|Viz [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití příkazu **připojit k procesu** .|
|Ladění aplikací pro univerzální aplikace Windows (UPW), OneCore, HoloLens a IoT aplikací, které se nepovedlo spustit ze sady Visual Studio|Ladit nainstalovaný balíček aplikace|neuvedeno|Viz [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití příkazu **připojit k procesu** .|

## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážek) při připojování k procesu, aplikace musí přesně odpovídat, místní zdroje a symbolů. To znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění.

Pro scénáře vzdálené ladění musí mít zdrojový kód (nebo kopii zdrojového kódu) otevřen v sadě Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako v místním počítači.

V některých místní ladění scénářích můžete ladit v sadě Visual Studio bez přístupu ke zdroji Pokud jsou k dispozici v aplikaci správný symbol soubory. Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění. Další informace najdete v tématu [Určení symbolů a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a>Řešení chyb připojení
 Pokud ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu, ke kterým se může ladicí program připojit, jsou zobrazeny a vybrány v dialogovém okně **Vybrat typ kódu** .

 V některých případech můžete úspěšně připojit ladicí program k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, která běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované pro některé typy kódu, ale nikoli pro jiné komponenty vzdáleného ladění. Může dojít také při pokusu o připojení ke dvěma nebo více procesům pro přímé ladění databáze. SQL ladění podporuje připojení pouze jednoho procesu.

 Pokud ladicí program je možné se připojit k některým, ale ne všechny typy kódu, zobrazí se zpráva označující, ke kterým typům se nepodařilo připojit.

 Pokud ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete přejít k ladění procesu. Budete moci ladit pouze typy kódu, které byly úspěšně připojeny. Nepřipojené kódu v procesu bude stále spuštěn, ale nebudete moci nastavit zarážky, zobrazit data ani provádět jiné operace ladění na tento kód.

 Pokud potřebujete konkrétnější informace o Proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze tomuto typu kódu.

 **Chcete-li získat konkrétní informace o tom, proč se typ kódu nepodařilo připojit:**

1. Odpojte od procesu. V nabídce **ladění** vyberte **Odpojit vše**.

1. Znovu připojte k procesu, vyberte pouze typ kódu, který se nepodařilo připojit.

    1. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** .

    2. Vyberte **Vybrat**.

    3. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Zrušte výběr jiných typů kódu.

    4. Vyberte **OK**.

    5. V dialogovém okně **připojit k procesu** vyberte **připojit**.

    Tentokrát připojení zcela selže a dostanete konkrétní chybovou zprávu.

## <a name="see-also"></a>Viz také

- [Ladění více procesů](../debugger/debug-multiple-processes.md)
- [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
