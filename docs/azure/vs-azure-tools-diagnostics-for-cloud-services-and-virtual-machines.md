---
title: Diagnostika pro Azure Cloud Services a virtuální počítače
description: Naučte se, jak nastavit diagnostiku pro ladění cloudových služeb Azure a virtuálních počítačů v sadě Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 9912a7fa0e83c5433e0eba1c7ffa23763331af6b
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508493"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Nastavení diagnostiky pro službu Azure Cloud Services a virtuální počítače
Pokud potřebujete řešit potíže s cloudovou službou Azure nebo virtuálním počítačem, můžete pomocí sady Visual Studio snadněji nastavit Azure Diagnostics. Diagnostika zaznamenává systémová data a data protokolování do virtuálních počítačů a instancí virtuálních počítačů, které spouštějí vaši cloudovou službu. Diagnostická data se přenesou na účet úložiště, který zvolíte. Další informace o protokolování diagnostiky v Azure najdete v tématu [Povolení protokolování diagnostiky pro Web Apps v Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

V tomto článku vám ukážeme, jak pomocí sady Visual Studio zapnout a nastavit Azure Diagnostics, a to před i po nasazení. Naučte se, jak nastavit diagnostiku na virtuálních počítačích Azure, jak vybrat typy diagnostických informací, které se mají shromažďovat, a jak tyto informace zobrazit po shromáždění.

K nastavení Azure Diagnostics můžete použít jednu z následujících možností:

* Změnit nastavení diagnostiky v dialogovém okně **Konfigurace diagnostiky** v aplikaci Visual Studio. Nastavení se ukládají do souboru s názvem Diagnostics. wadcfgx (v sadě Azure SDK 2,4 a starších verzích se tento soubor nazývá Diagnostics. wadcfg). Můžete také přímo upravit konfigurační soubor. Pokud soubor ručně aktualizujete, změny konfigurace se projeví při příštím nasazení cloudové služby do Azure nebo spuštění služby v emulátoru.
* Pomocí Průzkumníka cloudu nebo Průzkumník serveru v aplikaci Visual Studio změňte nastavení diagnostiky pro cloudovou službu nebo virtuální počítač, na kterém běží.

## <a name="azure-sdk-26-diagnostics-changes"></a>Změny diagnostiky Azure SDK 2,6
Následující změny se vztahují na projekty Azure SDK 2,6 a novější v sadě Visual Studio:

* Místní emulátor teď podporuje diagnostiku. To znamená, že můžete shromažďovat diagnostická data a zajistit, že vaše aplikace vytvoří správné trasování při vývoji a testování v aplikaci Visual Studio. Připojovací řetězec `UseDevelopmentStorage=true` zapne shromažďování diagnostických dat při spuštění projektu cloudové služby v sadě Visual Studio pomocí emulátoru Azure Storage. Všechna diagnostická data se shromažďují v účtu úložiště pro vývoj.
* Připojovací řetězec účtu úložiště diagnostiky `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` je uložený v souboru konfigurace služby (. cscfg). V sadě Azure SDK 2,5 je účet úložiště diagnostiky zadaný v souboru Diagnostics. wadcfgx.

Připojovací řetězec funguje jinak v některých klíčových způsobech v sadě Azure SDK 2,6 a novější oproti Azure SDK 2,4 a staršímu:

* V Azure SDK 2,4 a starších verzích se připojovací řetězec používá modulem plug-in pro diagnostiku k získání informací o účtu úložiště pro přenos diagnostických protokolů.
* Sada Visual Studio v sadě Azure SDK 2,6 a novějších používá připojovací řetězec pro diagnostiku k nastavení rozšíření Azure Diagnostics s příslušnými informacemi o účtu úložiště během publikování. Připojovací řetězec můžete použít k definování různých účtů úložiště pro různé konfigurace služby, které aplikace Visual Studio používá během publikování. Vzhledem k tomu, že modul plug-in Diagnostika není po sadě Azure SDK 2,5 k dispozici, nemůže soubor. cscfg sám nastavit diagnostické rozšíření. Rozšíření musíte nastavit samostatně pomocí nástrojů, jako je Visual Studio nebo PowerShell.
* Z důvodu zjednodušení procesu nastavení diagnostického rozšíření pomocí prostředí PowerShell obsahuje výstup balíčku ze sady Visual Studio pro rozšíření diagnostiky pro každou roli kód XML pro veřejnou konfiguraci. Visual Studio používá připojovací řetězec pro diagnostiku k naplnění informací o účtu úložiště ve veřejné konfiguraci. Veřejné konfigurační soubory se vytvoří ve složce rozšíření. Veřejné konfigurační soubory používají vzor pojmenování PaaSDiagnostics. &lt; název role \>.PubConfig.xml. Jakékoli nasazení založené na prostředí PowerShell mohou pomocí tohoto modelu namapovat každou konfiguraci na roli.
* [Azure Portal](https://portal.azure.com) používá připojovací řetězec v souboru. cscfg pro přístup k diagnostickým datům. Data se zobrazí na kartě **monitorování** . Připojovací řetězec je nutný k nastavení služby pro zobrazení podrobných dat monitorování na portálu.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrace projektů do Azure SDK 2,6 a novější
Když migrujete ze sady Azure SDK 2,5 na sadu Azure SDK 2,6 nebo novější, pokud jste v souboru. wadcfgx měli zadaný účet úložiště diagnostiky, zůstane účet úložiště v tomto souboru. Pokud chcete využít flexibilitu při používání různých účtů úložiště pro různé konfigurace úložiště, přidejte do svého projektu připojovací řetězec ručně. Pokud migrujete projekt ze sady Azure SDK 2,4 nebo starší do sady Azure SDK 2,6, připojovací řetězce diagnostiky se zachovají. Všimněte si ale změn v tématu Jak se zpracovávají připojovací řetězce v sadě Azure SDK 2,6 popsané v předchozí části.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Jak Visual Studio Určuje účet úložiště diagnostiky
* Pokud je v souboru. cscfg zadán připojovací řetězec diagnostiky, sada Visual Studio ho použije k nastavení rozšíření diagnostiky během publikování a při generování souborů XML veřejné konfigurace během balení.
* Pokud v souboru. cscfg není zadaný připojovací řetězec diagnostiky, sada Visual Studio se vrátí k použití účtu úložiště, který je zadaný v souboru. wadcfgx, a nastaví diagnostické rozšíření pro publikování a za účelem generování souborů XML veřejných konfigurací během balení.
* Připojovací řetězec diagnostiky v souboru. cscfg má přednost před účtem úložiště v souboru. wadcfgx. Pokud je v souboru. cscfg zadán připojovací řetězec diagnostiky, aplikace Visual Studio použije tento připojovací řetězec a ignoruje účet úložiště v souboru. wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Co jsou připojovací řetězce pro aktualizaci vývoje pro vývoj... Chcete udělat zaškrtávací políčko?
Možnost **aktualizace připojovacích řetězců úložiště pro diagnostiku a ukládání do mezipaměti s Microsoft Azure přihlašovacími údaji účtu úložiště při publikování do Microsoft Azure** je pohodlný způsob, jak aktualizovat všechny připojovací řetězce účtu úložiště pro vývoj s účtem služby Azure Storage, který zadáte během publikování.

Například pokud zaškrtnete toto políčko a připojovací řetězec diagnostiky určíte `UseDevelopmentStorage=true` při publikování projektu do Azure, Visual Studio automaticky aktualizuje připojovací řetězec diagnostiky s účtem úložiště, který jste zadali v Průvodci publikováním. Pokud se ale skutečný účet úložiště zadal jako připojovací řetězec diagnostiky, použije se místo něj tento účet.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Rozdíly v diagnostických funkcích v sadě Azure SDK 2,4 a starších verzích vs. Azure SDK 2,5 a novější
Pokud upgradujete projekt ze sady Azure SDK 2,4 a starší na sadu Azure SDK 2,5 nebo novější, pamatujte na následující rozdíly v diagnostických funkcích:

* **Rozhraní API pro konfiguraci jsou zastaralá**. Programová konfigurace diagnostiky je k dispozici v sadě Azure SDK 2,4 a starších verzích, ale je zastaralá v sadě Azure SDK 2,5 a novější. Pokud je konfigurace diagnostiky aktuálně definovaná v kódu, musíte nastavení znovu nakonfigurovat od nuly v migrovaném projektu, aby se zajistila jeho funkčnost. Konfigurační soubor diagnostiky pro sadu Azure SDK 2,4 je Diagnostics. wadcfg. Konfigurační soubor diagnostiky pro sadu Azure SDK 2,5 a novější je Diagnostics. wadcfgx.
* **Diagnostiku aplikací cloudových služeb lze konfigurovat pouze na úrovni role**. V Azure SDK 2,5 a novějších nemůžete na úrovni instance nastavit diagnostiku pro aplikace cloudové služby.
* **Pokaždé, když nasadíte aplikaci, konfigurace diagnostiky se aktualizuje**. To může způsobit problémy parity, pokud změníte konfiguraci diagnostiky ze sady Visual Studio Průzkumník serveru a pak znovu nasadíte aplikaci.
* **V sadě Azure SDK 2,5 a novějších jsou výpisy stavu systému nakonfigurovány v konfiguračním souboru diagnostiky, nikoli v kódu**. Pokud máte v kódu nakonfigurované výpisy stavu systému, je nutné ručně přenést konfiguraci z kódu do konfiguračního souboru. Při migraci do Azure SDK 2,6 se přenesou výpisy stavu systému.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Zapněte diagnostiku v projektech cloudové služby ještě předtím, než je nasadíte.
V aplikaci Visual Studio můžete shromažďovat diagnostická data pro role, které běží v Azure, když službu spustíte v emulátoru před nasazením. Všechny změny nastavení diagnostiky v aplikaci Visual Studio jsou uloženy v konfiguračním souboru Diagnostics. wadcfgx. Tato nastavení určují účet úložiště, do kterého se při nasazení cloudové služby uloží diagnostická data.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Zapnutí diagnostiky v aplikaci Visual Studio před nasazením

1. V místní nabídce role vyberte možnost **vlastnosti**. V dialogovém okně **vlastnosti** role vyberte kartu **Konfigurace** .
2. V části **Diagnostika** se ujistěte, že je zaškrtnuté políčko **Povolit diagnostiku** .

    ![Přístup k možnosti Povolit diagnostiku](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Chcete-li zadat účet úložiště pro diagnostická data, vyberte tlačítko se třemi tečkami (...).

    ![Zadejte účet úložiště, který se má použít.](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. V dialogovém okně **vytvořit připojovací řetězec úložiště** určete, jestli se chcete připojit pomocí emulátoru Azure Storage, předplatného Azure nebo ručně zadaných přihlašovacích údajů.

    ![Účet Storage – dialogové okno](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * Pokud vyberete možnost **emulátor úložiště Microsoft Azure**, připojovací řetězec je nastaven na hodnotu `UseDevelopmentStorage=true` .
   * Pokud vyberete **své předplatné**, můžete vybrat předplatné Azure, které chcete použít, a zadat název účtu. Pokud chcete spravovat předplatná Azure, vyberte **Spravovat účty**.
   * Pokud vyberete možnost **ručně zadané přihlašovací údaje**, zadejte název a klíč účtu Azure, který chcete použít.
5. Chcete-li zobrazit dialogové okno **Konfigurace diagnostiky** , vyberte možnost **Konfigurovat**. S výjimkou adresářů pro **Obecné** a **protokoly**představuje každá karta zdroj dat diagnostiky, který můžete shromažďovat. Výchozí karta **Obecné** nabízí následující možnosti shromažďování diagnostických dat: **jenom chyby**, **všechny informace**a **vlastní plán**. Možnost **pouze výchozí chyby** používá minimální velikost úložiště, protože nepřenáší upozornění nebo zprávy trasování. Možnost **všechny informace** přenáší většinu informací, používá nejvíce úložiště, a proto je nejdražším parametrem.

   > [!NOTE]
   > Minimální podporovaná velikost pro "disková kvóta v MB" je 50 MB a výchozí velikost je 4 GB. Pokud však shromažďujete výpisy paměti, zvyšte tuto hodnotu na vyšší hodnotu, jako je 10 GB.
   >

    ![Povolit diagnostiku a konfiguraci Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. V tomto příkladu vyberte možnost **vlastního plánu** , abyste mohli shromážděná data přizpůsobit.
7. V poli disková **kvóta v MB** můžete nastavit, kolik místa se má v účtu úložiště pro diagnostická data přidělit. Můžete změnit nebo přijmout výchozí hodnotu.
8. Na každé kartě diagnostických dat, která chcete shromáždit, zaškrtněte políčko **Povolit přenos pro \<log type\> ** . Například pokud chcete shromažďovat protokoly aplikací, zaškrtněte na kartě **protokoly aplikací** políčko **Povolit přenos protokolů aplikací** . Také zadejte všechny další informace, které jsou požadovány pro každý typ dat diagnostiky. Informace o konfiguraci pro každou kartu najdete v části **Nastavení diagnostických zdrojů dat** dále v tomto článku.
9. Po povolení shromažďování všech diagnostických dat vyberte **OK**.
10. Spusťte v aplikaci Visual Studio projekt cloudové služby Azure obvyklým způsobem. Při použití vaší aplikace se informace protokolu, které jste povolili, uloží do účtu úložiště Azure, který jste zadali.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Zapnutí diagnostiky na virtuálních počítačích Azure
V aplikaci Visual Studio můžete shromažďovat diagnostická data pro virtuální počítače Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Zapnutí diagnostiky na virtuálních počítačích Azure

1. V Průzkumník serveru vyberte uzel Azure a pak se připojte k předplatnému Azure, pokud ještě nejste připojení.
2. Rozbalte uzel **Virtual Machines** . Můžete vytvořit nový virtuální počítač nebo vybrat existující uzel.
3. V místní nabídce požadovaného virtuálního počítače vyberte **Konfigurovat**. Zobrazí se dialogové okno Konfigurace virtuálního počítače.

    ![Konfigurace virtuálního počítače Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Pokud ještě není nainstalovaná, přidejte rozšíření Microsoft Monitoring Agent Diagnostics. S tímto rozšířením můžete shromažďovat diagnostická data pro virtuální počítač Azure. V části **nainstalovaná rozšíření**vyberte v rozevíracím seznamu **Vybrat dostupné rozšíření** možnost **Microsoft Monitoring Agent Diagnostika**.

    ![Nainstalovat rozšíření virtuálního počítače Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > K dispozici jsou další diagnostická rozšíření pro vaše virtuální počítače. Další informace najdete v tématu [rozšíření virtuálních počítačů a funkce pro Windows](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Chcete-li přidat rozšíření a zobrazit dialogové okno **Konfigurace diagnostiky** , vyberte možnost **Přidat**.
6. Pokud chcete zadat účet úložiště, vyberte **Konfigurovat**a pak vyberte **OK**.

    Každá karta (kromě adresářů **obecně** a **protokolu**) představuje zdroj dat diagnostiky, který můžete shromažďovat.

    ![Povolit diagnostiku a konfiguraci Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Výchozí karta **všeobecně**nabízí následující možnosti shromažďování diagnostických dat: **jenom chyby**, **všechny informace**a **vlastní plán**. Výchozí možnost, **pouze chyby**, využívá minimální velikost úložiště, protože nepřenosuje upozornění nebo zprávy trasování. Možnost **všechny informace** přenáší nejvíc informací a je tedy nejdražším parametrem z podmínek úložiště.
7. V tomto příkladu vyberte možnost **vlastního plánu** , abyste mohli přizpůsobit shromážděná data.
8. V poli **disková kvóta v MB** určuje, kolik místa chcete přidělit účtu úložiště pro diagnostická data. Pokud chcete, můžete změnit výchozí hodnotu.
9. Na každé kartě diagnostických dat, která chcete shromáždit, zaškrtněte políčko **Povolit přenos pro \<log type\> ** zaškrtávací políčko.

    Například pokud chcete shromažďovat protokoly aplikací, zaškrtněte políčko **Povolit přenos protokolů aplikace** na kartě **protokoly aplikací** . Také zadejte všechny další informace, které jsou požadovány pro každý typ dat diagnostiky. Informace o konfiguraci pro každou kartu najdete v části **Nastavení diagnostických zdrojů dat** dále v tomto článku.
10. Až budete mít povolenou kolekci všech diagnostických dat, vyberte **OK**.
11. Uložte aktualizovaný projekt.

    Zpráva v okně **protokolu aktivit Microsoft Azure** označuje, že se virtuální počítač aktualizoval.

## <a name="set-up-diagnostics-data-sources"></a>Nastavení zdrojů dat diagnostiky
Po povolení shromažďování diagnostických dat můžete zvolit přesně to, jaké zdroje dat chcete shromažďovat, a jaké informace se shromažďují. V dalších částech najdete popis karet v dialogovém okně **Konfigurace diagnostiky** a o tom, co každá z možností konfigurace znamená.

### <a name="application-logs"></a>Protokoly aplikací
Protokoly aplikací mají diagnostické informace, které jsou vytvářeny webovou aplikací. Pokud chcete zaznamenat protokoly aplikací, zaškrtněte políčko **Povolit přenos protokolů aplikací** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů aplikací do svého účtu úložiště, změňte hodnotu **period přenosů (min)** . Množství informací zachycených v protokolu můžete také změnit nastavením hodnoty **úrovně protokolu** . Pokud například chcete získat další informace, vyberte možnost **podrobné** . můžete také vybrat možnost **kritické** a zachytit jenom kritické chyby. Pokud máte konkrétního poskytovatele diagnostiky, který generuje protokoly aplikací, můžete protokoly zachytit tak, že do pole **identifikátor GUID poskytovatele** přidáte identifikátor GUID poskytovatele.

  ![Protokoly aplikací](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Další informace o protokolech aplikací najdete v tématu [Povolení protokolování diagnostiky pro Web Apps v Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Protokoly událostí Windows
Chcete-li zaznamenat protokoly událostí systému Windows, zaškrtněte políčko **Povolit přenos protokolů událostí systému Windows** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů událostí do svého účtu úložiště, změňte hodnotu **Doba přenosu (min)** . Zaškrtněte políčka pro typy událostí, které chcete sledovat.

![Protokoly událostí](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Pokud používáte sadu Azure SDK 2,6 nebo novější a chcete zadat vlastní zdroj dat, zadejte ho do **\<Data source name\>** textového pole a pak vyberte **Přidat**. Zdroj dat se přidá do souboru Diagnostics. cfcfg.

Pokud používáte sadu Azure SDK 2,5 a chcete zadat vlastní zdroj dat, můžete ho přidat do `WindowsEventLog` části souboru Diagnostics. wadcfgx, jako v následujícím příkladu:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Čítače výkonu
Informace čítače výkonu vám pomůžou najít problémová místa systému a doladit výkon systému a aplikace. Další informace najdete v tématu [Vytvoření a použití čítačů výkonu v aplikaci Azure](/azure/cloud-services/diagnostics-performance-counters). Chcete-li zachytit čítače výkonu, zaškrtněte políčko **Povolit přenos čítačů výkonu** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů událostí do svého účtu úložiště, změňte hodnotu **Doba přenosu (min)** . Zaškrtněte políčka pro čítače výkonu, které chcete sledovat.

![Čítače výkonu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Chcete-li sledovat čítač výkonu, který není uveden, zadejte čítač výkonu pomocí navrhované syntaxe. a pak vyberte **Přidat**. Operační systém na virtuálním počítači určuje, které čítače výkonu můžete sledovat. Další informace o syntaxi najdete v tématu [Určení cesty čítače](/windows/win32/perfctrs/specifying-a-counter-path).

### <a name="infrastructure-logs"></a>Protokoly infrastruktury
Protokoly infrastruktury obsahují informace o diagnostické infrastruktuře Azure, modulu RemoteAccess a modulu RemoteForwarder. Chcete-li shromáždit informace o protokolech infrastruktury, zaškrtněte políčko **Povolit přenos protokolů infrastruktury** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů infrastruktury do svého účtu úložiště, změňte hodnotu **Doba přenosu (min)** .

![Protokoly diagnostické infrastruktury](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Další informace najdete v tématu [shromáždění dat protokolování pomocí Azure Diagnostics](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="log-directories"></a>Adresáře protokolů
Adresáře protokolů obsahují data shromážděná z adresářů protokolů pro požadavky Internetová informační služba (IIS), neúspěšné žádosti nebo složky, které vyberete. Chcete-li zachytávání adresářů protokolů, zaškrtněte políčko **Povolit přenos adresářů protokolů** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů a vaším účtem úložiště, změňte hodnotu **period přenosů (min)** .

Zaškrtněte políčka u protokolů, které chcete shromažďovat, jako jsou **protokoly IIS** a protokoly **neúspěšných žádostí** . K dispozici jsou výchozí názvy kontejnerů úložiště, ale můžete změnit jejich názvy.

Protokoly můžete zachytit z libovolné složky. Zadejte cestu v části **protokol z absolutního adresáře** a pak vyberte **Přidat adresář**. Protokoly jsou zachyceny v určených kontejnerech.

![Adresáře protokolů](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Protokoly ETW
Pokud používáte [trasování událostí pro Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) a chcete zaznamenávat protokoly ETW, zaškrtněte políčko **Povolit přenos protokolů ETW** . Pokud chcete zvýšit nebo snížit interval mezi přenosem protokolů a vaším účtem úložiště, změňte hodnotu **period přenosů (min)** .

Události jsou zachyceny ze zdrojů událostí a manifestů událostí, které zadáte. Pokud chcete zadat zdroj události, v části **zdroje událostí** zadejte název a pak vyberte **Přidat zdroj události**. Podobně můžete zadat manifest události v části **manifesty událostí** a pak vybrat **Přidat manifest události**.

![Protokoly ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

Architektura ETW je podporována v ASP.NET prostřednictvím tříd v oboru názvů [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) . Obor názvů Microsoft. WindowsAzure. Diagnostics, který dědí z a rozšiřuje standardní třídy [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) , umožňuje použití [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) jako protokolovacího rozhraní v prostředí Azure. Další informace najdete v tématu [převzetí řízení protokolování a trasování v Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) a [Povolení diagnostiky ve službě Azure Cloud Services a virtuálních počítačích](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Výpisy stavu systému
Pokud chcete zachytit informace o tom, kdy instance role selže, zaškrtněte políčko **Povolit přenos výpisů stavu systému** . (Vzhledem k tomu, že ASP.NET zpracovává většinu výjimek, je tato funkce obecně užitečná pouze pro role pracovního procesu.) Chcete-li zvýšit nebo snížit procento místa v úložišti, které je pro výpisy stavu systému, změňte hodnotu **kvóta adresáře (%)** . Můžete změnit kontejner úložiště, ve kterém jsou uložené výpisy stavu systému, a vybrat, zda chcete zachytit **úplný** nebo **zkrácený** výpis.

Aktuálně sledované procesy jsou uvedeny na následujícím snímku obrazovky. Zaškrtněte políčka pro procesy, které chcete zachytit. Pokud chcete do seznamu přidat jiný proces, zadejte název procesu a pak vyberte **Přidat proces**.

![Výpisy stavu systému](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Další informace najdete v tématu [převzetí řízení protokolování a trasování v Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) a [Diagnostika Microsoft Azure části 4: Vlastní protokolovací komponenty a Azure Diagnostics 1,3 změny](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Zobrazit diagnostická data
Jakmile shromáždíte diagnostická data pro cloudovou službu nebo virtuální počítač, můžete si ji zobrazit.

### <a name="to-view-cloud-service-diagnostics-data"></a>Zobrazení diagnostických dat cloudové služby
1. Nasaďte cloudovou službu obvyklým způsobem a pak ji spusťte.
2. Diagnostická data můžete zobrazit buď v sestavě, kterou aplikace Visual Studio generuje, nebo v tabulkách v účtu úložiště. Chcete-li zobrazit data v sestavě, otevřete Průzkumníka cloudu nebo Průzkumník serveru, otevřete místní nabídku uzlu pro požadovanou roli a pak vyberte možnost **Zobrazit diagnostická data**.

    ![Zobrazit diagnostická data](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Zobrazí se sestava, která zobrazuje dostupná data.

    ![Sestava Diagnostika Microsoft Azure v aplikaci Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Pokud se nezobrazuje poslední data, možná budete muset počkat na uplynutí doby přenosu.

    Pokud chcete data hned aktualizovat, vyberte odkaz **aktualizovat** . Pokud chcete data aktualizovat automaticky, vyberte interval v rozevíracím seznamu **Automatické aktualizace** . Pokud chcete exportovat data chyby, vyberte tlačítko **exportovat do sdíleného svazku clusteru** a vytvořte soubor hodnot oddělených čárkami, který můžete otevřít v excelovém listu.

    V Průzkumníku cloudu nebo Průzkumník serveru otevřete účet úložiště, který je přidružený k nasazení.
3. Otevřete diagnostické tabulky v prohlížeči tabulky a potom zkontrolujte shromážděná data. Pro protokoly služby IIS a vlastní protokoly můžete otevřít kontejner objektů BLOB. V následující tabulce jsou uvedeny tabulky nebo kontejnery objektů blob, které obsahují data pro různé soubory protokolu. Kromě dat pro tento soubor protokolu obsahují položky tabulky **EventTickCount**, **DeploymentID**, **role**a **RoleInstance**, které vám pomůžou zjistit, který virtuální počítač a role vygenerovala data a kdy.

   | Diagnostická data | Popis | Umístění |
   | --- | --- | --- |
   | Protokoly aplikací |Protokoluje, že váš kód generuje voláním metod třídy **System. Diagnostics. Trace** . |WADLogsTable |
   | Protokoly událostí |Data z protokolů událostí systému Windows na virtuálních počítačích. Systém Windows ukládá informace v těchto protokolech, ale aplikace a služby používají protokoly k nahlášení chyb nebo informací o protokolu. |WADWindowsEventLogsTable |
   | Čítače výkonu |Data můžete shromažďovat na jakémkoli čítači výkonu, který je k dispozici na virtuálním počítači. Operační systém poskytuje čítače výkonu, které zahrnují řadu statistik, jako je využití paměti a čas procesoru. |WADPerformanceCountersTable |
   | Protokoly infrastruktury |Protokoly, které jsou generovány přímo z diagnostické infrastruktury. |WADDiagnosticInfrastructureLogsTable |
   | Protokoly IIS |Protokoly, které zaznamenávají webové požadavky. Pokud vaše cloudová služba získá značný objem provozu, můžou být tyto protokoly zdlouhavé. Tato data je vhodné shromažďovat a ukládat pouze v případě, že je potřebujete. |V kontejneru objektů BLOB v části wad-IIS-failedreqlogs se v cestě k tomuto nasazení, roli a instanci můžete najít protokoly neúspěšných požadavků. Úplné protokoly najdete v části wad-IIS-LogFiles. Položky pro každý soubor jsou vytvořeny v tabulce WADDirectories. |
   | Výpisy stavu systému |Poskytuje binární image procesu vaší cloudové služby (obvykle role pracovního procesu). |WAD-drcení – výpis kontejneru objektů BLOB |
   | Vlastní soubory protokolu |Protokoly dat, která jste předdefinovány. |V části kód můžete zadat umístění vlastních souborů protokolů v účtu úložiště. Můžete například zadat vlastní kontejner objektů BLOB. |
4. Pokud jsou data libovolného typu zkrácena, můžete zkusit zvětšit vyrovnávací paměť pro tento datový typ nebo zkrátit interval mezi přenosy dat z virtuálního počítače na účet úložiště.
5. Volitelné Vyprázdnit data z účtu úložiště občas omezíte celkové náklady na úložiště.
6. Po úplném nasazení se soubor Diagnostics. cscfg (. wadcfgx pro sadu Azure SDK 2,5) aktualizuje v Azure a vaše cloudová služba vezme všechny změny v konfiguraci diagnostiky. Pokud místo toho aktualizujete existující nasazení, soubor. cscfg není v Azure aktualizovaný. Nastavení diagnostiky můžete i nadále měnit pomocí postupu v následující části. Další informace o provedení úplného nasazení a aktualizaci stávajícího nasazení najdete v tématu [Průvodce publikováním aplikací Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Zobrazení dat diagnostiky virtuálního počítače
1. V místní nabídce pro virtuální počítač vyberte **Zobrazit diagnostická data**.

    ![Zobrazení diagnostických dat ve virtuálním počítači Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Zobrazí se dialogové okno **Souhrn diagnostiky** .

    ![Souhrn diagnostiky virtuálních počítačů Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Pokud se nezobrazuje poslední data, možná budete muset počkat na uplynutí doby přenosu.

    Pokud chcete data hned aktualizovat, vyberte odkaz **aktualizovat** . Pokud chcete data aktualizovat automaticky, vyberte interval v rozevíracím seznamu **Automatické aktualizace** . Pokud chcete exportovat data chyby, vyberte tlačítko **exportovat do sdíleného svazku clusteru** a vytvořte soubor hodnot oddělených čárkami, který můžete otevřít v excelovém listu.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Nastavení diagnostiky cloudové služby po nasazení
Pokud zkoumáte problém s cloudovou službou, která je už spuštěná, možná budete chtít shromáždit data, která jste nezadali před tím, než jste původně nasadili roli. V takovém případě můžete začít shromažďovat tato data změnou nastavení v Průzkumník serveru. Diagnostiku můžete nastavit buď pro jednu instanci, nebo pro všechny instance v roli v závislosti na tom, jestli otevřete dialogové okno **Konfigurace diagnostiky** z místní nabídky pro instanci nebo pro roli. Pokud nakonfigurujete uzel role, budou všechny změny, které provedete, platit pro všechny instance. Pokud nakonfigurujete uzel instance, veškeré změny, které provedete, se vztahují pouze na tuto instanci.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Nastavení diagnostiky pro běžící cloudovou službu
1. V Průzkumník serveru rozbalte uzel **Cloud Services** a potom rozbalte seznam uzlů, abyste našli roli nebo instanci (nebo obojí), kterou chcete prozkoumat.

    ![Konfigurace diagnostiky](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. V místní nabídce uzlu instance nebo uzlu role vyberte **aktualizovat nastavení diagnostiky**a pak vyberte nastavení diagnostiky, která chcete shromažďovat.

    Informace o nastavení konfigurace najdete v části **Nastavení diagnostických zdrojů dat** v tomto článku. Informace o tom, jak zobrazit diagnostická data, najdete v části **zobrazení diagnostických dat** v tomto článku.

    Pokud změníte shromažďování dat v Průzkumník serveru, změny zůstanou v platnosti, dokud nebudete plně znovu nasazovat cloudovou službu. Použijete-li výchozí nastavení publikování, změny nebudou přepsány. Výchozím nastavením publikování je aktualizovat existující nasazení, nikoli provést úplné opětovné nasazení. Pokud chcete mít jistotu, že se nastavení v době nasazení vymažou, v Průvodci publikováním klikněte na kartu **Pokročilé nastavení** a zrušte zaškrtnutí políčka **aktualizace nasazení** . Při opětovném nasazení s tímto zaškrtávacím políčkem se nastavení vrátí do souboru. wadcfgx (nebo. wadcfg) jako nastaveného prostřednictvím editoru **vlastností** pro danou roli. Pokud aktualizujete nasazení, Azure zachová předchozí nastavení.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Řešení potíží s cloudovou službou Azure
Pokud máte problémy s projekty cloudové služby, jako je například role, která se zablokuje ve stavu "zaneprázdněno", opakovaně recykluje nebo vyvolá vnitřní chybu serveru, existují nástroje a techniky, které můžete použít k diagnostice a vyřešení problému. Konkrétní příklady běžných problémů a řešení a přehled konceptů a nástrojů, které můžete použít k diagnostice a opravě těchto chyb, najdete v tématu [diagnostická data služby Azure PaaS COMPUTE](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data).

## <a name="q--a"></a>Otázky a odpovědi
**Jaká je velikost vyrovnávací paměti a jak velká má být?**

U každé instance virtuálního počítače omezuje kvóta, kolik dat diagnostiky může být uloženo v místním systému souborů. Kromě toho určujete velikost vyrovnávací paměti pro každý typ dat diagnostiky, který je k dispozici. Tato velikost vyrovnávací paměti funguje jako individuální kvóta pro tento typ dat. Chcete-li určit celkovou kvótu a množství paměti, které zbývá, Prohlédněte si dolní část dialogového okna pro diagnostický datový typ. Pokud zadáte větší vyrovnávací paměť nebo více typů dat, získáte přístup k celkové kvótě. Celkovou kvótu můžete změnit úpravou konfiguračního souboru Diagnostics. wadcfg nebo. wadcfgx. Diagnostická data jsou uložena ve stejném systému souborů jako data vaší aplikace. Pokud vaše aplikace používá velké množství místa na disku, neměli byste zvýšit celkovou kvótu pro diagnostiku.

**Jaká je přenosová doba a jak dlouho by měla být?**

Doba přenosu je doba, která uplyne mezi zachycením dat. Po každém období přenosu se data přesunou z místního systému souborů na virtuálním počítači do tabulek v účtu úložiště. Pokud množství shromažďovaných dat překročí kvótu před koncem období přenosu, budou starší data zahozena. Pokud data ztratíte, protože vaše data přesahují velikost vyrovnávací paměti nebo celkovou kvótu, možná budete chtít zkrátit dobu přenosu.

**V jakém časovém pásmu jsou časová razítka?**

Časová razítka jsou v místním časovém pásmu datového centra, které hostuje vaši cloudovou službu. Používají se tři následující sloupce s časovým razítkem v tabulkách protokolu:

* **PreciseTimeStamp**: časové razítko ETW události. To znamená čas, kdy se událost protokoluje z klienta.
* **Timestamp**: hodnota pro **PreciseTimeStamp** se zaokrouhluje na hranici četnosti nahrávání. Například pokud je vaše frekvence nahrávání 5 minut a čas události 00:17:12, časové RAZÍTKo je 00:15:00.
* **Časové razítko**: časové razítko, pro které se entita vytvořila v tabulce Azure.

**Návody spravovat náklady při shromažďování diagnostických informací?**

Výchozí nastavení (**úroveň protokolu** je nastavená **na chyba**a **perioda přenosu** nastavené na **1 minutu**) jsou navržené tak, aby se minimalizovaly náklady. Náklady na výpočetní výkon se zvyšují při shromažďování dalších diagnostických dat nebo při snížení doby přenosu. Neshromážděte více dat, než kolik potřebujete, a nezapomeňte zakázat shromažďování dat, když už ho nepotřebujete. Tuto akci můžete kdykoli znovu povolit, a to i v době běhu, jak je popsáno výše v tomto článku.

**Návody shromažďování neúspěšných požadavků – protokoly služby IIS?**

Služba IIS ve výchozím nastavení neshromažďuje protokoly chybných požadavků. Službu IIS můžete nastavit tak, aby shromáždila protokoly neúspěšných požadavků úpravou souboru web.config pro webovou roli.

**Nedaří se mi získat informace o trasování z RoleEntryPoint metod, jako je OnStart. Co je?**

Metody **RoleEntryPoint** jsou volány v kontextu WAIISHost.exe, nikoli ve službě IIS. Informace o konfiguraci v web.config, které obvykle umožňují trasování, se nepoužívají. Chcete-li tento problém vyřešit, přidejte do projektu webové role soubor. config a pojmenujte jej tak, aby odpovídal výstupnímu sestavení, které obsahuje kód **RoleEntryPoint** . V projektu výchozí webové role by měl být název souboru. config WAIISHost.exe.config. Do tohoto souboru přidejte následující řádky:

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

V okně **vlastnosti** nastavte vlastnost **Kopírovat do výstupního adresáře** na **Kopírovat vždy**.

## <a name="next-steps"></a>Další kroky
Další informace o protokolování diagnostiky v Azure najdete v tématu [Povolení diagnostiky v azure Cloud Services a virtuálních počítačích](/azure/cloud-services/cloud-services-dotnet-diagnostics) a [Povolení protokolování diagnostiky pro Web Apps v Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
