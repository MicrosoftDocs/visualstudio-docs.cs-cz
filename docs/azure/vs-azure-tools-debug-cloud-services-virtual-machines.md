---
title: Ladění cloudové služby Azure nebo virtuálního počítače
description: Ladění cloudové služby nebo virtuálního počítače v sadě Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 2536a56f76a048cab6a3bf9a5ec026d22fe112a7
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489737"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Ladění cloudové služby Azure nebo virtuálního počítače v Sadě Visual Studio

Visual Studio nabízí různé možnosti pro ladění cloudových služeb Azure a virtuálních počítačů.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby v místním počítači

Můžete ušetřit čas a peníze pomocí výpočetníe emulátor Azure k ladění cloudové služby v místním počítači. Laděním služby místně před nasazením můžete zvýšit spolehlivost a výkon bez placení za výpočetní čas. Některé chyby však může dojít pouze při spuštění cloudové služby v azure sám. Tyto chyby můžete ladit, pokud povolíte vzdálené ladění při publikování služby a potom připojíte ladicí program k instanci role.

Emulátor simuluje službu Azure Compute a běží ve vašem místním prostředí, takže můžete testovat a ladit cloudovou službu před nasazením. Emulátor zpracovává životní cyklus instancí rolí a poskytuje přístup k simulovaným prostředkům, jako je například místní úložiště. Při ladění nebo spuštění služby z visual studia automaticky spustí emulátor jako aplikace na pozadí a potom nasadí službu do emulátoru. Emulátor můžete použít k zobrazení služby při spuštění v místním prostředí. Můžete spustit plnou verzi nebo expresní verzi emulátoru. (Počínaje Azure 2.3 je výchozí expresní verze emulátoru.) Viz [Použití emulátoru Express spustit a ladění cloudové služby místně](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Ladění cloudové služby v místním počítači

1. Na řádku nabídek zvolte **Ladění**, **Spustit ladění** a spusťte projekt cloudové služby Azure. Jako alternativu můžete stisknout Klávesu F5. Zobrazí se zpráva, že výpočetní emulátor se spouští. Po spuštění emulátoru se ikona na hlavním panelu systému potvrdí.

    ![Emulátor Azure v systémové liště](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Zobrazte uživatelské rozhraní pro emulátor výpočetních prostředků otevřením místní nabídky pro ikonu Azure v oznamovací oblasti a pak vyberte **Zobrazit uživatelské rozhraní počítačového emulátoru**.

    Levé podokno ui zobrazuje služby, které jsou aktuálně nasazeny do emulátoru výpočetního prostředí a instance role, které je spuštěna každá služba. Službu nebo role můžete zvolit pro zobrazení životního cyklu, protokolování a diagnostických informací v pravém podokně. Pokud zaostření vložíte do horního okraje zahrnutého okna, rozbalí se a vyplní pravé podokno.

3. Krokovat aplikace výběrem příkazů v nabídce **ladění** a nastavení zarážek v kódu. Při procházení aplikace v ladicím programu jsou podokna aktualizována aktuálním stavem aplikace. Když zastavíte ladění, nasazení aplikace se odstraní. Pokud vaše aplikace obsahuje webovou roli a nastavili jste vlastnost Akce po spuštění pro spuštění webového prohlížeče, spustí Visual Studio webovou aplikaci v prohlížeči. Pokud změníte počet instancí role v konfiguraci služby, musíte zastavit cloudovou službu a restartovat ladění, abyste mohli ladit tyto nové instance role.

    > [!NOTE]
    > Když zastavíte spuštění nebo ladění služby, místní emulátor výpočetních prostředků a emulátor úložiště nejsou zastaveny. Je nutné je explicitně zastavit z oznamovací oblasti.

## <a name="debug-a-cloud-service-in-azure"></a>Ladění cloudové služby v Azure

Chcete-li ladit cloudovou službu ze vzdáleného počítače, musíte tuto funkci explicitně povolit při nasazení cloudové služby tak, aby požadované služby (například msvsmon.exe) byly nainstalovány na virtuálních počítačích, na kterých jsou spuštěny instance rolí. Pokud jste při publikování služby nepovolili vzdálené ladění, je nutné službu znovu publikovat s povoleným vzdáleným laděním.

Pokud povolíte vzdálené ladění pro cloudovou službu, nevykazuje snížený výkon nebo vznikají další poplatky. Nepoužívejte vzdálené ladění v produkční službě, protože klienti, kteří službu používají, mohou být nepříznivě ovlivněni.

> [!NOTE]
> Při publikování cloudové služby z Visual Studia můžete povolit **IntelliTrace** pro všechny role v této službě, které se zaměřují na rozhraní .NET Framework 4 nebo .NET Framework 4.5. Pomocí **IntelliTrace**, můžete zkoumat události, ke kterým došlo v instanci role v minulosti a reprodukovat kontext z této doby. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a Visual Studia](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) a Using [IntelliTrace](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Povolení vzdáleného ladění pro cloudovou službu

1. Otevřete místní nabídku pro projekt Azure a pak vyberte **Publikovat**.

2. Vyberte **pracovní** prostředí a konfiguraci **ladění.**

    To je jen vodítko. Můžete se rozhodnout spustit testovací prostředí v produkčním prostředí. Pokud však povolíte vzdálené ladění v produkčním prostředí, může to mít nepříznivý vliv na uživatele. Můžete zvolit konfiguraci vydání, ale konfigurace ladění usnadňuje ladění.

    ![Zvolte konfiguraci ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Postupujte podle obvyklých kroků, ale zaškrtněte **políčko Povolit vzdálený debugger pro všechny role** na kartě **Upřesnit nastavení.**

    ![Konfigurace ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Připojení ladicího programu ke cloudové službě v Azure

1. V Průzkumníkovi serveru rozbalte uzel pro cloudovou službu.

2. Otevřete místní nabídku pro instanci role nebo role, ke které chcete připojit, a pak vyberte **Připojit ladicí program**.

    Pokud ladicí program role, ladicí program sady Visual Studio připojí ke každé instanci této role. Ladicí program bude přerušit na zarážku pro první instance role, která spustí tento řádek kódu a splňuje všechny podmínky této zarážky. Pokud ladicí program ladicí program připojí pouze k této instanci a zalomí na zarážky pouze v případě, že konkrétní instance spustí tento řádek kódu a splňuje podmínky zarážky.

    ![Připojit ladicí program](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Po ladicí program připojí k instanci, ladění jako obvykle. Ladicí program se automaticky připojí k příslušnému hostitelskému procesu pro vaši roli. V závislosti na roli je ladicí program připojí w3wp.exe, WaWorkerHost.exe nebo WaIISHost.exe. Chcete-li ověřit proces, ke kterému je ladicí program připojen, rozbalte uzel instance v Průzkumníkovi serveru. Další informace o procesech Azure najdete v tématu [Architektura rolí Azure.](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/)

    ![Dialogové okno Vybrat typ kódu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Chcete-li identifikovat procesy, ke kterým je ladicí program připojen, otevřete dialogové okno Procesy na řádku nabídek výběrem možnosti Ladění, Windows, Procesy. (Klávesnice: Ctrl+Alt+Z) Chcete-li odpojit určitý proces, otevřete jeho místní nabídku a vyberte možnost **Proces odpojení**. Nebo vyhledejte uzel instance v Průzkumníkovi serveru, vyhledejte proces, otevřete jeho místní nabídku a vyberte **Proces odpojení**.

    ![Ladění procesů](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Při vzdáleném ladění se vyhněte dlouhým zarážekm v zarážky. Azure zpracovává proces, který je zastaven déle než několik minut jako nereagující a zastaví odesílání provozu do této instance. Pokud zastavíte příliš dlouho, msvsmon.exe odpojí od procesu.

Chcete-li odpojit ladicí program od všech procesů ve vaší instanci nebo roli, otevřete místní nabídku role nebo instance, kterou ladíte, a pak vyberte **Debugger odpojit**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Omezení vzdáleného ladění v Azure

Z Azure SDK 2.3 vzdálené ladění má následující omezení:

* S povolenou vzdálenou ladění, nelze publikovat cloudovou službu, ve kterém každá role má více než 25 instancí.
* Ladicí program používá porty 30400 až 30424, 31400 až 31424 a 32400 až 32424. Pokud se pokusíte použít některý z těchto portů, nebudete moct publikovat svou službu a v protokolu aktivit pro Azure se zobrazí jedna z následujících chybových zpráv:

  * Při ověřování souboru CSCFG proti souboru CSDEF došlo k chybě.
    Rozsah rezervovaných portů pro koncový bod Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector role 'role' se překrývá s již definovaným portem nebo rozsahem.
  * Přidělení se nezdařilo. Zkuste to zopakovat později, zkuste zmenšit velikost virtuálního počítače nebo počet instancí role nebo zkuste nasadit do jiné oblasti.

## <a name="debugging-azure-virtual-machines"></a>Ladění virtuálních počítačů Azure

Programy spuštěné na virtuálních počítačích Azure můžete ladit pomocí Průzkumníka serveru v sadě Visual Studio. Když povolíte vzdálené ladění na virtuálním počítači Azure, Azure nainstaluje rozšíření vzdáleného ladění na virtuálním počítači. Potom můžete připojit k procesům ve virtuálním počítači a ladit jako obvykle.

> [!NOTE]
> Virtuální počítače vytvořené prostřednictvím zásobníku Správce prostředků Azure lze vzdáleně ladit pomocí Průzkumníka Cloud v Visual Studiu 2015. Další informace najdete [v tématu Správa prostředků Azure pomocí Cloud Exploreru](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Ladění virtuálního počítače Azure

1. V Průzkumníkovi serveru rozbalte uzel Virtuální počítače a vyberte uzel virtuálního počítače, který chcete ladit.

2. Otevřete místní nabídku a vyberte **Povolit ladění**. Na dotaz, jestli jste si jistí, jestli chcete povolit ladění ve virtuálním počítači, vyberte **Ano**.

    Azure nainstaluje rozšíření vzdáleného ladění na virtuálním počítači, aby bylo možné ladění.

    ![Příkaz Virtuální počítač povolit ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Po dokončení instalace rozšíření vzdáleného ladění otevřete kontextovou nabídku virtuálního počítače a vyberte **Připojit ladicí program...**

    Azure získá seznam procesů na virtuálním počítači a zobrazí je v dialogovém okně Připojit k procesu.

    ![Připojit ladicí příkaz](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. V dialogovém okně **Připojit k procesu** vyberte **možnost Vybrat,** chcete-li seznam výsledků omezit tak, aby zobrazoval pouze typy kódu, který chcete ladit. Můžete ladit 32bitový nebo 64bitový spravovaný kód, nativní kód nebo obojí.

    ![Dialogové okno Vybrat typ kódu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Vyberte procesy, které chcete ladit na virtuálním počítači, a pak vyberte **Připojit**. Můžete například zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci ve virtuálním počítači. Další informace najdete [v tématu Ladění jednoho nebo více procesů v sadě Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) a [architektura rolí Azure.](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/)

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Vytvoření webového projektu a virtuálního počítače pro ladění

Před publikováním projektu Azure může být užitečné otestovat ho v uzavřeném prostředí, které podporuje scénáře ladění a testování a kde můžete nainstalovat testovací a monitorovací programy. Jedním ze způsobů, jak spustit tyto testy, je vzdálené ladění aplikace ve virtuálním počítači.

Projekty Visual Studio ASP.NET nabízejí možnost vytvořit šikovný virtuální počítač, který můžete použít pro testování aplikací. Virtuální počítač obsahuje běžně potřebné koncové body, jako je PowerShell, Vzdálená plocha a WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Vytvoření webového projektu a virtuálního počítače pro ladění

1. V sadě Visual Studio vytvořte novou ASP.NET webovou aplikaci.

2. V dialogovém okně Nový ASP.NET projekt v části Azure zvolte **virtuální počítač** v rozevíracím seznamu. Ponechte zaškrtnuté políčko **Vytvořit vzdálené zdroje.** Chcete-li pokračovat, vyberte **možnost OK.**

    Zobrazí se dialogové okno **Vytvořit virtuální počítač v Azure.**

    ![Dialogové okno Vytvořit ASP.NET webový projekt](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Pokud ještě nejste přihlášení, budete požádáni o přihlášení ke svému účtu Azure.

3. Vyberte různá nastavení virtuálního počítače a pak vyberte **OK**. Další informace najdete [v tématu Virtuální počítače.](/azure/virtual-machines/)

    Název, který zadáte pro název DNS, bude název virtuálního počítače.

    ![Vytvoření virtuálního počítače v dialogovém okně Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure vytvoří virtuální počítač a pak zřídí a nakonfiguruje koncové body, jako je vzdálená plocha a nasazení webu

4. Po úplné konfiguraci virtuálního počítače vyberte uzel virtuálního počítače v Průzkumníkovi serveru.

5. Otevřete místní nabídku a vyberte **Povolit ladění**. Na dotaz, jestli jste si jistí, jestli chcete povolit ladění ve virtuálním počítači, vyberte **Ano**.

    Azure nainstaluje rozšíření vzdáleného ladění do virtuálního počítače, aby bylo možné ladění.

    ![Příkaz Virtuální počítač povolit ladění](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Protokol aktivit Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publikování projektu podle [návodu: Nasazení webového projektu pomocí publikování jedním kliknutím v sadě Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Vzhledem k tomu, že chcete ladit na virtuálním počítači, vyberte na stránce **Nastavení** průvodce **publikováním webu** **ladění** jako konfiguraci ladění. Tím zajistíte, že symboly kódu jsou k dispozici při ladění.

    ![Publish settings (Nastavení publikování)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. V **možnostech publikování souboru**vyberte **odebrat další soubory v cílovém umístění,** pokud byl projekt již nasazen dříve.

8. Po publikování projektu v kontextové nabídce virtuálního počítače v Průzkumníkovi serveru vyberte **Připojit ladicí program...**

    Azure získá seznam procesů na virtuálním počítači a zobrazí je v dialogovém okně Připojit k procesu.

    ![Připojit ladicí příkaz](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. V dialogovém okně **Připojit k procesu** vyberte **možnost Vybrat,** chcete-li seznam výsledků omezit tak, aby zobrazoval pouze typy kódu, který chcete ladit. Můžete ladit 32bitový nebo 64bitový spravovaný kód, nativní kód nebo obojí.

    ![Dialogové okno Vybrat typ kódu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Vyberte procesy, které chcete ladit na virtuálním počítači, a pak vyberte **Připojit**. Můžete například zvolit proces w3wp.exe, pokud jste chtěli ladit webovou aplikaci ve virtuálním počítači. Další informace najdete [v tématu Ladění jednoho nebo více procesů v sadě Visual Studio.](https://msdn.microsoft.com/library/jj919165.aspx)

## <a name="next-steps"></a>Další kroky

* Pomocí **aplikace IntelliTrace** můžete shromažďovat protokol volání a událostí z tiskového serveru. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a Visual Studia](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Pomocí **diagnostiky Azure** můžete protokolovat podrobné informace z kódu spuštěného v rolích, ať už jsou role spuštěné ve vývojovém prostředí nebo v Azure. Viz [Shromažďování dat protokolování pomocí Diagnostika Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).
