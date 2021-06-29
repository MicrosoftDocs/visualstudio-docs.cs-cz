---
title: Ladění cloudové služby nebo virtuálního počítače Azure
description: Ladění cloudové služby nebo virtuálního počítače v Visual Studio
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 8669e4636be28d6462c6658a54fc818bae577905
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997667"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Ladění cloudové služby nebo virtuálního počítače Azure v Visual Studio

Visual Studio nabízí různé možnosti ladění cloudových služeb Azure a virtuálních počítačů.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby na místním počítači

Můžete ušetřit čas a peníze pomocí emulátoru Azure Compute k ladění cloudové služby na místním počítači. Když službu místně ladíte před nasazením, můžete zvýšit spolehlivost a výkon, aniž byste platili za výpočetní čas. K některým chybám ale může dojít pouze při spuštění cloudové služby v samotném Azure. Tyto chyby můžete ladit, pokud povolíte vzdálené ladění při publikování služby a pak připojíte ladicí program k instanci role.

Emulátor simuluje Azure Compute a běží ve vašem místním prostředí, abyste mohli otestovat a ladit cloudovou službu před nasazením. Emulátor zpracovává životní cyklus instancí rolí a poskytuje přístup k simulovaném prostředkům, jako je místní úložiště. Když službu ladíte nebo spouštíte z Visual Studio, automaticky spustí emulátor jako aplikaci na pozadí a pak službu nasadí do emulátoru. K zobrazení služby při spuštění v místním prostředí můžete použít emulátor. Můžete spustit plnou verzi nebo expresní verzi emulátoru. (Počínaje Azure 2.3 je výchozí expresní verze emulátoru.) Další [informace najdete v tématu Místní spuštění a ladění cloudové služby pomocí emulátoru Express.](vs-azure-tools-emulator-express-debug-run.md)

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby na místním počítači

1. Na řádku nabídek vyberte **Ladit spustit** ladění a  >   spusťte projekt cloudové služby Azure. Alternativně můžete stisknout klávesu F5. Zobrazí se zpráva, že se spouští emulátor výpočtů. Po spuštění emulátoru to potvrdí ikona na hlavním panelu systému.

    ![Emulátor Azure na hlavním panelu systému](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Otevřete místní nabídku pro ikonu Azure v oznamovací oblasti a vyberte Zobrazit uživatelské rozhraní emulátoru výpočtů a zobrazte uživatelské rozhraní **emulátoru výpočtů.**

    V levém podokně uživatelského rozhraní se zobrazují služby, které jsou aktuálně nasazené do emulátoru výpočetních prostředků, a instance rolí, ve které je každá služba spuštěná. Službu nebo role můžete zvolit tak, aby se v pravém podokně zobrazují informace o životním cyklu, protokolování a diagnostice. Pokud fokus dáte do horního okraje zahrnutých oken, rozbalí se, aby vyplnil pravé podokno.

3. Projdete aplikaci výběrem příkazů v **nabídce Ladit** a nastavením zarážek v kódu. Při krokech aplikace v ladicím programu se podokna aktualizují aktuálním stavem aplikace. Když zastavíte ladění, nasazení aplikace se odstraní. Pokud vaše aplikace obsahuje webovou roli a nastavili jste vlastnost Akce spuštění na spuštění webového prohlížeče, Visual Studio spustí webovou aplikaci v prohlížeči. Pokud změníte počet instancí role v konfiguraci služby, musíte zastavit cloudovou službu a pak restartovat ladění, abyste mohli ladit tyto nové instance role.

    > [!NOTE]
    > Když zastavíte spuštění nebo ladění služby, místní emulátor výpočtů a emulátor úložiště se nezastaví. Musíte je explicitně zastavit v oznamovací oblasti.

## <a name="debug-a-cloud-service-in-azure"></a>Ladění cloudové služby v Azure

Pokud chcete ladit cloudovou službu ze vzdáleného počítače, musíte tuto funkci povolit explicitně při nasazení cloudové služby, aby se na virtuálních počítačích, na které běží instance rolí, nainstalovaly požadované služby (například msvsmon.exe). Pokud jste při publikování služby nepomožňovali vzdálené ladění, musíte službu znovu publikovat s povoleným vzdáleným laděním.

Pokud povolíte vzdálené ladění pro cloudovou službu, nebude se vykazovat snížený výkon ani se vám za něj nesnížují další poplatky. Nepoužívejte vzdálené ladění v produkční službě, protože to může nepříznivě ovlivnit klienty, kteří službu používají.

> [!NOTE]
> Při publikování cloudové služby z Visual Studio můžete nástroj **IntelliTrace** povolit pro všechny role v této službě, které cílí na .NET Framework 4 nebo .NET Framework 4.5. Pomocí nástroje **IntelliTrace** můžete zkoumat události, ke kterým došlo v instanci role v minulosti, a reprodukovat kontext od této doby. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a Visual Studio a](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) Použití [IntelliTrace.](../debugger/intellitrace.md)

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Povolení vzdáleného ladění pro cloudovou službu

