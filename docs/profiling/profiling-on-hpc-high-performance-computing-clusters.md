---
title: Profilace v clusterech HPC (High Performance Computing) | Microsoft Docs
description: Přečtěte si, jak můžete profilovat výpočetní uzly clusterů HPC se systémem Microsoft Windows pomocí metody vzorkování sady Visual Studio Nástroje pro profilaci.
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3faea797d57ca8874a198e5ee1bf76708ee20e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917565"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>Profilování v clusterech HPC (High Performance Computing)

Pomocí metody vzorkování sady Visual Studio Nástroje pro profilaci můžete profilovat výpočetní uzly clusterů HPC se systémem Microsoft Windows. Další informace o HPC naleznete v tématu [Windows HPC](https://azure.microsoft.com/solutions/big-compute/) na webu společnosti Microsoft.

## <a name="prerequisites"></a>Požadavky

Chcete-li vytvořit profil na výpočetním uzlu HPC, je nutné provést následující akce:

- Nainstalujte sadu Microsoft HPC Pack 2008 na stejný počítač jako sadu Visual Studio. Počítač nemusí být součástí clusteru HPC. Sadu HPC Pack můžete nainstalovat na [webu služby Stažení softwaru](https://www.microsoft.com/download/details.aspx?id=4812).

- Nainstalujte .NET Framework 4 a samostatnou verzi Nástroje pro profilaci na výpočetním uzlu HPC. V instalačním médiu sady Visual Studio jsou k dispozici programy pro .NET Framework i samostatné profilery. **Poznámka:** Po instalaci .NET Framework a před instalací Nástroje pro profilaci je nutné restartovat výpočetní prostředí.

  Chcete-li nainstalovat .NET Framework 4 a samostatné Nástroje pro profilaci na aktivním výpočetním uzlu HPC a povolit profilaci na počítači s clustery, postupujte podle následujících kroků:

1. Otevřete okno příkazového řádku, které je nainstalováno se sadou HPC Pack.

2. Do samostatných příkazových výzev zadejte následující příkazy:

    1. `clusrun /all /scheduler:`*% Hlavnímu uzlu%% FxPath%*`/q /norestart`

    2. `clusrun /all /scheduler:`*% Hlavnímu uzlu%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:`*% Hlavnímu uzlu%% ProfilerPath%*`/q /norestart`

| | |
|------------------| - |
| *Hlavnímu uzlu* | Název hlavního uzlu clusteru |
| *%FxPath%* | Cesta k instalačnímu programu .NET Framework 4. V instalačním médiu sady Visual Studio je cesta: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Cesta k samostatné verzi instalačního programu Nástroje pro profilaci. V instalačním médiu sady Visual Studio je cesta: Standalone Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>Profil na výpočetním uzlu HPC

Relace profilování se konfiguruje pomocí Průvodce výkonem HPC k určení clusteru HPC a cílových informací. Můžete nastavit další možnosti na stránkách vlastností výkonnostní relace. Nástroje pro profilaci automaticky nasadit nezbytné cílové binární soubory a spustit Profiler a aplikaci HPC.

1. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem HPC**. Pokud příkaz není k dispozici, ujistěte se, že máte výše uvedené požadavky.

2. Na první stránce průvodce klikněte na tlačítko **Další** .

3. Na druhé stránce průvodce vyberte aplikaci, kterou chcete profilovat.

   - Chcete-li profilovat projekt, který je aktuálně otevřen v aplikaci [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , vyberte možnost **jedna nebo více dostupných projektů** a potom v seznamu vyberte název projektu.

   - Chcete-li profilovat binární soubor, který není v otevřeném projektu, vyberte **spustitelný soubor (. Soubor EXE)** .

4. Klikněte na **Next** (Další).

5. Na třetí stránce průvodce:

    - Pokud profilovat spustitelný soubor, který není v otevřeném projektu, zadejte cestu k binárnímu souboru v poli **Jaká je úplná cesta ke spustitelnému** souboru.

    - Pokud profilovat spustitelný soubor, který není v otevřeném projektu, můžete zadat argumenty příkazového řádku, které se mají předat procesu v **argumentech příkazového řádku**.

    - Ve **vzdáleném pracovním adresáři** zadejte cestu ke složce, kterou používají instance procesů na jednotlivých výpočetních uzlech.

    - V části **umístění nasazení** zadejte cestu k adresáři, který server HPC používá k přípravě imagí pro nasazení.

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

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Nastavení vlastností profilace HPC pomocí stránek vlastností relace výkonu

Vlastnosti relace výkonu, které nastavíte v průvodci profilací HPC, můžete změnit na stránce vlastností spuštění HPC na stránce vlastností výkonnostní relace. Další možnosti nastavíte na stránce Pokročilé vlastnosti HPC.

### <a name="to-open-the-performance-session-property-pages"></a>Otevření stránek vlastností výkonnostní relace

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

### <a name="advanced-properties"></a>Rozšířené vlastnosti

| Vlastnost | Popis |
|---------------------------------------| - |
| **Název projektu** | Název aktuálního [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projektu nebo řešení. |
| **Vyčistit při zastavení profileru** | V případě hodnoty true odstraní binární soubory, které byly nasazeny do spouštěcího adresáře. Soubory a adresáře vytvořené uživatelským programem nejsou v tomto kroku odebrány. Pokud se spouštěcí adresář a adresář pro nasazení vytvořily pomocí rozhraní IDE, rozhraní IDE se je pokusí odebrat, ale to neudělá, pokud mají soubory, které rozhraní IDE nenasazeno. |
| **Další soubory k nasazení** | Určuje středníkem oddělený seznam všech dalších souborů, které mají být nasazeny na výpočetním uzlu. Kliknutím na tlačítko se třemi tečkami (**...**) můžete vybrat více souborů pomocí dialogového okna. |
| **Mpiexec – příkaz** | Určuje aplikaci, která spustí aplikaci MPI. Výchozí hodnota je **mpiexec.exe** |
| **Argumenty mpiexec** | Určuje argumenty, které se mají předat příkazu mpiexec.exe. |
| **Požadované uzly v clusteru** | Určuje počet uzlů v clusteru, na kterých se má aplikace spustit. |
| **Nasazení souborů CRT** | V případě hodnoty true nasadí čas spuštění C/C++ v clusteru. |
| **Skript předběžného profilu** | Určuje cestu a název souboru skriptu, který má být spuštěn na místním vývojovém počítači před spuštěním relace profilování. |
| **Argumenty skriptu před profilem** | Určuje argumenty, které se mají předat skriptu předběžného profilu. |
| **Skript po profilaci** | Určuje cestu a název souboru skriptu, který má být spuštěn na místním vývojovém počítači po ukončení relace profilování. |
| **Argumenty skriptu po profilaci** | Určuje argumenty, které se mají předat skriptu po profilu. |
