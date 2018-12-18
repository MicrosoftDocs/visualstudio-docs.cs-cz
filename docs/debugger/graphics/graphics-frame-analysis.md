---
title: Analýzy grafických snímků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0ae541830adab222b07d1f16ce99e4957e380e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838098"
---
# <a name="graphics-frame-analysis"></a>Analýza grafických snímků
Analýza grafických snímků v analyzátoru grafiky sady Visual Studio použijte k analýze a optimalizovat výkon vykreslování Direct3D hře nebo aplikaci.  

## <a name="frame-analysis"></a>Analýza snímků  
 Analýza snímků používá stejné informace, které jsou zachyceny v souboru protokolu grafiky pro účely diagnostiky, ale používá ke shrnutí výkon vykreslování místo. Informace o výkonu se zaznamenávají do protokolu při zachytávání; Místo toho informace o výkonu je generováno později během analýzu snímků, události časování a shromažďování statistik přehrát rámce. Tento přístup má několik výhod oproti zaznamenávání informací o výkonu při zachytávání:  
  
- Analýza snímků můžete průměrné výsledky z více jednotlivými cykly stejné rámce, který zajišťuje souhrnu výkonu statisticky zvuku.  
  
- Analýza snímků můžete generovat informace o výkonu pro hardwarové konfigurace a jiná zařízení než ten, ve kterém byly informace zachyceny.  
  
- Analýza snímků můžete vygenerovat nový souhrny výkonu z dříve zaznamenaných informací – například když jsou optimalizované nebo zpřístupňují další funkce ladění ovladače GPU.  
  
  Kromě těchto výhod analýza snímků můžete také provádět změny rámce vykreslení během přehrávání tak, aby se může zobrazit informace o tom, jak tyto změny mohou ovlivnit výkon vykreslování aplikace. Tyto informace můžete se rozhodnout mezi potenciální optimalizační strategie, aniž by bylo nutné implementovat všechny a pak zachytíte a všechny jeho výsledky porovnání sami.  
  
  I když se analýza snímků je primárně určena pomoci dosáhnout vyšší výkon vykreslování, je stejně můžete dosáhnout lepší vizuální kvality pro danou výkonu cíl nebo snížení spotřeby energie GPU.  
  
  Pokud chcete zobrazit ukázku analýzy snímků přínosech pro vaši aplikaci, můžete se podívat [analýza grafických snímků Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) videa na webu Channel 9.  
  
