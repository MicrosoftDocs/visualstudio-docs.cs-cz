---
title: Profilace v clusterech HPC (High Performance Computing) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b63f9ddf29ff74a4aa4bf089c266e12e37bb2f50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535535"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilování v klastrech HPC (High Performance Computing)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete profilovat výpočetní uzly clusterů HPC se systémem Microsoft Windows pomocí metody vzorkování [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] Nástroje pro profilaci nebo. Další informace o HPC naleznete v tématu [Big Compute: HPC & Batch](https://azure.microsoft.com/solutions/big-compute/) na webu společnosti Microsoft.  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li vytvořit profil na výpočetním uzlu HPC, je nutné provést následující akce:  
  
- Nainstalujte sadu Microsoft HPC Pack 2008 na stejný počítač jako [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . Počítač nemusí být součástí clusteru HPC. Sadu HPC Pack můžete nainstalovat na [webu služby Stažení softwaru](https://www.microsoft.com/download/details.aspx?id=2800).  
  
- Do [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] výpočetního uzlu HPC nainstalujte a samostatnou verzi nástroje pro profilaci. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]V instalačním médiu nástroje jsou k dispozici i samostatné profilery [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] . **Poznámka:** Po nainstalování [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a před instalací nástroje pro profilaci musíte výpočetní prostředí restartovat.  
  
  Pokud chcete nainstalovat [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] a samostatné nástroje pro profilaci na aktivním výpočetním uzlu HPC a povolit profilaci na počítači s clustery, postupujte takto:  
  
1. Otevřete okno příkazového řádku, které je nainstalováno se sadou HPC Pack.  
  
2. Do samostatných příkazových výzev zadejte následující příkazy:  
  
    1. `clusrun /all /scheduler:`*% Hlavnímu uzlu%% FxPath%*`/q /norestart`  
  
    2. `clusrun /all /scheduler:`*% Hlavnímu uzlu%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3. `clusrun /all /scheduler:`*% Hlavnímu uzlu%% ProfilerPath%*`/q /norestart`  
  
|Element syntax|Popis|  
|-|-|  
|*Hlavnímu uzlu*|Název hlavního uzlu clusteru|  
|*%FxPath%*|Cesta k [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] Instalačnímu programu Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] instalačním médiu je cesta: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Cesta k samostatné verzi instalačního programu Nástroje pro profilaci. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] instalačním médiu je cesta: Standalone Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Profilace na výpočetním uzlu HPC  
 Relace profilování se konfiguruje pomocí Průvodce výkonem HPC k určení clusteru HPC a cílových informací. Můžete nastavit další možnosti na stránkách vlastností výkonnostní relace. Nástroje pro profilaci automaticky nasadit nezbytné cílové binární soubory a spustit Profiler a aplikaci HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Profilování na výpočetním uzlu HPC  
  
1. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem HPC**. Pokud příkaz není k dispozici, ujistěte se, že máte výše uvedené požadavky.  
  
2. Na první stránce průvodce klikněte na tlačítko **Další** .  
  
