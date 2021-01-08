---
title: Připojení ladicího programu ke spuštěným procesům
description: Zjistěte, jak připojit ladicí program sady Visual Studio ke spuštěnému procesu na místním nebo vzdáleném počítači.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fb2fde5d5629b84ccd0e136c132a200b154ea71
ms.sourcegitcommit: dc71e9030ff35bb26916572b431d4d9e78df3d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031039"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům

Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Po spuštění procesu vyberte **ladit**  >  **připojit k procesu** nebo stiskněte **klávesovou zkratku CTRL** + **+** + **P** v aplikaci Visual Studio a připojte ladicí program k procesu pomocí dialogového okna **připojit k procesu** .

Pomocí příkazu **připojit k procesu** můžete ladit spuštěné aplikace v místních nebo vzdálených počítačích, ladit současně více procesů, ladit aplikace, které nebyly vytvořeny v aplikaci Visual Studio, nebo ladit jakoukoli aplikaci, kterou jste nespustili ze sady Visual Studio, pomocí připojeného ladicího programu. Například pokud spouštíte aplikaci bez ladicího programu a narazíte na výjimku, můžete připojit ladicí program k procesu, na kterém aplikace běží, a zahájit ladění.

> [!TIP]
> Nejste si jisti, jestli pro váš scénář ladění chcete použít **připojit k procesu** ? Viz [běžné scénáře ladění](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Připojte se k běžícímu procesu na místním počítači.

Chcete-li se rychle znovu připojit k procesu, který jste k dřív připojili, přečtěte si téma [opětovné připojení k procesu](#BKMK_reattach).

**Připojení k procesu v místním počítači:**

1. V aplikaci Visual Studio vyberte **ladit**  >  **připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL** + **+** + **P**) k otevření dialogového okna **připojit k procesu** .

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
>Můžete se připojit k více aplikacím pro ladění, ale v ladicím programu je aktivní jenom jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studio **umístění** .

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojit k procesu ve vzdáleném počítači

Můžete také vybrat vzdálený počítač v dialogovém okně **připojit k procesu** , zobrazit seznam dostupných procesů spuštěných v tomto počítači a připojit se k jednomu nebo více procesům pro ladění. Vzdálený ladicí program (*msvsmon.exe*) musí být spuštěný na vzdáleném počítači. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

Podrobnější pokyny pro ladění aplikací ASP.NET, které byly nasazeny do služby IIS, najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Chcete-li se připojit ke spuštěnému procesu na vzdáleném počítači:**

1. V aplikaci Visual Studio vyberte **ladit**  >  **připojit k procesu** (nebo stiskněte klávesovou **zkratku CTRL** + **+** + **P**) k otevření dialogového okna **připojit k procesu** .

1. Ověřte **Typ připojení**.

   Ve většině scénářů můžete použít **výchozí**. Některé scénáře, například ladění systému Linux nebo aplikace s využitím kontejnerů, vyžadují jiný typ připojení. Další informace naleznete v dalších částech tohoto článku nebo v tématu [běžné scénáře ladění](#BKMK_Scenarios).

1. V poli **cíl připojení** vyberte vzdálený počítač pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **cíle připojení** a v rozevíracím seznamu vyberte název počítače.
   - Do pole **cíl připojení** zadejte název počítače a stiskněte klávesu **ENTER**.

     Ověřte, že Visual Studio přidá požadovaný port do názvu počítače, který se zobrazí ve formátu: **\<remote computer name> :p** .

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022` ). 4024 je výchozí port pro vzdálený ladicí program sady Visual Studio 2019 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu IP a port (například `123.45.678.9:4022` ). 4022 je výchozí port pro vzdálený ladicí program sady Visual Studio 2017 x64. Další přiřazení portů vzdáleného ladicího programu najdete v tématu [Přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).

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
>Můžete se připojit k více aplikacím pro ladění, ale v ladicím programu je aktivní jenom jedna aplikace. Aktivní aplikaci můžete nastavit na panelu nástrojů nebo v okně **procesy** ladění Visual Studio **umístění** .

V některých případech se při ladění v relaci vzdálené plochy (Terminálové služby) nezobrazí seznam **procesy k** dispozici všechny dostupné procesy. Pokud používáte aplikaci Visual Studio jako uživatel s omezeným uživatelským účtem, seznam **procesy k dispozici** nebude zobrazovat procesy spuštěné v relaci 0. Relace 0 se používá pro služby a jiné serverové procesy, včetně *w3wp.exe*. Problém můžete vyřešit tak, že spustíte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] účet správce nebo spustíte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z konzoly serveru místo relace Terminálové služby.

Pokud ani jedno z těchto řešení není možné, je třetí možností připojit se k procesu spuštěním `vsjitdebugger.exe -p <ProcessId>` z příkazového řádku Windows. ID procesu můžete určit pomocí *tlist.exe*. Chcete-li získat *tlist.exe*, Stáhněte a nainstalujte ladicí nástroje pro Windows, které jsou k dispozici na adrese  [WDK a programu WinDbg ke stažení](/windows-hardware/drivers/download-the-wdk).

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Připojení k procesu .NET Core běžícímu na Linux pomocí SSH

Další informace najdete v tématu [vzdálené ladění .NET Core běžící na Linux pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Připojení k procesu běžícímu na kontejneru Docker

Od sady Visual Studio 2019 můžete připojit ladicí program sady Visual Studio k procesu běžícímu na kontejneru Docker. Kontejner Docker .NET Core pro Linux najdete v tématu [připojení k procesu spuštěnému v kontejneru Docker platformy Linux](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). V případě kontejneru Docker v systému Windows najdete informace v tématu [připojení k procesu běžícímu na kontejneru Docker systému Windows](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container).

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Opětovné připojení k procesu

Můžete se rychle znovu připojit k procesům, které jste předtím připojili k procesu, a to tak, že zvolíte možnost **ladění** znovu  >  **připojit k procesu** (**SHIFT** + **ALT** + **P**). Když vyberete tento příkaz, ladicí program se okamžitě pokusí připojit k poslednímu procesu, ke kterému jste se připojili, a to tak, že se pokusí vyhledat předchozí ID procesu a pokud selže, a to tak, že bude odpovídat předchozímu názvu procesu. Pokud se nenajde žádné shody nebo pokud má několik procesů stejný název, otevře se dialogové okno **připojit k procesu** , abyste mohli vybrat správný proces.

> [!NOTE]
> Příkaz znovu **připojit k procesu** je k dispozici od začátku v aplikaci Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Běžné scénáře ladění

V následující tabulce je uvedeno několik běžných scénářů ladění, které vám pomůžou určit, jestli se má použít **k procesu připojení** a jaký proces se má připojit, a to s odkazy na další pokyny, které jsou k dispozici. (Seznam není vyčerpávající.)

U některých typů aplikací, jako jsou aplikace pro univerzální aplikace pro Windows (UWP), se nepřipojujte přímo k názvu procesu, ale místo toho použijte možnost **ladit nainstalovaný balíček aplikace** v aplikaci Visual Studio (viz tabulka).

Aby ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute` . To můžete do kódu přidat automaticky tak, že propojíte s možností linkeru [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Pro ladění skriptů na straně klienta musí být ladění skriptů povoleno v prohlížeči. Pro ladění skriptu na straně klienta v Chrome vyberte **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge-chrom)** jako typ kódu a v závislosti na typu vaší aplikace možná budete muset zavřít všechny instance Chromu a spustit prohlížeč v režimu ladění (typ `chrome.exe --remote-debugging-port=9222` z příkazového řádku). V dřívějších verzích sady Visual Studio byla ladicí program skriptu pro Chrome **Webová sada**.

Chcete-li rychle vybrat běžící proces, ke kterému se chcete připojit, v aplikaci Visual Studio zadejte **klávesovou zkratku CTRL** + **+** + **P** a zadejte první písmeno názvu procesu.

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4,5 na serveru služby IIS|Použití vzdálených nástrojů a **připojení k procesu**|*w3wp.exe*|Viz [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) .|
|Vzdálené ladění ASP.NET Core na serveru služby IIS|Použití vzdálených nástrojů a **připojení k procesu**|*w3wp.exe* nebo *dotnet.exe*|Počínaje rozhraním .NET Core 3 se *w3wp.exe* proces používá pro výchozí [model hostování v aplikaci](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models). Nasazení aplikací najdete v tématu [publikování do služby IIS](/aspnet/core/host-and-deploy/iis/). Podrobnější informace najdete v tématu [vzdálené ladění ASP.NET Core na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach) .|
|Ladění skriptu na straně klienta na místním serveru IIS pro podporované typy aplikací |Použít **připojit k procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe* nebo *iexplore.exe*|Ladění skriptu musí být povoleno. Pro Chrome musíte také spustit Chrome v režimu ladění (typ `chrome.exe --remote-debugging-port=9222` z příkazového řádku) a v poli **připojit k** vyberte **JavaScript (Chrome)** .|
|Ladění aplikace v C#, Visual Basic nebo C++ na místním počítači|Použít buď standardní ladění (**F5**), nebo **připojit k procesu**|*\<appname>soubor. exe*|Ve většině scénářů použijte standardní ladění a **Nepřipojujte se k procesu**.|
|Vzdálené ladění desktopové aplikace pro Windows|Vzdálené nástroje|–| Viz téma [vzdálené ladění aplikace v C# nebo Visual Basic](../debugger/remote-debugging-csharp.md) nebo [vzdálené ladění aplikace C++](../debugger/remote-debugging-cpp.md) .|
|Ladění .NET Core v Linuxu|Použít **připojit k procesu**|*dotnet.exe* nebo jedinečný název procesu|Pokud chcete použít SSH, přečtěte si téma [vzdálené ladění .NET Core běžící na Linux pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Pro kontejnerové aplikace najdete informace v tématu [připojení k procesu běžícímu v kontejneru Docker](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container).|
|Ladění kontejnerové aplikace|Použít **připojit k procesu**|*dotnet.exe* nebo jedinečný název procesu|Viz [připojení k procesu běžícímu v kontejneru Docker](../debugger/attach-to-process-running-in-docker-container.md) .|
|Vzdálené ladění Pythonu v systému Linux|Použít **připojit k procesu**|*debugpy*|Viz téma [připojit se vzdáleně od nástrojů Pythonu](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools) .|
|Ladění aplikace v ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použít **připojit k procesu**|*iiexpress.exe*|To může být užitečné při rychlejším načítání aplikace, například (například) při profilaci. |
|Ladění dalších podporovaných typů aplikací v procesu serveru|Pokud je server vzdálený, použijte nástroje Remote Tools a **Připojte se k procesu** .|*chrome.exe*, *iexplore.exe* nebo jiné procesy|V případě potřeby použijte Sledování prostředků k usnadnění identifikace procesu. Viz téma [vzdálené ladění](../debugger/remote-debugging.md).|
|Vzdálené ladění aplikace pro univerzální aplikace pro Windows (UWP), OneCore, HoloLens nebo IoT|Ladit nainstalovaný balíček aplikace|–|Viz [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití příkazu **připojit k procesu** .|
|Ladění aplikace pro univerzální aplikace pro Windows (UWP), OneCore, HoloLens nebo IoT, kterou jste nespustili ze sady Visual Studio|Ladit nainstalovaný balíček aplikace|–|Viz [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití příkazu **připojit k procesu** .|

## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážky při zarážce) při připojování k procesu, aplikace musí přesně odpovídat vašemu místnímu zdroji a symbolům. To znamená, že ladicí program musí být schopný načíst správné [soubory symbolů (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Ve výchozím nastavení to vyžaduje sestavení ladění.

Pro scénáře vzdáleného ladění musíte mít zdrojový kód (nebo kopii zdrojového kódu), který je již otevřen v aplikaci Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako na místním počítači.

V některých místních scénářích ladění můžete ladit v aplikaci Visual Studio bez přístupu ke zdroji, pokud jsou v aplikaci k dispozici správné soubory symbolů. Ve výchozím nastavení to vyžaduje sestavení ladění. Další informace najdete v tématu [Určení symbolů a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Řešení chyb připojení

V některých scénářích může ladicí program potřebovat, aby mohl správně identifikovat typ kódu, který se má ladit. Pokud jsou hodnoty připojení správně nastavené (můžete zobrazit správný proces v seznamu **procesy k dispozici** ), ale ladicí program se nepodaří připojit, zkuste vybrat nejvhodnější typ připojení v seznamu **Typ připojení** , který může být potřeba, například když ladíte aplikaci pro Linux nebo Python. Pokud používáte výchozí typ připojení, můžete alternativně vybrat konkrétní typ kódu, ke kterému se chcete připojit, jak je popsáno dále v této části.

Pokud se ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu, ke kterým se může ladicí program připojit, jsou zobrazeny a vybrány v dialogovém okně [Vybrat typ kódu](../debugger/select-code-type-dialog-box.md) .

V některých případech se ladicí program může úspěšně připojit k jednomu typu kódu, ale ne k jinému typu kódu. K tomu obvykle dochází v těchto případech:

- Pokusíte se připojit k procesu, který je spuštěn ve vzdáleném počítači. Vzdálený počítač může mít nainstalované komponenty pro vzdálené ladění pro některé typy kódu, ale ne pro jiné.
- Pokusíte se připojit ke dvěma nebo více procesům pro přímé ladění databáze. Ladění SQL podporuje připojení pouze k jednomu procesu.

Pokud je ladicí program schopný připojit k některým typům kódu, ale ne ke všem, zobrazí se zpráva s identifikací, které typy se nepodařilo připojit.

Pokud se ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete pokračovat v ladění procesu. Budete moct ladit jenom typy kódu, které se úspěšně připojily. Nepřipojený kód v procesu bude stále spuštěn, ale nebudete moci nastavovat zarážky, zobrazovat data ani provádět jiné operace ladění tohoto kódu.

Chcete-li získat konkrétnější informace o tom, proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze k tomuto typu kódu.

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
