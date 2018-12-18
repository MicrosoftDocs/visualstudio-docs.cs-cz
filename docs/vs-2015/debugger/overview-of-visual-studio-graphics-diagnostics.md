---
title: Přehled diagnostiky grafiky sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4ff1b4b74dae005b48f297fa26413fd371fe3f1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051420"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Přehled diagnostiky grafiky sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio *diagnostiky grafiky* je sada nástrojů pro nahrávání a pak analýzu problémů vykreslování a výkon v aplikacích rozhraní Direct3D. Diagnostika grafiky je použít v aplikacích, které běží místně v počítači Windows v emulátoru zařízení Windows nebo na vzdálený počítač nebo zařízení.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Použití Diagnostiky grafiky k ladění problémů s vykreslováním
 Ladění problémů s vykreslováním v aplikaci s bohatou grafikou není tak přímočaré jako spuštění ladicího programu a krokování kódu. V každém snímku jsou produkovány stovky tisíc jedinečných pixelů podle komplexní sady stavu, dat, parametrů a kódu. Z těchto pixelů může problém, který chcete diagnostikovat, vykazovat pouze několik málo pixelů. A aby věci byly ještě složitější, kód, který generuje každý pixel, je spouštěn na specializovaném hardwaru, který paralelně zpracovává stovky pixelů. Tradiční nástroje a techniky ladění, které je obtížné využít i v kódu s malým počtem vláken, jsou v případě velkého množství dat neúčinné.

 Nástroje diagnostiky grafiky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou navržené tak, abychom vám pomohli najít problémů s vykreslováním pomocí vizuálních artefaktů, které označují problém a pak trasování zpět ke zdroji problému se zaměříte jenom na relevantní kód shaderu, kanálu fáze, kreslení volání, prostředky a stavu zařízení – ve zdrojovém kódu aplikace vlastní.

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX
 Diagnostika grafiky podporuje aplikace používající rozhraní Direct3D 12, Direct3D 11 a Direct3D 10 a poskytuje omezenou podporu pro aplikace, které používají rozhraní Direct2D. Nepodporuje aplikace, které používají starší verze rozhraní Direct3D, DirectDraw nebo jiné grafické rozhraní API.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 a Direct3D 12
 Windows 10 přináší další verze rozhraní Direct3D, *Direct3D 12*, který je odlišný od rozhraní Direct3D 10 a Direct3D 11. Tyto rozdíly vrácení DirectX na zarovnání s moderních grafických hardwaru a jeho plného potenciálu unleashing, ale také přenést velké změny rozhraní API a umístit větší zodpovědnost na programátorovi, aby Správa prostředků životnost a množství kolizí. Skvělé ladicí nástroje, je zásadní umožňující programátorům grafiky při tomto přechodu postupovali, takže diagnostiky grafiky v sadě Visual Studio 2015 podporuje Direct3D12 vpravo od začátku. Bez ohledu na rozdíly udržuje diagnostiky grafiky s Direct3D 12-paritu funkcí s diagnostikou grafiky s Direct3D 11.2 pomocí funkce Analýza snímků na aktuální výjimku. Brzy podporu pro analýzu snímků v Direct3D 12 se přidají, za nímž následuje nové diagnostické nástroje, které pomáhají při řešení nové typy chyb, které můžete narazit v Direct3D 12.

 Windows 10 také udržuje pro podporu pro předchozí verze rozhraní Direct3D, hry a aplikace, které spoléhají na ně. Diagnostika grafiky ve Visual Studiu 2015 i nadále podporuje Direct3D 10 a Direct3D 11 ve Windows 10, stejně jako na Windows 8.1.

### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 a Direct3D 11.2
 V [!INCLUDE[win81](../includes/win81-md.md)], DirectX 11.2 zavádí nové funkce, které zahrnují podporu pro zaznamenání grafických informací prostřednictvím jeho modulu runtime. [!INCLUDE[win81](../includes/win81-md.md)] používá nové zachytávání založených na prostředí runtime – označované jako *robustní zachycení*– výhradně pro všechny verze rozhraní DirectX, které [!INCLUDE[win81](../includes/win81-md.md)] podporuje. Robustní zachycení také podporuje nové funkce rozhraní Direct3D 11.2.

