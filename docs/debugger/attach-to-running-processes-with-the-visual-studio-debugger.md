---
title: Připojení ladicího programu ke spuštěným procesům
description: zjistěte, jak připojit ladicí program Visual Studio ke spuštěnému procesu na místním nebo vzdáleném počítači.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9774878b8d8862fca0b8b35de924b7bc1ab45656
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280522"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům

ladicí program Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. po spuštění procesu vyberte **ladit**  >  **připojit k procesu** nebo stiskněte **klávesovou zkratku Ctrl** + **+** + **p** v Visual Studio a k procesu připojte ladicí program k procesu pomocí dialogového okna **připojit k** procesu.

pomocí příkazu **připojit k procesu** můžete ladit spuštěné aplikace na místních nebo vzdálených počítačích, ladit současně více procesů, ladit aplikace, které nebyly vytvořeny v Visual Studio, nebo ladit jakoukoli aplikaci, kterou jste nespustili z Visual Studio pomocí připojeného ladicího programu. Například pokud spouštíte aplikaci bez ladicího programu a narazíte na výjimku, můžete připojit ladicí program k procesu, na kterém aplikace běží, a zahájit ladění.

> [!TIP]
> Nejste si jisti, jestli pro váš scénář ladění chcete použít **připojit k procesu** ? Viz [běžné scénáře ladění](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Připojte se k běžícímu procesu na místním počítači.

Chcete-li se rychle znovu připojit k procesu, který jste k dřív připojili, přečtěte si téma [opětovné připojení k procesu](#BKMK_reattach).

**Připojení k procesu v místním počítači:**

1. v Visual Studio vyberte **ladit**  >  **připojit k procesu** (nebo stiskněte klávesovou **zkratku Ctrl** + **+** + **P**) k otevření dialogového okna **připojit k procesu** .

1. Ověřte **Typ připojení**.

   Ve většině scénářů můžete použít **výchozí**. Některé scénáře můžou vyžadovat jiný typ připojení. Další informace naleznete v dalších částech tohoto článku nebo v tématu [běžné scénáře ladění](#BKMK_Scenarios).

1. Nastavte **cíl připojení** na název místního počítače.

   ![Snímek obrazovky s dialogovým oknem připojit k procesu s cílem připojení nastaveným na název místního počítače](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. V seznamu **procesy k dispozici** vyhledejte a vyberte proces nebo procesy, ke kterým se chcete připojit.

   - Chcete-li rychle vybrat proces, zadejte jeho název nebo první písmeno do pole **filtrovat procesy** .

   - Pokud název procesu neznáte, procházejte seznamem nebo si prohlédněte [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů.

   >[!TIP]
   >Procesy lze spustit a zastavit na pozadí, zatímco je otevřeno dialogové okno **připojit k procesu** , takže seznam spuštěných procesů nemusí být vždy aktuální. Můžete kdykoli vybrat možnost **aktualizovat** , aby se zobrazil aktuální seznam.

1. V poli **připojit k** ověřte, že je uveden typ kódu, který chcete ladit. Výchozí **Automatické** nastavení funguje pro většinu typů aplikací.

   Pokud používáte **výchozí** typ připojení, můžete ručně vybrat typ kódu, ke kterému se chcete připojit. V opačném případě může být možnost **výběru** zakázána.

   Ruční výběr typů kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu**.
      Pokud dojde k chybě při pokusu o připojení k procesu v seznamu, můžete použít dialogové okno [Vybrat typ kódu](../debugger/select-code-type-dialog-box.md) , který vám může pomoct problém [vyřešit](#BKMK_Troubleshoot_attach_errors) .
   1. Vyberte typy kódu, které chcete ladit.
   1. Vyberte **OK**.

1. Vyberte **připojit**.

>[!NOTE]
>Můžete se připojit k více aplikacím pro ladění, ale v ladicím programu je aktivní jenom jedna aplikace. aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studioho **umístění** .

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojit k procesu ve vzdáleném počítači

Můžete také vybrat vzdálený počítač v dialogovém okně **připojit k procesu** , zobrazit seznam dostupných procesů spuštěných v tomto počítači a připojit se k jednomu nebo více procesům pro ladění. Vzdálený ladicí program (*msvsmon.exe*) musí být spuštěný na vzdáleném počítači. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

podrobnější pokyny pro ladění ASP.NET aplikací, které byly nasazeny do služby IIS, najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Chcete-li se připojit ke spuštěnému procesu na vzdáleném počítači:**

1. v Visual Studio vyberte **ladit**  >  **připojit k procesu** (nebo stiskněte klávesovou **zkratku Ctrl** + **+** + **P**) k otevření dialogového okna **připojit k procesu** .

1. Ověřte **Typ připojení**.

   Ve většině scénářů můžete použít **výchozí**. Některé scénáře, například ladění systému Linux nebo aplikace s využitím kontejnerů, vyžadují jiný typ připojení. Další informace naleznete v dalších částech tohoto článku nebo v tématu [běžné scénáře ladění](#BKMK_Scenarios).

1. V poli **cíl připojení** vyberte vzdálený počítač pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **cíle připojení** a v rozevíracím seznamu vyberte název počítače.
   - Do pole **cíl připojení** zadejte název počítače a stiskněte klávesu **ENTER**.

     ověřte, že Visual Studio přidá požadovaný port do názvu počítače, který se zobrazí ve formátu: **\<remote computer name> :p** .

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022` ). 4024 je výchozí port pro vzdálený ladicí program Visual Studio 2019 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022` ). 4022 je výchozí port pro vzdálený ladicí program Visual Studio 2017 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

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
     >Pokud se pokusíte připojit k procesu vlastněné nedůvěryhodným uživatelským účtem, zobrazí se potvrzení dialogového okna Upozornění zabezpečení. Další informace najdete v tématu [Upozornění zabezpečení: připojení k procesu, který vlastní nedůvěryhodný uživatel, může být nebezpečné. Pokud tyto informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. V poli **připojit k** ověřte, že je uveden typ kódu, který chcete ladit. Výchozí **Automatické** nastavení funguje pro většinu typů aplikací.

   Pokud používáte **výchozí** typ připojení, můžete ručně vybrat typ kódu, ke kterému se chcete připojit. V opačném případě může být možnost **výběru** zakázána.

   Ruční výběr typů kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu**.
      Pokud dojde k chybě při pokusu o připojení k procesu v seznamu, můžete použít dialogové okno [Vybrat typ kódu](../debugger/select-code-type-dialog-box.md) , který vám může pomoct problém [vyřešit](#BKMK_Troubleshoot_attach_errors) .
   1. Vyberte **OK**.

6. Vyberte **připojit**.

>[!NOTE]
>Můžete se připojit k více aplikacím pro ladění, ale v ladicím programu je aktivní jenom jedna aplikace. aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studioho **umístění** .

V některých případech se při ladění v relaci vzdálené plochy (Terminálové služby) nezobrazí seznam **procesy k** dispozici všechny dostupné procesy. pokud používáte Visual Studio jako uživatel, který má omezený uživatelský účet, seznam **procesy k dispozici** nebude zobrazovat procesy spuštěné v relaci 0. Relace 0 se používá pro služby a jiné serverové procesy, včetně *w3wp.exe*. Problém můžete vyřešit tak, že spustíte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] účet správce nebo spustíte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z konzoly serveru místo relace Terminálové služby.

pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu spuštěním `vsjitdebugger.exe -p <ProcessId>` z příkazového řádku Windows. ID procesu můžete určit pomocí *tlist.exe*. chcete-li získat *tlist.exe*, stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na adrese [WDK a WinDbg ke stažení](/windows-hardware/drivers/download-the-wdk).

## <a name="attach-to-a-net-core-process-running-on-azure-app-service-windows"></a>Připojení k procesu .NET Core běžícímu na Azure App Service (Windows)

pokud publikujete do Azure App Service (Windows), najdete možnost **připojit ladicí program** v nabídce **...** v části **hostování**. Visual Studio se pokusí připojit vzdálený ladicí program k instanci Azure App Service (Windows), do které profil publikuje.

:::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Snímek obrazovky s možností připojit ladicí program v rámci stránky Souhrn publikování":::

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Připojení k procesu .NET Core běžícímu na Linux pomocí SSH

Další informace najdete v tématu [vzdálené ladění .NET Core běžící na Linux pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Připojení k procesu běžícímu na kontejneru Docker

počínaje Visual Studio 2019 můžete připojit Visual Studio ladicího programu k procesu běžícímu na kontejneru docker. Informace o kontejneru Dockeru s Linuxem v .NET Core najdete v tématu Připojení k procesu [spuštěném v kontejneru Dockeru s Linuxem.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container) Informace o Windows Dockeru najdete v tématu Připojení k procesu spuštěném na [Windows Kontejner Dockeru.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Opětovné připojování k procesu

K procesům, ke kterých jste byli dříve připojení, se můžete rychle znovu připojit tak, že zvolíte Ladit znovu připojit k  >  **procesu** (**Shift** + **Alt** + **P**). Když zvolíte tento příkaz, ladicí program se okamžitě pokusí připojit k posledním procesům, ke kterých jste se připojili, a to tak, že se nejprve pokusí najít shodu s předchozím ID procesu, a pokud se to nepovede, podle názvu předchozího procesu. Pokud se nenašly žádné shody nebo pokud má  několik procesů stejný název, otevře se dialogové okno Připojit k procesu, abyste mohli vybrat správný proces.

> [!NOTE]
> Příkaz **Znovu se připojovat k procesu** je k dispozici od Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Běžné scénáře ladění

Následující tabulka obsahuje několik  běžných scénářů ladění s odkazy na další pokyny, pokud je k dispozici, abyste si pomohli určit, jestli se má použít příkaz Připojit k procesu a k jakým procesům se připojit. (Seznam není vyčerpávající.)

U některých typů aplikací, jako jsou aplikace pro Univerzální aplikaci Windows App (UPW), se  nepřipojíte přímo k názvu procesu, ale místo toho použijete možnost nabídky Ladit balíček nainstalované aplikace v Visual Studio (viz tabulka).

Aby se ladicí program připojovat ke kódu napsanému v jazyce C++, musí kód generovat `DebuggableAttribute` . Tento kód můžete do kódu přidat automaticky propojením s možností [linkeru /ASSEMBLYDEBUG.](/cpp/build/reference/assemblydebug-add-debuggableattribute)

Pro ladění skriptů na straně klienta musí být v prohlížeči povolené ladění skriptů. Pro ladění skriptu na straně klienta v Chromu zvolte jako typ kódu **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge – Chromium)** a v závislosti na typu aplikace možná budete muset zavřít všechny instance Chromu a spustit prohlížeč v režimu ladění (zadejte z `chrome.exe --remote-debugging-port=9222` příkazového řádku). V dřívějších verzích Visual Studio ladicí program skriptu pro Chrome byl **Webová sada**.

Pokud chcete rychle vybrat spuštěný proces, ke Visual Studio, zadejte **Ctrl** Alt P a pak zadejte první písmeno +  + názvu procesu.

|Scenario|Metoda ladění|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Použití vzdálených nástrojů **a připojení k procesu**|*w3wp.exe*|Viz [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Vzdálené ladění ASP.NET Core na serveru služby IIS|Použití vzdálených nástrojů **a připojení k procesu**|*w3wp.exe* nebo *dotnet.exe*|Počínaje .NET Core 3 *sew3wp.exe* pro výchozí model hostování v [aplikaci.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Informace o nasazení aplikací najdete v [tématu Publikování do služby IIS.](/aspnet/core/host-and-deploy/iis/) Podrobnější informace najdete v tématu Vzdálené [ladění ASP.NET Core na vzdáleném počítači se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Ladění skriptu na straně klienta na místním serveru služby IIS pro podporované typy aplikací |Použití **připojení k procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe* nebo *iexplore.exe*|Ladění skriptů musí být povolené. V prohlížeči Chrome musíte také spustit Chrome v režimu ladění (napište z příkazového řádku) a v poli Připojit k vyberte `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome).** |
|Ladění aplikace v jazyce C#, Visual Basic nebo C++ na místním počítači|Použijte standardní ladění (**F5**) nebo **Attach to Process (Připojit k procesu).**|*\<appname>.exe*|Ve většině scénářů použijte standardní ladění a ne **Připojit k procesu**.|
|Vzdálené ladění Windows desktopové aplikace|Vzdálené nástroje|–| Viz [Vzdálené ladění aplikace v jazyce C# nebo Visual Basic nebo](../debugger/remote-debugging-csharp.md) Vzdálené ladění aplikace v [jazyce C++](../debugger/remote-debugging-cpp.md)|
|Ladění .NET Core v Linuxu|Použití **připojení k procesu**|*dotnet.exe* nebo jedinečný název procesu|Informace o použití SSH najdete v tématu [Vzdálené ladění .NET Core běžící v Linuxu pomocí SSH.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) Informace o kontejnerizovaných [aplikacích najdete v tématu Připojení k procesu spuštěném v kontejneru Dockeru.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Ladění kontejnerizované aplikace|Použití **připojení k procesu**|*dotnet.exe* nebo jedinečný název procesu|Viz [Připojení k procesu spuštěném v kontejneru Dockeru.](../debugger/attach-to-process-running-in-docker-container.md)|
|Vzdálené ladění Pythonu v Linuxu|Použití **připojení k procesu**|*debugpy*|Viz [Vzdálené připojení z nástrojů Pythonu.](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Ladění ASP.NET aplikace na místním počítači po spuštění aplikace bez ladicího programu|Použití **připojení k procesu**|*iiexpress.exe*|To může být užitečné k rychlejšímu načítání aplikace, například (například) při profilaci. |
|Ladění dalších podporovaných typů aplikací v serverových procesech|Pokud je server vzdálený, použijte vzdálené nástroje a **připojte se k procesu.**|*chrome.exe,* *iexplore.exe* nebo jiné procesy|V případě potřeby Sledování prostředků s identifikací tohoto procesu. Viz [Vzdálené ladění.](../debugger/remote-debugging.md)|
|Vzdálené ladění univerzální Windows App (UPW), OneCore, HoloLens nebo aplikace IoT|Ladění balíčku nainstalované aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace místo](debug-installed-app-package.md) použití možnosti Připojit k **procesu.**|
|Ladění univerzální Windows App (UPW), OneCore, HoloLens nebo IoT, které jste nezačátku Visual Studio|Ladění balíčku nainstalované aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace místo](debug-installed-app-package.md) použití možnosti Připojit k **procesu.**|

## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Pokud chcete při připojování k procesu použít úplné funkce ladicího programu Visual Studio (například při zarážek), musí aplikace přesně odpovídat místnímu zdroji a symbolům. To znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (.pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Ve výchozím nastavení to vyžaduje sestavení pro ladění.

Ve scénářích vzdáleného ladění musíte mít zdrojový kód (nebo kopii zdrojového kódu) již otevřený v Visual Studio. Binární soubory zkompilované aplikace na vzdáleném počítači musí pochovat ze stejného sestavení jako na místním počítači.

V některých scénářích místního ladění můžete ladit v Visual Studio bez přístupu ke zdroji, pokud aplikace obsahuje správné soubory symbolů. Ve výchozím nastavení to vyžaduje sestavení pro ladění. Další informace najdete v tématu [Určení symbolu a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Řešení potíží s chybami připojení

V některých scénářích může ladicí program potřebovat pomoc se správným určením typu kódu, který se má ladit. Pokud jsou hodnoty připojení správně nastavené (správný proces  můžete zobrazit v seznamu Dostupné procesy), ale ladicí program se  nepodaří připojit, zkuste v seznamu Typ připojení vybrat nejvhodnější typ připojení, který může být vyžadován, například pokud ladíte aplikaci v Linuxu nebo Pythonu. Pokud používáte výchozí typ připojení, můžete alternativně vybrat konkrétní typ kódu, ke který se chcete připojit, jak je popsáno dále v této části.

Když se ladicí program připojí ke spuštěnému procesu, může tento proces obsahovat jeden nebo více typů kódu. Typy kódu, ke které se ladicí program může připojit, se zobrazí a vyberou v [dialogovém okně Vybrat typ](../debugger/select-code-type-dialog-box.md) kódu.

V některých případech se ladicí program může úspěšně připojit k jednomu typu kódu, ale ne k jinému typu kódu. K tomu obvykle dochází v případě, že:

- Pokusíte se připojit k procesu, který běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované součásti vzdáleného ladění pro některé typy kódu, ale ne pro jiné.
- Pokusíte se připojit ke dvěma nebo více procesům pro přímé ladění databáze. SQL ladění podporuje připojení pouze k jednomu procesu.

Pokud se ladicí program může připojit k některým(ale ne všem) typům kódu, zobrazí se zpráva s identifikací typů, které se nepodařilo připojit.

Pokud se ladicí program úspěšně připojí alespoň k jednomu typu kódu, můžete pokračovat laděním procesu. Budete moct ladit pouze typy kódu, které byly úspěšně připojeny. Nepřipojovaný kód v procesu se bude stále spouštět, ale nebudete moct nastavovat zarážky, zobrazit data ani s kódem provádět jiné operace ladění.

Pokud chcete konkrétnější informace o tom, proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze k typu kódu.

**Chcete-li získat konkrétní informace o tom, proč se typ kódu nepodařilo připojit:**

1. Odpojte se od procesu. V nabídce **ladění** vyberte **Odpojit vše**.

1. Znovu se připojte k procesu a vyberte jenom typ kódu, který se nepovedlo připojit.

    1. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** .

    2. Vyberte **Vybrat**.

    3. V dialogovém okně **Vybrat typ kódu** vyberte možnost **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Zrušte výběr ostatních typů kódu.

    4. Vyberte **OK**.

    5. V dialogovém okně **připojit k procesu** vyberte **připojit**.

    Tentokrát se připojení zcela nezdaří a zobrazí se konkrétní chybová zpráva.

## <a name="see-also"></a>Viz také

- [Ladění více procesů](../debugger/debug-multiple-processes.md)
- [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
