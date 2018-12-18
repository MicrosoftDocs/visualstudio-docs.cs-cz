---
title: Využití GPU | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3068f614275c14d022ed4d74fa6a10ffe396f68b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817500"
---
# <a name="gpu-usage"></a>Využití GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástroje využití GPU ve výkon sady Visual Studio a centra diagnostiky sady pro lepší pochopení využití vysoké úrovně hardwaru aplikace Direct3D. Můžete to zjistit, jestli je výkon vaší aplikace vázané na procesor nebo vázané na GPU a získat přehled o tom, jak můžete použít hardwarové platformy efektivněji. Využití GPU podporuje aplikace používající rozhraní Direct3D 12, Direct3D 11 a Direct3D 10; nepodporuje se jiné grafické rozhraní API, jako je například Direct2D nebo OpenGL.  
  
 Toto je **sestava využití GPU** okno:  
  
 ![Sestava využití GPU, s konkrétním procesoru a GPU časové osy](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Požadavky  
 Následují požadavky na použití nástroje využití GPU, kromě požadavků na diagnostiky grafiky.  
  
- GPU a ovladače, které podporují instrumentace nezbytné časování.  
  
  > [!NOTE]
  >  Další informace o podporovaný hardware a ovladačů najdete v tématu [hardwarem a ovladači podporují](#hwsupport) na konci tohoto dokumentu.  
  
  Další informace o požadavcích diagnostiky grafiky, naleznete v tématu [Začínáme](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Pomocí nástroje využití GPU  
 Při spuštění aplikace v systému pomocí nástroje využití GPU Visual Studio vytvoří relaci diagnostiky grafů souhrnné informace o využití GPU v reálném čase a vykreslování výkonu vaší aplikace.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Chcete-li spustit nástroj využití GPU:  
  
1. V hlavní nabídce zvolte **ladění**, pak **výkon a Diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).  
  
2. V Centru pro výkon a diagnostiku, zaškrtněte políčko vedle položky **využití GPU**. Volitelně můžete zaškrtnutím políčka vedle jiné nástroje, které vás zajímají. Můžete spustit několik výkonu a diagnostické nástroje souběžně, což umožňuje získat komplexnější přehled o výkonu vaší aplikace.  
  
    ![Zvolte diagnostické nástroje, které chcete použít. ](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   >  Ne všechny výkonu a diagnostické nástroje je možné ve stejnou dobu.  
  
3. Zvolte modrá **Start** tlačítko v dolní části rozcestníku výkon a Diagnostika ke spouštění vaší aplikace v nabídce Nástroje, které jste vybrali.  
  
   Souhrnné informace, které se zobrazí v reálném čase zahrnuje časování snímků, frekvence snímků a využití GPU. Všechny tyto údaje vykreslovacích nezávisle na sobě, ale použít obecného časového měřítka, takže můžete snadno se týkají mezi nimi.  
  
   **Rámec doba (ms)** a **snímků za sekundu (FPS)** grafy obsahují dva červené, vodorovných čar, který cílí výkonu představují 30 a 60 snímků za sekundu. V **rámec čas** grafu překročení cíle výkonnosti po graf pod řádkem a chybějící ho po grafu nad řádek vaší aplikace. Počet snímků za druhý graf je opakem – vaše aplikace je vyšší než cílový výkon při graf je vyšší než řádku a chybějící ho po graf pod řádkem. Tyto grafy se používají především, chcete-li získat základní představu o výkonu vaší aplikace a k identifikaci slow-downs, které můžete chtít prozkoumat – například, náhlému poklesu v snímkovou frekvenci nebo špička využití GPU.  
  
   Při spouštění vaší aplikace v pomocí nástroje využití GPU se relace diagnostiky taky shromažďuje podrobné informace o událostí grafiky, které byly spouštěny na GPU. Tyto informace slouží ke generování podrobnější sestavu o tom, jak vaše aplikace využívá hardware. Vzhledem k tomu, že tato sestava trvá nějakou dobu ke generování ze shromážděných informací, je k dispozici pouze po dokončení shromažďování údajů o informace diagnostickou relaci.  
  
   Když chcete podívat na výkon nebo využití vydávání lépe, zastavte shromažďování informací o výkonu, takže lze generovat sestavy.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Umožňuje generovat a prohlížet sestavy využití GPU:  
  
1. V dolní části okna diagnostické relace, zvolte **zastavit shromažďování** propojení nebo stisknutím klávesy **Zastavit** v levém horním rohu.  
  
    ![Shromažďování informací o časování GPU a CPU. ](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. V horní části sestavy vyberte oddíl jednu z grafů, které ukazuje tento problém, že který chcete prozkoumat. Výběr může být až 3 sekund; delší oddíly se zkrátí spíš na začátku.  
  
    ![Příspěvek&#45;kolekce, vyberte oblast, chcete-li zobrazit podrobnosti](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. V dolní části sestavy, zvolte **podrobnosti** odkaz v **. klikněte zde k zobrazení podrobností o využití GPU pro tento rozsah** zprávu zobrazíte podrobné časová osa vašeho výběru.  
  
    ![Příspěvek&#45;kolekce s rozsah vybraný](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Otevře se nový dokument s kartami, která obsahuje sestavu. Sestava využití GPU vám umožní zobrazit zahájení události grafiky na CPU, až dorazí do místa GPU a jak dlouho trvalo GPU k jeho provedení. Tyto informace pomáhají identifikovat problémová místa a příležitosti pro zvýšení paralelismu ve vašem kódu.  
  
## <a name="using-the-gpu-usage-report"></a>Pomocí sestavy využití GPU  
 Horní části sestavy využití GPU zobrazuje časové osy pro procesoru aktivita, aktivita vykreslování GPU a aktivitu kopírování, která GPU. Tyto časové rámce jsou rozděleny ve světle šedý, svislé pruhy, které představují impulsu VSync zobrazení; frekvence pruhy odpovídá obnovovací frekvence jednoho zobrazení (vybrali pomocí **zobrazení** rozevíracího seznamu) tato data využití GPU se shromažďovala ze. Protože zobrazení může mít vyšší obnovovací frekvence než cílový výkon vaší aplikace nemusí být 1 až 1 vztah mezi impulsu vsync a chcete, aby vaše aplikace k dosažení frekvenci snímků. Podle jeho výkonu cílové musí aplikace dokončí zpracování, provádět vykreslování a volání Present() na cílové snímkové frekvence, ale vykreslený snímek se nezobrazí až do další impulsu vsync po Present().  
  
 Dolní části zobrazí seznam událostí grafiky, ke kterým došlo během časového období sestavy.  
  
 Tady je **sestava využití GPU** okno:  
  
 ![Sestava využití GPU, s konkrétním procesoru a GPU časové osy](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Pokud vyberete jednu z událostí v dolní části sestavy umístí značku na odpovídající události v příslušné časové osy, obvykle jedné ve vlákně procesoru, která reprezentuje volání rozhraní API a další události na jednom z časové osy GPU, který představuje při GPU dokončení úkolu. Podobně pokud vyberete jednu z událostí na časové ose zvýrazní odpovídající událost v dolní části sestavy. Při zvětšení mimo časové osy v horní části sestavy, jsou viditelné pouze události, která se nejvíce časově náročné. Pokud chcete zobrazit události, které mají kratší dobu trvání, zvětšení časové osy stisknutím klávesy Ctrl a kolečka na zařízení nebo změny velikosti ovládacího prvku v levém dolním rohu na horním panelu. Můžete také přetáhnout na časové ose panelu obsahu můžete procházet zaznamenané události.  
  
 A umožňují najít, co hledáte, můžete filtrovat sestavu využití GPU na základě názvy, ID vlákna a název události; procesu Kromě toho můžete zvolit, které zobrazení obnovovací frekvence určuje vysnc řádky a může seřadit události hierarchicky Pokud vaše aplikace používá ID3DUserDefinedAnnotation rozhraní pro příkazy vykreslování skupiny.  
  
 Tady jsou další podrobnosti:  
  
|Ovládací prvek filtru|Popis|  
|--------------------|-----------------|  
|**Proces**|Název procesu, které vás zajímají. V tomto rozevíracím seznamu jsou zahrnuté všechny procesy, které používá GPU během diagnostické relace. Barva spojených s procesem v této rozevírací seznam je barva aktivity vlákna ve níže časové osy.|  
|**vlákno**|ID vlákna, které vás zajímají. Ve vícevláknové aplikaci pomůže vám izolovat konkrétní vlákna, které patří k procesu, který vás zajímá. Události související s vybranou vlákna jsou vyznačené na každé časové osy.|  
|**Zobrazení**|Počet zobrazení se zobrazí jehož obnovovací frekvence **Poznámka:** některé ovladače lze nastavit zobrazíte více fyzických zobrazí jako jeden, velké virtuální zobrazení. Jediné zobrazení uvedené, může se zobrazit i v případě, že tento počítač má připojené více monitorů.|  
|**Filtr**|Klíčová slova, které vás zajímají. Události v dolní části sestavy bude obsahovat pouze ty, které odpovídají klíčové slovo, ať už zcela nebo zčásti. Více klíčových slov můžete určit jejich oddělením středníkem (;).|  
|**Hierarchie řazení**|Zaškrtávací políčko, která označuje, zda události – definice prostřednictvím uživatelské značky--hierarchií jsou zachovány nebo ignorovat.|  
  
 Seznam událostí v dolní části sestavy využití GPU zobrazují podrobnosti o každé události.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název události**|Název události grafiky. Události obvykle odpovídá jedné události na časové ose vlákna CPU a jednu událost na časové ose GPU.<br /><br /> Názvy událostí může být "zjednodušeně", pokud využití GPU se nepodařilo zjistit název události. Další informace najdete v poznámce dál v této tabulce.|  
|**Spuštění CPU (ns)**|Čas události se inicializovala na CPU při volání rozhraní API Direct3D. Čas se měří v nanosekundách, vzhledem k při spuštění aplikace.|  
|**Spuštění GPU (ns)**|Čas události se inicializovala na GPU. Čas se měří v nanosekundách, vzhledem k při spuštění aplikace.|  
|**Doba trvání GPU (ns)**|Čas události trvalo dokončení na GPU v nanosekundách.|  
|**Název procesu**|Název aplikace, odkud událost pochází.|  
|**ID vlákna**|ID vlákna, odkud událost pochází.|  
  
> [!IMPORTANT]
>  Windows 8.1 se vyžaduje pro attribution události. Kromě toho pokud GPU nebo ovladač nepodporují funkce nezbytné instrumentace, všechny události se zobrazí jako "zjednodušeně". Ujistěte se, že aktualizace ovladače GPU a zkuste to znovu, pokud dochází k tomuto problému. Další informace najdete v tématu [hardwarem a ovladači podporují](#hwsupport) níže.  
  
## <a name="gpu-usage-settings"></a>Nastavení využití GPU  
 Můžete nakonfigurovat pomocí nástroje využití GPU se odložit kolekce profilace informace, a ne od lze shromažďovat informace o co nejdříve po spuštění aplikace. Protože velikost profilování informace můžou být důležité, to je užitečné, když víte, že zpomalení výkonu vaší aplikace se zobrazí až později.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Chcete-li odložit, profilace od začátku aplikace:  
  
1.  V hlavní nabídce zvolte **ladění**, pak **výkon a Diagnostika** (klávesnice: stiskněte kombinaci kláves Alt + F2).  
  
2.  V Centru pro výkon a diagnostiku, postupujte **nastavení** odkaz **využití GPU**.  
  
3.  V části **konfigurace profilace GPU**na **Obecné** stránky vlastností, zrušte **zahájíte profilaci na začátku aplikace** zaškrtávací políčko odložit profilace.  
  
     ![Konfigurace při spuštění shromažďování využití GPU](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
>  Odkládá se profilování se aktuálně nepodporuje pro aplikace rozhraní Direct3D 12.  
  
 Při shromažďování informací profilování odložení pomocí tohoto nastavení, bude k dispozici v dolní části okna nástroje využití GPU dodatečný odkaz, při spuštění aplikace v systému pomocí nástroje využití GPU. Aby začal shromažďovat analytické informace, zvolte **Start** odkaz v **zahájení shromažďování dalších podrobných dat o využití GPU** zprávy.  
  
##  <a name="hwsupport"></a> Hardware a podpoře ovladačů  
 Jsou podporovány následující hardwarové GPU a ovladače:  
  
|Dodavatele|Popis GPU|Požadovaná verze ovladače|  
|------------|---------------------|-----------------------------|  
|Intel®|4. generace Intel® procesory (Haswell)<br /><br /> – Procesor Intel® HD, High Density grafiky (GT1)<br />– Procesor Intel® HD, High Density grafiky 4200 (GT2)<br />– Procesor Intel® HD, High Density grafiky 4400 (GT2)<br />– Procesor Intel® HD, High Density grafiky 4600 (GT2)<br />– P4600 procesor Intel® HD, High Density grafiky (GT2)<br />– P4700 procesor Intel® HD, High Density grafiky (GT2)<br />– Procesor Intel® HD, High Density grafiky 5000 (GT3)<br />– Grafika procesor Intel® Iris™ 5100 (GT3)<br />– Procesor Intel® Iris™ Pro grafiky 5200 (GT3e)|--(použijte nejnovější ovladače)|  
|AMD®|Většina od AMD Radeon™ HD, High Density 7000-series (nezahrnuje AMD Radeon™ HD, High Density 7350 7670)<br /><br /> Akcelerátory AMD Radeon™ GPU, AMD FirePro™ GPU a AMD FirePro GPU poskytuje funkci architektura grafiky Core další (GCN).<br /><br /> AMD® E-Series a AMD A-series urychlení zpracování jednotky (APU) poskytuje funkci architektura grafiky Core další (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 nebo vyšší|  
|NVIDIA®|Většina od NVIDIA GeForce® 400-series.<br /><br /> Poskytuje funkci architektura Fermi™, Kepler™ nebo Maxwell™ grafických procesorů NVIDIA® GeForce®, která využívá GPU NVIDIA Quadro® a grafický procesor NVIDIA® Tesla™ akcelerátory.|343.37 nebo vyšší|  
  
 V tuto chvíli nepodporuje konfigurace s více GPU například NVIDIA® SLI™ a AMD Crossfire™. Nastavení hybridní grafiky, jako je například NVIDIA® Optimus™ a AMD Enduro™ jsou podporovány.  
  
## <a name="see-also"></a>Viz také:  
  
-   [Vyřešit Palčivé problémy s grafikou nástroje pro vaše hry pomocí DirectX (video)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
-   [Nástroj využití GPU v sadě Visual Studio (video)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
-   [Nástroj využití GPU ve Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
  
-   [Využití GPU pro DirectX v sadě Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)