## <a name="using-frame-analysis"></a>Pomocí analýza snímků  
 Než budete moct použít analýzu snímků, budete muset zachytit informace grafiky z aplikace za běhu, stejně jako když použijete některou z dalších analyzátoru grafiky sady nástrojů. Pak v okně dokumentu (.vsglog) protokol grafiky zvolte **analýza snímků** kartu.  
  
 ![Vyberte kartu analýza snímků](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")  
  
 Po dokončení analýzy, výsledky se zobrazí. Horní části na kartu analýza snímků zobrazí časového harmonogramu a tabulku souhrnu. Dolní část zobrazuje tabulky podrobností. Pokud se během přehrávání byly vygenerovány chyby nebo varování, ty jsou uvedené výše na časové ose; odtud můžete použít odkazy na další informace o chybách a upozorněních.  
  
### <a name="interpreting-results"></a>Interpretace výsledků  
 Interpretací výsledků jednotlivých variant lze odvodit, užitečné informace o vaší aplikaci prvku vykreslování, výkonu a chování. Další informace o vykreslování variant najdete v tématu [varianty](#Variants) dále v tomto článku.  
  
 Některé výsledky přímo udávají, jak varianty ovlivňuje výkon vykreslování:  
  
- Pokud varianta varianty filtrování textur zvýšení výkonu jsme si ukázali, potom pomocí filtrování ve vaší aplikaci varianty textur zobrazí podobné zvýšení výkonu.  
  
- Pokud varianta oblasti zobrazení 1 x 1 jsme si ukázali, zvýšení výkonu, pak snižuje velikost cíle vykreslování v aplikaci bude vylepšit výkon vykreslování.  
  
- Pokud varianta komprese textur BC zvýšení výkonu jsme si ukázali, pak pomocí komprese textur BC ve vaší aplikaci se zobrazí podobné zvýšení výkonu.  
  
- Pokud varianta 2xMSAA má skoro stejný výkon jako typ variant 0xMSAA, můžete povolit 2xMSAA ve vaší aplikaci zlepšovat kvalitu vykreslování bez dalších nákladů ve výkonu.  
  
  Další výsledky by mohla naznačovat hlubší, jemnější dopady na výkon vaší aplikace:  
  
- Pokud varianta oblasti zobrazení 1 x 1 zobrazuje velmi náročné na výkon, vaše aplikace pravděpodobně spotřebovává další fillrate, než je k dispozici. Pokud se tato varianta zobrazí bez zvýšení výkonu, pravděpodobně příliš mnoho vrcholy aplikace zpracovává.  
  
- Pokud varianta 16bpp vykreslování cílového formátu ukazuje významného zvýšení výkonu, vaše aplikace pravděpodobně spotřebovává příliš mnoho paměti šířky pásma.  
  
- Pokud varianta rozměrů textury Half/Quarter ukazuje významného zvýšení výkonu, vaše textury pravděpodobně zabírat moc paměti, spotřebovat příliš velkou šířku pásma nebo neefektivnímu využití mezipaměti textur. Pokud se tato varianta zobrazí žádné změny ve výkonu, můžete použít větší, podrobnější textury pravděpodobně bez nutnosti platit snížení výkonu.  
  
  Když jsou k dispozici čítačů hardwaru, můžete je shromažďovat velmi podrobné informace o proč může utrpení vykreslování výkon vaší aplikace. Hloubka uzavření dotazy nepodporují všechna zařízení 9.2 a vyšší úroveň funkcí (**pixelů occluded** čítače) a časová razítka. Další čítače hardwaru může být k dispozici, v závislosti na, jestli má výrobce GPU implementované čítačů hardwaru a vystavený v jeho ovladače. Potvrďte přesnou příčinu na výsledky zobrazené v souhrnu tabulce můžete použít tyto čítače – například můžete určit, jestli overdraw je faktor prozkoumáním procento pixelů, které byly occluded testem hloubky.  
  
### <a name="timeline-and-summary-table"></a>Časová osa a souhrnnou tabulku  
 Ve výchozím nastavení časového harmonogramu a tabulku se souhrnem se zobrazí a ostatní oddíly, jsou sbaleny.  
  
#### <a name="timeline"></a>Časová osa  
 Časová osa ukazuje základní informace o časování volání draw vzhledem k mezi sebou. Protože větší pruhy odpovídají delší dobu draw, můžete rychle najít v rámci nejdražší volání vykreslování. Po zobrazení zachyceného snímku obsahuje velký počet volání draw, nakreslit více kreslí volání jsou sloučeny do jednoho panelu jehož délka je součtem těchto volání.  
  
 ![Časová osa ukazuje draw&#45;volání náklady. ](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")  
  
 Přesuňte ukazatel na pruh zobrazíte která volání draw událost odpovídá panelu. Že vybereme pruh způsobí, že seznam událostí k synchronizaci na tuto událost.  
  
#### <a name="table"></a>Tabulka  
 Všechna čísla pod na časové ose tabulce relativní výkon jednotlivých vykreslování variant pro každé volání draw s ohledem na vaše aplikace výchozí vykreslení. Každý sloupec zobrazuje hodnotu typu variant různých vykreslování a každý řádek představuje jinou draw volání, který je identifikován v sloupci nejvíce vlevo. Odsud můžete použít odkaz na událost v okně seznam událostí grafiky.  
  
 ![V souhrnu tabulce jsou uvedeny různé varianty. ](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")  
  
 Druhý sloupec v tabulce shrnutí nejvíce vlevo zobrazí čas vykreslování směrného plánu vaší aplikace – to znamená, dobu trvá, vaše aplikace výchozí vykreslení. k dokončení volání draw. Zbývající sloupce zobrazí relativní výkon jednotlivých vykreslování variant jako procento směrného plánu, takže je snazší zjistit, jestli se výkon. Procenta větší než 100 % trval déle, než standardních hodnot – to znamená výkonu byl vypnut – a menší než 100 % jeho obsahu trvalo méně času procenta – zvýšil výkon.  
  
 Hodnoty absolutní časování směrný plán a relativní časování vykreslování variant jsou ve skutečnosti střední průměry více běhů – 5 ve výchozím nastavení. Tento průměrný pomáhá zajistit data časování spolehlivý a konzistentní. Lze ukazatele pro každou buňku v tabulce k prozkoumání minimum, maximum, průměr a hodnoty mediánu časování, které nebyly pozorovány při kreslení výsledky, které volání a vykreslování variant byly vygenerovány. Zobrazí se také standardní hodnoty časování.  
  
#### <a name="hot-draw-calls"></a>"Horkou" volání kreslení  
 Aby pozornost k vykreslení volání, které využívají větší část celkové čas vykreslování nebo, který může být neobvykle pomalé z důvodů, které by se vyhnout, řádek, který obsahuje následující volání draw "horkými" je označeno šedou barvou red při vlastní směrný plán časování je více než jeden Směrodatná odchylka delší než střední načasování všechna volání příkazu pro vykreslení v rámci směrného plánu.  
  
 ![Toto volání DrawIndexed má horké a studené variant. ](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Statistický význam  
 Analýza snímků vám pozornost k vykreslení varianty, které mají nejvyšší relevanci Určuje statistické význam jednotlivých vykreslování variant a zobrazí ta významné jako tučné písmo. Zobrazí ty, které zlepšují výkon zeleně a ty, které sníží výkon červeně. Zobrazí výsledky, které nejsou statisticky významná jako normální typu.  
  
 ![Statistické relevence variant volání draw](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")  
  
 Pokud chcete zjistit statistické relevance, analýza snímků používá [Studentova t-test](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Tabulka podrobností  
 Pod souhrnem tabulka je tabulka podrobnosti, které ve výchozím nastavení je sbalený. Obsah z tabulky Details závisí na hardwarové platformě zařízení pro přehrávání. Informace o podporovaných hardwarové platformy najdete v tématu [hardwarovou podporu](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Platformy, které nepodporují čítačů hardwaru  
 Většina platforem plně nepodporují čítačů hardwaru s GPU – patří mezi ně všechny procesory Intel, AMD a nVidia v současnosti nabízejí. Pokud neexistují žádné čítače hardwaru shromažďovat, se zobrazí pouze jedna tabulka podrobností a obsahuje střední absolutní časování všech variant.  
  
 ![Tabulka podrobností a některé varianty přehrávání. ](media/pix_frame_analysis_details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Platformy, které podporují čítačů hardwaru  
 Pro platformy, které podporují čítačů hardwaru s GPU – například nVidia T40 SOC a všechny Soc Qualcomm – několik tabulek podrobnosti jsou zobrazeny, jeden pro každý typ variant. Každý čítač dostupného hardwaru shromážděných pro každý typ variant vykreslování a zobrazit své vlastní tabulky Podrobnosti.  
  
 ![Pokud je podporovaná, zobrazí se čítačů hardwaru. ](media/pix_frame.png "pix_frame")  
  
 Informace z čítače hardwaru poskytuje velmi podrobné zobrazení chování specifické hardwarové platformy pro každé volání draw, která vám pomůže identifikovat příčiny problémových míst výkonu velmi přesně.  
  
> [!NOTE]
>  Jiné hardwarové platformy podporují různé čítače; neexistuje žádný standardní. Čítače a co představují jsou určeny výhradně každého výrobce GPU.  
  
### <a name="marker-regions-and-events"></a>Oblasti značky a události  
 Analýza snímků podporuje uživatelem definované události značek a skupiny událostí. Jsou zobrazeny v souhrnnou tabulku a podrobností tabulky.  
  
 Rozhraní API ID3DUserDefinedAnnotation nebo starší verzi D3DPERF_ řadu rozhraní API slouží k vytvoření značky a skupiny. Při použití řady D3DPERF_ rozhraní API můžete přiřadit každý značky a skupiny barva, která se analýza snímků se zobrazí jako barevný vzdálené správy v rámci řádky, které obsahují značka události nebo značky begin/end skupiny událostí a jejich obsah. Tato funkce vám umožňují rychle identifikovat důležité vykreslování události nebo zvýrazňující skupiny událostí.  
  
### <a name="warnings-and-errors"></a>Upozornění a chyby  
 Analýza snímků se příležitostně dokončí s upozornění ani chyby, které jsou shrnuty nad časovou osou a podrobně popsané v dolní části na kartu analýza snímků.  
  
 Obvykle upozornění a chyby jsou pouze k informačním účelům a nevyžadují zásahu.  
  
 Upozornění obvykle signalizují, že hardwarovou podporu chybí, ale je možné pracovat kolem, není možné shromáždit čítače hardwaru nebo některé údaje o výkonu nemusí být spolehlivé – například při řešení má nepříznivý vliv na to.  
  
 Chyby obvykle signalizují, že implementace analýzy snímků má chyby, ovladač obsahuje chyby, hardwarovou podporu chybí a nelze pracoval kolem nebo aplikace bude něco, co není podporovaná přehráváním.  
  
### <a name="retries"></a>Počet opakování  
 Pokud GPU při přechodu stavu napájení během analýzy snímků, musí průchodu ovlivněné analýzy opakovat, protože GPU clockspeed změnit a relativní časování výsledky a tím zneplatněny.  
  
 Analýza snímků omezuje počet 10 opakování. Pokud má vaše platforma agresivní spotřeby nebo prostřednictvím brány hodiny, může způsobit analýza snímků ohlásit chybu, protože došlo k překročení limitu opakování a selhání. Je možné zmírnit potíže resetováním řízení spotřeby vaší platformě a hodiny, bude méně agresivní, pokud ji povolí platformu omezování rychlosti.  
  
##  <a name="HardwareSupport"></a> Hardwarovou podporu  
  
### <a name="timestamps-and-occlusion-queries"></a>Časová razítka a uzavření dotazů  
 Časová razítka jsou podporované na všech platformách, které podporují analýzu snímků. Hloubka uzavření dotazy – vyžadované pro čítač pixelů Occluded – jsou podporovány na platformách, které podporují úroveň funkcí 9.2 nebo vyšší.  
  
> [!NOTE]
>  I když časová razítka se podporuje na všech platformách, které podporují analýzu snímků, přesnost a důslednost časová razítka se liší od platformách.  
  
### <a name="gpu-counters"></a>Čítače GPU  
 Podpora GPU čítačů hardwaru je závislá na hardwaru.  
  
 Vzhledem k tomu, že žádný počítač GPU nVidia, Intel nebo AMD v současné době nabízena podporuje čítačů hardwaru s GPU spolehlivě, analýza snímků neshromažďuje čítače z nich. Analýza snímků však čítačů hardwaru shromažďovat následující GPU, která je spolehlivě podporuje:  
  
- nVidia T40 (Tegra4)
  
  Žádná jiná platforma, která podporuje analýzu snímků shromažďuje čítače hardwarové GPU.  
  
> [!NOTE]
>  Vzhledem k tomu čítačů hardwaru s GPU hardwarové prostředky, může trvat několik průchodů za účelem shromažďování kompletní sadu čítačů hardwaru pro každý typ variant vykreslování. V důsledku toho neurčené pořadí, ve které GPU se shromažďují čítače.  
  
## <a name="unsupported-scenarios"></a>Nepodporované scénáře  
 Některé z mnoha možností použití analýza snímků nejsou podporovány nebo jsou právě nápad.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Zaznamená přehrávání vysokou úroveň funkcí na zařízeních s nižší úrovně  
 V analyzátoru grafiky sady při přehrávání souboru protokolu grafiky, která používá vyšší úroveň funkcí než počítač pro přehrávání podporuje, se automaticky vrátí k technologiím WARP. V analýza snímků se explicitně nepřecházel k WARP a vygeneruje chybu, je užitečné pro zkoumání správnosti aplikace Direct3D, ale ne pro zkoumání jeho výkon.  
  
> [!NOTE]
>  I když je potřeba vzít v úvahu problémy úroveň funkcí, můžete zachytit a přehrávání souborů na zařízeních a jiné hardwarové konfigurace protokolu grafiky. Protokol grafiky můžete přehrát zpět, dokud nebude obsahovat rozhraní API nebo použijte úrovní funkcí, které nejsou podporovány na počítači pro přehrávání souboru protokolu.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 a nižší  
 Pokud vaše aplikace volá rozhraní API Direct3D 10, analýza snímků nebudou rozpoznávání nebo je profil, i když jsou rozpoznány a používají jiné nástroje pro analyzátor grafiky sady.
  
> [!NOTE]
>  To platí jenom pro rozhraní Direct3D volání rozhraní API, které používáte, není úrovní funkcí.

### <a name="warp"></a>WARP  
 Analýza snímků je určena pro použití k profilu a zvýšení výkonu vykreslování na skutečný hardware. Spouštění analýzy snímků na zařízení WARP není zabráněno, ale není obvykle vhodné výkonu vzhledem k tomu, že běží na vyšší kategorie procesoru WARP je pomalejší než i nejméně podporující moderní GPU a protože WARP výkonu může značně lišit v závislosti na konkrétním procesoru je spuštěn na.  
  
##  <a name="Variants"></a> Varianty  
 Každá změna, kterou analýza snímků se provede tak, jak je vykreslen blok při přehrávání se označuje jako *variant*. Varianty, které zkoumá analýza snímků odpovídají běžné, je poměrně snadné provedených změn může zlepšit výkon při vykreslování nebo kvality vaší aplikace – například nezmenšit velikost této textury, komprese textur nebo povolte různé druhy anti-aliasing. Varianty přepsání kontextu obvykle vykreslování a parametry vaší aplikace. Toto je souhrn:  
  
|Variant|Popis|  
|-------------|-----------------|  
|**Velikosti oblasti zobrazení 1 x 1**|Snižuje rozměry zobrazení na všechny cíle vykreslení na 1 × 1 pixelů.<br /><br /> Další informace najdete v tématu [varianta velikosti oblasti zobrazení 1 x 1](1x1-viewport-size-variant.md)|  
|**0x MSAA**|Zakáže více ukázka vyhlazování (MSAA) na všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0 x / 2 x / 4 x MSAA variant](0x-2x-4x-msaa-variants.md)|  
|**2x MSAA**|Umožňuje 2 x více ukázka vyhlazování (MSAA) na všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0 x / 2 x / 4 x MSAA variant](0x-2x-4x-msaa-variants.md)|  
|**4x MSAA**|Umožňuje 4 x více ukázka vyhlazování (MSAA) na všechny cíle vykreslování.<br /><br /> Další informace najdete v tématu [0 x / 2 x / 4 x MSAA variant](0x-2x-4x-msaa-variants.md)|  
|**Filtrování bodu textury**|Nastaví režim filtrování `DXD11_FILTER_MIN_MAG_MIP_POINT` (bod filtrování textur) pro všechny ukázky odpovídající textury.<br /><br /> Další informace najdete v tématu [bod, bilineární, Trilinear a varianty Anisotropního filtrování textur](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrování varianty textury**|Nastaví režim filtrování `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (varianty textury filtrování) pro všechny ukázky odpovídající textury.<br /><br /> Další informace najdete v tématu [bod, bilineární, Trilinear a varianty Anisotropního filtrování textur](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrování trilineárního textury**|Nastaví režim filtrování `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (trilineárního textury filtrování) pro všechny ukázky odpovídající textury.<br /><br /> Další informace najdete v tématu [bod, bilineární, Trilinear a varianty Anisotropního filtrování textur](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Textura anisotropního filtrování**|Nastaví režim filtrování `DXD11_FILTER_ANISOTROPIC` a `MaxAnisotropy` k `16` (16 x textury anisotropního filtrování) pro všechny ukázky odpovídající textury.<br /><br /> Další informace najdete v tématu [bod, bilineární, Trilinear a varianty Anisotropního filtrování textur](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**16bpp vykreslování cílového formátu**|Nastaví formát pixelu na `DXGI_FORMAT_B5G6R5_UNORM` (16bpp 565 formátu) pro všechny vykreslování cíle a backbuffers.<br /><br /> Další informace najdete v tématu [16bpp vykreslování cílového formátu typu Variant](16bpp-render-target-format-variant.md)|  
|**Generování Mipmap**|Umožňuje mapy mip na všechny textury, které nejsou cíle vykreslování.<br /><br /> Další informace najdete v tématu [varianta generování Mipmap](mip-map-generation-variant.md).|  
|**Rozměry textury polovinu**|Snižuje rozměrů textury na všechny textury, které nejsou cíle vykreslení na polovinu své původní velikosti v každém rozměru. Například 256 x 128 textury se zkrátilo na texely 128 x 64.<br /><br /> Další informace najdete v tématu [Half/Quarter textury dimenze Variant](half-quarter-texture-dimensions-variant.md).|  
|**Rozměry textury čtvrtletí**|Snižuje rozměrů textury na všechny textury, které nejsou cíle vykreslování na čtvrtletí jejich původní velikost v každém rozměru. Například 256 x 128 textury sníží texely 64 x 32.<br /><br /> Další informace najdete v tématu [Half/Quarter textury dimenze Variant](half-quarter-texture-dimensions-variant.md).|  
|**Komprese textur BC**|Umožňuje zablokovat kompresi na všechny textury, které mají B8G8R8X8, B8G8R8A8 nebo R8G8B8A8 variant formát pixelu. Varianty formátu B8G8R8X8 komprimování pomocí BC1; S použitím BC3 jsou komprimované B8G8R8A8 a R8G8B8A8 formátu variant.<br /><br /> Další informace najdete v tématu [BC textury komprese Variant](bc-texture-compression-variant.md).|  
  
 Výsledek pro většinu varianty je doporučené: "25 procent rychlejší je snížení velikosti textury na polovinu" nebo "Povolení 2 x MSAA je pouze 2 % pomaleji". Ostatní varianty může vyžadovat další výklad – například pokud variantu, která změní rozměry zobrazení 1 x 1 zobrazuje velké výkonnější, může to znamenat, že se tak s nízkou výplně mírou; bottlenecked vykreslování případně pokud neexistuje žádné významné změny ve výkonu, může to znamenat, že se zpracováním vrcholu bottlenecked vykreslování.