### <a name="limited-direct2d-support"></a>Omezená podpora rozhraní Direct2D
 Protože Direct2D je rozhraní API uživatelského režimu, které navazuje na Direct3D, můžete Diagnostiku grafiky použít k ladění problémů s vykreslováním v aplikacích, které využívají Direct2D. Protože jsou však zaznamenány pouze základní události rozhraní Direct3D namísto událostí rozhraní Direct2D na vyšší úrovni, události Direct2D se na seznamu událostí grafiky nezobrazí. A protože vztah mezi událostmi rozhraní Direct2D a výslednými událostmi rozhraní Direct3D není vždy jasný, použití Diagnostiky grafiky k ladění problémů s vykreslováním v aplikacích, které používají Direct2D, není vždy přímočaré. Nadále můžete Diagnostiku grafiky použít k získání informací o problémech s vykreslováním na nízké úrovni v aplikacích, které používají rozhraní Direct2D.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Funkce diagnostiky grafiky sady Visual Studio
 Diagnostika grafiky má vyhrazené rozhraní – okno Graphics Analyzer – pro některé nástroje pro diagnostiku problémů s vykreslováním, ale také přidá do rozhraní sady Visual Studio.

### <a name="the-graphics-toolbar-visual-studio"></a>Panel nástrojů grafika (Visual Studio)
 Panel nástrojů grafika poskytuje rychlý přístup k příkazům diagnostiky grafiky.

 **Spustit diagnostiku** tlačítko spustí aplikaci v rámci diagnostiky grafiky. Když je aplikace spuštěna v rámci diagnostiky grafiky **zachytit příští vykreslený snímek** tlačítko je povolené.

### <a name="diagnostics-capture-interface"></a>Rozhraní zachycení diagnostiky
 Při spuštění aplikace v rámci diagnostiky grafiky sady Visual Studio zobrazí rozhraní relace diagnostiky, můžete použít k zachycení snímků a také zobrazuje aktuální zatížení CPU a GPU. Abyste mohli snadno identifikovat snímky, které můžete chtít zaznamenat z důvodu jejich výkonové charakteristiky, spíše než chyb při vykreslování se zobrazí zatížení CPU a GPU.

 To není jediný způsob, jak ale zachycování snímků. Můžete také zachytit snímky pomocí rozhraní zachytávání prostřednictvím kódu programu, nebo pomocí příkazového řádku pro zachytávání program dxcap.exe.

 Zobrazit [Capturing Graphics Information](../debugger/capturing-graphics-information.md) Další informace.

### <a name="gpu-usage"></a>Využití GPU
 Diagnostika grafiky můžete také Profilovat výkon vaší aplikace Direct3D. Protože profilačních dat by být zkosené zaznamenávání podrobností událostí grafiky, to je oddělená od zachytávání snímků pro použití se Graphics Analyzeru.

 Zobrazit [využití GPU](../debugger/gpu-usage.md) Další informace.

### <a name="directx-control-panel"></a>Ovládací panel rozhraní DirectX
 Ovládací panel rozhraní DirectX je součástí rozhraní DirectX, které můžete použít ke změně způsobu, jakým se rozhraní DirectX chová – například povolit verzi ladění runtime komponent rozhraní DirectX a výběr druhu zpráv ladění, které jsou zaznamenány, a zakázat použití určitých funkcí hardwaru grafiky k emulaci hardwaru s méně funkcemi. Tato úroveň kontroly nad rozhraním DirectX vám může pomoct ladit a testovat vaši aplikaci DirectX. Ovládací panel rozhraní DirectX zobrazíte ze sady Visual Studio.

##### <a name="to-open-the-directx-control-panel"></a>Otevření ovládacího panelu rozhraní DirectX

-   V panelu nabídky zvolte **ladění**, **grafiky**, **ovládací Panel rozhraní DirectX**.

