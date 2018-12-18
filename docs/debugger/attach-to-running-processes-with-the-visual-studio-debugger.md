---
title: Připojení ke spuštěným procesům pomocí ladicího programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 09/27/2018
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ed9670795e11b0d98b3703445450b468a93aa8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068458"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Připojení ladicího programu sady Visual Studio ke spuštěným procesům
Ladicí program sady Visual Studio můžete připojit ke spuštěnému procesu na místním nebo vzdáleném počítači. Poté, co je proces spuštěn, vybrat **ladění** > **připojit k procesu** nebo stiskněte klávesu **Ctrl**+**Alt** + **P** ve Visual Studiu a použít **připojit k procesu** dialogové okno připojit ladicí program k procesu.

Můžete použít **připojit k procesu** k ladění aplikace běžící na místních nebo vzdálených počítačích, ladění více procesů současně, ladění aplikace, které nebyly vytvořené v sadě Visual Studio nebo ladění libovolnou aplikaci, můžete se nepovedlo spustit ze sady Visual Studio s ladicí program se připojil. Například pokud máte spuštěnou aplikaci bez ladicího programu a k výjimce, můžete potom připojit ladicí program k procesu spuštění aplikace a spusťte ladění.

Informace o základní ladění v sadě Visual Studio najdete v tématu [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).

