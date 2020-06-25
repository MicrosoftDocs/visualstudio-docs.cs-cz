---
title: Využití GPU | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aa4cce032a5eb80a11568a83c1166b5690bd688
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85279874"
---
# <a name="gpu-usage"></a>Využití GPU

Pomocí nástroje využití GPU v centru pro výkon a diagnostiku sady Visual Studio můžete lépe pochopit využití hardwaru v rámci vysoké úrovně vaší aplikace Direct3D. Pomůže vám zjistit, jestli výkon vaší aplikace je vázaný na procesor nebo s PROCESORem, a získat přehled o tom, jak můžete používat hardware platformy efektivněji. Použití GPU podporuje aplikace, které používají Direct3D 12, Direct3D 11 a Direct3D 10. Nepodporuje jiná rozhraní API grafiky, jako je Direct2D nebo OpenGL.

Okno **Sestava využití GPU** vypadá takto:

![Snímek sestavy o využití GPU s PROCESORem a časovými osami GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Požadavky

Kromě požadavků na Diagnostika grafiky se pro použití nástroje použití GPU vyžadují následující:

- GPU a ovladač podporující potřebnou instrumentaci časování.

  > [!NOTE]
  > Další informace o podporovaném hardwaru a ovladačích najdete v článku [Podpora hardwaru a ovladačů](#hwsupport) na konci tohoto dokumentu.

Další informace o požadavcích na Diagnostika grafiky najdete v tématu [Začínáme](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>Použití nástroje využití GPU

Při spuštění aplikace v nástroji využití GPU vytvoří Visual Studio relaci diagnostiky. Tato relace vykresluje informace vysoké úrovně o výkonu vykreslování vaší aplikace a využití GPU v reálném čase.

Spuštění nástroje použití GPU:

1. V hlavní nabídce zvolte možnost **ladění**  >  **výkonu a diagnostiky** (nebo na klávesnici stiskněte klávesy Alt + F2).

2. V centru pro **výkon a diagnostiku** zaškrtněte políčko vedle **použití GPU**. Volitelně můžete zaškrtnout políčka vedle dalších nástrojů, které vás zajímají. Můžete spustit několik nástrojů pro výkon a diagnostiku současně a získat tak úplný přehled o výkonu vaší aplikace.

    ![Snímek obrazovky centra pro výkon a diagnostiku s vybraným využitím GPU](media/gpuusageselected.png "Vybralo se využití GPU")

   > [!NOTE]
   > Ne všechny nástroje pro výkon a diagnostiku se dají používat současně.

3. V dolní části centra pro **výkon a diagnostiku** vyberte **Spustit** a spusťte svou aplikaci pod vybranými nástroji.

Informace vysoké úrovně zobrazené v reálném čase zahrnují časování snímků, kmitočet snímků a využití GPU. Každá z těchto informací je nezávislá na grafu nezávisle, ale všechny používají společný časový rozsah, abyste mohli snadno pochopit vztahy.

Každý graf **doby snímku (MS)** a **snímků za sekundu (FPS)** má dvě červené, vodorovné čáry, které ukazují cíle výkonnosti 60 a 30 snímků za sekundu. V grafu snímku v čase vaše aplikace přesáhne cíl výkonu, když je graf pod řádkem, a když je graf nad řádkem, neobdrží cíl. Pro grafy snímků za sekundu se jedná o opak: vaše aplikace překračuje cílový výkon, když je graf nad řádkem, a když je graf pod řádkem, neodkazuje se na cíl. Pomocí těchto grafů primárně získáte nejdůležitější představu o výkonu vaší aplikace a k identifikaci pomalých příčin, které byste mohli chtít prozkoumat. Další šetření může být například odůvodněné, pokud se vám zobrazí náhlé vyřazení snímků za sekundu nebo Špička využití GPU.

I když je vaše aplikace spuštěná v nástroji využití GPU, shromažďuje relace diagnostiky také podrobné informace o událostech grafiky, které byly spuštěny na GPU. Tyto informace slouží k vygenerování podrobnějšího sestavování, jak vaše aplikace využívá hardware. Vzhledem k tomu, že tato sestava vygenerovala z shromážděných informací určitou dobu, je k dispozici až po dokončení diagnostické relace shromažďování informací.

Pokud se chcete podívat na problém s výkonem nebo využitím přesněji, zastavte shromažďování informací o výkonu, abyste mohli vytvořit sestavu.

Generování a zobrazení sestavy využití GPU:

1. V dolní části okna diagnostické relace zvolte odkaz **Zastavit shromažďování** nebo v levém horním rohu vyberte **zastavit** .

   ![Snímek obrazovky okna diagnostické relace](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. V horní části sestavy vyberte část v jednom z grafů, které zobrazují problém, který chcete prozkoumat. Váš výběr může trvat až 3 sekundy. Delší oddíly jsou zkráceny směrem k začátku.

   ![Snímek obrazovky okna diagnostické relace](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Chcete-li zobrazit detailní časovou osu výběru, v dolní části sestavy v **... Kliknutím sem zobrazíte podrobnosti o využití GPU pro tuto** zprávu o rozsahu. Vyberte **Zobrazit podrobnosti**.

   ![Snímek obrazovky okna diagnostické relace s vybraným rozsahem](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Tento výběr otevře nový dokument s kartami, který obsahuje sestavu. Sestava využití GPU vám pomůže zjistit, kdy se událost grafiky spouští na procesoru, když dosáhne GPU a jak dlouho je GPU trvá. Tyto informace vám pomůžou identifikovat slabá místa a příležitosti pro zvýšení paralelismu v kódu.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exportovat do GPUView nebo Windows Performance Analyzer

Počínaje sadou Visual Studio 2017 můžete tato data otevřít pomocí [GPUView](/windows-hardware/drivers/display/using-gpuview) a [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Stačí vybrat **otevřít v GpuView** nebo **otevřít v** odkazech WPA umístěných v pravém dolním rohu relace diagnostiky.

![Snímek obrazovky okna diagnostické relace se zvýrazněnými odkazy](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Použití sestavy využití GPU

Horní část sestavy využití GPU zobrazuje časové osy aktivity zpracování procesoru, aktivity vykreslování GPU a aktivity kopírování GPU. Tyto časové osy jsou rozdělené světlem šedé, svislé pruhy, které označují vsync zobrazení. Frekvence pruhů se shoduje s frekvencí aktualizace jednoho ze zobrazení (vybraná pomocí rozevíracího seznamu **zobrazení** ), ze kterých se data využití GPU shromáždila.

Vzhledem k tomu, že displej může mít vyšší obnovovací frekvenci než cíl výkonu vaší aplikace, nemusí se jednat o vztah 1:1 mezi vsync a snímkovou frekvencí, kterou má vaše aplikace dosáhnout. Aby bylo možné splnit svůj cíl výkonu, aplikace musí dokončit všechny zpracování, provést vykreslování a uskutečnit `Present()` hovor na cílovém kmitočtu. Vykreslený snímek se nezobrazí až do dalšího vsync po `Present()` , ale.

V dolní části sestavy využití GPU jsou uvedené události grafiky, ke kterým došlo během časového období sestavy. Když vyberete událost, zobrazí se značka v odpovídajících událostech v příslušných časových osách. Obvykle jedna událost v vlákně procesoru zobrazuje volání rozhraní API, zatímco jiná událost na jedné z časových os GPU ukazuje, kdy GPU dokončila úlohu. Podobně když vyberete událost na časové ose, sestava zvýrazní odpovídající událost grafiky v dolní části sestavy.

Když se v horní části sestavy přiblížíte k časovým limitům, budou se zobrazovat jenom ty nejnáročnější události, které jsou časově náročné. Pokud chcete zobrazit události, které mají kratší dobu trvání, přihlaste se k časové ose pomocí kombinace kláves CTRL + kolo na polohovacím zařízení nebo ovládacího prvku škálování v levém dolním rohu horního panelu. Můžete také přetáhnout obsah panelu Časová osa a procházet zaznamenanými událostmi.

Chcete-li najít, co hledáte, vyfiltrujte sestavu využití GPU na základě názvů procesů, ID vláken a názvu události. Navíc můžete zvolit, která obnovovací frekvence displeje určuje vysnc čáry. Události můžete seřadit hierarchicky, pokud vaše aplikace používá rozhraní [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) k seskupení příkazů pro vykreslování.

 Tady jsou další podrobnosti:

|Ovládací prvek filtru|Popis|
|--------------------|-----------------|
|**Proces**|Název procesu, který vás zajímá. V tomto rozevíracím seznamu jsou zahrnuty všechny procesy, které používaly GPU během diagnostické relace. Barva přidružená k procesu je barva aktivity vlákna v časových osách.|
|**Doporučujeme**|ID vlákna, které vás zajímá. V aplikaci s více vlákny vám tyto informace pomůžou izolovat konkrétní vlákna, která patří do procesu, na který vás zajímá. Události přidružené k vybranému vláknu jsou v každé časové ose zvýrazněné.|
|**Displej**|Počet zobrazení, jejichž obnovovací frekvence je zobrazena. Některé ovladače lze nakonfigurovat tak, aby zobrazovaly více fyzických displejů jako jeden velký virtuální displej. V seznamu se může zobrazit jenom jedno zobrazení, i když má počítač k němu připojeno více obrazovek.|
|**Filtr**|Klíčová slova, která vás zajímají. Události v dolní části sestavy budou zahrnovat pouze ty, které odpovídají klíčovému slovu, zcela nebo částečně. Můžete zadat více klíčových slov tak, že je oddělíte středníkem (;).|
|**Řazení hierarchie**|Zaškrtávací políčko, které určuje, zda hierarchie událostí definované prostřednictvím uživatelských značek jsou zachovány nebo ignorovány.|

Seznam událostí v dolní části sestavy využití GPU zobrazuje podrobnosti o každé události.

|Sloupec|Popis|
|------------|-----------------|
|**Název události**|Název události grafiky Událost obvykle odpovídá události v časové ose vlákna procesoru a události časové osy GPU. Pokud použití GPU nedokáže určit název události, můžou být názvy událostí bez *atributů* . Další informace najdete v poznámce za touto tabulkou.|
|**Spuštění CPU (NS)**|Čas, kdy byla událost zahájena na CPU voláním rozhraní Direct3D API. Čas se měří v nanosekundách, relativně ke spuštění aplikace.|
|**Spuštění GPU (NS)**|Čas zahájení události v GPU Čas se měří v nanosekundách, relativně ke spuštění aplikace.|
|**Trvání GPU (NS)**|Čas v nanosekundách, který trvalo dokončení události na GPU.|
|**Název procesu**|Název aplikace, ze které byla událost přijata.|
|**ID vlákna**|ID vlákna, ze kterého byla událost přijata.|

> [!IMPORTANT]
> Pokud grafické procesory nebo ovladače nepodporují potřebné funkce instrumentace, zobrazí se všechny události jako *neatributované*. Pokud se setkáte s tímto problémem, aktualizujte ovladač GPU a zkuste to znovu. Další informace najdete v tématu [Podpora hardwaru a ovladačů](#hwsupport) na konci tohoto dokumentu.

## <a name="gpu-usage-settings"></a>Nastavení využití GPU

Nástroj využití GPU můžete nakonfigurovat tak, aby odložil shromažďování informací o profilaci, a ne začít shromažďovat informace ihned po spuštění aplikace. Vzhledem k tomu, že velikost informací profilace může být významná, tato akce je užitečná, když víte, že zpomalení výkonu vaší aplikace se nezobrazí až později.

Odložení profilování od začátku aplikace:

1. V hlavní nabídce zvolte možnost **ladění**  >  **výkonu a diagnostiky** (nebo na klávesnici stiskněte klávesy Alt + F2).

2. V centru pro **výkon a diagnostiku** vedle možnosti **použití GPU**vyberte odkaz **Nastavení** .

3. V části **Konfigurace profilace GPU**na stránce **Obecné** vlastnosti zrušte zaškrtnutí políčka **zahájit profilování při spuštění aplikace** a odložit profilaci.

   ![Snímek stránek vlastností objektu se zobrazením možností kolekce](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> V tuto chvíli nemůžete odložit profilaci pro aplikace Direct3D 12.

Po spuštění aplikace v nástroji využití GPU bude v dolní části okna nástroje využití GPU k dispozici další odkaz. Pokud chcete začít shromažďovat informace o profilování, klikněte na odkaz **Spustit** v části **začít shromažďovat další podrobnou datovou zprávu o využití GPU** .

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a>Podpora hardwaru a ovladačů

Podporuje se následující hardware a ovladače GPU:

|Dodavatel|Popis GPU|Vyžaduje se verze ovladače.|
|------------|---------------------|-----------------------------|
|Intel®|4. generace procesorů Intel® Core (' Haswell ')<br /><br /> – Intel® HD Graphics (GT1)<br />– Intel® HD Graphics 4200 (GT2)<br />– Intel® HD Graphics 4400 (GT2)<br />– Intel® HD Graphics 4600 (GT2)<br />– Intel® HD Graphics P4600 (GT2)<br />– Intel® HD Graphics P4700 (GT2)<br />– Intel® HD Graphics 5000 (GT3)<br />– Intel® Iris™ Graphics 5100 (GT3)<br />– Intel® Iris™ pro Graphics 5200 (GT3e)|(použít nejnovější ovladače)|
|® AMD|Většina od procesorů AMD Radeon™ HD 7000-Series (nezahrnuje AMD Radeon™ HD 7350-7670)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU a akcelerátory GPU AMD FirePro s architekturou GCN (Graphics Next)<br /><br /> AMD® E-series a AMD a-Series akcelerované výpočetní jednotky (APUs) s architekturou GCN (Graphics Core Next) (Kaveri, Kabini, Temash, Beema, Mullins,)|14,7 RC3 nebo novější|
|® NVIDIA|Většina od® NVIDIA GeForce® 400-Series<br /><br /> NVIDIA® GeForce® GPU, NVIDIA Quadro® GPU a NVIDIA® Tesla™ akcelerátory GPU, které nabízí Fermi™, Kepler™ nebo Maxwell™ Architecture|343,37 nebo novější|

 Konfigurace s více grafickými procesory, například NVIDIA® SLI™ a AMD Crossfire™, nejsou v tuto chvíli podporované. Podporují se nastavení hybridní grafiky, jako je například NVIDIA® Optimus™ a AMD Enduro™.
