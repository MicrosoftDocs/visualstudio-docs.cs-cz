---
title: Analýza grafických snímků | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 943436a64f50523905a03ed2a87e91508d1b7471
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911485"
---
# <a name="graphics-frame-analysis"></a>Analýza grafických snímků
Pomocí Analýza grafických snímků v Analyzátor grafiky sady Visual Studio můžete analyzovat a optimalizovat výkon vykreslování vaší hry nebo aplikace Direct3D.

## <a name="frame-analysis"></a>Analýza snímků
 Analýza snímků používá stejné informace, které jsou zachyceny v souboru protokolu grafiky pro účely diagnostiky, ale používá je k sumarizaci výkonu vykreslování. Informace o výkonu se během zachytávání nezaznamenají do protokolu. místo toho jsou informace o výkonu generovány později během analýzy snímků pomocí událostí časování a shromažďováním statistik při přehrávání snímku. Tento přístup má několik výhod oproti zaznamenávání informací o výkonu během zachytávání:

- Analýza snímků může průměrně vymezit více přehráváními stejného snímku, aby bylo zajištěno, že souhrn výkonu bude statisticky zdravý.

- Analýza snímků může vygenerovat informace o výkonu pro hardwarové konfigurace a jiná zařízení než ta, ve které byly informace zachyceny.

- Analýza snímků může vygenerovat nové souhrnné údaje o výkonu z dříve zaznamenaných informací – například když jsou ovladače GPU optimalizované nebo zpřístupňují další funkce ladění.

  Kromě těchto výhod může analýza snímků také provádět změny v tom, jak je snímek vykreslen během přehrávání, aby mohl prezentovat informace o tom, jak tyto změny mohou ovlivnit výkon vykreslování aplikace. Tyto informace můžete použít k rozhodnutí z potenciálních strategií optimalizace bez nutnosti jejich implementace a následnému zachycení a porovnání všech výsledků.

  I když je analýza snímků primárně určena k tomu, aby vám pomohla dosáhnout rychlejšího vykreslování, může vám to zároveň usnadnit lepší vizuální kvalitu pro daný cíl výkonu nebo snížit spotřebu energie GPU.

  Chcete-li zobrazit ukázku, která analýza snímků může pro vaši aplikaci udělat, můžete se podívat na video v [aplikaci Visual Studio Analýza grafických snímků](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) na Channel 9.