> [!TIP]
> Nejste si jistí, jestli se má použít **připojit k procesu** pro váš scénář ladění? Zobrazit [běžné scénáře ladění](#BKMK_Scenarios). 

##  <a name="BKMK_Attach_to_a_running_process"></a> Připojit ke spuštěnému procesu na místním počítači  

Chcete-li rychle znovu připojit k procesu připojen k dříve, přečtěte si téma [znovu připojit k procesu](#BKMK_reattach). 

Ladění procesu ve vzdáleném počítači, naleznete v tématu [připojit k procesu ve vzdáleném počítači](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Chcete-li se připojit k procesu v místním počítači:**  

1. V sadě Visual Studio, vyberte **ladění** > **připojit k procesu** (nebo stiskněte klávesu **Ctrl**+**Alt** + **P**) Chcete-li otevřít **připojit k procesu** dialogové okno.
  
   **Typ připojení** by mělo být nastavené **výchozí**. **Cíl připojení** by měl být název vašeho místního počítače. 
  
   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
2. V **procesy k dispozici** seznamu vyhledejte a vyberte proces nebo chcete připojit k procesům.  

   - Chcete-li rychle vyberte proces, zadejte její název nebo první písmena **procesy filtrování** pole. 
  
   - Pokud neznáte název procesu, projděte si seznam nebo se [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů. 
  
   >[!TIP]
   >Procesy můžete spouštět a zastavovat na pozadí při **připojit k procesu** dialogové okno je otevřená, takže seznam běžících procesů nemusí být vždy aktuální. Můžete vybrat **aktualizovat** kdykoli zobrazit aktuální seznam. 
  
3. V **připojit k** pole, ujistěte se, že je uveden typ kódu, plánujete-li ladit. Výchozí hodnota **automatické** nastavení funguje pro většinu typů aplikací. 
  
   Ručně vyberte typy kódu:
   1. Klikněte na tlačítko **vyberte**. 
   1. V **vybrat typ kódu** dialogovém okně vyberte **ladit tyto typy kódu**.
   1. Vyberte typy kódu, který chcete ladit.
   1. Vyberte **OK**.
  
4. Vyberte **připojit**.
  
>[!NOTE]
>Můžete být připojení k několika aplikacím pro ladění, ale současně je aktivní v ladicím programu jenom jedna aplikace. Můžete nastavit aktivní aplikace v sadě Visual Studio **umístění ladění** nástrojů nebo **procesy** okna.  

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Připojit k procesu ve vzdáleném počítači  

Můžete také vybrat vzdálený počítač v **připojit k procesu** dialogovém okně zobrazit seznam dostupných procesů spuštěných na tomto počítači a připojit se k jedné nebo více procesům pro ladění. Vzdálený ladicí program (*msvsmon.exe*) musí běžet na vzdáleném počítači. Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md). 

Podrobnější pokyny k ladění aplikací ASP.NET, které jsou nasazené do služby IIS najdete v tématu [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Připojit ke spuštěnému procesu ve vzdáleném počítači:**  

1. V sadě Visual Studio, vyberte **ladění** > **připojit k procesu** (nebo stiskněte klávesu **Ctrl**+**Alt** + **P**) Chcete-li otevřít **připojit k procesu** dialogové okno.
  
2. **Typ připojení** by měl být **výchozí** většině případů. V **cíl připojení** vyberte vzdáleného počítače pomocí jedné z následujících metod:

   - Vyberte šipku rozevíracího seznamu vedle **cíl připojení**a z rozevíracího seznamu vyberte název počítače.  
   - Zadejte název počítače **cíl připojení** pole.
      
     > [!NOTE]
     > Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste použít IP adresu a port adresu (například `123.45.678.9:4022`). 4022 je výchozím portem pro vzdálený ladicí program sady Visual Studio 2017 x64. Ostatní přiřazení portů vzdáleného ladicího programu, najdete v části [přiřazení portů vzdáleného ladicího programu](remote-debugger-port-assignments.md).  
      
   - Vyberte **najít** vedle **cíl připojení** otevřete okno **vzdálená připojení** dialogové okno. **Vzdálená připojení** dialogové okno obsahuje všechna zařízení, které jsou v místní podsíti, nebo přímo připojené k vašemu počítači. Možná budete muset [otevřete UDP port 3702](../debugger/remote-debugger-port-assignments.md) na serveru ke zjištění vzdáleného zařízení. Vyberte počítač nebo zařízení a potom klikněte na tlačítko **vyberte**. 
  
   > [!NOTE]
   > **Typ připojení** nastavení zůstává mezi relacemi ladění. **Cíl připojení** nastavení zůstává mezi relacemi ladění pouze v případě, že došlo k úspěšnému připojení ladění u, které cílí.

3. Klikněte na tlačítko **aktualizovat** k naplnění **procesy k dispozici** seznamu.
     
    >[!TIP]
    >Procesy můžete spouštět a zastavovat na pozadí při **připojit k procesu** dialogové okno je otevřená, takže seznam běžících procesů nemusí být vždy aktuální. Můžete vybrat **aktualizovat** kdykoli zobrazit aktuální seznam. 
     
4. V **procesy k dispozici** seznamu vyhledejte a vyberte proces nebo chcete připojit k procesům.  

   - Chcete-li rychle vyberte proces, zadejte její název nebo první písmena **procesy filtrování** pole. 
  
   - Pokud neznáte název procesu, projděte si seznam nebo se [běžné scénáře ladění](#BKMK_Scenarios) pro některé běžné názvy procesů. 
  
   - Chcete-li najít procesů spuštěných v rámci všech uživatelských účtů, vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.
      
     >[!NOTE]
     >Pokud se pokusíte připojit k procesu vlastněnému nedůvěryhodným uživatelským účtem, zobrazí se potvrzovací dialogové okno s upozorněním zabezpečení. Další informace najdete v části [upozornění zabezpečení: připojení k procesu vlastněnému nedůvěryhodným uživatelským může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
      
5. V **připojit k** pole, ujistěte se, že je uveden typ kódu, plánujete-li ladit. Výchozí hodnota **automatické** nastavení funguje pro většinu typů aplikací. 
  
   Ručně vyberte typy kódu:
   1. Klikněte na tlačítko **vyberte**. 
   1. V **vybrat typ kódu** dialogovém okně vyberte **ladit tyto typy kódu**.
   1. Vyberte typy kódu, který chcete ladit.
   1. Vyberte **OK**.
  
6. Vyberte **připojit**.
  
>[!NOTE]
>Můžete být připojení k několika aplikacím pro ladění, ale současně je aktivní v ladicím programu jenom jedna aplikace. Můžete nastavit aktivní aplikace v sadě Visual Studio **umístění ladění** nástrojů nebo **procesy** okna.  

V některých případech při ladění v relaci vzdálené plochy (Terminálová služba) **procesy k dispozici** seznamu nezobrazí všechny procesy k dispozici. Pokud používáte Visual Studio jako uživatel, který má omezený uživatelský účet, **procesy k dispozici** seznamu nezobrazí procesy spuštěné v relaci 0. Relace 0 se používá pro služby a ostatních serverové procesy, včetně *w3wp.exe*. Problém můžete vyřešit spuštěním [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pod účtem správce nebo spuštěním [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z konzoly serveru místo relace Terminálové služby. 

Pokud ani jeden z těchto řešení je možné, třetí možnost je připojit k procesu spuštěním `vsjitdebugger.exe -p <ProcessId>` z příkazového řádku Windows. Můžete určit pomocí id procesu *tlist.exe*. Chcete-li získat *tlist.exe*, stáhněte a nainstalujte ladění nástroje pro Windows, k dispozici na [soubory ke stažení sady WDK a WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Znovu připojit k procesu

Můžete rychle znovu připojit k procesům, které byly dříve přiřazená výběrem **ladění** > **znovu připojit k procesu** (**Shift** + **Alt**+**P**). Název procesu, když zvolíte tento příkaz, ladicí program se okamžitě pokusí připojit k naposledy procesy, které jste připojili při prvním pokusu odpovídat ID předchozího procesu a pokud se nezdaří, to provede spárováním odpovídajících na předchozí. Pokud nejsou nalezeny žádné shody, nebo pokud několik procesů mají stejný název, **připojit k procesu** dialogové okno se otevře, takže můžete vybrat správný proces.

> [!NOTE]
> **Znovu připojit k procesu** příkaz Novinky v sadě Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Běžné scénáře ladění

Při určování, jestli se má použít **připojit k procesu** a jaký proces se připojit k, v následující tabulce jsou uvedeny několik běžných ladění scénářů, s odkazy na další pokyny najdete tam, kde je k dispozici. (Seznam není vyčerpávající.) 

Pro některé typy aplikací, jako jsou aplikace pro univerzální aplikace pro Windows (UPW), nemusíte připojit přímo k názvu procesu, ale použít **ladit nainstalovaný balíček aplikace** nabídce Možnosti v sadě Visual Studio (viz tabulka).

Ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute`. Můžete přidat to do kódu automaticky díky propojení s [/assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute) – možnost linkeru.

Pro ladění skriptů na straně klienta musí být ladění skriptů povoleno v prohlížeči. Pro ladění skriptů na straně klienta v Chrome, zvolte **komponenty Webkit** psaní kódu a v závislosti na typu aplikace, je nutné zavřít všechny instance chromu a spuštění prohlížeče v režimu ladění (typ `chrome.exe --remote-debugging-port=9222` z příkazového řádku).

Chcete-li rychle vybrat běžící proces pro připojení, v sadě Visual Studio, zadejte **Ctrl**+**Alt**+**P**a pak zadejte první písmeno Název procesu.

|Scénář|Debug – metoda|Název procesu|Poznámky a odkazy|
|-|-|-|-|
|Vzdálené ladění ASP.NET 4 nebo 4.5 na serveru služby IIS|Pomocí nástrojů pro vzdálenou a **připojit k procesu**|*W3wp.exe*|Zobrazit [vzdálené ladění ASP.NET ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Vzdálené ladění ASP.NET Core na server služby IIS|Pomocí nástrojů pro vzdálenou a **připojit k procesu**|*dotnet.exe*|Nasazení aplikace, najdete v tématu [publikovat do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html). Ladění, naleznete v tématu [vzdálené ladění ASP.NET Core ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Ladění skriptů na straně klienta na místním serveru IIS, pro typy podporovaných aplikací |Použití **připojit k procesu**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, nebo *iexplore.exe*|Musí být povoleno ladění skriptu. Pro Chrome, je nutné spustit také Chrome v režimu ladění a vyberte **komponenty Webkit kód** v **připojit k** pole.|
|Ladění aplikací v jazyce C#, Visual Basic nebo C++ v místním počítači|Použijte buď [standardní ladění](../debugger/getting-started-with-the-debugger.md) nebo **připojit k procesu**|*\<název_aplikace > .exe*|Ve většině případů použijte standardní ladění a ne **připojit k procesu**.|
|Vzdálené ladění aplikace klasické pracovní plochy Windows|Vzdálené nástroje|Není k dispozici| Zobrazit [vzdáleného ladění aplikace v jazyce C# nebo Visual Basic](../debugger/remote-debugging-csharp.md) nebo [vzdálené ladění aplikací v C++](../debugger/remote-debugging-cpp.md)|
|Ladění aplikace ASP.NET v místním počítači po spuštění aplikace bez ladicího programu|Použití **připojit k procesu**|*iiexpress.exe*|To může být užitečné k vytvoření aplikace načíst rychleji, například (třeba) při profilování. |
|Ladit další typy aplikací podporované v procesu serveru|Pokud je vzdálený server, pomocí nástrojů pro vzdálenou, a **připojit k procesu**|*Chrome.exe*, *iexplore.exe*, nebo jiných procesů|V případě potřeby použijte k identifikaci procesu Sledování prostředků. Zobrazit [vzdálené ladění](../debugger/remote-debugging.md).|
|Vzdálené ladění aplikací pro univerzální aplikace Windows (UPW), OneCore, HoloLens a IoT aplikací|Ladit nainstalovaný balíček aplikace|Není k dispozici|Zobrazit [ladění balíčku nainstalované aplikace](debug-installed-app-package.md) namísto použití **připojit k procesu**|
|Ladění aplikací pro univerzální aplikace Windows (UPW), OneCore, HoloLens a IoT aplikací, které se nepovedlo spustit ze sady Visual Studio|Ladit nainstalovaný balíček aplikace|Není k dispozici|Zobrazit [ladění balíčku nainstalované aplikace](debug-installed-app-package.md) namísto použití **připojit k procesu**|  
  
## <a name="use-debugger-features"></a>Použití funkcí ladicího programu

Chcete-li používat úplné funkce ladicího programu sady Visual Studio (například zarážek) při připojování k procesu, aplikace musí přesně odpovídat, místní zdroje a symbolů. To znamená, ladicí program musí být schopný načíst správný [symbolů (PDB) soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění.

Pro scénáře vzdálené ladění musí mít zdrojový kód (nebo kopii zdrojového kódu) otevřen v sadě Visual Studio. Binární soubory kompilované aplikace na vzdáleném počítači musí pocházet ze stejného sestavení jako v místním počítači.

V některých místní ladění scénářích můžete ladit v sadě Visual Studio bez přístupu ke zdroji Pokud jsou k dispozici v aplikaci správný symbol soubory. Ve výchozím nastavení tento postup vyžaduje sestavení pro ladění. Další informace najdete v tématu [určit symboly a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Řešení potíží s chybami připojení  
 Pokud ladicí program připojí ke spuštěnému procesu, proces může obsahovat jeden nebo více typů kódu. Typy kódu k se může připojit ladicí program se zobrazí a jsou vybrány v **vybrat typ kódu** dialogové okno.  
  
 V některých případech můžete úspěšně připojit ladicí program k jednomu typu kódu, ale ne k jinému typu kódu. Tato situace může nastat, pokud se pokoušíte připojit k procesu, která běží na vzdáleném počítači. Vzdálený počítač může mít nainstalované pro některé typy kódu, ale nikoli pro jiné komponenty vzdáleného ladění. Může dojít také při pokusu o připojení ke dvěma nebo více procesům pro přímé ladění databáze. SQL ladění podporuje připojení pouze jednoho procesu.  
  
 Pokud ladicí program je možné se připojit k některým, ale ne všechny typy kódu, zobrazí se zpráva označující, ke kterým typům se nepodařilo připojit.  
  
 Pokud ladicí program úspěšně připojí k alespoň jednomu typu kódu, můžete přejít k ladění procesu. Budete moci ladit pouze typy kódu, které byly úspěšně připojeny. Nepřipojené kódu v procesu bude stále spuštěn, ale nebudete moci nastavit zarážky, zobrazit data ani provádět jiné operace ladění na tento kód.  
  
 Pokud potřebujete konkrétnější informace o Proč se ladicímu programu nepodařilo připojit k typu kódu, zkuste se znovu připojit pouze tomuto typu kódu.  
  
 **Získání konkrétních informací o Proč se nepodařilo připojit typ kódu:**  
  
1.  Odpojte od procesu. Na **ladění** nabídce vyberte možnost **Odpojit vše**.  
  
1.  Znovu připojte k procesu, vyberte pouze typ kódu, který se nepodařilo připojit.  
  
    1.  V **připojit k procesu** dialogového okna, vyberte v procesu **procesy k dispozici** seznamu.  
  
    2.  Vyberte **vyberte**.  
  
    3.  V **vybrat typ kódu** dialogovém okně vyberte **ladit tyto typy kódu** a typ kódu, který se nepodařilo připojit. Zrušte výběr jiných typů kódu.  
  
    4.  Vyberte **OK**.  
  
    5.  V **připojit k procesu** dialogu **připojit**.  
  
    Tentokrát připojení zcela selže a dostanete konkrétní chybovou zprávu.  
  
## <a name="see-also"></a>Viz také:  
 [Ladění více procesů](../debugger/debug-multiple-processes.md)   
 [Ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
 