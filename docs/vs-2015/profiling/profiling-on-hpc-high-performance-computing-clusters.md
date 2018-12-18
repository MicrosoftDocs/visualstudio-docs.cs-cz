---
title: Profilace v prostředí HPC (High Performance Computing) clusterů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6b0838a7fb3db86290647fadec9ca3572cbdf90
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809152"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilace v klastrech HPC (High Performance Computing)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete provádět profilaci na výpočetních uzlech clusterů Microsoft Windows HPC pomocí metody odběru vzorků [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] nebo [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] nástroje pro profilaci. Další informace o HPC naleznete v tématu [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) na webu společnosti Microsoft.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li Profilovat na výpočetním uzlu HPC, postupujte takto:  
  
- Instalace sady Microsoft HPC Pack 2008 na stejném počítači jako [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Počítač nemá se jednat o část cluster prostředí HPC. Instalací sady HPC Pack na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
- Nainstalujte [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] a samostatné verze nástrojů pro profilaci na HPC v prostředí výpočetního uzlu. Instalace aplikací pro obě [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a samostatný profiler jsou k dispozici na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] instalačního média. **Poznámka:** po instalaci je nutné restartovat výpočetní [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a před instalací nástrojů pro profilaci.  
  
  Chcete-li nainstalovat [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] a samostatného nástroje pro profilaci na aktivní prostředí HPC výpočetních uzlů a povolit profilaci na počítači clusteru, postupujte podle těchto kroků:  
  
1.  Otevřete okno příkazového řádku, který je nainstalován se sadou HPC pack.  
  
2.  Samostatné příkazového řádku zadejte následující příkazy:  
  
    1.  `clusrun /all /scheduler:` *Hlavní uzel % % FxPath %* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *% Hlavního uzlu* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *Hlavní uzel % % ProfilerPath %* `/q /norestart`  
  
|||  
|-|-|  
|*% Hlavního uzlu*|Název hlavního uzlu clusteru.|  
|*%FxPath%*|Cesta k [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] Instalační služby. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] instalačním médiu je cesta: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Cesta k verzi samostatného instalačního programu nástrojů pro profilaci sady. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] instalačním médiu je cesta: samostatná Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Profilace do výpočetního uzlu HPC  
 Konfigurace relace profilování pomocí Průvodce výkonem HPC můžete určit informace o pro cluster a cílové prostředí HPC. Můžete nastavit další možnosti na stránkách vlastností relace výkonu. Nástroje pro profilaci automaticky nasadit binární soubory nezbytné cíl a spustit profiler a aplikací HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Chcete-li Profilovat do výpočetního uzlu HPC  
  
1.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem HPC**. Pokud příkazu není k dispozici, ujistěte se, že jsou splněné požadavky uvedené výše.  
  
2.  Klikněte na tlačítko **Další** na první stránce průvodce.  
  
3.  Na druhé stránce průvodce vyberte aplikaci, kterou chcete Profilovat.  
  
    -   Chcete-li Profilovat projekt, který je právě otevřen v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], vyberte **jeden nebo více dostupných projektů** možnost a potom ze seznamu vyberte název projektu.  
  
    -   Chcete-li Profilovat binární soubor, který není v otevřeném projektu vyberte **spustitelný soubor (. Soubor EXE)** možnost.  
  
4.  Klikněte na tlačítko **Další**.  
  
5.  Na třetí stránce průvodce:  
  
    -   Pokud profilujete spustitelný soubor, který není v otevřeném projektu, zadejte cestu k binárnímu souboru v **co je úplná cesta ke spustitelnému souboru**.  
  
    -   Pokud profilujete spustitelný soubor, který není v otevřeném projektu, můžete zadat jakékoli argumenty příkazového řádku k předání do procesu v **argumenty příkazového řádku**.  
  
    -   V **vzdálené pracovní adresář**, zadejte cestu ke složce, který je používán instancí procesu na jednotlivých výpočetních uzlech.  
  
    -   V **umístění nasazení**, zadejte cestu k adresáři, který používá HPC server do fáze imagí pro nasazení.  
  
6.  Klikněte na tlačítko **Další**.  
  
7.  Na čtvrté stránce průvodce:  
  
    -   V **hlavní uzel** seznamu, klikněte na počítač, který funguje jako hlavní uzel HPC při spuštění profilace. Hlavní uzel může být "localhost", který vám umožní do profilu na místním počítači bez nutnosti pro cluster.  
  
    -   V **počet procesů** seznamu, klikněte na počet instancí aplikace ke spuštění.  
  
    -   Z **profilace možnosti** vyberte cíli profilování.  
  
         Chcete-li Profilovat konkrétního procesu v clusteru, vyberte **profil v pořadí** možnost a potom z rozevíracího seznamu vyberte řád procesu.  
  
         Chcete-li Profilovat proces nebo procesy, které běží na konkrétním uzlu v clusteru HPC, vyberte **profilu na uzlu** možnosti a pak vyberte uzel z rozevíracího seznamu.  
  