## <a name="graphics-analyzer"></a>Analyzátor grafiky
 Visual Studio Graphics Analyzer je vyhrazený rozhraní pro zkoumání problémů vykreslování a výkonu v snímky, které jste zaznamenali. V analyzátoru grafiky sady najdete několik nástrojů, které vám pomůžou prozkoumat a pochopit chování vykreslování vaší aplikace. Každý nástroj zpřístupňuje jiný druh informací o rámec, který je kontrolován a nástroje jsou navrženy pro použití ve vzájemné součinnosti intuitivně úzký-v na zdroji problému vykreslování, počínaje její vzhled v framebuffer.

 Tento obrázek ukazuje typické rozvržení nástroje v Graphics Analyzeru.

 ![Všechny obrázky okna ladicího programu](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Panel nástrojů grafika (analyzátoru grafiky sady)
 Panel nástrojů grafika poskytuje rychlý přístup k analyzátoru grafiky sady nástrojů systému windows.

 ![Panel nástrojů grafika v režimu Diagnostika grafiky](../debugger/media/vsg-toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Dokument grafických protokolů
 V analyzátoru grafiky je dokument grafických protokolů nejvýraznější panel nástrojů. Toto okno představuje všechny snímky, které jste zachytili spuštěním vaší aplikace v rámci diagnostiky grafiky. Tady můžete vybrat jiný snímek prozkoumat nebo vybrat konkrétní bod, který chcete prozkoumat pomocí nástroje z historie pixelů. Framebuffer obrázek zobrazený v tomto dokumentu tak, aby odrážely aktuálně vybrané události tak, aby viděli vliv framebuffer v čase.

 [Dokument grafických protokolů](../debugger/graphics-log-document.md) je také vstupní bod do nástroje Analýza snímků, které vám pomůže porozumět výkonu tohoto objektu frame mění způsob, jak jsou nakonfigurované některé aspekty vykreslování a poskytnutím výsledky srovnávacích testů porovnání s původní.

### <a name="event-list"></a>Seznam událostí
 Grafické události označit každé volání rozhraní API Direct3D a uživatelem definovanou událost.

 [Seznam událostí](../debugger/graphics-event-list.md) zobrazí všechny události grafiky, které byly zaznamenány během rámce při zkoumání. A umožňují najít, co je důležité, můžete hierarchicky zobrazit seznam událostí – s poslední změny stavu pod následné nakreslit volání, nebo ve formátu časové osy. Kromě toho události se barevně podle toho, ke které patří do fronty a můžete filtrovat, aby obsahoval pouze události, které vás zajímají.

 Když vyberete událost v seznamu, zbývající části nástroje pro analýzu grafiky odráží stav rámce v době této události. Tímto způsobem vidíte účinek jakékoli události na GPU. Přímý vliv jakékoli draw volat framebuffer, například vidíte i v případě, že se stane po volání draw následné skryt. Některé události obsahují také hypertextové odkazy můžete provést, abyste zobrazili další podrobnosti o jeho parametry nebo objektů souvisejících prostředků.

### <a name="pipeline-stages"></a>Fáze zřetězení
 Každé volání draw ve vaší aplikaci prochází zřetězení grafiky poskytované rozhraní Direct3D. V každé fázi v kanálu je výstup z předchozí fáze transformovány sadou malý program, volá shaderu a potom předá do další fáze, až se nakonec vykreslí na obrazovce. Mnoho chyb při vykreslování vyskytovat na hranici mezi fáze zřetězení při výstupní formát se liší, než se očekává, že další fází nebo při libovolné jedné fáze jednoduše produkuje nesprávné výsledky. Za normálních okolností pouze získání konečných výsledků uvidíte na obrazovce a nelze snadno zjistit, kde v kanálu došlo k chybě.

 [Fáze zřetězení](../debugger/graphics-pipeline-stages.md) okno vizualizuje výsledek každou z fází nezávisle na sobě, takže můžete snadněji určit, které fázi k problému vykreslování se nejprve zobrazí v. Jakmile jste zjistili, který fáze to znamená, můžete začít ladění jeho shaderu přímo z okna fáze zřetězení.

### <a name="graphics-state"></a>Stav grafiky
 Vykreslování operace závisí na mnoha stavu, který je obvykle rozdělena mezi více objektů. Různé druhy problémů s vykreslováním jsou způsobené nesprávně nakonfigurovanými stavu.

 [Stavu](../debugger/graphics-state.md) okno shromažďuje relevantní pro každé volání draw pohromadě na jednom místě informace o stavu, takže je jednodušší zjistit, a také nakreslit vybraná vystoupení, změny stavu, ke kterým došlo od předchozího volání.

### <a name="pixel-history"></a>Historie pixelů
 Ve vytváření složitých scén není, pixel na být stín více než jednou v jeden snímek. Někdy je právě přepsána, ale jiné časy jsou zkombinované barvy starší barva dohromady a dosahovat efektů, jako je například průhlednost. Když výsledek je spolu kombinovat nemá správné vzhled nelze zjistit snadno Pokud je to proto, že jeden z barvy byl nesprávný, nebo pokud dojde k nějakému problému s tak, jak byly sloučeny. Jindy objekt může zobrazit chyběla, protože jeho příspěvku obrazového bodu byl odmítnut z nějakého důvodu.

 [Historie pixelů](../debugger/graphics-pixel-history.md) okno vizualizuje kompletní shaderu historii každý pixel v rámci, včetně odmítnuté příspěvků. Příspěvky, které nebyly odmítnuty zobrazí nezpracované shaderu výsledky a jak byl každou novou barvu kombinovat s předchozím histogramem. Pomocí těchto informací je mnohem jednodušší zdroj chyby v pixelech, který blend shaderu výsledky nebo když vykreslené objektu chybí, protože jeho příspěvku obrazového bodu nesprávně byl odmítnut.

### <a name="event-call-stack"></a>Zásobník volání událostí
 Kód shaderu není jediný zdroj problémů s vykreslováním v aplikaci rozhraní Direct3D, někdy zdrojovém kódu vaší aplikace předá parametr nesprávné nebo neprovede konfiguraci Direct3D úplně vpravo. Jeden typ chyby, funkci bylo uvedeno výše, historie pixelů, vám může pomoct najít při vykreslené objekt nebyl nalezen, protože byly odmítnuty jeho pixelů. Předejít těmto chybám obvykle dochází, když je špatně nakonfigurovaný. nastavení, jako ten, který určuje, jak se provádí testem hloubky a obvykle lze najít vaše chyba někde v zásobníku volání chybí objekt nakreslete volání.

 [Zásobník volání událostí](../debugger/graphics-event-call-stack.md) okno zobrazuje úplný zásobník volání každé události grafiky v seznamu událostí, a dokonce umožňuje přejít do své aplikace zdrojový kód, pokud informace o ladění je k dispozici. Jedná se o výkonný nástroj pro následující chybu z kde se poprvé objeví, na grafickém procesoru zpět k původu ve zdrojovém kódu vaší aplikace.

### <a name="object-table"></a>Tabulka objektů
 Každý snímek vaší aplikace vykreslení je pravděpodobně založená na stovky nebo i tisíce objektů prostředků. Ty můžete zahrnout back vyrovnávací paměti a vykreslení cíle, textury, vyrovnávací paměti vrcholů, vyrovnávací paměť indexu, obecné vyrovnávací paměti – téměř vše, co si pamatuje Direct3D je objekt.

 [Tabulky objektů](../debugger/graphics-object-table.md) zobrazí všechny objekty, které existují v okamžiku událostí grafiky vybrali v seznamu událostí. Protože většina objektů v typické aplikaci jsou textury, je optimalizovaná seznam událostí zobrazíte podrobnosti související s imagí na první pohled. Sloupec typu sděluje, kterým druhem objektu je v každém řádku a zobrazuje další sloupec formátu dílčí typ nebo verzi objektu. Další podrobnosti jsou také zobrazeny. Některé objekty mají také hypertextových odkazů, které můžete provést, abyste objekt s více specializované prohlížeč, jako je například textury (textury jako obrázek zobrazit) nebo vyrovnávací paměti (můžete zvolit, jak prohlížeč vyrovnávací paměti analyzuje a zobrazuje počet bajtů nezpracované vyrovnávací paměti tak, že definujete vyrovnávací paměti Formát).

### <a name="frame-analysis"></a>Analýza snímků
 Grafiky vaše aplikace právě nemusí být správné – je třeba je příliš rychle. Dokonce i na méně výkonných zařízení, jako jsou přenosné počítače s integrované grafické nebo mobilní telefony. A stále potřebují vypadat moc velký.

 [Analýza snímků](../debugger/graphics-frame-analysis.md) nástroj zkoumá potenciální optimalizací výkonu automaticky mění způsob, jak aplikace používá rozhraní Direct3D a poskytnutím výsledky srovnávacích testů pro porovnání. Analýza snímků můžete například povolit mip mapování na každý textury, které může odhalit textury, které můžou mít užitek z mapování mip, ale aktuálně nemáte, povolené. Na hardwaru, která ho podporuje, analýza snímků také prezentuje informace shromážděné z čítače výkonu GPU – tato úroveň informací může identifikovat problémy s výkonem úrovni hardwaru, jako je například vysoké množství přepínání načítání textury nebo Neúspěšné přístupy do mezipaměti.

 Ale analýza snímků není jen o přejděte rychle – jde o získání většiny výkonu současně přitom ztráty minimální množství vizuální kvality. Někdy nevyužívá nákladné efekt, který vypadá velmi velké zobrazení na stejné dopad při prohlížení na malé obrazovce telefonu, kde jednodušší vliv může vypadat stejně dobře bez vyprázdnění baterie. Automatické změny a výsledkům srovnávacích testů, které poskytuje grafické analýzy můžete najít rovnováhu, která je nejvhodnější pro vaši aplikaci v široké škále zařízení.

## <a name="see-also"></a>Viz také
 [Nástroj příkazového řádku pro zachytávání](../debugger/command-line-capture-tool.md) [ladicí program HLSL](../debugger/hlsl-shader-debugger.md)
