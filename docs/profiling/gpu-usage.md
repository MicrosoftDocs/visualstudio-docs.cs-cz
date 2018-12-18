---
title: Využití GPU | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8265ae81b5ea1c6395af352f8f981f41f77cea8
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220941"
---
# <a name="gpu-usage"></a>Využití GPU

Pomocí nástroje využití GPU ve výkon sady Visual Studio a centra diagnostiky sady pro lepší pochopení základní hardware využití vaší aplikace Direct3D. Pomůže vám zjistit, jestli je výkon vaší aplikace vázané na procesor nebo vázané na GPU a získat přehled o tom, jak můžete použít hardwarové platformy efektivněji. Využití GPU podporuje aplikace používající rozhraní Direct3D 12, Direct3D 11 a Direct3D 10; nepodporuje se jiné grafické rozhraní API, jako je například Direct2D nebo OpenGL.

Tento snímek obrazovky ukazuje **sestava využití GPU** okno:

![Sestava využití GPU, s konkrétním procesoru a GPU časové osy](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Požadavky

Následující požadavky pro použití pomocí nástroje využití GPU přidejte požadavky na nástroj Diagnostika grafiky.

- GPU a ovladače, které podporují instrumentace nezbytné časování.

  > [!NOTE]
  > Další informace o podporovaný hardware a ovladačů najdete v tématu [hardwarem a ovladači podporují](#hwsupport) na konci tohoto dokumentu.

  Další informace o požadavcích diagnostiky grafiky, naleznete v tématu [Začínáme](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="using-the-gpu-usage-tool"></a>Pomocí nástroje využití GPU

 Při spuštění aplikace v systému pomocí nástroje využití GPU bude Visual Studio v reálném čase vytvoří relaci diagnostiky tohoto grafy souhrnné informace o využití GPU a vykreslování výkonu vaší aplikace.

**Chcete-li spustit nástroj využití GPU:**

1. V hlavní nabídce zvolte **ladění**, pak **výkon a Diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).

2. V Centru pro výkon a diagnostiku, zaškrtněte políčko vedle položky **využití GPU**. Volitelně můžete zaškrtnutím políčka vedle jiné nástroje, které vás zajímají. Můžete spustit několik výkonu a diagnostické nástroje souběžně, což umožňuje získat komplexnější přehled o výkonu vaší aplikace.

    ![Zvolte diagnostické nástroje, které chcete použít. ](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Ne všechny výkonu a diagnostické nástroje je možné ve stejnou dobu.

3. Zvolte modrá **Start** tlačítko v dolní části rozcestníku výkon a Diagnostika ke spouštění vaší aplikace v nabídce Nástroje, které jste vybrali.

   Základní informace, které se zobrazí v reálném čase zahrnuje časování snímků, frekvence snímků a využití GPU. Všechny tyto údaje se zaneseny do nezávisle na sobě grafu, ale použít obecného časového měřítka, takže můžete snadno se týkají mezi nimi.

   **Rámec doba (ms)** a **snímků za sekundu (FPS)** grafy má dvě červené, vodorovných čar, který cílí výkonu zobrazit 30 a 60 snímků za sekundu. V **rámec čas** grafu, vaše aplikace překračuje cíl výkonnosti při graf je pod řádkem a výpadky cíl po nad čáru grafu. Pro snímky za druhé grafu, je opakem – aplikace překračuje cílový výkon při graf je vyšší než řádku a výpadky cíl, když je graf pod řádkem. Tyto grafy se používají především, chcete-li získat základní představu o výkonu vaší aplikace a k identifikaci slow-downs, které můžete chtít prozkoumat, jako je například náhlému poklesu v snímkovou frekvenci nebo špička využití GPU.

   Při spouštění vaší aplikace v pomocí nástroje využití GPU se relace diagnostiky taky shromažďuje podrobné informace o událostí grafiky, které byly spouštěny na GPU. Tyto informace slouží ke generování podrobnější sestavu o tom, jak vaše aplikace využívá hardware. Vzhledem k tomu, že tato sestava trvá nějakou dobu ke generování ze shromážděných informací, je k dispozici pouze po dokončení shromažďování údajů o informace diagnostickou relaci.

   Když chcete podívat na výkon nebo využití vydávání lépe, zastavte shromažďování informací o výkonu, takže lze generovat sestavy.

**Umožňuje generovat a prohlížet sestavy využití GPU:**

1. V dolní části okna diagnostické relace, zvolte **zastavit shromažďování** propojení nebo stisknutím klávesy **Zastavit** v levém horním rohu.

   ![Shromažďování informací o časování GPU a CPU. ](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. V horní části sestavy vyberte oddíl jednu z grafů, které ukazuje tento problém, že který chcete prozkoumat. Výběr může být až 3 sekund; delší oddíly se zkrátí spíš na začátku.

   ![Příspěvek&#45;kolekce, vyberte oblast, chcete-li zobrazit podrobnosti](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. V dolní části sestavy, zvolte **podrobnosti** odkaz v **.. klikněte zde k zobrazení podrobností o využití GPU pro tento rozsah** zprávu zobrazíte podrobné časová osa vašeho výběru.

   ![Příspěvek&#45;kolekce s rozsah vybraný](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   Tato volba otevře nový dokument s kartami, která obsahuje sestavu. Sestava využití GPU vám se zobrazí při spuštění události grafiky na CPU, až dorazí do místa GPU a jak dlouho trvá GPU k jeho provedení. Tyto informace pomáhají identifikovat problémová místa a příležitosti pro zvýšení paralelismu ve vašem kódu.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exportovat do GPUView nebo Analyzátor výkonu Windows

Od verze Visual Studio 2017, můžete otevřít tato data s [GPUView](/windows-hardware/drivers/display/using-gpuview) a [Analyzátor výkonu Windows](/windows-hardware/test/wpt/windows-performance-analyzer). Stačí vybrat **otevřít v GpuView** nebo **otevřít ve WPA** odkazy nachází v pravém dolním rohu diagnostické relace.

![Otevřít v...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Pomocí sestavy využití GPU

Horní části sestavy využití GPU zobrazuje časové osy pro procesoru aktivita, aktivita vykreslování GPU a aktivitu kopírování, která GPU. Tyto časové rámce jsou rozděleny ve světle šedý, svislé pruhy, které označují impulsu VSync zobrazení. Frekvence pruhy odpovídá obnovovací frekvence jednoho zobrazení (vybrali pomocí **zobrazení** rozevíracího seznamu) tato data využití GPU se shromažďovala ze. Protože zobrazení můžou mít vyšší obnovovací frekvence než cílový výkon vaší aplikace, nemusí být 1 až 1 vztah mezi impulsu vsync a chcete, aby vaše aplikace k dosažení frekvenci snímků. Podle jeho cíl výkonnosti, musí aplikace dokončete veškeré zpracování, proveďte vykreslování a volání Present() na cílové snímkové frekvence. Vykreslený snímek nebudou zobrazovat až do další impulsu vsync po Present(), i když.

Dolní části zobrazí seznam událostí grafiky, ke kterým došlo během časového období sestavy.

Tady je **sestava využití GPU** okno:

![Sestava využití GPU, s konkrétním procesoru a GPU časové osy](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Vyberte událost v dolní části sestavy, zobrazí se v odpovídající události v příslušné časové osy značku. Obvykle jednu událost ve vlákně procesoru ukazuje volání rozhraní API další událost v jednom z časové osy GPU se zobrazí po dokončení úlohy GPU. Podobně když vyberete událost na časové ose, sestava zvýrazní odpovídající událost v dolní části sestavy. Při zvětšení mimo časové osy v horní části sestavy, jsou viditelné pouze události, která se nejvíce časově náročné. Pokud chcete zobrazit události, které mají kratší dobu trvání, zvětšení časové osy stisknutím klávesy Ctrl a kolečka na zařízení nebo změny velikosti ovládacího prvku v levém dolním rohu na horním panelu. Můžete také přetáhnout na časové ose panelu obsahu můžete procházet zaznamenané události.

To vám umožní najít, co hledáte, filtr sestava využití GPU na základě procesu názvy, ID vlákna a název události. Kromě toho můžete zvolit, které zobrazení obnovovací frekvence určuje vysnc řádky. Můžete řadit události hierarchicky Pokud vaše aplikace používá [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) rozhraní pro příkazy vykreslování skupiny.

 Tady jsou další podrobnosti:

|Ovládací prvek filtru|Popis|
|--------------------|-----------------|
|**Proces**|Název procesu, které vás zajímají. V tomto rozevíracím seznamu jsou zahrnuté všechny procesy, které používá GPU během diagnostické relace. Barva spojených s procesem v této rozevírací seznam je barva aktivity vlákna ve níže časové osy.|
|**vlákno**|ID vlákna, které vás zajímají. Ve vícevláknové aplikaci tyto informace můžete izolovat konkrétní vlákna, které patří k procesu, který vás zajímá. Události související s vybranou vlákna jsou vyznačené na každé časové osy.|
|**Zobrazení**|Počet zobrazení se zobrazí jehož obnovovací frekvence **Poznámka:** některé ovladače lze nastavit zobrazíte více fyzických zobrazí jako jeden, velké virtuální zobrazení. Jediné zobrazení uvedené, může se zobrazit i v případě, že tento počítač má připojené více monitorů.|
|**Filtr**|Klíčová slova, které vás zajímají. Události v dolní části sestavy bude obsahovat pouze ty, které odpovídají klíčové slovo, ať už zcela nebo zčásti. Více klíčových slov můžete určit jejich oddělením středníkem (;).|
|**Hierarchie řazení**|Zaškrtávací políčko, která označuje, zda události – definice prostřednictvím uživatelské značky--hierarchií jsou zachovány nebo ignorovat.|

 Seznam událostí v dolní části sestavy využití GPU zobrazují podrobnosti o každé události.

|Sloupec|Popis|
|------------|-----------------|
|**Název události**|Název události grafiky. Události obvykle odpovídá událost na časové ose vlákna CPU a časová osa událost GPU.<br /><br /> Názvy událostí může být "zjednodušeně", pokud využití GPU se nepodařilo zjistit název události. Další informace najdete v poznámce dál v této tabulce.|
|**Spuštění CPU (ns)**|Čas události se inicializovala na CPU při volání rozhraní API Direct3D. Čas se měří v nanosekundách, vzhledem k při spuštění aplikace.|
|**Spuštění GPU (ns)**|Čas události se inicializovala na GPU. Čas se měří v nanosekundách, vzhledem k při spuštění aplikace.|
|**Doba trvání GPU (ns)**|Čas události trvalo dokončení na GPU v nanosekundách.|
|**Název procesu**|Název aplikace, odkud událost pochází.|
|**ID vlákna**|ID vlákna, odkud událost pochází.|

> [!IMPORTANT]
> Pokud GPU nebo ovladač nepodporují funkce nezbytné instrumentace, všechny události se zobrazí jako "zjednodušeně". Ujistěte se, že aktualizace ovladače GPU a zkuste to znovu, pokud dochází k tomuto problému. Další informace najdete v tématu [hardwarem a ovladači podporují](#hwsupport) níže.

## <a name="gpu-usage-settings"></a>Nastavení využití GPU

Můžete nakonfigurovat pomocí nástroje využití GPU se odložit kolekce profilace informace, a ne od lze shromažďovat informace o co nejdříve po spuštění aplikace. Protože velikost profilování informace můžou být důležité, tato akce je užitečná, když víte, že zpomalení výkonu vaší aplikace se zobrazí až později.

**Chcete-li odložit, profilace od začátku aplikace:**

1. V hlavní nabídce zvolte **ladění**, pak **výkon a Diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).

2. V Centru pro výkon a diagnostiku, postupujte **nastavení** odkaz **využití GPU**.

3. V části **konfigurace profilace GPU**na **Obecné** stránky vlastností, zrušte **zahájíte profilaci na začátku aplikace** zaškrtávací políčko odložit profilace.

   ![Konfigurace při spuštění shromažďování využití GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Odkládá se profilování se aktuálně nepodporuje pro aplikace rozhraní Direct3D 12.

Po spuštění aplikace v systému pomocí nástroje využití GPU dodatečný odkaz bude k dispozici v dolní části okna nástroje využití GPU. Aby začal shromažďovat analytické informace, zvolte **Start** odkaz v **zahájení shromažďování dalších podrobných dat o využití GPU** zprávy.

## <a name="hwsupport"></a> Hardware a podpoře ovladačů

Jsou podporovány následující hardwarové GPU a ovladače:

|Dodavatele|Popis GPU|Požadovaná verze ovladače|
|------------|---------------------|-----------------------------|
|Intel®|4. generace Intel® procesory (Haswell)<br /><br /> – Procesor Intel® HD, High Density grafiky (GT1)<br />– Procesor Intel® HD, High Density grafiky 4200 (GT2)<br />– Procesor Intel® HD, High Density grafiky 4400 (GT2)<br />– Procesor Intel® HD, High Density grafiky 4600 (GT2)<br />– P4600 procesor Intel® HD, High Density grafiky (GT2)<br />– P4700 procesor Intel® HD, High Density grafiky (GT2)<br />– Procesor Intel® HD, High Density grafiky 5000 (GT3)<br />– Grafika procesor Intel® Iris™ 5100 (GT3)<br />– Procesor Intel® Iris™ Pro grafiky 5200 (GT3e)|--(použijte nejnovější ovladače)|
|AMD®|Většina od AMD Radeon™ HD, High Density 7000-series (nezahrnuje AMD Radeon™ HD, High Density 7350 7670)<br /><br /> Akcelerátory AMD Radeon™ GPU, AMD FirePro™ GPU a AMD FirePro GPU poskytuje funkci architektura grafiky Core další (GCN).<br /><br /> AMD® E-Series a AMD A-series urychlení zpracování jednotky (APU) poskytuje funkci architektura grafiky Core další (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 nebo vyšší|
|NVIDIA®|Většina od NVIDIA GeForce® 400-series.<br /><br /> Poskytuje funkci architektura Fermi™, Kepler™ nebo Maxwell™ grafických procesorů NVIDIA® GeForce®, která využívá GPU NVIDIA Quadro® a grafický procesor NVIDIA® Tesla™ akcelerátory.|343.37 nebo vyšší|

 V tuto chvíli nepodporuje konfigurace s více GPU například NVIDIA® SLI™ a AMD Crossfire™. Nastavení hybridní grafiky, jako je například NVIDIA® Optimus™ a AMD Enduro™ jsou podporovány.

## <a name="see-also"></a>Viz také:

- [Vyřešit Palčivé problémy s grafikou nástroje pro vaše hry pomocí DirectX (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [Nástroj využití GPU v sadě Visual Studio (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [Nástroj využití GPU ve Visual Studio 2013 Update 4 CTP1 (blog)](https://blogs.msdn.microsoft.com/vcblog/2014/09/04/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [Využití GPU pro DirectX v sadě Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [GPUView](/windows-hardware/drivers/display/using-gpuview)
- [Analyzátor výkonu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)