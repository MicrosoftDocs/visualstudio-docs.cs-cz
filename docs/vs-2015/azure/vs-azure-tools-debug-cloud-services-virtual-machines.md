---
title: Ladění cloudové služby Azure nebo virtuálního počítače
description: Ladění cloudové služby nebo virtuálního počítače v aplikaci Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: ac1f47d3daabf800a308d73727f750f971ace4e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919168"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Ladění cloudové služby Azure nebo virtuálního počítače v aplikaci Visual Studio

Visual Studio nabízí různé možnosti pro ladění cloudových služeb a virtuálních počítačů Azure.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby v místním počítači

Můžete ušetřit čas a peníze pomocí emulátoru služby COMPUTE Azure pro ladění cloudové služby na místním počítači. Laděním služby v místním prostředí před tím, než je nasadíte, můžete zvýšit spolehlivost a výkon bez placení za výpočetní čas. K nějakým chybám ale může docházet jenom při spuštění cloudové služby v Azure. Tyto chyby můžete ladit, pokud povolíte vzdálené ladění při publikování služby a pak připojíte ladicí program k instanci role.

Emulátor simuluje službu Azure COMPUTE a spustí ji v místním prostředí, abyste mohli otestovat a ladit cloudovou službu před tím, než ji nasadíte. Emulátor zpracovává životní cyklus instancí rolí a poskytuje přístup k simulovaným prostředkům, například k místnímu úložišti. Při ladění nebo spuštění služby ze sady Visual Studio automaticky spustí emulátor jako aplikaci na pozadí a potom nasadí vaši službu do emulátoru. Emulátor můžete použít k zobrazení služby, když běží v místním prostředí. Můžete spustit úplnou verzi nebo expresní verzi emulátoru. (Počínaje verzí Azure 2,3 je expresní verze emulátoru výchozí.) [Místní spuštění a ladění cloudové služby najdete v článku použití emulátoru Express](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby v místním počítači

1. Na panelu nabídek vyberte možnost **ladit**, **Spustit ladění** a spusťte projekt cloudové služby Azure. Alternativně můžete stisknout klávesu F5. Zobrazí se zpráva, že se spouští emulátor Compute. Po spuštění emulátoru se ikona na hlavním panelu systému potvrdí.

    ![Emulátor Azure na hlavním panelu systému](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Zobrazte uživatelské rozhraní pro emulátor služby COMPUTE tak, že otevřete místní nabídku ikony Azure v oznamovací oblasti a pak vyberete **Zobrazit uživatelské rozhraní emulátoru výpočtů**.

    V levém podokně uživatelského rozhraní se zobrazují služby, které jsou aktuálně nasazené do emulátoru služby COMPUTE a instance rolí, na kterých je každá služba spuštěná. Můžete zvolit službu nebo role pro zobrazení životního cyklu, protokolování a diagnostické informace v pravém podokně. Pokud umístíte fokus do horního okraje zahrnutého okna, rozbalí se, aby se naplnilo pravé podokno.

3. Proveďte krokování aplikace výběrem příkazů v nabídce **ladění** a nastavením zarážek ve vašem kódu. Při procházení aplikace v ladicím programu se podokna aktualizují s aktuálním stavem aplikace. Při zastavení ladění se nasazení aplikace odstraní. Pokud vaše aplikace obsahuje webovou roli a nastavili jste vlastnost Akce spuštění pro spuštění webového prohlížeče, Visual Studio spustí webovou aplikaci v prohlížeči. Pokud změníte počet instancí role v konfiguraci služby, musíte zastavit svou cloudovou službu a pak znovu spustit ladění, abyste mohli ladit tyto nové instance role.

    > [!NOTE]
    > Když zastavíte nebo ladíte službu, místní emulátor služby COMPUTE a emulátor úložiště se nezastaví. Je nutné je explicitně zastavit z oznamovací oblasti.

## <a name="debug-a-cloud-service-in-azure"></a>Ladění cloudové služby v Azure

Chcete-li ladit cloudovou službu ze vzdáleného počítače, je nutné povolit tuto funkci explicitně při nasazení cloudové služby, aby byly na virtuálních počítačích, které spouštějí vaše instance rolí, nainstalovány požadované služby (například msvsmon.exe). Pokud jste nepovolili vzdálené ladění při publikování služby, budete muset službu znovu publikovat se zapnutým vzdáleným laděním.

Pokud povolíte vzdálené ladění pro cloudovou službu, neprojeví se tím snížený výkon nebo se účtují další poplatky. Nepoužívejte vzdálené ladění na provozní službě, protože klienti, kteří službu používají, můžou být nepříznivě ovlivněné.

> [!NOTE]
> Když publikujete cloudovou službu ze sady Visual Studio, můžete povolit **IntelliTrace** pro jakékoli role v této službě, které cílí na .NET Framework 4 nebo .NET Framework 4,5. Pomocí **IntelliTrace**můžete prošetřit události, k nimž došlo v instanci role v minulosti, a vytvořit kontext z tohoto času. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md) a [použití IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Povolení vzdáleného ladění pro cloudovou službu

1. Otevřete místní nabídku pro projekt Azure a pak vyberte **publikovat**.

2. Vyberte **pracovní** prostředí a konfiguraci **ladění** .

    Toto je jenom základní pravidlo. Můžete se rozhodnout pro spuštění testovacích prostředí v produkčním prostředí. Pokud ale povolíte vzdálené ladění v produkčním prostředí, můžete uživatele negativně ovlivnit. Můžete vybrat konfiguraci vydané verze, ale konfigurace ladění usnadňuje ladění.

    ![Zvolit konfiguraci ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Postupujte podle obvyklých kroků, ale zaškrtněte políčko **Povolit vzdálený ladicí program pro všechny role** na kartě **Upřesnit nastavení** .

    ![Konfigurace ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Připojení ladicího programu ke cloudové službě v Azure

1. V Průzkumník serveru rozbalte uzel pro cloudovou službu.

2. Otevřete místní nabídku role nebo instance role, ke které se chcete připojit, a pak vyberte **připojit ladicí program**.

    Při ladění role se ladicí program sady Visual Studio připojí k jednotlivým instancím této role. Ladicí program se přeruší na zarážce pro první instanci role, která spouští tento řádek kódu a splňuje všechny podmínky této zarážky. Při ladění instance se ladicí program připojí pouze k této instanci a přeruší se na zarážce pouze v případě, že tato konkrétní instance spouští tento řádek kódu a splňuje podmínky zarážky.

    ![Připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po připojení ladicího programu k instanci aplikace proveďte ladění obvyklým způsobem. Ladicí program se automaticky připojí k příslušnému hostitelskému procesu pro vaši roli. V závislosti na tom, jaká role je, ladicí program se připojí k w3wp.exe, WaWorkerHost.exe nebo WaIISHost.exe. Chcete-li ověřit proces, ke kterému je připojen ladicí program, rozbalte uzel instance v Průzkumník serveru. Další informace o procesech Azure najdete v tématu [Architektura rolí Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) .

    ![Dialog Vybrat typ kódu – dialogové okno](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Chcete-li identifikovat procesy, ke kterým je připojen ladicí program, otevřete dialogové okno procesy v panelu nabídek a zvolte možnost ladění, Windows, procesy. (Klávesnice: CTRL + ALT + Z) Chcete-li odpojit určitý proces, otevřete místní nabídku a vyberte možnost **Odpojit proces**. Nebo vyhledejte uzel instance v Průzkumník serveru, najděte proces, otevřete místní nabídku a pak vyberte **Odpojit proces**.

    ![Ladění procesů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Vyhněte se dlouhému zastavení při zarážce při vzdáleném ladění. Azure považuje proces, který se zastavil déle než několik minut, když přestane reagovat a zastaví odesílání provozu do této instance. Pokud se zastavíte příliš dlouho, msvsmon.exe se od tohoto procesu odpojí.

Pokud chcete odpojit ladicí program od všech procesů ve vaší instanci nebo roli, otevřete místní nabídku pro roli nebo instanci, kterou ladíte, a pak vyberte **Odpojit ladicí program**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Omezení vzdáleného ladění v Azure

V rámci Azure SDK 2,3 má vzdálené ladění následující omezení:

* Když je povolené vzdálené ladění, nemůžete publikovat cloudovou službu, ve které má kterákoli role víc než 25 instancí.
* Ladicí program používá porty 30400 až 30424, 31400 až 31424 a 32400 až 32424. Pokud se pokusíte použít některý z těchto portů, nebudete moct publikovat vaši službu a v protokolu aktivit pro Azure se zobrazí jedna z následujících chybových zpráv:

  * Při ověřování souboru. cscfg proti souboru. csdef došlo k chybě.
    Rozsah rezervovaných portů ' Range ' pro koncový bod Microsoft. WindowsAzure. plugins. Remotedebuggeru. Connector role ' role ' se překrývá s již definovaným portem nebo rozsahem.
  * Přidělení nebylo úspěšné. Zkuste to prosím znovu později, zkuste zmenšit velikost virtuálního počítače nebo počet instancí rolí nebo zkuste nasazení nasadit do jiné oblasti.

## <a name="debugging-azure-virtual-machines"></a>Ladění virtuálních počítačů Azure

Můžete ladit programy, které běží na virtuálních počítačích Azure pomocí Průzkumník serveru v aplikaci Visual Studio. Když povolíte vzdálené ladění na virtuálním počítači Azure, nainstaluje Azure na virtuální počítač rozšíření pro vzdálené ladění. Pak se můžete na virtuálním počítači připojit k procesům a ladit běžným způsobem.

> [!NOTE]
> Virtuální počítače vytvořené prostřednictvím zásobníku Azure Resource Manageru se dají vzdáleně ladit pomocí Průzkumníka cloudu v sadě Visual Studio 2015. Další informace najdete v tématu [Správa prostředků Azure pomocí Průzkumníka cloudu](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Ladění virtuálního počítače Azure

1. V Průzkumník serveru rozbalte uzel Virtual Machines a vyberte uzel virtuálního počítače, který chcete ladit.

2. Otevřete kontextovou nabídku a vyberte možnost **Povolit ladění**. Pokud se zobrazí dotaz, jestli chcete povolit ladění na virtuálním počítači, vyberte **Ano**.

    Azure na virtuálním počítači nainstaluje rozšíření pro vzdálené ladění, aby se povolilo ladění.

    ![Příkaz pro povolení ladění virtuálních počítačů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po dokončení instalace rozšíření vzdáleného ladění otevřete místní nabídku virtuálního počítače a vyberte **připojit ladicí program...**

    Azure získá seznam procesů na virtuálním počítači a zobrazí je v dialogovém okně připojit k procesu.

    ![Příkaz připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. V dialogovém okně **připojit k procesu** vyberte **Vybrat** , chcete-li omezit seznam výsledků tak, aby se zobrazily pouze typy kódu, který chcete ladit. Můžete ladit 32-bit nebo 64 spravovaný kód, nativní kód nebo obojí.

    ![Dialog Vybrat typ kódu – dialogové okno](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Vyberte procesy, které chcete na virtuálním počítači ladit, a pak vyberte **připojit**. Například můžete zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci na virtuálním počítači. Další informace najdete v tématu [ladění jednoho nebo více procesů v aplikaci Visual Studio a v](https://msdn.microsoft.com/library/jj919165.aspx) [architektuře rolí Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) .

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

3. Vyberte různá nastavení virtuálního počítače a pak vyberte **OK**. Další informace najdete v tématu [Virtual Machines](/previous-versions/azure/jj156003(v=azure.100)) .

    Název, který zadáte jako název DNS, bude název virtuálního počítače.

    ![Dialogové okno vytvořit virtuální počítač v Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure vytvoří virtuální počítač a pak zřídí a nakonfiguruje koncové body, jako je třeba Vzdálená plocha a Nasazení webu

4. Jakmile je virtuální počítač plně nakonfigurovaný, vyberte uzel virtuálního počítače v Průzkumník serveru.

5. Otevřete kontextovou nabídku a vyberte možnost **Povolit ladění**. Pokud se zobrazí dotaz, jestli chcete povolit ladění na virtuálním počítači, vyberte **Ano**.

    Azure do virtuálního počítače nainstaluje rozšíření pro vzdálené ladění, aby bylo možné ladění povolit.

    ![Příkaz pro povolení ladění virtuálních počítačů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publikujte projekt tak, jak je uvedeno v tématu [Postupy: nasazení webového projektu pomocí publikování jedním kliknutím v aplikaci Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Vzhledem k tomu, že chcete ladit na virtuálním počítači, vyberte na stránce **Nastavení** v průvodci **publikováním webu** možnost **ladit** jako konfiguraci. Tím zajistíte, že jsou k dispozici symboly kódu při ladění.

    ![Publish settings (Nastavení publikování)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. V **možnostech publikování souboru**vyberte možnost **odebrat další soubory v cílovém umístění** , pokud již projekt byl nasazen v dřívějším čase.

8. Po publikování projektu vyberte v místní nabídce virtuálního počítače v Průzkumník serveru **připojit ladicí program...**

    Azure získá seznam procesů na virtuálním počítači a zobrazí je v dialogovém okně připojit k procesu.

    ![Příkaz připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. V dialogovém okně **připojit k procesu** vyberte **Vybrat** , chcete-li omezit seznam výsledků tak, aby se zobrazily pouze typy kódu, který chcete ladit. Můžete ladit 32-bit nebo 64 spravovaný kód, nativní kód nebo obojí.

    ![Dialog Vybrat typ kódu – dialogové okno](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Vyberte procesy, které chcete na virtuálním počítači ladit, a pak vyberte **připojit**. Například můžete zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci na virtuálním počítači. Další informace najdete v tématu [ladění jednoho nebo více procesů v aplikaci Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) .

## <a name="next-steps"></a>Další kroky

* Pomocí **IntelliTrace** můžete shromažďovat protokol volání a událostí ze serveru vydaných verzí. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

* Pomocí **Azure Diagnostics** můžete protokolovat podrobné informace z kódu spuštěného v rámci rolí, ať už role běží ve vývojovém prostředí nebo v Azure. Viz [shromažďování dat protokolování pomocí Azure Diagnostics](https://msdn.microsoft.com/library/gg433048.aspx).
