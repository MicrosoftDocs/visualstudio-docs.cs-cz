---
title: Profilování clusterů HPC (High Performance Computing) | Dokumenty společnosti Microsoft
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f2d3949194dedab6d7e7ea2faa1aea304d889bc4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772117"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>Profil na clusterech HPC (high performance computing)

Můžete profilovat na výpočetních uzlech clusterů HPC systému Microsoft Windows pomocí metody vzorkování nástrojů profilování sady Visual Studio. Další informace o hpc naleznete [v tématu Windows HPC](https://azure.microsoft.com/solutions/big-compute/) na webu společnosti Microsoft.

## <a name="prerequisites"></a>Požadavky

Chcete-li profil na výpočetní uzel HPC, musíte provést následující kroky:

- Nainstalujte sadu Microsoft HPC Pack 2008 do stejného počítače jako visual studio. Počítač nemusí být součástí clusteru HPC. Balíček HPC Pack můžete nainstalovat na [webu služby Stažení softwaru](https://www.microsoft.com/download/details.aspx?id=4812).

- Nainstalujte rozhraní .NET Framework 4 a samostatnou verzi nástrojů profilování do výpočetního uzlu HPC. Instalace programů pro rozhraní .NET Framework a samostatného profileru jsou k dispozici na instalačním médiu sady Visual Studio. **Poznámka:** Výpočetní prostředky je nutné restartovat po instalaci rozhraní .NET Framework a před instalací nástrojů pro profilování.

  Chcete-li nainstalovat rozhraní .NET Framework 4 a samostatné nástroje pro profilování do aktivního výpočetního uzlu HPC a povolit profilování v clusteru, postupujte takto:

1. Otevřete okno příkazového řádku, které je nainstalováno pomocí sady HPC.

2. Na samostatných příkazových řádekch zadejte následující příkazy:

    1. `clusrun /all /scheduler:`*%HeadNode% %FxPath%*`/q /norestart`

    2. `clusrun /all /scheduler:`*%HeadNode%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:`*%HeadNode% %ProfilerPath%*`/q /norestart`

| | |
|------------------| - |
| *%HeadNode%* | Název hlavního uzlu clusteru. |
| *%FxPath%* | Cesta k instalačnímu programu rozhraní .NET Framework 4. Na instalačním médiu sady Visual Studio je cesta: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Cesta k samostatné verzi instalačního programu Nástroje profilování. Na instalačním médiu sady Visual Studio je cesta: Samostatný profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>Profil na výpočetním uzlu HPC

Relaci profilování nakonfigurujete pomocí Průvodce výkonem HPC k určení clusteru HPC a cílových informací. Můžete nastavit další možnosti na stránkách vlastností relace výkonu. Nástroje profilování automaticky nasadit potřebné cílové binární soubory a spustit profiler a aplikace HPC.

1. V nabídce **Analyzovat** klepněte na **tlačítko Spustit Průvodce výkonem HPC**. Pokud příkaz není k dispozici, ujistěte se, že máte výše uvedené požadavky.

2. Na první stránce průvodce klikněte na **Další.**

3. Na druhé stránce průvodce vyberte aplikaci, kterou chcete profilovat.

   - Chcete-li profilovat projekt, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]který je aktuálně otevřen v aplikaci , vyberte možnost **Jeden nebo více dostupných projektů** a potom vyberte název projektu ze seznamu.

   - Chcete-li profil binární soubor, který není v otevřeném projektu vyberte **spustitelný soubor (. EXE soubor).**

4. Klikněte na **Další**.

5. Na třetí stránce průvodce:

    - Pokud profilujete spustitelný soubor, který není v otevřeném projektu, zadejte cestu k binárnímu souboru v části **Co je úplná cesta ke spustitelnému souboru**.

    - Pokud profilujete spustitelný soubor, který není v otevřeném projektu, můžete zadat všechny argumenty příkazového řádku, které mají být předany procesu v **argumentech příkazového řádku**.

    - V **adresáři Vzdálené pracovní nastavení**zadejte cestu ke složce, která je používána instancemi procesu na jednotlivých výpočetních uzlech.

    - V **umístění nasazení**zadejte cestu k adresáři, který server HPC používá k vymezení bitových kopií pro nasazení.

6. Klikněte na **Další**.

7. Na čtvrté stránce průvodce:

    - V seznamu **Hlavní uzel** klikněte na počítač, který funguje jako hlavní uzel HPC v profilování spustit. Hlavní uzel může být "localhost", který umožňuje profilovat v místním počítači bez nutnosti clusteru.

    - V seznamu **Počet procesů** klikněte na počet instancí aplikace, které chcete spustit.

    - V seznamu **Možnosti profilování** vyberte cíl profilování.

         Chcete-li profilovat konkrétní proces v clusteru, vyberte možnost **Profil při hodnocení** a pak vrozené pořadí procesu z rozevíracího seznamu.

         Chcete-li profilovat proces nebo procesy spuštěné na konkrétním uzlu v clusteru HPC, vyberte možnost **Profil na uzlu** a pak vyberte uzel z rozevíracího seznamu.

8. Klikněte na **Další**.

9. Na páté stránce průvodce můžete okamžitě spustit profiler a proces profilování nebo spustit profilování později pomocí Průzkumníka výkonu.

    - Chcete-li profilování spustit okamžitě, vyberte **možnost Spustit profilování po dokončení průvodce,** nebo zrušte zaškrtnutí políčka, chcete-li profilování spustit ručně.

10. Klikněte na **Finish** (Dokončit).

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Nastavení vlastností profilování HPC pomocí stránek vlastností relace výkonu

Vlastnosti relace výkonu, které jste nastavili v Průvodci profilováním HPC na stránce Vlastnosti spuštění HPC na stránce vlastností relace výkonu. Na stránce Upřesnit vlastnosti HPC nastavíte další možnosti.

### <a name="to-open-the-performance-session-property-pages"></a>Otevření stránek vlastností relace výkonu

1. V případě potřeby otevřete soubor relace výkonu (.psess) v Průzkumníku výkonu. V nabídce **Soubor** klikněte na **Otevřít** a vyhledejte soubor.

2. V Průzkumníku výkonu klikněte pravým tlačítkem myši na název relace výkonu a potom klikněte na **příkaz Vlastnosti**.

3. V dialogovém okně Stránky vlastností použijte jednu z následujících metod:

    - Klikněte na **Obecné** a pak vyberte **Shromáždit v clusteru HPC,** chcete-li zapnout profilování HPC, nebo zrušte zaškrtnutí políčka pro zakázání profilování HPC.

    - Klepnutím na **vlastnosti spuštění HPC** změňte vlastnosti, které spouštějí aplikaci HPC.

    - Chcete-li nastavit další možnosti, klepněte na možnost **IHPC Advanced Properties** .

### <a name="hpc-launch-properties"></a>Vlastnosti spuštění HPC

|Vlastnost|Popis|
|--------------|-----------------|
|**Hlavní uzel**|Určuje počítač, který funguje jako hlavní uzel HPC v profilování spustit.|
|**Počet procesů**|Určuje počet instancí aplikace, které mají být spuštěny v profilované aplikaci.|
|**Profil na hodnosti**|Chcete-li profilovat konkrétní proces v clusteru, vyberte možnost **Profil při hodnocení** a pak vrozené pořadí procesu z rozevíracího seznamu.|
|**Profil na uzlu**|Chcete-li profilovat proces nebo procesy spuštěné na konkrétním uzlu v clusteru HPC, vyberte možnost **Profil na uzlu** a pak vyberte uzel z rozevíracího seznamu.|
|**Vzdálený pracovní adresář**|Určuje cestu ke složce, která je používána instancemi procesu na jednotlivých výpočetních uzlech.|
|**Umístění nasazení**|Určuje cestu k adresáři, který server HPC používá k vymezení bitových kopií pro nasazení.|

### <a name="advanced-properties"></a>Upřesňující vlastnosti

| Vlastnost | Popis |
|---------------------------------------| - |
| **Název projektu** | Název aktuálního [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projektu nebo řešení. |
| **Vyčistit při zastavení profileru** | Pokud true, odebere binární soubory, které byly nasazeny do adresáře spuštění. Soubory a adresáře vytvořené uživatelským programem nejsou v tomto kroku odebrány. Pokud adresář spuštění a adresář nasazení byly vytvořeny rozhraní IDE, ide pokusí odebrat, ale neučiní tak, pokud mají soubory, které nejsou nasazeny ide. |
| **Další soubory k nasazení** | Určuje seznam dalších souborů, které mají být nasazeny v výpočetním uzlu, seseznamem dalších souborů, které mají být nasazeny. Klepnutím na tlačítko se třemi tečkami (**...**) můžete vybrat více souborů pomocí dialogového okna. |
| **Mpiexec, příkaz** | Určuje aplikaci, která spustí aplikaci MPI. Výchozí hodnota je **mpiexec.exe** |
| **Argumenty Mpiexec** | Určuje argumenty, které mají být předávány příkazu mpiexec.exe. |
| **Požadované uzly v clusteru** | Určuje počet uzlů v clusteru, ve kterém má být aplikace spuštěna. |
| **Nasazení souborů CRT** | Pokud true, nasazuje c/c++ doba běhu v clusteru. |
| **Skript s předběžným profilem** | Určuje cestu a název souboru skriptu, který má být spuštěn v místním vývojovém počítači před zahájením relace profilování. |
| **Argumenty skriptu před profilem** | Určuje argumenty, které mají být předávány skriptu předběžného profilu. |
| **Skript post-profil** | Určuje cestu a název souboru skriptu, který má být spuštěn v místním vývojovém počítači po ukončení relace profilování. |
| **Argumenty skriptu pro profil** | Určuje argumenty, které mají být předávány skriptu post-profile. |