3. Na druhé stránce průvodce vyberte aplikaci, kterou chcete profilovat.  
  
    - Chcete-li profilovat projekt, který je aktuálně otevřen v aplikaci [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , vyberte možnost **jedna nebo více dostupných projektů** a potom v seznamu vyberte název projektu.  
  
    - Chcete-li profilovat binární soubor, který není v otevřeném projektu, vyberte **spustitelný soubor (. Soubor EXE)** .  
  
4. Klikněte na **Next** (Další).  
  
5. Na třetí stránce průvodce:  
  
    - Pokud profilovat spustitelný soubor, který není v otevřeném projektu, zadejte cestu k binárnímu souboru v poli **Jaká je úplná cesta ke spustitelnému**souboru.  
  
    - Pokud profilovat spustitelný soubor, který není v otevřeném projektu, můžete zadat argumenty příkazového řádku, které se mají předat procesu v **argumentech příkazového řádku**.  
  
    - Ve **vzdáleném pracovním adresáři**zadejte cestu ke složce, kterou používají instance procesů na jednotlivých výpočetních uzlech.  
  
    - V části **umístění nasazení**zadejte cestu k adresáři, který server HPC používá k přípravě imagí pro nasazení.  
  
6. Klikněte na **Next** (Další).  
  
7. Na čtvrté stránce průvodce:  
  
    - V seznamu **hlavní uzel** klikněte na počítač, který funguje jako hlavní uzel HPC při spuštění profilace. Hlavní uzel může být "localhost", který umožňuje profilovat místní počítač bez nutnosti clusteru.  
  
    - V seznamu **počet procesů** klikněte na počet instancí aplikace, které mají být spuštěny.  
  
    - V seznamu **možností profilace** vyberte cíl profilace.  
  
         Chcete-li profilovat určitý proces v clusteru, vyberte možnost **profil na základě pořadí** a potom v rozevíracím seznamu vyberte pořadí procesu.  
  
         Chcete-li profilovat proces nebo procesy, které jsou spuštěny na konkrétním uzlu v clusteru HPC, vyberte možnost **profil v uzlu** a potom v rozevíracím seznamu vyberte uzel.  
  
8. Klikněte na **Next** (Další).  
  
9. Na páté stránce průvodce se můžete rozhodnout pro okamžité spuštění profileru a procesu profilování nebo pro pozdější spuštění profilování pomocí Prohlížeč výkonu.  
  
    - Vyberte **Spustit profilaci po dokončení průvodce** pro okamžité spuštění profilování, nebo zrušte zaškrtnutí políčka pro spuštění profilování ručně.  
  
10. Klikněte na **Finish** (Dokončit).  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Nastavení vlastností profilace HPC pomocí stránek vlastností výkonnostní relace  
 Vlastnosti relace výkonu, které nastavíte v průvodci profilací HPC, můžete změnit na stránce vlastností spuštění HPC na stránce vlastností výkonnostní relace. Další možnosti nastavíte na stránce Pokročilé vlastnosti HPC.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Otevření stránek vlastností výkonnostní relace  
  
1. V případě potřeby otevřete v Prohlížeč výkonu soubor relace výkonu (. psess). V nabídce **soubor** klikněte na **otevřít** a vyhledejte soubor.  
  
2. V Prohlížeč výkonu klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.  
  
3. V dialogovém okně stránky vlastností použijte jednu z následujících metod:  
  
    - Klikněte na **Obecné** a potom vyberte **shromáždit na clusteru HPC** , abyste mohli profilaci HPC zapnout nebo zrušit zaškrtnutí tohoto políčka, abyste zakázali profilaci HPC.  
  
    - Kliknutím na **Vlastnosti spuštění HPC** změňte vlastnosti, které SPOUŠTĚJÍ aplikaci HPC.  
  
    - Kliknutím na **Upřesnit vlastnosti HPC** nastavte další možnosti.  
  
### <a name="hpc-launch-properties"></a>Vlastnosti spuštění HPC  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Hlavní uzel**|Určuje počítač, který funguje jako hlavní uzel HPC při spuštění profilace.|  
|**Počet procesů**|Určuje počet instancí aplikace, které mají být spuštěny v profilované aplikaci.|  
|**Profil v pořadí**|Chcete-li profilovat určitý proces v clusteru, vyberte možnost **profil na základě pořadí** a potom v rozevíracím seznamu vyberte pořadí procesu.|  
|**Profil na uzlu**|Chcete-li profilovat proces nebo procesy, které jsou spuštěny na konkrétním uzlu v clusteru HPC, vyberte možnost **profil v uzlu** a potom v rozevíracím seznamu vyberte uzel.|  
|**Vzdálený pracovní adresář**|Určuje cestu ke složce, která je používána instancemi procesů na jednotlivých výpočetních uzlech.|  
|**Umístění nasazení**|Určuje cestu k adresáři, který server HPC používá k přípravě imagí pro nasazení.|  
  
### <a name="advanced-properties"></a>Upřesnit vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Název projektu**|Název aktuálního [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] projektu nebo řešení.|  
|**Vyčistit při zastavení profileru**|V případě hodnoty true odstraní binární soubory, které byly nasazeny do spouštěcího adresáře. Soubory a adresáře vytvořené uživatelským programem nejsou v tomto kroku odebrány. Pokud se spouštěcí adresář a adresář pro nasazení vytvořily pomocí rozhraní IDE, rozhraní IDE se je pokusí odebrat, ale to neudělá, pokud mají soubory, které rozhraní IDE nenasazeno.|  
|**Další soubory k nasazení**|Určuje středníkem oddělený seznam všech dalších souborů, které mají být nasazeny na výpočetním uzlu. Kliknutím na tlačítko se třemi tečkami (**...**) můžete vybrat více souborů pomocí dialogového okna.|  
|**Mpiexec – příkaz**|Určuje aplikaci, která spustí aplikaci MPI. Výchozí hodnota je **mpiexec.exe**|  
|**Argumenty mpiexec**|Určuje argumenty, které se mají předat příkazu mpiexec.exe.|  
|**Požadované uzly v clusteru**|Určuje počet uzlů v clusteru, na kterých se má aplikace spustit.|  
|**Nasazení souborů CRT**|V případě hodnoty true nasadí čas spuštění C/C++ v clusteru.|  
|**Skript předběžného profilu**|Určuje cestu a název souboru skriptu, který má být spuštěn na místním vývojovém počítači před spuštěním relace profilování.|  
|**Argumenty skriptu před profilem**|Určuje argumenty, které se mají předat skriptu předběžného profilu.|  
|**Skript po profilaci**|Určuje cestu a název souboru skriptu, který má být spuštěn na místním vývojovém počítači po ukončení relace profilování.|  
|**Argumenty skriptu po profilaci**|Určuje argumenty, které se mají předat skriptu po profilu.|
