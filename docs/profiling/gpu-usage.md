---
title: Využití GPU | Dokumenty společnosti Microsoft
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f16a518542e8acab636da6e395fdfee8d7a25085
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969804"
---
# <a name="gpu-usage"></a>Využití GPU

Pomocí nástroje využití GPU v centru Visual Studio Performance and Diagnostics Hub lépe porozumíte vysoké muzice hardwaru vaší aplikace Direct3D. Pomůže vám zjistit, jestli je výkon vaší aplikace vázaný na procesor nebo gpu a získat přehled o tom, jak můžete efektivněji používat hardware platformy. Využití GPU podporuje aplikace, které používají Direct3D 12, Direct3D 11 a Direct3D 10; nepodporuje jiná grafická rozhraní API, například Direct2D nebo OpenGL.

Tento snímek obrazovky ukazuje okno **Sestava využití GPU:**

![Sestava využití GPU s časovými osami PROCESORU a GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Požadavky

Následující požadavky pro použití nástroje využití GPU přidávají požadavky na diagnostiku grafiky.

- GPU a ovladač, které podporují potřebné časování instrumentace.

  > [!NOTE]
  > Další informace o podporovaném hardwaru a ovladačích naleznete v [tématu Podpora hardwaru a ovladačů](#hwsupport) na konci tohoto dokumentu.

  Další informace o požadavcích na diagnostiku grafiky naleznete v [tématu Začínáme](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="using-the-gpu-usage-tool"></a>Použití nástroje využití GPU

 Když spustíte aplikaci v rámci nástroje využití GPU, Visual Studio vytvoří diagnostickou relaci, která v reálném čase vykresluje informace na vysoké úrovni o výkonu vykreslování vaší aplikace a využití GPU.

**Spuštění nástroje využití GPU:**

1. V hlavní nabídce zvolte **Ladění**, pak **Výkon a diagnostika** (Klávesnice: Stisknutí kláves Alt+F2).

2. V centru Výkon a diagnostika zaškrtněte políčko vedle **služby Využití GPU**. Volitelně zaškrtněte políčka vedle dalších nástrojů, které vás zajímají. Můžete spustit několik nástrojů pro výkon a diagnostiku současně, abyste získali úplnější představu o výkonu aplikace.

    ![Vyberte diagnostické nástroje, které chcete použít.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Ne všechny nástroje pro výkon a diagnostiku lze použít současně.

3. Zvolte modré tlačítko **Start** v dolní části centra Výkon a diagnostika, abyste aplikaci spustili pod vybranými nástroji.

   Informace na vysoké úrovni, které se zobrazují v reálném čase, zahrnují časování snímků, kmitočet snímků a využití GPU. Každá z těchto informací je zobrazena nezávisle, ale použijte společnou časovou osu, abyste mezi nimi mohli snadno propojit.

   Grafy **Frame time (ms)** a **frames per second (FPS)** mají dvě červené vodorovné čáry, které zobrazují výkonnostní cíle 60 a 30 snímků za sekundu. V grafu **čas rámce** aplikace překročí cíl výkonu, když je graf pod čárou, a netrefí cíl, když je graf nad čárou. Pro graf snímků za sekundu je to naopak – vaše aplikace překročí cíl výkonu, když je graf nad čárou, a mine cíl, když je graf pod čárou. Tyto grafy se primárně používají k získání vysoké úrovně představu o výkonu vaší aplikace a k identifikaci zpomalení, které budete chtít prozkoumat, jako je například náhlý pokles kmitočet snímků nebo špička využití GPU.

   Zatímco vaše aplikace běží v rámci nástroje využití GPU, relace diagnostiky také shromažďuje podrobné informace o grafických událostech, které byly provedeny na GPU. Tyto informace se používají ke generování podrobnější sestavy o tom, jak vaše aplikace využívá hardware. Vzhledem k tomu, že tato sestava trvá nějakou dobu generovat ze shromážděných informací, je k dispozici pouze po dokončení relace diagnostiky shromažďování informací.

   Pokud se chcete podívat na výkon nebo využití problému podrobněji, přestat shromažďovat informace o výkonu tak, aby sestava může být generována.

**Jak generovat a zobrazit sestavu využití GPU:**

1. V dolní části okna relace diagnostiky zvolte odkaz **Zastavit kolekci** nebo stiskněte **klávesu Stop** v levém horním rohu.

   ![Shromažďujte informace o časování GPU a procesoru.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. V horní části sestavy vyberte oddíl z jednoho z grafů, který zobrazuje problém, který chcete prozkoumat. Výběr může být dlouhý až 3 sekundy; delší úseky jsou zkráceny směrem k začátku.

   ![Zveřejnit&#45;kolekce, vybrat rozsah pro zobrazení podrobností](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. V dolní části sestavy zvolte odkaz **podrobnosti zobrazení** v **... kliknutím sem zobrazíte podrobnosti o využití GPU pro** tuto zprávu o rozsahu a zobrazte tak podrobnou časovou osu vašeho výběru.

   ![Zaúčtovat&#45;kolekce s vybraným rozsahem](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   Tento výběr otevře nový dokument s kartami, který obsahuje sestavu. Sestava využití GPU vám pomůže zjistit, kdy je grafická událost spuštěna v procesoru, když dosáhne GPU a jak dlouho gpu trvá, než ji spustí. Tyto informace vám mohou pomoci identifikovat kritické body a příležitosti pro zvýšení paralelismu ve vašem kódu.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Export do nástroje GPUView nebo Windows Performance Analyzer

Počínaje Visual Studio 2017, můžete otevřít tato data s [GPUView](/windows-hardware/drivers/display/using-gpuview) a [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Stačí vybrat **otevřít v GpuView** nebo **Otevřít v WPA** odkazy umístěné v pravém dolním bodě diagnostické relace.

![Otevřít v...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Použití sestavy Využití GPU

V horní části sestavy využití GPU se zobrazí časové osy pro aktivitu zpracování procesoru, aktivitu vykreslování GPU a aktivitu kopírování GPU. Tyto časové osy jsou rozděleny světle šedými svislými pruhy, které indikují vsync displeje. Frekvence pruhů odpovídá obnovovací frekvenci jednoho z displejů (vybraných pomocí rozevíracího **seznamu Display),** ze kterého byla shromážděna data o využití grafického procesoru. Vzhledem k tomu, že displej může mít vyšší obnovovací frekvenci, než je cíl výkonu vaší aplikace, nemusí existovat vztah 1:1 mezi vsync a snímkovou frekvencí, které má vaše aplikace dosáhnout. Chcete-li splnit svůj cíl výkonu, aplikace musí dokončit veškeré zpracování, provést vykreslování a provést volání Present() na cílovou snímkovou frekvenci. Vykreslený snímek se však zobrazí až vsync po Present().

V dolní části se zobrazí seznam grafických událostí, ke kterým došlo během časového období sestavy.

Tady je okno **Sestava využití GPU:**

![Sestava využití GPU s časovými osami PROCESORU a GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Když vyberete událost v dolní části sestavy, zobrazí se značka na odpovídajících událostech v příslušných časových osách. Obvykle jedna událost ve vlákně procesoru zobrazuje volání rozhraní API, zatímco jiná událost na jedné z časových os GPU zobrazuje, když GPU dokončil úlohu. Podobně když vyberete událost na časové ose, sestava zvýrazní odpovídající událost v dolní části sestavy. Při oddálení časových os v horní části sestavy jsou viditelné pouze časově nejnáročnější události. Chcete-li zobrazit události, které mají kratší dobu trvání, přibližte časové osy pomocí kláves Ctrl + kolečko na ukazovacím zařízení nebo ovládací prvek změny měřítka v levém dolním rohu horního panelu. Obsah panelu časové osy můžete také přetažením panelu časové osy procházet zaznamenané události.

Chcete-li najít, co hledáte, filtrujte sestavu využití GPU na základě názvů procesů, ID vláken a názvu události. Kromě toho můžete zvolit, která obnovovací frekvence displeje určuje řádky vysnc. Události můžete seřadit hierarchicky, pokud vaše aplikace používá rozhraní [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) ke skupinovým příkazům vykreslování.

 Tady jsou další podrobnosti:

|Ovládací prvek filtru|Popis|
|--------------------|-----------------|
|**Proces**|Název procesu, který vás zajímá. Všechny procesy, které používaly GPU během relace diagnostiky jsou zahrnuty v této rozevírací rozbalené. Barva přidružená k procesu v tomto rozevíracím seznamu je barva aktivity vlákna v následujících časových osách.|
|**Vlákno**|ID vlákna, které vás zajímá. V aplikaci s více vlákny vám tyto informace mohou pomoci izolovat konkrétní vlákna, která patří k procesu, který vás zajímá. Události přidružené k vybranému vláknu jsou zvýrazněny v každé časové ose.|
|**Displej**|Číslo zobrazení, jehož obnovovací frekvence je zobrazena **Poznámka:** Některé ovladače mohou být nakonfigurovány tak, aby zobrazovaly více fyzických displejů jako jeden velký virtuální displej. Může se zobrazit pouze jeden zobrazený displej, a to i v případě, že zařízení má připojeno více displejů.|
|**Filtr**|Klíčová slova, která vás zajímají. Události v dolní části přehledu budou zahrnovat pouze ty, které odpovídají klíčovému slovu zcela nebo zčásti. Můžete zadat více klíčových slov jejich oddělením s středníkem (;).|
|**Řazení hierarchie**|Zaškrtávací políčko, které označuje, zda jsou hierarchie událostí definované pomocí uživatelských značek zachovány nebo ignorovány.|

 Seznam událostí v dolní části sestavy využití GPU zobrazuje podrobnosti o každé události.

|Sloupec|Popis|
|------------|-----------------|
|**Název události**|Název grafické události. Událost obvykle odpovídá události v časové ose vlákna procesoru a události časové osy GPU.<br /><br /> Názvy událostí mohou být "unattributed", pokud využití GPU nebylo možné určit název události. Další informace naleznete v poznámce pod touto tabulkou.|
|**Zahájení procesoru (ns)**|Čas, kdy byla událost zahájena na procesoru voláním rozhraní DIRECT3D API. Čas se měří v nanosekundách, vzhledem k době, kdy se aplikace spustila.|
|**Začátek GPU (ns)**|Čas, kdy byla událost zahájena na GPU. Čas se měří v nanosekundách vzhledem k době, kdy byla aplikace spuštěna.|
|**Doba trvání GPU (ns)**|Čas, který událost trvalo dokončit na GPU, v nanosekundách.|
|**Název procesu**|Název aplikace, ze které událost pochází.|
|**ID vlákna**|ID vlákna, ze kterého událost pochází.|

> [!IMPORTANT]
> Pokud váš GRAFICKÝ PROCESOR nebo ovladač nepodporuje potřebné funkce instrumentace, všechny události se zobrazí jako "unattributed". Nezapomeňte aktualizovat ovladač GPU a zkuste to znovu, pokud dojde k tomuto problému. Další informace naleznete v [tématu Podpora hardwaru a ovladačů](#hwsupport) níže.

## <a name="gpu-usage-settings"></a>Nastavení využití GPU

Nástroj využití GPU můžete nakonfigurovat tak, aby odložil shromažďování informací o profilování, místo toho, abyste začali shromažďovat informace, jakmile se aplikace spustí. Vzhledem k tomu, že velikost informací o profilování může být významná, je tato akce užitečná, když víte, že zpomalení výkonu aplikace se zobrazí až později.

**Odložení profilování od začátku aplikace:**

1. V hlavní nabídce zvolte **Ladění**, pak **Výkon a diagnostika** (Klávesnice: Stisknutí kláves Alt+F2).

2. V centru Výkon a diagnostika postupujte podle odkazu **nastavení** vedle **položky Využití GPU**.

3. V části **Konfigurace profilování GPU zrušte**na stránce **Vlastností Obecné** zaškrtnutí **políčka Zahájit profilování při spuštění aplikace,** chcete-li profilování odložit.

   ![Konfigurace při spuštění kolekce využití GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Odkládání profilování není v současné době podporováno pro aplikace Direct3D 12.

Po spuštění aplikace v nástroji využití GPU bude k dispozici další odkaz v dolní části okna nástroje Využití GPU. Chcete-li začít shromažďovat informace o profilování, zvolte odkaz **Start** ve **zprávě Začít shromažďovat další podrobná data využití GPU.**

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a>Podpora hardwaru a ovladačů

Podporován je následující hardware a ovladače GPU:

|Dodavatel|Popis GPU|Je vyžadována verze ovladače.|
|------------|---------------------|-----------------------------|
|Informace ®|4. generace procesorů Intel® ("Haswell")<br /><br /> - Intel® HD grafika (GT1)<br />- Intel® HD grafika 4200 (GT2)<br />- Intel® HD grafika 4400 (GT2)<br />- Intel® HD grafika 4600 (GT2)<br />- Intel® HD grafika P4600 (GT2)<br />- Intel® HD grafika P4700 (GT2)<br />- Intel® HD grafika 5000 (GT3)<br />- Intel® Iris™ grafika 5100 (GT3)<br />- Intel® Iris™ Pro Grafika 5200 (GT3e)|-- (použijte nejnovější ovladače)|
|AMD®|Nejvíce od amd radeon™ HD 7000-série (s výjimkou AMD Radeon™ HD 7350-7670)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU a akcelerátory GPU AMD FirePro s architekturou Graphics Core Next (GCN).<br /><br /> AMD® E-Series a AMD A-series Accelerated Processing Units (APU) s architekturou Graphics Core Next (GCN) ('Kaveri', 'Kabini', 'Temash' , 'Beema', 'Mullins')|14.7 RC3 nebo vyšší|
|NVIDIA®|Nejvíce od dob NVIDIA® GeForce® 400-series.<br /><br /> NVIDIA® GpU®, NVIDIA Quadro® GPU a NVIDIA® Tesla™ gpu akcelerátory představovat Fermi™, Kepler™, nebo Maxwell™ architektura.|343.37 nebo vyšší|

 Konfigurace s více GPU, jako je NVIDIA® SLI™ a AMD Crossfire™ nejsou v současné době podporovány. Hybridní nastavení grafiky, jako je NVIDIA® Optimus™ a AMD Enduro™ jsou podporovány.

## <a name="see-also"></a>Viz také

- [Řešení náročných problémů s grafikou pomocí nástrojů DirectX (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [Nástroj pro použití GPU v sadě Visual Studio (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [Nástroj pro použití GPU ve Visual Studiu 2013 Update 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [Využití GPU pro DirectX v sadě Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [Zobrazení GPU](/windows-hardware/drivers/display/using-gpuview)
- [Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)