8.  Klikněte na tlačítko **Další**.  
  
9. Na páté stránce průvodce můžete k okamžitému spuštění profileru a profilování procesu nebo spuštění profilování později pomocí prohlížeče výkonu.  
  
    -   Vyberte **spustit profilaci po dokončení průvodce** ke spuštění profilace okamžitě, nebo ponechejte políčko nezaškrtnuté, chcete-li spustit profilování ručně.  
  
10. Klikněte na tlačítko **Dokončit**.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Nastavení vlastností prostředí HPC profilace pomocí stránky vlastností relace výkonu  
 Můžete změnit vlastnosti relace výkonu, které jste nastavili v prostředí HPC profilace průvodci na stránce vlastností spuštění HPC na stránce vlastností relace výkonu. Můžete nastavit další možnosti na stránce HPC Upřesnit vlastnosti.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>K otevření stránek vlastností relace výkonu  
  
1.  V případě potřeby otevřete soubor výkonnostní relace (.psess) v prohlížeči výkonu. Na **souboru** nabídky, klikněte na tlačítko **otevřít** a soubor vyhledejte.  
  
2.  V prohlížeči výkonu, klikněte pravým tlačítkem na název relace výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
3.  V dialogovém okně stránky vlastností použijte jednu z následujících metod:  
  
    -   Klikněte na tlačítko **Obecné** a pak vyberte **shromažďování v clusteru HPC** HPC profilace nebo zrušte zaškrtnutí políčka Zakázat HPC profilace.  
  
    -   Klikněte na tlačítko **HPC spuštění vlastnosti** -li změnit vlastnosti, které spouští aplikace HPC.  
  
    -   Klikněte na tlačítko **HPC Upřesnit vlastnosti** můžete nastavit další možnosti  
  
### <a name="hpc-launch-properties"></a>Vlastnosti spuštění HPC  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Hlavní uzel**|Určuje počítač, který funguje jako hlavní uzel HPC během spuštění profilování.|  
|**Počet procesů**|Určuje počet instancí aplikace na spouštění v profilované aplikaci.|  
|**Provádějte profilaci na pořadí**|Chcete-li Profilovat konkrétního procesu v clusteru, vyberte **profil v pořadí** možnost a potom z rozevíracího seznamu vyberte řád procesu.|  
|**Provádějte profilaci na uzlu**|Chcete-li Profilovat proces nebo procesy, které běží na konkrétním uzlu v clusteru HPC, vyberte **profilu na uzlu** možnosti a pak vyberte uzel z rozevíracího seznamu.|  
|**Vzdálený pracovní adresář**|Určuje cestu ke složce, který je používán instancí procesu na jednotlivých výpočetních uzlech.|  
|**Umístění nasazení**|Určuje cestu k adresáři, který používá HPC server do fáze imagí pro nasazení.|  
  
### <a name="advanced-properties"></a>Upřesnit vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**název projektu**|Název aktuálního [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] projekt nebo řešení.|  
|**Vyčištění při zastavení profileru**|V případě hodnoty true odeberou binární soubory, které jsou nasazené v prováděcím adresáři. V tomto kroku se neodeberou soubory a adresáře vytvořené programem uživatele. Pokud provádění adresář a adresáře nasazení vytvořené integrovaným vývojovým prostředím, rozhraní IDE se pokusí odebrat je ale nelze provést, pokud mají soubory nejsou nasazené v integrovaném vývojovém prostředí.|  
|**Další soubory k nasazení**|Určuje středníky oddělený seznam případných dalších souborů k nasazení na výpočetním uzlu. Můžete kliknout na tlačítko se třemi tečkami (**...** ) Chcete-li vybrat více souborů pomocí dialogového okna.|  
|**Příkaz Mpiexec**|Určuje aplikaci, která spustí aplikace MPI. Výchozí hodnota je **mpiexec.exe**|  
|**Argumenty Mpiexec**|Určuje argumenty pro příkaz mpiexec.exe.|  
|**Požadované uzly v clusteru**|Určuje počet uzlů v clusteru, ve kterém se spustí aplikace.|  
|**Nasazení souborů CRT**|V případě hodnoty true nasadí C/C++, doba spuštění v clusteru.|  
|**Předem profilu skriptu**|Určuje cestu a název souboru skriptu ke spuštění v místním vývojovém počítači před spuštěním relace profilování.|  
|**Předem profilu argumenty skriptu**|Určuje argumenty předané skriptu předběžné profilu.|  
|**Skript po profilu**|Určuje cestu a název souboru skriptu ke spuštění v místním vývojovém počítači po ukončení relace profilování.|  
|**Argumenty skriptu po profilu**|Určuje argumenty předané skriptu po profilu.|



