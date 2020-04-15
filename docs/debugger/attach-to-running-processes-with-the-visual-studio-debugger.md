---
title: Připojit ke spuštěným procesům pomocí ladicího programu | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 04/14/2020
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
ms.openlocfilehash: 075f5b0df703e31ea265085f422567a4fb5298a4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385483"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům
Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu v místním nebo vzdáleném počítači. Po spuštění procesu vyberte **ladit** > **připojit k procesu** nebo stiskněte **Ctrl**+**Alt**+**P** v sadě Visual Studio a pomocí dialogového okna Připojit k **procesu** připojte ladicí program k procesu.

**Pomocí funkce Připojit k procesu** můžete ladit spuštěné aplikace v místních nebo vzdálených počítačích, ladit více procesů současně, ladit aplikace, které nebyly vytvořeny v sadě Visual Studio, nebo ladit všechny aplikace, které jste nezačali v sadě Visual Studio s připojeným ladicím programem. Například pokud používáte aplikaci bez ladicího programu a stiskl výjimku, pak můžete připojit ladicí program k procesu spuštění aplikace a začít ladění.

> [!TIP]
> Nejste si jisti, zda použít **připojit k procesu** pro váš scénář ladění? Viz [Běžné scénáře ladění](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Připojení ke spuštěnému procesu v místním počítači

Chcete-li rychle znovu připojit k procesu, ke kterému jste byli připojeni dříve, přečtěte si informace [o opětovném připojení k procesu](#BKMK_reattach).

Chcete-li ladit proces ve vzdáleném počítači, přečtěte si informace [o připojení k procesu ve vzdáleném počítači](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Chcete-li ladit proces .NET Core v kontejneru Linux Docker, přečtěte si informace [o připojení ke kontejneru Linux Docker](#BKMK_Linux_Docker_Attach).
::: moniker-end

**Připojení k procesu v místním počítači:**

1. V sadě Visual Studio vyberte **možnost Připojit** > **k procesu** (nebo stisknutím **klávesy Ctrl**+**Alt**+**P**) otevřete dialogové okno Připojit k **procesu.**

   **Typ připojení** by měl být nastaven na **výchozí**. **Cíl připojení** by měl být název místního počítače.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. V seznamu **Dostupné procesy** vyhledejte a vyberte proces nebo procesy, ke kterým chcete být připojeni.

   - Chcete-li proces rychle vybrat, zadejte jeho název nebo první písmeno do pole **Filtrovat procesy.**

   - Pokud neznáte název procesu, projděte seznam nebo se podívejte na [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů.

   >[!TIP]
   >Procesy lze spustit a zastavit na pozadí, když je otevřené dialogové okno **Připojit k procesu,** takže seznam spuštěných procesů nemusí být vždy aktuální. Chcete-li zobrazit aktuální seznam, můžete kdykoli vybrat možnost **Aktualizovat.**

3. V poli **Připojit k** se ujistěte, že je uveden typ kódu, který chcete ladit. Výchozí **automatické** nastavení funguje pro většinu typů aplikací.

   Ruční výběr typů kódu:
   1. Klepněte na **tlačítko Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte Ladit tyto typy **kódů**.
   1. Vyberte typy kódu, které chcete ladit.
   1. Vyberte **OK**.

4. Vyberte **Připojit**.

>[!NOTE]
>Můžete být připojeni k více aplikacím pro ladění, ale pouze jedna aplikace je aktivní v ladicím programu najednou. Aktivní aplikaci můžete nastavit v panelu nástrojů **umístění ladění** sady Visual Studio nebo v okně **Procesy.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Připojení k procesu ve vzdáleném počítači

Můžete také vybrat vzdálený počítač v dialogovém okně **Připojit k procesu,** zobrazit seznam dostupných procesů spuštěných v tomto počítači a připojit se k jednomu nebo více procesům pro ladění. Vzdálený ladicí program (*msvsmon.exe*) musí být spuštěn ve vzdáleném počítači. Další informace naleznete [v tématu Vzdálené ladění](../debugger/remote-debugging.md).

Podrobnější pokyny pro ladění aplikací ASP.NET, které byly nasazeny do služby IIS, naleznete [v tématu Vzdálené ladění ASP.NET ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Připojení ke spuštěnému procesu ve vzdáleném počítači:**

1. V sadě Visual Studio vyberte **možnost Připojit** > **k procesu** (nebo stisknutím **klávesy Ctrl**+**Alt**+**P**) otevřete dialogové okno Připojit k **procesu.**

2. **Typ připojení** by měl být **výchozí** pro většinu případů. V cílovém poli **Připojení** vyberte vzdálený počítač pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **cíle připojení**a vrozené mačká název počítače z rozevíracího seznamu.
   - Do pole Cíl **připojení** zadejte název počítače a stiskněte **enter**.

     Ověřte, zda aplikace Visual Studio přidá požadovaný port k názvu počítače, který se zobrazí ve formátu: ** \<název vzdáleného počítače>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu `123.45.678.9:4022`IP a portu (například). 4024 je výchozí port pro vzdálený ladicí program Visual Studio 2019 x64. Další přiřazení portů vzdáleného ladicího programu naleznete v [tématu Vzdálená přiřazení portů ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít adresu `123.45.678.9:4022`IP a portu (například). 4022 je výchozí port pro vzdálený ladicí program Visual Studio 2017 x64. Další přiřazení portů vzdáleného ladicího programu naleznete v [tématu Vzdálená přiřazení portů ladicího programu](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Kliknutím na tlačítko **Najít** vedle **cílového** pole Připojení otevřete dialogové okno **Vzdálená připojení.** Dialogové okno **Vzdálená připojení** obsahuje seznam všech zařízení, která jsou v místní podsíti nebo jsou přímo připojena k počítači. Chcete-li zjistit vzdálená zařízení, bude pravděpodobně nutné [otevřít port UDP 3702](../debugger/remote-debugger-port-assignments.md) na serveru. Vyberte požadovaný počítač nebo zařízení a klepněte na tlačítko **Vybrat**.

   > [!NOTE]
   > Nastavení **typu Připojení** přetrvává mezi relacemi ladění. Nastavení **cíle připojení** přetrvává mezi relacemi ladění pouze v případě, že u tohoto cíle došlo k úspěšnému připojení ladění.

3. Kliknutím na **Aktualizovat** naplníte seznam **Dostupné procesy.**

    >[!TIP]
    >Procesy lze spustit a zastavit na pozadí, když je otevřené dialogové okno **Připojit k procesu,** takže seznam spuštěných procesů nemusí být vždy aktuální. Chcete-li zobrazit aktuální seznam, můžete kdykoli vybrat možnost **Aktualizovat.**

4. V seznamu **Dostupné procesy** vyhledejte a vyberte proces nebo procesy, ke kterým chcete být připojeni.

   - Chcete-li proces rychle vybrat, zadejte jeho název nebo první písmeno do pole **Filtrovat procesy.**

   - Pokud neznáte název procesu, projděte seznam nebo se podívejte na [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů.

   - Chcete-li najít procesy spuštěné pod všemi uživatelskými účty, zaškrtněte políčko **Zobrazit procesy od všech uživatelů.**

     >[!NOTE]
     >Pokud se pokusíte připojit k procesu vlastněného nedůvěryhodným uživatelským účtem, zobrazí se potvrzení dialogového okna s upozorněním zabezpečení. Další informace naleznete v [tématu Upozornění zabezpečení: Připojení k procesu vlastněného nedůvěryhodným uživatelem může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte se k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. V poli **Připojit k** se ujistěte, že je uveden typ kódu, který chcete ladit. Výchozí **automatické** nastavení funguje pro většinu typů aplikací.

   Ruční výběr typů kódu:
   1. Klepněte na **tlačítko Vybrat**.
   1. V dialogovém okně **Vybrat typ kódu** vyberte Ladit tyto typy **kódů**.
   1. Vyberte typy kódu, které chcete ladit.
   1. Vyberte **OK**.

6. Vyberte **Připojit**.

>[!NOTE]
>Můžete být připojeni k více aplikacím pro ladění, ale pouze jedna aplikace je aktivní v ladicím programu najednou. Aktivní aplikaci můžete nastavit v panelu nástrojů **umístění ladění** sady Visual Studio nebo v okně **Procesy.**

V některých případech při ladění v relaci vzdálené plochy (Terminálová služba) seznam **procesů k dispozici** nezobrazí všechny dostupné procesy. Pokud používáte Visual Studio jako uživatel, který má omezený uživatelský účet, seznam **dostupných procesů** nezobrazí procesy, které jsou spuštěny v relaci 0. Relace 0 se používá pro služby a další serverové procesy, včetně *w3wp.exe*. Problém můžete vyřešit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spuštěním pod účtem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] správce nebo spuštěním z konzoly serveru namísto relace Terminálové služby.

Pokud ani jedno z těchto řešení není možné, třetí možností je `vsjitdebugger.exe -p <ProcessId>` připojit se k procesu spuštěním z příkazového řádku systému Windows. ID procesu můžete určit pomocí *souboru tlist.exe*. Chcete-li získat *soubor tlist.exe*, stáhněte a nainstalujte nástroje pro ladění pro systém Windows, které jsou k dispozici na [webu WDK a WinDbg ke stažení](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Připojení k procesu .NET Core běžícímu na Linuxu pomocí SSH

Další informace naleznete [v tématu Vzdálené ladění .NET Core běžící na Linuxu pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Připojení k procesu spuštěnému v kontejneru Linux Dockeru

Ladicí program sady Visual Studio můžete připojit k procesu spuštěnému v kontejneru Linux .NET Core Docker v místním nebo vzdáleném počítači pomocí dialogového okna **Připojit k procesu.**

> [!IMPORTANT]
> Chcete-li použít tuto funkci, musíte nainstalovat zatížení .NET Core Cross-Platform Development a mít místní přístup ke zdrojovému kódu.

**Připojení ke spuštěnému procesu v kontejneru Linux Dockeru:**

1. V sadě Visual Studio vyberte **možnost Ladění > Připojit k procesu (CTRL+ALT+P),** chcete-li otevřít dialogové okno Připojit k **procesu.**

![Připojit k nabídce Proces](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Nastavte **typ připojení** do **Dockeru (Linux Container).**
3. Vyberte **Najít...** a nastavte **cíl připojení** pomocí dialogového okna Vybrat **kontejner Dockeru.**

    Proces kontejneru Dockeru můžete ladit místně nebo vzdáleně.
    
    **Chcete-li ladit proces kontejneru Dockermístně:**
    1. Nastavte **hostitele cli Dockeru** na **místní počítač**.
    1. Vyberte spuštěný kontejner, ke kterému chcete připojit ze seznamu, a stiskněte **tlačítko OK**.
    
    ![Vybrat nabídku kontejnerů Dockeru](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Chcete-li vzdáleně ladit proces kontejneru Dockeru:**
    
    > [!NOTE] 
    > Existují dvě možnosti pro vzdálené připojení ke spuštěnému procesu v kontejneru Dockeru. První možnost, použití SSH, je ideální, pokud nemáte v místním počítači nainstalované nástroje Dockeru.  Pokud máte nástroje Dockeru nainstalované místně a máte daemon dockeru, který je nakonfigurovaný pro přijímání vzdálených požadavků, vyzkoušejte druhou možnost pomocí daemonu Dockeru.

    1. ***Připojení ke vzdálenému počítači přes SSH:***
        1. Chcete-li se připojit ke vzdálenému systému, vyberte možnost **Přidat.**<br/>
        ![Připojení ke vzdálenému systému](../debugger/media/connect-remote-system.png "Připojení ke vzdálenému systému")
        1. Vyberte spuštěný kontejner, ke kterému se chcete připojit po úspěšném připojení k SSH nebo daemonu a stiskněte **OK**.

    
    1. ***Nastavení cíle na vzdálený kontejner, ve kterých běží proces prostřednictvím [daemonu Dockeru](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Zadejte adresu daemonu (tj. přes TCP, IP, atd.) v **hostiteli Dockeru (Volitelné)** a klikněte na odkaz aktualizace.
        1. Vyberte spuštěný kontejner, ke kterému se chcete připojit po úspěšném připojení ke daemonu, a stiskněte **tlačítko OK**.

4. Vyberte odpovídající proces kontejneru ze seznamu **dostupných procesů** a vyberte **Připojit,** chcete-li spustit ladění procesu kontejneru jazyka C# v sadě Visual Studio!

    ![Dokončená nabídka Připojit Dockeru](../debugger/media/docker-attach-complete.png "Dokončena linuxová nabídka připojení Dockeru")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Připojení k procesu spuštěného v kontejneru Windows Dockeru

Ladicí program sady Visual Studio můžete připojit k procesu spuštěnému v kontejneru Windows Docker u místního počítače pomocí dialogového okna **Připojit k procesu.**

> [!IMPORTANT]
> Chcete-li tuto funkci používat s procesem .NET Core, musíte nainstalovat úlohu vývoje napříč platformami .NET Core a mít místní přístup ke zdrojovému kódu.

**Připojení ke spuštěnému procesu v kontejneru Windows Dockeru:**

1. V sadě Visual Studio vyberte **možnost Ladění > připojit se k procesu** (nebo **CTRL+ALT+P),** chcete-li otevřít dialogové okno **Připojit k procesu.**

   ![Připojit k nabídce Proces](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Nastavte **typ připojení** do **Dockeru (Kontejner Windows).**
3. Vyberte **Najít...** a nastavte **cíl připojení** pomocí dialogového okna Vybrat **kontejner Dockeru.**

    > [!IMPORTANT]
    > Cílový proces musí mít stejnou architekturu procesoru jako kontejner Docker Windows, na který běží.
    
   Nastavení cíle na vzdálený kontejner přes SSH je momentálně nedostupné a lze provést pouze pomocí daemondockeru.
    
    ***Nastavení cíle na vzdálený kontejner, ve kterých běží proces prostřednictvím [daemonu Dockeru](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Zadejte adresu daemonu (tj. přes TCP, IP, atd.) v **hostiteli Dockeru (Volitelné)** a klikněte na odkaz aktualizace. 

    1. Vyberte spuštěný kontejner, ke kterému se chcete připojit po úspěšném připojení ke daemonu, a zvolte OK.
    
4. Vyberte odpovídající proces kontejneru ze seznamu **dostupných procesů** a vyberte **Připojit,** chcete-li spustit ladění procesu kontejneru Jazyka C#.

    ![Dokončená nabídka Připojit Dockeru](../debugger/media/docker-attach-complete-windows.png "Dokončená nabídka Připojit Windows Docker")
    

5.  Zvolte odpovídající proces kontejneru ze seznamu dostupných procesů a zvolte **Připojit,** chcete-li spustit ladění procesu kontejneru Jazyka C#.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Opětovné připojení k procesu

K procesům, ke kterým jste byli dříve připojeni, se můžete rychle připojit tak, že zvolíte **Ladění** > **opětovného připojení ke zpracovat** **(Shift**+**Alt**+**P**). Pokud zvolíte tento příkaz, ladicí program se okamžitě pokusí připojit k posledním procesům, ke kterým jste připojeni, tím, že se nejprve pokusí porovnat předchozí ID procesu a pokud se nezdaří, porovnáním s předchozím názvem procesu. Pokud nejsou nalezeny žádné shody nebo pokud má několik procesů stejný název, otevře se dialogové okno **Připojit k procesu,** abyste mohli vybrat správný proces.

> [!NOTE]
> Příkaz **Znovu připojit k procesu** je k dispozici od spuštění v sadě Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Běžné scénáře ladění

Chcete-li zjistit, zda použít **připojit k procesu** a jaký proces připojit k, v následující tabulce je uvedeno několik běžných scénářů ladění s odkazy na další pokyny, pokud jsou k dispozici. (Seznam není vyčerpávající.)

U některých typů aplikací, jako jsou aplikace Universal App (UPW), se nepřipojujete přímo k názvu procesu, ale místo toho použijte možnost **nabídky Balíček aplikace Ladění** v sadě Visual Studio (viz tabulka).

Pro ladicí program připojit ke kódu napsanému v jazyce C++, kód musí vyzařovat `DebuggableAttribute`. Můžete přidat do kódu automaticky propojením s parametrem [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) linker.

Pro ladění skriptů na straně klienta musí být v prohlížeči povoleno ladění skriptů. Pro ladění skriptu na straně klienta v Chromu zvolte jako typ kódu **JavaScript (Chrome)** nebo **JavaScript (Microsoft Edge - Chromium)** a v závislosti na typu `chrome.exe --remote-debugging-port=9222` aplikace možná budete muset zavřít všechny instance Chromu a spustit prohlížeč v režimu ladění (typ z příkazového řádku). V dřívějších verzích sady Visual Studio byl ladicí program skriptu pro Chrome **webovou sadou**.

Chcete-li rychle vybrat spuštěný proces, ke kterému chcete připojit, zadejte v sadě Visual Studio **kombinaci**+**Alt**+**P**a zadejte první písmeno názvu procesu.

|Scénář|Metoda ladění|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Použití vzdálených nástrojů a **připojení ke zpracovat**|*w3wp.exe*|Viz [Vzdálené ladění ASP.NET ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Vzdálené ladění ASP.NET jádra na serveru služby IIS|Použití vzdálených nástrojů a **připojení ke zpracovat**|*w3wp.exe* nebo *dotnet.exe*|Počínaje rozhraním .NET Core 3 se proces *w3wp.exe* používá pro výchozí [model hostování v aplikaci](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models). Informace o nasazení aplikací najdete v tématu [Publikování ve službách IIS](/aspnet/core/host-and-deploy/iis/). Podrobnější informace naleznete v [tématu Vzdálené ladění ASP.NET jádra ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Ladění skriptu na straně klienta na místním serveru služby IIS pro podporované typy aplikací |Použít **připojit k procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe*nebo *iexplore.exe*|Ladění skriptů musí být povoleno. V chromu musíte chrome spustit také v `chrome.exe --remote-debugging-port=9222` ladicím režimu (zadejte text z příkazového řádku) a v poli **Připojit k** vybrat **JavaScript (Chrome).**|
|Ladění aplikace C#, Visual Basic nebo C++ v místním počítači|Použijte standardní ladění (**F5**) nebo **připojit k procesu**|*\<název aplikace>.exe*|Ve většině scénářů použijte standardní ladění a **nepřipojit k procesu**.|
|Vzdálené ladění aplikace pro plochu windows|Vzdálené nástroje|–| Viz [Vzdálené ladění aplikace Jazyka C# nebo Visual Basic](../debugger/remote-debugging-csharp.md) nebo Vzdálené ladění aplikace [c++](../debugger/remote-debugging-cpp.md)|
|Ladění .NET Core na Linuxu|Použít **připojit k procesu**|*dotnet.exe*|Informace o použití SSH naleznete [v tématu Vzdálené ladění .NET Core běžící na Linuxu pomocí SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Ladění aplikace ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použít **připojit k procesu**|*iiexpress.exe*|To může být užitečné, aby se vaše aplikace načítat rychleji, například (například) při profilování. |
|Ladění jiných podporovaných typů aplikací v procesu serveru|Pokud je server vzdálený, použijte vzdálené nástroje a **připojit k procesu**|*chrome.exe*, *iexplore.exe*nebo jiné procesy|V případě potřeby použijte program Sledování prostředků k identifikaci procesu. Viz [Vzdálené ladění](../debugger/remote-debugging.md).|
|Vzdálené ladění univerzální aplikace pro Windows (UPW), OneCore, HoloLens nebo aplikace IoT|Ladění nainstalovaného balíčku aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití připojení k **procesu**|
|Ladění univerzální aplikace pro Windows (UPW), OneCore, HoloLens nebo aplikace IoT, kterou jste nespustili z Visual Studia|Ladění nainstalovaného balíčku aplikace|–|Viz [Ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md) namísto použití připojení k **procesu**|

## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Chcete-li použít úplné funkce ladicího programu sady Visual Studio (jako je stisknutí zarážek) při připojování k procesu, aplikace musí přesně odpovídat místnímu zdroji a symbolům. To znamená, že ladicí program musí být schopen načíst správné [soubory symbol (.pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Ve výchozím nastavení to vyžaduje sestavení ladění.

Pro scénáře vzdáleného ladění musíte mít zdrojový kód (nebo kopii zdrojového kódu) již otevřený v sadě Visual Studio. Zkompilované binární soubory aplikací ve vzdáleném počítači musí pocházet ze stejného sestavení jako v místním počítači.

V některých místních scénářích ladění můžete ladit v sadě Visual Studio bez přístupu ke zdroji, pokud jsou v aplikaci k dispozici správné soubory symbolů. Ve výchozím nastavení to vyžaduje sestavení ladění. Další informace naleznete [v tématu Specify symbol and source files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a>Poradce při potížích s chybami připojení
 Když ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódů, ke ninidátu se mohou připojit, se zobrazí a vyberou v dialogovém okně **Vybrat typ kódu.**

 V některých případech ladicí program lze úspěšně připojit k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, který je spuštěn ve vzdáleném počítači. Ve vzdáleném počítači mohou být nainstalovány součásti vzdáleného ladění pro některé typy kódů, ale ne pro jiné. Může také dojít, pokud se pokusíte připojit k dva nebo více procesů pro přímé ladění databáze. Ladění SQL podporuje připojení pouze k jednomu procesu.

 Pokud ladicí program je schopen připojit k některé, ale ne všechny typy kódu, zobrazí se zpráva identifikující typy, které se nepodařilo připojit.

 Pokud ladicí program úspěšně připojí alespoň jeden typ kódu, můžete pokračovat v ladění procesu. Budete moci ladit pouze typy kódu, které byly úspěšně připojeny. Nepřipojený kód v procesu bude stále spuštěn, ale nebudete moci nastavit zarážky, zobrazit data nebo provádět jiné operace ladění v tomto kódu.

 Pokud chcete konkrétnější informace o tom, proč se ladicí program nepodařilo připojit k typu kódu, zkuste znovu připojit pouze tento typ kódu.

 **Chcete-li získat konkrétní informace o tom, proč se nepodařilo připojit typ kódu:**

1. Odpojte se od procesu. V nabídce **Ladění** vyberte **odpojit vše**.

1. Znovu připojit k procesu, výběr pouze typ kódu, který se nepodařilo připojit.

    1. V dialogovém okně **Připojit k procesu** vyberte proces v seznamu **Dostupné procesy.**

    2. Vyberte **Vybrat**.

    3. V dialogovém okně **Vybrat typ kódu** vyberte ladit tyto typy **kódů** a typ kódu, který se nepodařilo připojit. Odznačte ostatní typy kódů.

    4. Vyberte **OK**.

    5. V dialogovém okně **Připojit k procesu** vyberte **Připojit**.

    Tentokrát se připojení zcela nezdaří a zobrazí se konkrétní chybová zpráva.

## <a name="see-also"></a>Viz také

- [Ladění více procesů](../debugger/debug-multiple-processes.md)
- [Ladění just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
