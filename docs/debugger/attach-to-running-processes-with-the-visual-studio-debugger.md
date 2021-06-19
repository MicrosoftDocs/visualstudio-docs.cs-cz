---
title: Připojení ladicího programu ke spuštěným procesům
description: Zjistěte, jak připojit Visual Studio ke spuštěnému procesu na místním nebo vzdáleném počítači.
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
ms.openlocfilehash: 5e3836403af80d06a2ecaa7f77cb7f49f0c6f0e8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389784"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům

Ladicí program nástroje Visual Studio připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Po spuštění procesu vyberte Ladit připojit k procesu nebo stiskněte Ctrl Alt p v Visual Studio a pomocí dialogového okna Připojit k procesu připojte  >   ladicí program  +  +  k procesu. 

Pomocí možnosti  Připojit k procesu můžete ladit spuštěné aplikace na místních nebo vzdálených počítačích, ladit více procesů současně, ladit aplikace, které nebyly vytvořeny v Visual Studio, nebo ladit aplikace, které jste nezačal od Visual Studio s připojeným ladicím programem. Pokud například spustíte aplikaci bez ladicího programu a dojde k výjimce, můžete ladicí program připojit k procesu, který aplikaci spustí, a zahájit ladění.

> [!TIP]
> Nejste si jistí, jestli **pro scénář ladění použít** možnost Připojit k procesu? Viz [Běžné scénáře ladění.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Připojení k běžící procesu na místním počítači

Pokud se chcete rychle znovu připojit k dříve připojenému procesu, podívejte se na stránku [Opětovné připojení k procesu](#BKMK_reattach).

**Připojení k procesu na místním počítači:**

1. V Visual Studio vyberte **Připojit** k procesu ladění (nebo stiskněte  >   **Ctrl** + **Alt** + **P)**  a otevřete dialogové okno Připojit k procesu.

1. Zkontrolujte **typ připojení**.

   Ve většině scénářů můžete použít výchozí **.** Některé scénáře mohou vyžadovat jiný typ připojení. Další informace najdete v dalších částech tohoto článku nebo v tématu Běžné [scénáře ladění.](#BKMK_Scenarios)

1. Nastavte **cíl připojení** na název místního počítače.

   ![Snímek obrazovky s dialogem Připojit k procesu a cílem připojení nastaveným na název místního počítače](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. V seznamu **Dostupné procesy** vyhledejte a vyberte proces nebo procesy, ke které se chcete připojit.

   - Pokud chcete proces rychle vybrat, zadejte jeho název nebo první písmeno do pole **Procesy** filtru.

   - Pokud název procesu ještě nevíte, projděte si seznam [](#BKMK_Scenarios) nebo si projděte běžné scénáře ladění pro některé běžné názvy procesů.

   >[!TIP]
   >Procesy se mohou spustit a  zastavit na pozadí, když je otevřené dialogové okno Připojit k procesu, takže seznam spuštěných procesů nemusí být vždy aktuální. Aktuální seznam **můžete** kdykoli zobrazit výběrem možnosti Aktualizovat.

1. V poli **Připojit** k se ujistěte, že je uvedený typ kódu, který chcete ladit. Výchozí automatické **nastavení** funguje pro většinu typů aplikací.

   Pokud používáte výchozí **typ** připojení, můžete ručně vybrat typ kódu, ke které se chcete připojit. Jinak může **být možnost** Vybrat zakázaná.

   Ruční výběr typů kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém **okně Vybrat typ** kódu vyberte **Ladit tyto typy kódu.**
      Pokud při pokusu o připojení k procesu v seznamu dojde [](../debugger/select-code-type-dialog-box.md) k selhání, můžete problém vyřešit pomocí dialogového okna Vybrat [typ](#BKMK_Troubleshoot_attach_errors) kódu.
   1. Vyberte typy kódu, které chcete ladit.
   1. Vyberte **OK**.

1. Vyberte **Attach (Připojit).**

>[!NOTE]
>Můžete být připojeni k více aplikacím pro ladění, ale v ladicím programu je současně aktivní pouze jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů Visual Studio **panelu** nástrojů nebo v okně **Procesy.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojení k procesu ve vzdáleném počítači

Můžete také vybrat vzdálený počítač  v dialogovém okně Připojit k procesu, zobrazit seznam dostupných procesů spuštěných v tomto počítači a připojit se k jednomu nebo více procesům pro ladění. Vzdálený ladicí program (*msvsmon.exe*) musí být spuštěn na vzdáleném počítači. Další informace najdete v tématu [Vzdálené ladění.](../debugger/remote-debugging.md)

Podrobnější pokyny pro ladění aplikací ASP.NET nasazených do služby IIS najdete v tématu Vzdálené ladění ASP.NET na vzdáleném počítači [se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Připojení ke spuštěnému procesu ve vzdáleném počítači:**

1. V Visual Studio vyberte **Připojit** k procesu ladění (nebo stiskněte  >   **Ctrl** + **Alt** + **P)**  a otevřete dialogové okno Připojit k procesu.

1. Zkontrolujte **typ připojení**.

   Ve většině scénářů můžete použít výchozí **.** Některé scénáře, jako je ladění Linuxu nebo kontejnerizované aplikace, vyžadují jiný typ připojení. Další informace najdete v dalších částech tohoto článku nebo v tématu Běžné [scénáře ladění.](#BKMK_Scenarios)

1. V **poli Cíl** připojení vyberte vzdálený počítač pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **položky Cíl připojení** a v rozevíracím seznamu vyberte název počítače.
   - Do pole Cíl připojení zadejte **název** počítače a stiskněte **Enter.**

     Ověřte, Visual Studio k názvu počítače přidá požadovaný port, který se zobrazí ve formátu **\<remote computer name> :p ort.**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít IP adresu a adresu portu (například `123.45.678.9:4022` ). 4024 je výchozí port vzdáleného ladicího programu Visual Studio 2019 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu.](remote-debugger-port-assignments.md)

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít IP adresu a adresu portu (například `123.45.678.9:4022` ). 4022 je výchozí port vzdáleného ladicího programu pro Visual Studio 2017 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu.](remote-debugger-port-assignments.md)

     ::: moniker-end

   - Výběrem **tlačítka** Najít vedle pole **Cíl připojení** otevřete dialogové okno **Vzdálená** připojení. Dialogové **okno Vzdálená** připojení obsahuje seznam všech zařízení, která jsou v místní podsíti nebo jsou přímo připojená k vašemu počítači. Možná budete muset [na serveru otevřít port UDP 3702,](../debugger/remote-debugger-port-assignments.md) abyste zjistili vzdálená zařízení. Vyberte počítač nebo zařízení, které chcete, a potom klikněte na **Vybrat.**

   > [!NOTE]
   > Nastavení **Typ připojení se** zachová mezi ladicími relacemi. Nastavení **Cíl připojení se** zachová mezi ladicími relacemi pouze v případě, že došlo k úspěšnému připojení k ladění s tímto cílem.

3. Kliknutím **na** Aktualizovat naplňte **seznam Dostupné** procesy.

    >[!TIP]
    >Procesy se mohou spustit a  zastavit na pozadí, když je otevřené dialogové okno Připojit k procesu, takže seznam spuštěných procesů nemusí být vždy aktuální. Aktuální seznam **můžete** kdykoli zobrazit výběrem možnosti Aktualizovat.

4. V seznamu **Dostupné procesy** vyhledejte a vyberte proces nebo procesy, ke které se chcete připojit.

   - Pokud chcete proces rychle vybrat, zadejte jeho název nebo první písmeno do pole **Procesy** filtru.

   - Pokud název procesu ještě nevíte, projděte si seznam [](#BKMK_Scenarios) nebo si projděte běžné scénáře ladění pro některé běžné názvy procesů.

   - Pokud chcete vyhledat procesy spuštěné pod všemi uživatelskými účty, zaškrtněte **políčko Zobrazit procesy od všech** uživatelů.

     >[!NOTE]
     >Pokud se pokusíte připojit k procesu vlastněného nedůvěryhodným uživatelským účtem, zobrazí se dialogové okno s upozorněním zabezpečení. Další informace najdete v tématu Upozornění zabezpečení: Připojení k procesu vlastněného nedůvěryhodným uživatelem může [být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jistí, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. V poli **Připojit** k se ujistěte, že je uvedený typ kódu, který chcete ladit. Výchozí automatické **nastavení** funguje pro většinu typů aplikací.

   Pokud používáte výchozí **typ** připojení, můžete ručně vybrat typ kódu, ke které se chcete připojit. Jinak může **být možnost** Vybrat zakázaná.

   Ruční výběr typů kódu:
   1. Klikněte na **Vybrat**.
   1. V dialogovém **okně Vybrat typ** kódu vyberte **Ladit tyto typy kódu.**
      Pokud při pokusu o připojení k procesu v seznamu dojde [](../debugger/select-code-type-dialog-box.md) k selhání, můžete problém vyřešit pomocí dialogového okna Vybrat [typ](#BKMK_Troubleshoot_attach_errors) kódu.
   1. Vyberte **OK**.

6. Vyberte **Attach (Připojit).**

>[!NOTE]
>Můžete být připojeni k více aplikacím pro ladění, ale v ladicím programu je současně aktivní pouze jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů Visual Studio **panelu** nástrojů nebo v okně **Procesy.**

V některých případech se při ladění v relaci Vzdálené  plochy (Terminálová služba) v seznamu Dostupné procesy nezobrazí všechny dostupné procesy. Pokud používáte Visual Studio jako uživatel s omezeným uživatelským  účtem, v seznamu Dostupné procesy se nebudou zobrazovat procesy spuštěné v relaci 0. Relace 0 se používá pro služby a další serverové procesy, včetně *w3wp.exe*. Tento problém můžete vyřešit spuštěním účtu správce nebo spuštěním z konzoly serveru místo z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] relace Terminálové služby.

Pokud žádné z těchto alternativních řešení není možné, třetí možností je připojit se k procesu spuštěním z `vsjitdebugger.exe -p <ProcessId>` příkazového řádku Windows. ID procesu můžete určit pomocí *tlist.exe*. Pokud chcete *získattlist.exe*, stáhněte a nainstalujte nástroje ladění pro Windows, které jsou k dispozici na adrese [wdk a soubory windbg ke stažení.](/windows-hardware/drivers/download-the-wdk)

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Připojení k procesu .NET Core spuštěného v Linuxu pomocí SSH

Další informace najdete v tématu Vzdálené [ladění .NET Core běžící v Linuxu pomocí SSH.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Připojení k procesu spuštěném v kontejneru Dockeru

Od Visual Studio 2019 můžete připojit ladicí program Visual Studio k procesu spuštěnému v kontejneru Dockeru. Informace o kontejneru Dockeru s Linuxem v .NET Core najdete v tématu Připojení k procesu [spuštěném v kontejneru Dockeru s Linuxem.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container) Informace o kontejneru Dockeru s Windows najdete v tématu Připojení k procesu [spuštěném v kontejneru Dockeru s Windows.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Opětovné připojování k procesu

K procesům, ke kterých jste byli dříve připojení, se můžete rychle znovu připojit tak, že zvolíte Ladit znovu připojit k  >  **procesu** (**Shift** + **Alt** + **P**). Když zvolíte tento příkaz, ladicí program se okamžitě pokusí připojit k posledním procesům, ke kterých jste se připojili, a to tak, že se nejprve pokusí najít shodu s předchozím ID procesu, a pokud se to nepovede, podle názvu předchozího procesu. Pokud se nenašly žádné shody nebo pokud má  několik procesů stejný název, otevře se dialogové okno Připojit k procesu, abyste mohli vybrat správný proces.

> [!NOTE]
> Příkaz **Znovu se připojovat k procesu** je k dispozici od Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Běžné scénáře ladění

Následující tabulka obsahuje několik  běžných scénářů ladění s odkazy na další pokyny, pokud je k dispozici, abyste si pomohli určit, jestli se má použít příkaz Připojit k procesu a k jakým procesům se připojit. (Seznam není vyčerpávající.)

U některých typů aplikací, jako jsou aplikace univerzální aplikace pro Windows (UPW), se  nepřipojíte přímo k názvu procesu, ale místo toho použijte možnost nabídky Ladit balíček nainstalované aplikace v Visual Studio (viz tabulka).

Aby se ladicí program připojovat ke kódu napsanému v jazyce C++, musí kód generovat `DebuggableAttribute` . Tento kód můžete do kódu přidat automaticky propojením s možností [linkeru /ASSEMBLYDEBUG.](/cpp/build/reference/assemblydebug-add-debuggableattribute)

Pro ladění skriptů na straně klienta musí být v prohlížeči povolené ladění skriptů. Pro ladění skriptu na straně klienta v Chromu zvolte jako typ kódu **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge – Chromium)** a v závislosti na typu aplikace možná budete muset zavřít všechny instance Chromu a spustit prohlížeč v režimu ladění (napište `chrome.exe --remote-debugging-port=9222` z příkazového řádku). V dřívějších verzích Visual Studio ladicí program skriptu pro Chrome byl **Webová sada**.

Pokud chcete rychle vybrat spuštěný proces, ke Visual Studio, zadejte **Ctrl** Alt P a pak zadejte první písmeno +  + názvu procesu.

|Scenario|Metoda ladění|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Použití vzdálených nástrojů **a připojení k procesu**|*w3wp.exe*|Viz [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Vzdálené ladění ASP.NET Core na serveru služby IIS|Použití vzdálených nástrojů **a připojení k procesu**|*w3wp.exe* nebo *dotnet.exe*|Počínaje .NET Core 3 *sew3wp.exe* pro výchozí model hostování v [aplikaci.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Informace o nasazení aplikací najdete v [tématu Publikování do služby IIS.](/aspnet/core/host-and-deploy/iis/) Podrobnější informace najdete v tématu Vzdálené [ladění ASP.NET Core na vzdáleném počítači se službou IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Ladění skriptu na straně klienta na místním serveru služby IIS pro podporované typy aplikací |Použití **připojení k procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe* nebo *iexplore.exe*|Ladění skriptů musí být povolené. V prohlížeči Chrome musíte také spustit Chrome v režimu ladění (napište z příkazového řádku) a v poli Připojit k vyberte `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome).** |
|Ladění aplikace v jazyce C#, Visual Basic nebo C++ na místním počítači|Použijte standardní ladění (**F5**) nebo **Attach to Process (Připojit k procesu).**|*\<appname>.exe*|Ve většině scénářů použijte standardní ladění a ne **Připojit k procesu**.|
|Vzdálené ladění desktopové aplikace pro Windows|Vzdálené nástroje|–| Viz [Vzdálené ladění aplikace v jazyce C# nebo Visual Basic nebo](../debugger/remote-debugging-csharp.md) Vzdálené ladění aplikace v [jazyce C++](../debugger/remote-debugging-cpp.md)|
|Ladění .NET Core v Linuxu|Použití **připojení k procesu**|*dotnet.exe* nebo jedinečný název procesu|Informace o použití SSH najdete v tématu [Vzdálené ladění .NET Core běžící v Linuxu pomocí SSH.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) Informace o kontejnerizovaných [aplikacích najdete v tématu Připojení k procesu spuštěném v kontejneru Dockeru.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Ladění kontejnerizované aplikace|Použití **připojení k procesu**|*dotnet.exe* nebo jedinečný název procesu|Viz [Připojení k procesu spuštěném v kontejneru Dockeru.](../debugger/attach-to-process-running-in-docker-container.md)|
|Vzdálené ladění Pythonu v Linuxu|Použití **připojení k procesu**|*debugpy*|Viz [Vzdálené připojení z nástrojů Pythonu.](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Ladění ASP.NET aplikace na místním počítači po spuštění aplikace bez ladicího programu|Použití **připojení k procesu**|*iiexpress.exe*|To může být užitečné k rychlejšímu načítání aplikace, například (například) při profilaci. |
|Ladění dalších podporovaných typů aplikací v serverových procesech|Pokud je server vzdálený, použijte vzdálené nástroje a **připojte se k procesu.**|*chrome.exe,* *iexplore.exe* nebo jiné procesy|V případě potřeby Sledování prostředků s identifikací tohoto procesu. Viz [Vzdálené ladění.](../debugger/remote-debugging.md)|
|Vzdálené ladění univerzální aplikace pro Windows (UPW), OneCore, HoloLens nebo aplikace IoT|Ladění balíčku nainstalované aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace místo](debug-installed-app-package.md) použití možnosti Připojit k **procesu.**|
|Ladění univerzální aplikace pro Windows (UPW), OneCore, HoloLens nebo IoT, kterou jste nezačáte Visual Studio|Ladění balíčku nainstalované aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace místo](debug-installed-app-package.md) použití možnosti Připojit k **procesu.**|

## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Pokud chcete při připojování k procesu používat úplné funkce ladicího programu Visual Studio (například při zarážek), musí aplikace přesně odpovídat místnímu zdroji a symbolům. To znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (.pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Ve výchozím nastavení to vyžaduje sestavení pro ladění.

Pro scénáře vzdáleného ladění musíte mít zdrojový kód (nebo kopii zdrojového kódu) již otevřený v Visual Studio. Binární soubory zkompilované aplikace na vzdáleném počítači musí pochovat ze stejného sestavení jako na místním počítači.

V některých scénářích místního ladění můžete ladit v Visual Studio bez přístupu ke zdroji, pokud aplikace obsahuje správné soubory symbolů. Ve výchozím nastavení to vyžaduje sestavení pro ladění. Další informace najdete v tématu [Určení symbolu a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Řešení potíží s chybami připojení

V některých scénářích může ladicí program potřebovat pomoc se správným určením typu kódu, který se má ladit. Pokud jsou hodnoty připojení správně nastavené (správný proces  můžete zobrazit v seznamu Dostupné procesy), ale ladicí program se  nepodaří připojit, zkuste v seznamu Typ připojení vybrat nejvhodnější typ připojení, který může být vyžadován, například pokud ladíte aplikaci v Linuxu nebo Pythonu. Pokud používáte výchozí typ připojení, můžete alternativně vybrat konkrétní typ kódu, ke který se chcete připojit, jak je popsáno dále v této části.

Když se ladicí program připojí ke spuštěnému procesu, může tento proces obsahovat jeden nebo více typů kódu. Typy kódu, ke které se ladicí program může připojit, se zobrazí a vyberou v [dialogovém okně Vybrat typ](../debugger/select-code-type-dialog-box.md) kódu.

V některých případech se ladicí program může úspěšně připojit k jednomu typu kódu, ale ne k jinému typu kódu. K tomu obvykle dochází v případě, že:

- Pokusíte se připojit k procesu, který běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované součásti vzdáleného ladění pro některé typy kódu, ale ne pro jiné.
- Pokusíte se připojit ke dvěma nebo více procesům pro přímé ladění databáze. Ladění SQL podporuje připojení pouze k jednomu procesu.

Pokud se ladicí program může připojit k některým(ale ne všem) typům kódu, zobrazí se zpráva s identifikací typů, které se nepodařilo připojit.

Pokud se ladicí program úspěšně připojí alespoň k jednomu typu kódu, můžete pokračovat laděním procesu. Budete moct ladit pouze typy kódu, které byly úspěšně připojeny. Nepřipojovaný kód v procesu se bude stále spouštět, ale nebudete moct nastavovat zarážky, zobrazit data ani s kódem provádět jiné operace ladění.

Pokud chcete konkrétnější informace o tom, proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze k typu kódu.

**Pokud chcete získat konkrétní informace o tom, proč se nepodařilo připojit typ kódu:**

1. Odpojte se od procesu. V **nabídce Ladit** vyberte **Odpojit vše.**

1. Znovu se připojte k procesu a vyberte pouze typ kódu, který se nepodařilo připojit.

    1. V dialogovém **okně Připojit** k procesu vyberte proces v seznamu **Dostupné** procesy.

    2. Vyberte **Vybrat**.

    3. V dialogovém **okně Vybrat typ** kódu vyberte **Ladit** tyto typy kódu a typ kódu, který se nepodařilo připojit. Zrušte výběr ostatních typů kódu.

    4. Vyberte **OK**.

    5. V dialogovém **okně Připojit** k procesu vyberte **Připojit.**

    Tentokrát připojení zcela selže a zobrazí se konkrétní chybová zpráva.

## <a name="see-also"></a>Viz také

- [Ladění více procesů](../debugger/debug-multiple-processes.md)
- [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
