---
title: Seznam grafických událostí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302124"
---
# <a name="graphics-event-list"></a>Seznam událostí grafiky
Pomocí seznamu událostí grafiky ve Visual Studiu Graphics Analyzer prozkoumejte události Direct3D, které byly zaznamenány při vykreslování rámce hry nebo aplikace.

 Toto je seznam událostí:

 ![Seznam událostí, které mají "Index" v jejich názvu.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Použití seznamu událostí
 Když vyberete událost v seznamu událostí, projeví se v informacích, které se zobrazí jinými nástroji pro analýzu grafiky; pomocí seznamu událostí ve shodě s těmito dalšími nástroji můžete podrobně prozkoumat problém vykreslování a určit jeho příčinu. Další informace o tom, jak můžete vyřešit problémy s vykreslováním pomocí seznamu událostí spolu s dalšími nástroji pro analýzu grafiky, naleznete v [tématu Příklady](graphics-diagnostics-examples.md).

 Efektivní použití funkcí seznamu událostí je důležité pro obcování složitých rámců, které mohou obsahovat tisíce událostí. Chcete-li seznam událostí používat efektivně, zvolte zobrazení, které vám nejlépe vyhovuje, pomocí vyhledávání filtrovat seznam událostí, pomocí odkazů se dozvíte více o objektech Direct3D, které jsou přidruženy k události, a pomocí tlačítek se šipkami rychle přemísťujte hovory mezi voláními.

### <a name="color-coded-events-in-direct3d-12"></a>Barevně odlišené události v Direct3D 12
 Direct3D 12 zveřejňuje více front, které odpovídají různým hardwarovým funkcím. K identifikaci fronty, která je přidružena k určité události grafiky v Direct3D 12, jsou události barevně odlišeny v seznamu událostí podle jejich fronty, když pracujete se zachycením aplikace Direct3D 12.

|Fronta Direct3D 12|Barvy|
|-----------------------|-----------|
|Vykreslit frontu|Green|
|Výpočetní fronta|Žlutý|
|Kopírovat frontu|Orange|

 Direct3D 11 nezveřejňuje více front, takže události nejsou barevně odlišeny v seznamu událostí, když pracujete se zachycením aplikace Direct3D 11.

### <a name="event-list-views"></a>Zobrazení seznamu událostí
 Seznam událostí podporuje dvě různá zobrazení, která organizují grafické události různými způsoby pro podporu pracovního postupu a předvoleb. První zobrazení je *pracovní zobrazení GPU,* které organizuje události a jejich přidružený stav hierarchicky. Druhé zobrazení je *zobrazení časové osy,* které organizuje události chronologicky v plochém seznamu.

 Zobrazení **Práce gpu** zobrazuje zachycené události a jejich stav v hierarchii. Nejvyšší úroveň hierarchie se skládá z událostí, jako je například volání kreslení, vymaže, prezentovat a ty, které se zabývají zobrazení. V seznamu událostí můžete rozbalit volání kreslení a zobrazit stav zařízení, který byl aktuální v době volání kreslení; a můžete dále rozbalit každý druh stavu a zobrazit události, které nastavují jejich hodnoty. Na této úrovni můžete také zjistit, zda byl určitý stav nastaven v předchozím rámci nebo zda byl nastaven více než jednou od posledního volání kreslení.

 Zobrazení **Časové osy** zobrazí každou zachycenou událost v chronologickém pořadí. Tento způsob uspořádání seznamu událostí je stejný jako v předchozích verzích sady Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Změna režimu zobrazení seznamu událostí

- V okně **Seznam událostí grafiky** nad seznamem událostí vyhledejte rozevírací seznam **Zobrazení** a zvolte zobrazení **časové osy** nebo pracovní zobrazení **GPU.**

### <a name="filtering-events"></a>Filtrování událostí
 Pomocí pole Hledat, které se nachází v pravém horním rohu okna **Seznam událostí grafiky,** můžete filtrovat seznam událostí tak, aby zahrnoval pouze události, jejichž názvy obsahují určitá klíčová slova. Pomocí `Vertex`seznamu `Draw;Primitive`se středníkem, který odpovídá událostem, které mají buď `Draw` nebo `Primitive` v jejich názvech, můžete určit jednotlivá klíčová slova, jako je uvedeno na předchozím obrázku. Hledání jsou citlivá na prázdné `VSSet` znaky `VS Set` – například na různá hledání – proto pečlivě vytvářejte vyhledávání.

### <a name="moving-between-draw-calls"></a>Přechod mezi voláními kreslení
 Vzhledem `Draw` k tomu, že zkoumání hovorů je obzvláště důležité, můžete pomocí tlačítek **Přejít na další výzvu** a Přejít na předchozí tlačítka **volání k losování,** která se nacházejí v levém horním rohu okna **Seznam událostí grafiky,** a rychle je mezi nimi vyhledat a přesunout mezi nimi.

### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty
 Chcete-li porozumět určitým grafickým událostem, můžete potřebovat další informace o aktuálním stavu objektů Direct3D nebo o objektech Direct3D, na které událost odkazuje. Mnoho událostí poskytuje odkazy na tyto informace, které můžete sledovat pro další podrobnosti.

## <a name="kinds-of-events-and-event-markers"></a>Druhy událostí a značek událostí
 Události, které jsou zobrazeny v seznamu událostí, jsou uspořádány do čtyř kategorií: obecné události, události kreslení, uživatelem definované skupiny událostí a uživatelem definované značky událostí. S výjimkou obecných událostí se každá událost zobrazí společně s ikonou, která označuje kategorii, do které patří.

|Ikona|Popis události|
|----------|-----------------------|
|(žádná ikona)|Obecná událost<br /> Jakákoli událost, která není uživatelem definovanou událostí, uživatelem definovanou skupinou událostí nebo událostí kreslení.|
|![Ikona události losování](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Událost kreslení<br /> Označí událost kreslení, ke které došlo během zachyceného rámce.|
|![Ikona značky definované události&#45;uživatel](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Uživatelem definovaná skupina událostí<br /> Skupiny související události, jak je definováno aplikací.|
|![Ikona značky definované události&#45;uživatel](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Uživatelem definovaná značka události<br /> Označí konkrétní umístění podle definice aplikace.|

## <a name="marking-user-defined-events-in-your-app"></a>Označení uživatelem definovaných událostí v aplikaci
 Události definované uživatelem jsou specifické pro vaši aplikaci. Můžete je použít ke korelaci významných událostí, ke kterým dochází ve vaší aplikaci, s událostmi v seznamu událostí grafiky. Můžete například vytvořit uživatelem definované skupiny událostí pro uspořádání souvisejících událostí , které slouží k uspořádání souvisejících událostí , do skupin nebo hierarchií, abyste mohli snadněji procházet seznam událostí, nebo můžete vytvořit značky, když jsou určité druhy objektů tak, abyste mohli snadno najít jejich grafické události v seznamu událostí.

 Chcete-li ve vaší aplikaci vytvořit skupiny a značky, použijte stejná rozhraní API, která direct3D poskytuje pro použití jinými nástroji pro ladění Direct3D. Tato rozhraní API se někdy mění mezi verzemi rozhraní Direct3D, ale základní funkce jsou stejné.

### <a name="user-defined-events-in-direct3d-12"></a>Uživatelem definované události v direct3D 12
 Chcete-li vytvořit skupiny a značky v rozhraní Direct3D 12, použijte rozhraní API popsaná v této části. Níže uvedená tabulka shrnuje api, která můžete použít v závislosti na tom, zda označujete události ve frontě příkazů nebo seznamu příkazů.

|Popis rozhraní API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Kontrola dostupnosti událostí definovaných uživatelem|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Zahájení skupiny událostí|[UDÁLOST PIXBegin](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[UDÁLOST PIXBegin](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Ukončení skupiny událostí|[UDÁLOST PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[UDÁLOST PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Vytvoření značky události|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Uživatelem definované události v direct3D 11 a starších
 Chcete-li vytvořit skupiny a značky v rozhraní Direct3D 11 nebo starší, použijte rozhraní API popsaná v této části. Následující tabulka shrnuje rozhraní API, která můžete použít pro různé verze Rozhraní Direct3D 11 a staršíverze rozhraní Direct3D.

|Popis rozhraní API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ řady API (Direct3D 11.0 a starší)|
|---------------------| - | - | - |
|Zahájení skupiny událostí|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Ukončení skupiny událostí|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Vytvoření značky události|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Můžete použít libovolné z těchto rozhraní API, které podporuje vaše verze Direct3D – například pokud cílíte `SetMarker` na `D3DPerf_SetMarker` rozhraní DIRECT3D 11.1 API, můžete použít buď nebo vytvořit značku události, ale ne `SetMarkerInt` proto, že je k dispozici pouze v Direct3D 11.2 – a dokonce můžete kombinovat ty, které podporují různé verze Direct3D dohromady ve stejné aplikaci.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historie zdrojů
Visual Studio 2017 a vyšší obsahují okno **Historie prostředků.**  Výběrem](media/gfx_watch.png) ikony ![sledování hodinek vedle položky v okně Seznam **událostí** se zobrazí okno Historie **zdrojů** zobrazené níže:

![Historie zdrojů](media/gfx_diag_resource_history.png)

Toto okno umožňuje zobrazit historii vybrané položky v seznamu událostí.  Rozevírací seznam v horní části lze použít k výběru dalších položek, které chcete zobrazit historii.  Horní polovina okna obsahuje **události nastavení rámce**.  Jedná se o události, které spadají do kategorie *Vytvořit* typ a jsou volání, která obvykle inicializovat a vytvořit prostředek.  Dolní polovina okna obsahuje část **Události rámce.**  Jedná se o normální události čtení a zápisu, ke kterým dochází během používání prostředku.

| Sloupec | Popis |
|-----------| - |
| **Typ** | Zobrazuje typ položky, obvykle *Vytvořit*, *Číst* a *zapisovat*. |
| **Zobrazit** | Zobrazí miniaturu zdroje v tomto okamžiku v čase.  Poklepáním na miniaturu otevřete v té době zobrazení podrobností o zdroji. |
| **Události** | Zobrazuje volání metody, ke kterému došlo, které vygenerovalo událost.  Libovolnou další historii jednotlivých položek lze zobrazit ![výběrem ikony](media/gfx_watch.png) hodinek na příslušném řádku.  Také každá položka, která je kreslena `m_commandList` modrým textem, například na obrázku výše, může být vybrána pro další podrobnosti. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Viz také
- [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)