## <a name="using-frame-analysis"></a>Použití analýzy snímků
 Než budete moct použít analýzu snímků, musíte zachytit informace grafiky z vaší aplikace při jejich spuštění, stejně jako při použití některého z dalších nástrojů pro analyzátor grafiky. Pak v okně dokument protokolu grafiky (. vsglog) zvolte kartu **Analýza snímků** .

 ![Vyberte kartu analýza snímků.](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")

 Po dokončení analýzy se zobrazí výsledky. Horní část karty analýza snímků zobrazuje časovou osu a tabulku souhrnu. V dolní části se zobrazí tabulky podrobností. Pokud byly během přehrávání generovány chyby nebo upozornění, jsou shrnuty nad časovou osou. odtud můžete postupovat podle odkazů a získat další informace o chybách a upozorněních.

### <a name="interpreting-results"></a>Interpretace výsledků
 Interpretací výsledků jednotlivých variant můžete odvodit užitečné informace o výkonu a chování vykreslování vaší aplikace. Další informace o vygenerování variant naleznete v části [varianty](#Variants) dále v tomto článku.

 Některé výsledky přímo ukazují, jak varianta ovlivňuje výkon vykreslování:

- Pokud variace filtrování textury varianty ukázala zvýšení výkonu, pak se pomocí filtrování textury varianty ve vaší aplikaci zobrazí podobné nárůsty výkonu.

- Pokud 1x1 zobrazení variant ukázalo nárůst výkonu, pak se zmenšení velikosti cílů vykreslování v aplikaci zvýší jeho výkon.

- Pokud variace komprese textury BC ukázala zvýšení výkonu, pak se pomocí komprese textury BC ve vaší aplikaci zobrazí podobný nárůst výkonu.

- Pokud má varianta 2xMSAA skoro stejný výkon jako 0xMSAA varianta, můžete povolit 2xMSAA ve vaší aplikaci, aby se zlepšila kvalita vykreslování bez nákladů na výkon.

  Další výsledky můžou navrhnout hlubší a jemnější dopad na výkon vaší aplikace:

- Pokud zobrazení variant 1x1 znázorňuje velmi velký nárůst výkonu, aplikace pravděpodobně spotřebovává více fillrate, než je k dispozici. Pokud tato varianta neukazuje žádné nárůsty výkonu, aplikace pravděpodobně zpracovává příliš mnoho vrcholů.

- Pokud varianta cílového formátu 16bpp vykreslování ukazuje výrazné zvýšení výkonu, aplikace pravděpodobně spotřebovává příliš velkou šířku pásma paměti.

- Pokud variace v poloviční/Čtvrtine znázorňuje výrazné zvýšení výkonu, vaše textury pravděpodobně zabírají příliš mnoho paměti, spotřebují příliš velkou šířku pásma nebo neefektivně používají mezipaměť textury. Pokud tato varianta ve výkonu nezobrazuje žádnou změnu, můžete pravděpodobně použít větší, podrobnější textury, aniž byste museli platit náklady na výkon.

  Když jsou k dispozici hardwarové čítače, můžete je použít ke shromáždění velmi podrobných informací o tom, proč může být výkon vykreslování vaší aplikace nakažený. Všechna zařízení na úrovni funkcí 9,2 a vyšší podporují hloubkové dotazy překrytí (zastíněna počítadla**pixelů** ) a časová razítka. Další hardwarové čítače můžou být dostupné v závislosti na tom, jestli výrobce GPU implementoval hardwarové čítače a vystavuje ho v jeho ovladači. Tyto čítače lze použít k potvrzení přesné příčiny výsledků zobrazených v tabulce souhrn – například můžete určit, zda je překreslování faktor, prozkoumáním procenta pixelů, které byly zastíněna testem hloubky.

### <a name="timeline-and-summary-table"></a>Časová osa a Souhrnná tabulka
 Ve výchozím nastavení se zobrazuje časová osa a tabulka souhrnů a ostatní oddíly jsou sbalené.

#### <a name="timeline"></a>Včasnost
 Časová osa zobrazuje přehled časování volání vytažení vzhledem k jinému typu. Vzhledem k tomu, že větší pruhy odpovídají delší době kreslení, můžete je použít k rychlému vyhledání nejdražších volání vykreslování v rámci rámce. Když zachycený snímek obsahuje velký počet volání remíz, vícenásobná volání vykreslování jsou kombinována do jednoho panelu, jehož délka je součet těchto volání vykreslování.

 ![Časová osa ukazuje&#45;náklady na volání remíz.](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")

 Můžete si ponechit ukazatel na panelu a zjistit, která událost nakresleného volání odpovídá pruhu. Výběr pruhu způsobí, že se seznam událostí synchronizuje s touto událostí.

#### <a name="table"></a>Tabulka
 Tabulka s čísly pod časovou osou zobrazuje relativní výkon jednotlivých variant vykreslování pro každé volání remíz s ohledem na výchozí vykreslování vaší aplikace. Každý sloupec zobrazuje jinou variantu vykreslování a každý řádek představuje jiné volání remízy, které je identifikované ve sloupci nejvíce vlevo; odsud můžete sledovat odkaz na událost v okně seznam událostí grafiky.

 ![Tabulka souhrnu zobrazuje různé varianty.](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")

 Druhý sloupec nejvíce vlevo v tabulce souhrn zobrazuje dobu vykreslování vaší aplikace, což je doba, po kterou bude mít výchozí vykreslování vaší aplikace k dokončení volání remízy. Zbývající sloupce znázorňují relativní výkon každé varianty vykreslování jako procentuální hodnotu směrného plánu, aby bylo snazší zjistit, zda se zvýšil výkon. Procentuální hodnoty větší než 100% trvaly déle než směrný plán – to znamená, že výkon je mimo provoz – a procentuální podíly menší než 100% trvalo méně času – výkon se zvýšil.

 Hodnoty absolutního časování standardních hodnot a relativního časování variant vykreslování jsou ve skutečnosti průměrem více spuštění – 5 ve výchozím nastavení. Tento průměr pomáhá zajistit spolehlivou a konzistentní časová data. Ukazatel na každou buňku v tabulce můžete podržet, chcete-li zjistit minimální, maximální, střední a mediánové hodnoty časování, které byly pozorovány při vygenerování výsledků pro toto volání vykreslení a variant vykreslování. Zobrazí se také časování standardních hodnot.

#### <a name="hot-draw-calls"></a>Volání "horkého" vykreslování
 Chcete-li věnovat pozornost vykreslení volání, která spotřebují větší část celkového času vykreslování nebo která by mohla být obvykle z důvodů, že se jim může vyhnout, je řádek, který obsahuje tato volání "horká", šedá červeně, pokud je vlastní časování vlastního směrného plánu více než jeden směrodatná odchylka je delší než střední hodnota načasování všech volání vykreslování v rámci rámečku.

 ![Toto volání DrawIndexed má horkou a studenou variantu.](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")

#### <a name="statistical-significance"></a>Statistická významnost
 Chcete-li věnovat pozornost vykreslování odchylek s nejvyšší závažností, analýza snímků určuje statistický význam každé varianty vykreslování a zobrazuje důležité hodnoty jako tučné písmo. Zobrazuje ty, které zlepšují výkon jako zelenou a ty, které snižují výkon jako červené. Zobrazuje výsledky, které nejsou statisticky důležité jako normální typ.

 ![Statistická významnost varianty volání draw](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")

 Aby bylo možné určit statistickou relevanci, analýza snímků používá [t-test studenta](https://en.wikipedia.org/wiki/Student's_t-test).

### <a name="details-table"></a>Tabulka podrobností
 Pod souhrnnou tabulkou je tabulka podrobností, která je ve výchozím nastavení sbalená. Obsah tabulky Details závisí na hardwarové platformě počítače pro přehrávání. Informace o podporovaných hardwarových platformách najdete v tématu [hardwarová podpora](#HardwareSupport).

#### <a name="platforms-that-do-not-support-hardware-counters"></a>Platformy, které nepodporují čítače hardwaru
 Většina platforem plně nepodporuje hardwarové čítače GPU – zahrnuje všechny GPU aktuálně nabízené technologií Intel, AMD a nVidia. Pokud neexistují žádné hardwarové čítače ke shromáždění, zobrazí se pouze jedna tabulka podrobností, která obsahuje střední absolutní časování všech variant.

 ![Tabulka podrobností a některé varianty přehrávání.](media/pix_frame_analysis_details.png "pix_frame_analysis_details")

#### <a name="platforms-that-support-hardware-counters"></a>Platformy, které podporují čítače hardwaru
 Pro platformy, které podporují čítače grafického procesoru (například nVidia T40 SOC a All Qualcomm SOC) se zobrazí několik tabulek s podrobnostmi, jedna pro každou variantu. Všechny dostupné čítače hardwaru se shromažďují pro každou variantu vykreslování a zobrazují se ve vlastní tabulce podrobností.

 ![Čítače hardwaru se zobrazí, pokud jsou podporovány.](media/pix_frame.png "pix_frame")

 Informace o čítači hardwaru poskytují velmi podrobné zobrazení konkrétního chování hardwarových platforem pro každé volání remíz, které vám může přispět k tomu, aby bylo obtížné určit příčinu kritických bodů výkonu.

> [!NOTE]
> Různé hardwarové platformy podporují různé čítače; neexistuje žádný standardní. Čítače a jejich reprezentace jsou určeny výhradně pro každého výrobce GPU.

### <a name="marker-regions-and-events"></a>Oblasti a události značek
 Analýza snímků podporuje uživatelsky definované značky událostí a skupiny událostí. Zobrazují se v tabulce souhrn a v tabulkách podrobností.

 K vytváření značek a skupin můžete použít buď rozhraní API ID3DUserDefinedAnnotation, nebo starší D3DPERF_ rozhraní API. Když použijete rodinu rozhraní API D3DPERF_, můžete přiřadit každou značku a seskupit barvu, kterou analýza snímků zobrazí jako barevný pruh v řádcích, které obsahují značku události nebo značky begin/end skupiny událostí a jejich obsah. Tato funkce vám může přispět k rychlé identifikaci důležitých událostí vykreslování nebo skupin událostí.

### <a name="warnings-and-errors"></a>Upozornění a chyby
 Analýza snímků se občas dokončí s upozorněními nebo chybami, které jsou shrnuté nad časovou osou a podrobně popsány v dolní části karty analýza snímků.

 Upozornění a chyby se většinou týkají pouze informativních účelů a nevyžadují žádný zásah.

 Upozornění obvykle signalizují, že hardwarová podpora není k dispozici, ale lze je vypracovat, nelze shromáždit čítače hardwaru nebo některá data o výkonu nemusí být spolehlivá – například v případě, že by to nepříznivě ovlivnilo alternativní řešení.

 Chyby obvykle signalizují, že implementace analýzy snímků má chyby, ovladač obsahuje chyby, hardwarová podpora není k dispozici a nelze ji vymezit nebo se aplikace pokusí o něco, co přehrávání nepodporuje.

### <a name="retries"></a>Opakování
 Pokud se GPU při analýze snímku dostanou přechodem do stavu napájení, je nutné opakovat úspěšnou analýzu, protože se změnila Clockspeed GPU a následně neověřené výsledky relativního časování.

 Analýza snímků omezuje počet opakování na 10. Pokud vaše platforma má agresivní řízení spotřeby nebo časová omezení, může způsobit selhání analýzy snímků a nahlásit chybu, protože překročila limit opakování. Tento problém možná budete moct zmírnit tím, že resetujete řízení spotřeby vaší platformy a omezení rychlosti hodin na méně agresivní, pokud to platforma umožňuje.

## <a name="HardwareSupport"></a>Hardwarová podpora

### <a name="timestamps-and-occlusion-queries"></a>Časová razítka a dotazy překrytí
 Časová razítka jsou podporovaná na všech platformách, které podporují analýzu snímků. Podrobné dotazy překrytí – vyžadované pro čítač pixelů zastíněna – jsou podporované na platformách, které podporují úroveň funkcí 9,2 nebo vyšší.

> [!NOTE]
> Přestože jsou časová razítka podporována na všech platformách, které podporují analýzu snímků, přesnost a konzistence časových razítek se liší od platforem až po platformu.

### <a name="gpu-counters"></a>Čítače GPU
 Podpora hardwarových čítačů GPU je závislá na hardwaru.

 Vzhledem k tomu, že žádný počítač GPU, který aktuálně nenabízí procesory Intel, AMD nebo nVidia, podporuje spolehlivé hardwarové čítače GPU, analýza snímků neshromažďuje čítače z nich. Analýza snímků ale shromažďuje čítače hardwaru z následujícího GPU, který je spolehlivě podporuje:

- nVidia T40 (Tegra4)

  Žádná jiná platforma, která nepodporuje analýzu snímků, shromažďuje hardwarové čítače GPU.

> [!NOTE]
> Vzhledem k tomu, že hardwarové čítače GPU jsou hardwarové prostředky, může trvat více průchodů, aby bylo možné shromáždit kompletní sadu hardwarových čítačů pro každou variantu vykreslování. V důsledku toho je pořadí, ve kterém se shromažďují počítadla GPU, neurčilo.

## <a name="unsupported-scenarios"></a>Nepodporované scénáře
 Některé způsoby použití analýzy snímků nejsou podporované nebo se nejedná o špatný nápad.

### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Přehrávání zachytávání na nejvyšší úrovni funkcí na zařízeních nižší úrovně
 Při použití analyzátoru grafiky při přehrávání souboru protokolu grafiky, který používá vyšší úroveň funkcí než počítač pro přehrávání, se automaticky vrátí k pokřivení. V analýze snímků se explicitně nevrátí zpět na OSNOVu a vygeneruje chybu – OSNOVa je užitečná pro zkoumání správnosti vaší aplikace Direct3D, ale ne pro zkoumání jejího výkonu.

> [!NOTE]
> I když je důležité mít na paměti na úrovni funkcí problémy, můžete zachytit a přehrát soubory protokolu grafiky v různých konfiguracích hardwaru a zařízeních. Protokol grafiky se dá přehrát, dokud soubor protokolu neobsahuje rozhraní API nebo nepoužívá úrovně funkcí, které se na počítači pro přehrávání nepodporují.

### <a name="direct3d-10-and-lower"></a>Direct3D 10 a nižší
 Pokud vaše aplikace volá rozhraní API Direct3D 10, analýza snímků nebude rozpoznána ani profilování, i když jsou rozpoznána a používána jinými nástroji pro analyzátor grafiky.

> [!NOTE]
> To platí jenom pro volání rozhraní Direct3D API, která používáte, a ne na úrovně funkcí.

### <a name="warp"></a>WARP
 Analýza snímků je určena k profilování a zlepšení výkonu vykreslování na reálném hardwaru. Spuštění analýzy snímků na zařízeních s vysokým výkonem se neznemožňuje, ale většinou se to neprojeví, protože se špičkovým procesorem v horním procesorovém procesoru pracuje pomalu, než s nejmenšími dostupnými moderními grafickými procesory a vzhledem k tomu, že se výkon pokřivení může velmi běží na.

## <a name="Variants"></a>Typy
 Každá změna, kterou analýza snímků provede, způsobem, jakým je snímek vykreslen během přehrávání, je označována jako *varianta*. Varianty, které analyzuje rámec, jsou v souladu se společnými, poměrně jednoduchými změnami, které můžete využít ke zlepšení výkonu nebo vizuální kvality vaší aplikace, například ke zmenšení velikosti textur, použití komprese textury nebo povolení různé druhy ochrany proti aliasům. Varianty přepíšou obvyklý kontext vykreslování a parametry vaší aplikace. Tady je přehled:

|Varianty|Popis|
|-------------|-----------------|
|**Velikost zobrazení 1x1**|Zmenší rozměry zobrazení na všech cílech vykreslování na 1x1 pixelů.<br /><br /> Další informace najdete v tématu [varianta velikosti zobrazení 1x1](1x1-viewport-size-variant.md) .|
|**0x MSAA**|Zakáže multi-Sample anti-aliasing (MSAA) pro všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0x/2x/4x varianty rozhraní MSAA](0x-2x-4x-msaa-variants.md) .|
|**2x MSAA**|Povoluje 2x multi-Sample anti-aliasing (MSAA) pro všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0x/2x/4x varianty rozhraní MSAA](0x-2x-4x-msaa-variants.md) .|
|**4x 4x**|Povoluje 4x multi-Sample anti-aliasing (MSAA) pro všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0x/2x/4x varianty rozhraní MSAA](0x-2x-4x-msaa-variants.md) .|
|**Filtrování textury bodu**|Nastaví režim filtrování na `DXD11_FILTER_MIN_MAG_MIP_POINT` (filtrování textury bodu) pro všechny vhodné ukázky textur.<br /><br /> Další informace naleznete v tématech [Point, varianty, trilineárního a Anisotropního Filtering texturs](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Varianty filtrování textury**|Nastaví režim filtrování na `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtrování textury varianty) pro všechny vhodné ukázky textur.<br /><br /> Další informace naleznete v tématech [Point, varianty, trilineárního a Anisotropního Filtering texturs](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Trilineárního filtrování textury**|Nastaví režim filtrování na `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtrování textury trilineárního) pro všechny vhodné ukázky textur.<br /><br /> Další informace naleznete v tématech [Point, varianty, trilineárního a Anisotropního Filtering texturs](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Anisotropního filtrování textury**|Nastaví režim filtrování na `DXD11_FILTER_ANISOTROPIC` a `MaxAnisotropy` na `16` (filtrování textury 16x anisotropního) pro všechny vhodné ukázky textur.<br /><br /> Další informace naleznete v tématech [Point, varianty, trilineárního a Anisotropního Filtering texturs](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Cílový formát vykreslování 16bpp**|Nastaví formát pixelu na `DXGI_FORMAT_B5G6R5_UNORM` (formát 16bpp, 565) pro všechny cíle vykreslování a přetečení.<br /><br /> Další informace najdete v tématu [variantu cílového formátu 16Bpp vykreslování](16bpp-render-target-format-variant.md) .|
|**MIP – generování mapování**|Povoluje mapy MIP u všech textur, které nejsou cílem vykreslování.<br /><br /> Další informace najdete v tématu [varianta generace v mapě MIP](mip-map-generation-variant.md).|
|**Rozměry s poloviční texturou**|Zmenší Rozměry textury na všech texturách, které nejsou v každé dimenzi cílem vykreslení na polovinu původní velikosti. Například textura 256x128 je zmenšena na 128x64 texelů.<br /><br /> Další informace najdete v tématu [variantní rozměry pro texturu v polovičním/čtvrtletí](half-quarter-texture-dimensions-variant.md).|
|**Čtvrtletí – dimenze textury**|Zmenší Rozměry textury na všech texturách, které nejsou vykreslovatelné na čtvrtletí původní velikosti v každé dimenzi. Například textura 256x128 je zmenšena na 64x32 texelů.<br /><br /> Další informace najdete v tématu [variantní rozměry pro texturu v polovičním/čtvrtletí](half-quarter-texture-dimensions-variant.md).|
|**Komprese textury BC**|Povoluje kompresi bloku na všech texturách, které mají variantu formátu B8G8R8X8, B8G8R8A8 nebo R8G8B8A8 pixelů. Varianty formátu B8G8R8X8 se komprimují pomocí BC1; Varianty formátu B8G8R8A8 a R8G8B8A8 se komprimují pomocí BC3.<br /><br /> Další informace naleznete v tématu [variace komprese textury BC](bc-texture-compression-variant.md).|

 Výsledek pro většinu variant je doporučený: "zmenšení velikosti textury na polovinu je 25 procent rychlejší" nebo "povolení dvojnásobku MSAA je pouze 2% pomalejší". Jiné varianty můžou vyžadovat další výklad – například pokud varianta, která mění rozměry zobrazení na 1x1, ukazuje velký nárůst výkonu, může to znamenat, že vykreslování je kritické kvůli nízké rychlosti vyplňování; případně, pokud nedochází ke značným změnám ve výkonu, může to znamenat, že při zpracování vrcholu je problém kritický pro vykreslování.