1. Otevřete místní nabídku pro projekt Azure a pak vyberte **Publish (Publikovat).**

2. Vyberte **pracovní prostředí a** **konfiguraci** Ladění.

    Toto je jenom vodítko. Testovací prostředí můžete spouštět v produkčním prostředí. Pokud ale povolíte vzdálené ladění v produkčním prostředí, může to mít nepříznivý vliv na uživatele. Můžete zvolit konfiguraci verze, ale konfigurace Ladění usnadňuje ladění.

    ![Zvolte konfiguraci ladění.](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Postupujte podle obvyklých kroků, ale na **kartě** Upřesnit nastavení zaškrtněte políčko Povolit vzdálený ladicí program pro všechny **role.**

    ![Konfigurace ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Připojení ladicího programu ke cloudové službě v Azure

1. V Průzkumník serveru rozbalte uzel pro vaši cloudovou službu.

2. Otevřete místní nabídku pro instanci role nebo role, ke které chcete připojit, a pak vyberte Attach Debugger (Připojit **ladicí program).**

    Při ladění role se ladicí Visual Studio připojí ke každé instanci této role. Ladicí program se přeruší na zarážce první instance role, která spouští tento řádek kódu a splňuje všechny podmínky této zarážky. Pokud ladíte instanci, ladicí program se připojí pouze k této instanci a přeruší se na zarážce pouze v případě, že konkrétní instance spustí tento řádek kódu a splňuje podmínky zarážky.

    ![Připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Jakmile se ladicí program připojí k instanci, ladění jako obvykle. Ladicí program se automaticky připojí k příslušnému hostitelskému procesu pro vaši roli. V závislosti na tom, jaká je role, se ladicí program připojí w3wp.exe, WaWorkerHost.exe nebo WaIISHost.exe. Pokud chcete ověřit proces, ke kterému je ladicí program připojený, rozbalte uzel instance v Průzkumník serveru. Další [informace o procesech](/archive/blogs/kwill/windows-azure-role-architecture) Azure najdete v tématu Architektura rolí Azure.

    ![Dialogové okno Vybrat typ kódu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Pokud chcete identifikovat procesy, ke kterým je ladicí program připojený, vyberte na řádku nabídek Ladit procesy systému Windows a otevřete  >    >   **dialogové** okno Procesy. (Klávesnice: Ctrl+Alt+Z) Pokud chcete odpojit konkrétní proces, otevřete jeho místní nabídku a pak vyberte **Odpojit proces.** Nebo vyhledejte uzel instance v Průzkumník serveru, vyhledejte proces, otevřete jeho místní nabídku a pak vyberte **Odpojit proces**.

    ![Ladění procesů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Při vzdáleném ladění se vyhněte dlouhým zastavením na zarážkách. Azure považuje proces, který je zastavený déle než několik minut, za nereagující a přestane do této instance odesílat provoz. Pokud zastavíte příliš dlouho, msvsmon.exe odpojí od procesu.

Pokud chcete ladicí program odpojit od všech procesů ve vaší instanci nebo roli, otevřete místní nabídku pro roli nebo instanci, kterou ladíte, a pak vyberte **Odpojit ladicí program.**

## <a name="limitations-of-remote-debugging-in-azure"></a>Omezení vzdáleného ladění v Azure

V sadě Azure SDK 2.3 má vzdálené ladění následující omezení:

* Když je povolené vzdálené ladění, nemůžete publikovat cloudovou službu, ve které má jakákoli role více než 25 instancí.
* Ladicí program používá porty 30400 až 30424, 31400 až 31424 a 32400 až 32424. Pokud se pokusíte použít některý z těchto portů, nebudete moct publikovat službu a v protokolu aktivit Pro Azure se zobrazí jedna z následujících chybových zpráv:

  * Chyba při ověřování souboru .cscfg proti souboru .csdef
    Rozsah vyhrazených portů pro koncový bod Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector role role se překrývá s již definovaným portem nebo rozsahem.
  * Přidělení selhalo. Zkuste to znovu později, zkuste snížit velikost virtuálního počítače nebo počet instancí rolí nebo zkuste nasazení do jiné oblasti.

## <a name="debugging-azure-virtual-machines"></a>Ladění virtuálních počítačů Azure

Programy, které běží na virtuálních počítačích Azure, můžete ladit pomocí Průzkumník serveru v Visual Studio. Když na virtuálním počítači Azure povolíte vzdálené ladění, Azure na tento virtuální počítač nainstaluje rozšíření vzdáleného ladění. Pak se můžete připojit k procesům na virtuálním počítači a ladit je běžným způsobem.

> [!NOTE]
> Virtuální počítače vytvořené prostřednictvím zásobníku Azure Resource Manageru je možné vzdáleně ladit pomocí Průzkumníka cloudu v Visual Studio 2015. Další informace najdete v tématu [Správa prostředků Azure pomocí Průzkumníka cloudu.](vs-azure-tools-resources-managing-with-cloud-explorer.md)

### <a name="to-debug-an-azure-virtual-machine"></a>Ladění virtuálního počítače Azure

1. V Průzkumník serveru rozbalte uzel Virtual Machines a vyberte uzel virtuálního počítače, který chcete ladit.

2. Otevřete místní nabídku a vyberte **Povolit ladění.** Když se zobrazí dotaz, jestli opravdu chcete povolit ladění na virtuálním počítači, vyberte **Ano.**

    Azure nainstaluje na virtuální počítač rozšíření vzdáleného ladění, aby bylo možné povolit ladění.

    ![Příkaz pro povolení ladění virtuálního počítače](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po dokončení instalace rozšíření vzdáleného ladění otevřete místní nabídku virtuálního počítače a vyberte **Připojit ladicí program...**

    Azure načte seznam procesů na virtuálním počítači a zobrazí je v **dialogovém okně Připojit k** procesu.

    ![Připojit příkaz ladicího programu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. V dialogovém **okně Připojit** k  procesu výběrem možnosti Vybrat omezte seznam výsledků tak, aby se zobrazují pouze typy kódu, které chcete ladit. Můžete ladit 32bitový nebo 64bitový spravovaný kód, nativní kód nebo obojí.

    ![Dialogové okno Vybrat typ kódu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Zvolte procesy, které chcete na virtuálním počítači ladit, a pak vyberte **Připojit.** Například můžete zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci na virtuálním počítači. Další informace najdete v tématu [ladění jednoho nebo více procesů v aplikaci Visual Studio a v](../debugger/debug-multiple-processes.md) [architektuře rolí Azure](/archive/blogs/kwill/windows-azure-role-architecture) .

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Vytvoření webového projektu a virtuálního počítače pro ladění

Před publikováním projektu Azure může být užitečné ho otestovat v obsaženém prostředí, které podporuje scénáře ladění a testování a kde můžete instalovat programy pro testování a monitorování. Jedním ze způsobů, jak tyto testy spustit, je vzdálené ladění aplikace na virtuálním počítači.

Projekty Visual Studio ASP.NET nabízejí možnost vytvořit praktický virtuální počítač, který můžete použít pro testování aplikací. Virtuální počítač zahrnuje běžně potřebné koncové body, jako je PowerShell, Vzdálená plocha a WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Vytvoření webového projektu a virtuálního počítače pro ladění

1. V aplikaci Visual Studio vytvořte novou webovou aplikaci v ASP.NET.

2. V dialogovém okně Nový projekt ASP.NET v části Azure v rozevíracím seznamu vyberte **virtuální počítač** . Ponechejte zaškrtnuté políčko **vytvořit vzdálené prostředky** . Pokračujte výběrem **OK** .

    Zobrazí se dialogové okno **vytvořit virtuální počítač v Azure** .

    ![Dialogové okno vytvořit webový projekt v ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Pokud ještě nejste přihlášení, zobrazí se výzva, abyste se přihlásili ke svému účtu Azure.

3. Zvolte různá nastavení virtuálního počítače a pak vyberte **OK**. Další informace najdete v tématu [Virtual Machines](/azure/virtual-machines/) .

    Název, který zadáte jako název DNS, bude název virtuálního počítače.

    ![Dialogové okno vytvořit virtuální počítač v Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure vytvoří virtuální počítač a pak zřídí a nakonfiguruje koncové body, jako je třeba Vzdálená plocha a Nasazení webu.

4. Jakmile je virtuální počítač plně nakonfigurovaný, vyberte uzel virtuálního počítače v Průzkumník serveru.

5. Otevřete kontextovou nabídku a vyberte možnost **Povolit ladění**. Pokud se zobrazí dotaz, jestli chcete povolit ladění na virtuálním počítači, vyberte **Ano**.

    Azure do virtuálního počítače nainstaluje rozšíření pro vzdálené ladění, aby bylo možné ladění povolit.

    ![Příkaz pro povolení ladění virtuálních počítačů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publikujte projekt tak, jak je uvedeno v tématu [Postupy: nasazení webového projektu pomocí One-Click publikování v aplikaci Visual Studio](/previous-versions/aspnet/dd465337(v=vs.110)). Vzhledem k tomu, že chcete ladit na virtuálním počítači, vyberte na stránce **Nastavení** v průvodci **publikováním webu** možnost **ladit** jako konfiguraci. Tím zajistíte, že jsou k dispozici symboly kódu při ladění.

    ![Publish settings (Nastavení publikování)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. V **možnostech publikování souboru** vyberte možnost **odebrat další soubory v cílovém umístění** , pokud již projekt byl nasazen v dřívějším čase.

8. Po publikování projektu vyberte v místní nabídce virtuálního počítače v Průzkumník serveru **připojit ladicí program...**

    Azure získá seznam procesů na virtuálním počítači a zobrazí je v dialogovém okně **připojit k procesu** .

    ![Příkaz připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. V dialogovém okně **připojit k procesu** vyberte **Vybrat** , chcete-li omezit seznam výsledků tak, aby se zobrazily pouze typy kódu, který chcete ladit. Můžete ladit 32-bit nebo 64 spravovaný kód, nativní kód nebo obojí.

    ![Dialog Vybrat typ kódu – dialogové okno](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Vyberte procesy, které chcete na virtuálním počítači ladit, a pak vyberte **připojit**. Například můžete zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci na virtuálním počítači. Další informace najdete v tématu [ladění jednoho nebo více procesů v aplikaci Visual Studio](../debugger/debug-multiple-processes.md) .

## <a name="next-steps"></a>Další kroky

* Pomocí **IntelliTrace** můžete shromažďovat protokol volání a událostí ze serveru vydaných verzí. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Pomocí **Azure Diagnostics** můžete protokolovat podrobné informace z kódu spuštěného v rámci rolí, ať už role běží ve vývojovém prostředí nebo v Azure. Viz [shromažďování dat protokolování pomocí Azure Diagnostics](/azure/cloud-services/cloud-services-dotnet-diagnostics).