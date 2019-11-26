---
title: Využití GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b2e827b180ae218f3dd42b124500e01260e72d82
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297395"
---
# <a name="gpu-usage"></a>Využití GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástroje využití GPU v centru pro výkon a diagnostiku sady Visual Studio můžete lépe pochopit využití hardwaru na vysoké úrovni vaší aplikace Direct3D. Můžete ji použít k určení, jestli výkon vaší aplikace je vázaný na procesor nebo na základě GPU, a získat přehled o tom, jak můžete používat hardware platformy efektivněji. Použití GPU podporuje aplikace, které používají Direct3D 12, Direct3D 11 a Direct3D 10; nepodporuje jiná rozhraní API grafiky, jako je Direct2D nebo OpenGL.  
  
 Toto je okno **sestavy využití GPU** :  
  
 ![Sestava využití GPU s časovými osami procesoru a GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Požadavky  
 Níže jsou uvedené požadavky na použití nástroje použití GPU, které kromě Diagnostika grafiky požadavků.  
  
- GPU a ovladač podporující potřebnou instrumentaci časování.  
  
  > [!NOTE]
  > Další informace o podporovaném hardwaru a ovladačích najdete v článku [Podpora hardwaru a ovladačů](#hwsupport) na konci tohoto dokumentu.  
  
  Další informace o požadavcích na Diagnostika grafiky najdete v tématu [Začínáme](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Použití nástroje využití GPU  
 Když spustíte aplikaci v nástroji využití GPU, Visual Studio vytvoří relaci diagnostiky, která bude graficky vykreslovat informace o výkonu vykreslování vaší aplikace a využití GPU v reálném čase.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Spuštění nástroje použití GPU:  
  
1. V hlavní nabídce zvolte položku **ladit**, **výkon a diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).  
  
2. V centru pro výkon a diagnostiku zaškrtněte políčko vedle **použití GPU**. Volitelně můžete zaškrtnout políčka vedle dalších nástrojů, které vás zajímají. Můžete spustit několik nástrojů pro výkon a diagnostiku současně a získat tak úplný přehled o výkonu vaší aplikace.  
  
    ![Vyberte diagnostické nástroje, které chcete použít.](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   > Ne všechny nástroje pro výkon a diagnostiku se dají používat současně.  
  
3. V dolní části centra pro výkon a diagnostiku klikněte na tlačítko Blue **Start** , aby se vaše aplikace spustila v rámci vybraných nástrojů.  
  
   Informace vysoké úrovně zobrazené v reálném čase zahrnují časování snímků, kmitočet snímků a využití GPU. Každá z těchto informací je nezávislá na grafu nezávisle, ale použijte běžný časový rozsah, abyste se mohli snadno spojit mezi nimi.  
  
   Grafy **doby snímku (MS)** a **snímků za sekundu (FPS)** obsahují dvě červené, vodorovné čáry, které reprezentují cíle výkonnosti 60 a 30 snímků za sekundu. V grafu **snímku v čase** vaše aplikace překračuje cílový výkon, když je graf pod řádkem a chybí, když je graf nad řádkem. U snímků za sekundu graf je opakem – vaše aplikace překračuje cílový výkon, když je graf nad řádkem a chybí, když je graf pod řádkem. Primárně se tyto grafy používají k získání vysoké představu o výkonu vaší aplikace a k identifikaci zpomalení, které byste mohli chtít prozkoumat – například na náhlém poklesu snímkové frekvence nebo špičky využití GPU.  
  
   I když je vaše aplikace spuštěná v nástroji využití GPU, shromažďuje relace diagnostiky také podrobné informace o událostech grafiky, které byly spuštěny na GPU. Tyto informace slouží k vygenerování podrobnějšího sestavování, jak vaše aplikace využívá hardware. Vzhledem k tomu, že tato sestava vygenerovala z shromážděných informací určitou dobu, je k dispozici až po dokončení diagnostické relace shromažďování informací.  
  
   Pokud chcete podrobněji sledovat výkon nebo využití problému, zastavte shromažďování informací o výkonu, aby bylo možné sestavu vygenerovat.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Generování a zobrazení sestavy využití GPU:  
  
1. V dolní části okna diagnostické relace zvolte odkaz **Zastavit shromažďování** nebo v levém horním rohu klikněte na **zastavit** .  
  
    ![Shromážděte informace o časování GPU a procesoru.](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. V horní části sestavy vyberte část v jednom z grafů, které zobrazují problém, který chcete prozkoumat. Váš výběr může trvat až 3 sekundy. delší oddíly jsou zkráceny směrem k začátku.  
  
    ![Po&#45;shromáždění kolekce vyberte rozsah, ve kterém chcete zobrazit podrobnosti.](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. V dolní části sestavy vyberte odkaz **Zobrazit podrobnosti** v **... Kliknutím sem zobrazíte podrobnosti o využití GPU pro tuto zprávu rozsahu,** abyste viděli detailní časovou osu výběru.  
  
    ![Publikovat&#45;kolekci s vybraným rozsahem](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Otevře se nový dokument s kartami, který obsahuje sestavu. Sestava využití GPU vám pomůže zjistit, kdy se v procesoru spustí grafická událost, když dosáhne GPU a jak dlouho trvá spuštění GPU. Tyto informace vám pomůžou identifikovat slabá místa a příležitosti pro zvýšení paralelismu v kódu.  
  
## <a name="using-the-gpu-usage-report"></a>Použití sestavy využití GPU  
 Horní část sestavy využití GPU zobrazuje časové osy aktivity zpracování procesoru, aktivity vykreslování GPU a aktivity kopírování GPU. Tyto časové osy jsou rozdělené světlem šedé, svislé pruhy, které představují vsync zobrazení. frekvence pruhů odpovídá obnovovací frekvenci jednoho ze zobrazení (vybraná pomocí rozevíracího seznamu **zobrazení** ), ze kterých se data využití GPU shromáždila. Vzhledem k tomu, že displej může mít vyšší obnovovací frekvenci než cíl výkonu vaší aplikace, nemusí se jednat o vztah 1:1 mezi vsync a snímkovou frekvencí, kterou má vaše aplikace dosáhnout. Aby bylo možné splnit svůj cíl výkonu, aplikace musí dokončit všechny zpracování, provádět vykreslování a učinit volání () na cílovém snímkovém snímku, ale vykreslený snímek nebude zobrazen až do dalšího vsync po přítomnosti ().  
  
 V dolní části se zobrazí seznam událostí grafiky, ke kterým došlo během časového období sestavy.  
  
 Tady je okno **sestavy využití GPU** :  
  
 ![Sestava využití GPU s časovými osami procesoru a GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Když vyberete jednu z událostí v dolní části sestavy, umístí se značka na odpovídající události v příslušných časových osách, obvykle jedna událost v vláknovém vlákně, která představuje volání rozhraní API, a další událost na jedné z časových os GPU, která představuje, když GPU dokončila se úloha. Podobně výběr jedné z událostí v časové ose zvýrazní odpovídající událost v dolní části sestavy. Při přiblížení časových os v horní části sestavy jsou viditelné pouze nejnáročné události, které jsou časově náročné. Pokud chcete zobrazit události, které mají kratší dobu trvání, přihlaste se k časové ose pomocí kombinace kláves CTRL + kolo na polohovacím zařízení nebo ovládacího prvku škálování v levém dolním rohu horního panelu. Můžete také přetáhnout obsah panelu Časová osa a procházet zaznamenanými událostmi.  
  
 Abyste vám pomohli najít, co hledáte, můžete filtrovat sestavu využití GPU na základě názvů procesů, ID vláken a názvu události. Kromě toho můžete zvolit, která obnovovací frekvence displeje určuje vysnc čáry, a hierarchicky třídit události, pokud vaše aplikace používá rozhraní ID3DUserDefinedAnnotation k seskupení příkazů pro vykreslování.  
  
 Tady jsou další podrobnosti:  
  
|Ovládací prvek filtru|Popis|  
|--------------------|-----------------|  
|**Přihlášení**|Název procesu, který vás zajímá. V tomto rozevíracím seznamu jsou zahrnuty všechny procesy, které používaly GPU v relaci diagnostiky. Barva, která je přidružená k procesu v tomto rozevíracím seznamu, je barva aktivity vlákna na časových osách níže.|  
|**Doporučujeme**|ID vlákna, které vás zajímá. V aplikaci s více vlákny vám může pomáhat izolovat konkrétní vlákna, která patří do procesu, na který zajímáte. Události přidružené k vybranému vláknu jsou v každé časové ose zvýrazněné.|  
|**Otevřete**|Počet zobrazených obnovovací frekvence, **Poznámka:** některé ovladače lze nakonfigurovat tak, aby zobrazovaly více fyzických zobrazení jako jeden velký virtuální displej. V seznamu se může zobrazit jenom jedno zobrazení, i když má počítač k němu připojeno více obrazovek.|  
|**Filtrovací**|Klíčová slova, která vás zajímají. Události v dolní části sestavy budou zahrnovat pouze ty, které odpovídají klíčovému slovu jako celek nebo částečně. Můžete zadat více klíčových slov tak, že je oddělíte středníkem (;).|  
|**Řazení hierarchie**|Zaškrtávací políčko, které určuje, zda hierarchie událostí – definované prostřednictvím uživatelských značek – jsou zachovány nebo ignorovány.|  
  
 Seznam událostí v dolní části sestavy využití GPU zobrazuje podrobnosti o každé události.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název události**|Název události grafiky Událost obvykle odpovídá jedné události v časové ose vlákna procesoru a jedné události na časové ose GPU.<br /><br /> Pokud využití GPU nedokázalo určit název události, můžou být názvy událostí bez atributů. Další informace najdete v poznámce pod touto tabulkou.|  
|**Spuštění CPU (NS)**|Čas, kdy byla událost zahájena na CPU voláním rozhraní Direct3D API. Čas se měří v nanosekundách, relativně ke spuštění aplikace.|  
|**Spuštění GPU (NS)**|Čas zahájení události v GPU Čas se měří v nanosekundách, relativně ke spuštění aplikace.|  
|**Trvání GPU (NS)**|Čas potřebný k dokončení události v GPU v nanosekundách.|  
|**Název procesu**|Název aplikace, ze které byla událost přijata.|  
|**ID vlákna**|ID vlákna, ze kterého byla událost přijata.|  
  
> [!IMPORTANT]
> Pro přidělení události je vyžadován Windows 8.1. Pokud navíc vaše GPU nebo ovladač nepodporuje potřebné funkce instrumentace, zobrazí se všechny události jako "bez atributu". Ujistěte se, že jste aktualizovali ovladač GPU, a zkuste to znovu, pokud se setkáte s tímto problémem. Další informace najdete v tématu [Podpora hardwaru a ovladačů](#hwsupport) níže.  
  
## <a name="gpu-usage-settings"></a>Nastavení využití GPU  
 Nástroj využití GPU můžete nakonfigurovat tak, aby odložil shromažďování informací o profilaci, a ne začít shromažďovat informace ihned po spuštění aplikace. Vzhledem k tomu, že velikost informací o profilech může být významná, to je užitečné, když víte, že zpomalení výkonu vaší aplikace se nezobrazí až později.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Odložení profilování od začátku aplikace:  
  
1. V hlavní nabídce zvolte položku **ladit**, **výkon a diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).  
  
2. V centru pro výkon a diagnostiku použijte odkaz **nastavení vedle možnosti** **využití GPU**.  
  
3. V části **Konfigurace profilace GPU**na stránce **Obecné** vlastnosti zrušte zaškrtnutí políčka **Spustit profilování v aplikaci začátek** a odložit profilaci.  
  
     ![Konfigurovat, kdy se spustí shromažďování využití GPU](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
> Pro aplikace Direct3D 12 se v současné době nepodporují odložení profilování.  
  
 Po odložení shromažďování informací o profilaci pomocí tohoto nastavení bude v dolní části okna nástroje využití GPU k dispozici další odkaz, když spustíte aplikaci v nástroji využití GPU. Pokud chcete začít shromažďovat informace o profilování, klikněte na odkaz **Spustit** v části **začít shromažďovat další podrobnou datovou zprávu o využití GPU** .  
  
## <a name="hwsupport"></a>Podpora hardwaru a ovladačů  
 Podporuje se následující hardware a ovladače GPU:  
  
|Dodavatele|Popis GPU|Vyžaduje se verze ovladače.|  
|------------|---------------------|-----------------------------|  
|Intel®|4\. generace procesorů Intel® Core (' Haswell ')<br /><br /> – Intel® HD Graphics (GT1)<br />– Intel® HD Graphics 4200 (GT2)<br />– Intel® HD Graphics 4400 (GT2)<br />– Intel® HD Graphics 4600 (GT2)<br />– Intel® HD Graphics P4600 (GT2)<br />– Intel® HD Graphics P4700 (GT2)<br />– Intel® HD Graphics 5000 (GT3)<br />– Intel® Iris™ Graphics 5100 (GT3)<br />– Intel® Iris™ pro Graphics 5200 (GT3e)|--(použít nejnovější ovladače)|  
|AMD®|Většina od AMD Radeon™ HD 7000-Series (nezahrnuje AMD Radeon™ HD 7350-7670)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU a akcelerátory GPU AMD FirePro s architekturou GCN (Graphics Next).<br /><br /> AMD® E-series a AMD a-Series akcelerované výpočetní jednotky (APUs) s architekturou GCN (Graphics Core Next) (Kaveri, Kabini, Temash, Beema, Mullins,)|14,7 RC3 nebo vyšší|  
|NVIDIA®|Nejvíce od NVIDIA® GeForce® 400-Series.<br /><br /> NVIDIA® GeForce® GPU, NVIDIA Quadro® GPU a NVIDIA® Tesla™ akcelerátory GPU, které nabízí Fermi™, Kepler™ nebo Maxwell™ architektury.|343,37 nebo vyšší|  
  
 Konfigurace s více grafickými procesory, jako je například NVIDIA® SLI™ a AMD Crossfire™, se v tuto chvíli nepodporují. Nastavení hybridní grafiky, jako je například NVIDIA® Optimus™ a AMD enduro™, je podporováno.  
  
## <a name="see-also"></a>Viz také:  
  
- [Řešení obtížných grafických problémů se hrou pomocí nástrojů DirectX (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
- [Nástroj využití GPU v aplikaci Visual Studio (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
- [Nástroj využití GPU ve Visual Studio 2013 Update 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)  
  
- [Využití GPU pro DirectX v aplikaci Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
