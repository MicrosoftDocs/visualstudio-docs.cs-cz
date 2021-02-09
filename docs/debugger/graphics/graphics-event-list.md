---
title: Seznam událostí grafiky | Microsoft Docs
description: Pomocí seznamu událostí grafiky v Analyzátor grafiky sady Visual Studio můžete prozkoumat události Direct3D, které byly zaznamenány při vykreslování snímku vaší hry nebo aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c964cda5cbe2903cf9511659b9a8f9bfb9f4aad6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884517"
---
# <a name="graphics-event-list"></a>Seznam událostí grafiky
Pomocí seznamu událostí grafiky v Analyzátor grafiky sady Visual Studio můžete prozkoumat události Direct3D, které byly zaznamenány při vykreslování snímku vaší hry nebo aplikace.

 Toto je seznam událostí:

 ![Seznam událostí, které mají v názvu "index".](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Použití seznamu událostí
 Když v seznamu událostí vyberete událost, projeví se v informacích zobrazených jinými nástroji pro analýzu grafiky. pomocí seznamu událostí ve vzájemné součinnosti s těmito dalšími nástroji můžete zjistit příčinu problému s vykreslováním podrobněji. Další informace o řešení problémů s vykreslováním pomocí seznamu událostí spolu s dalšími nástroji pro analýzu grafiky najdete v tématu [Příklady](graphics-diagnostics-examples.md).

 Efektivní použití funkcí seznamu událostí je důležité pro získání složitých rámců, které mohou obsahovat tisíce událostí. Chcete-li používat seznam událostí efektivně, vyberte zobrazení, které je pro vás nejvhodnější, pomocí funkce Search vyfiltrujte seznam událostí, Sledujte odkazy na Další informace o objektech Direct3D, které jsou přidruženy k události, a pomocí tlačítek se šipkami můžete rychle přecházet mezi voláními remíz.

### <a name="color-coded-events-in-direct3d-12"></a>Barevně kódované události v Direct3D 12
 Direct3D 12 zveřejňuje více front, které odpovídají různým hardwarovým funkcím. Aby bylo možné identifikovat frontu, která je přidružená k určité události grafiky v Direct3D 12, jsou události v seznamu událostí podle jejich fronty barevně kódované, když pracujete se zachycením aplikace Direct3D 12.

|Fronta Direct3D 12|Barva|
|-----------------------|-----------|
|Fronta vykreslování|Green|
|Výpočetní fronta|Žlutý|
|Kopírovat frontu|Oranžový|

 Direct3D 11 nevystavuje více front, takže při práci se zachytáváním aplikace Direct3D 11 nejsou události v seznamu událostí zakódované barevně.

### <a name="event-list-views"></a>Zobrazení seznamu událostí
 Seznam událostí podporuje dvě různá zobrazení, která uspořádávají události grafiky různými způsoby, jak podporovat pracovní postup a předvolby. Prvním zobrazením je *pracovní zobrazení GPU* , které uspořádá události a jejich přidružené stavy hierarchicky. Druhým zobrazením je *zobrazení časové osy* , které organizuje události chronologicky v nestrukturovaném seznamu.

 Zobrazení **práce GPU** zobrazuje zachycené události a jejich stav v hierarchii. Nejvyšší úroveň hierarchie je tvořena událostmi, jako jsou volání draw, vymazání, přítomné a ty, které se týkají zobrazení. V seznamu událostí můžete rozbalit volání vykreslování a zobrazit tak stav zařízení, který byl aktuální v okamžiku volání metody Draw; a dalším rozbalením jednotlivých stavů můžete zobrazit události, které nastavily jejich hodnoty. Na této úrovni můžete také zjistit, zda určitý stav byl nastaven v předchozím snímku nebo zda byl nastaven více než jednou od posledního volání metody Draw.

 Zobrazení **Časová osa** zobrazuje každou zachycenou událost v chronologickém pořadí. Tento způsob uspořádání seznamu událostí je stejný jako v předchozích verzích sady Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>Změna režimu zobrazení seznamu událostí

- V okně **seznam událostí grafiky** nad seznamem událostí najděte rozevírací seznam **zobrazení** a zvolte buď zobrazení **Časová osa** , nebo zobrazení **práce s grafickým procesorem** .

### <a name="filtering-events"></a>Filtrování událostí
 Pomocí vyhledávacího pole, které je umístěné v pravém horním rohu okna **seznam událostí grafiky** , můžete filtrovat seznam událostí tak, aby zahrnoval jenom události, jejichž názvy obsahují konkrétní klíčová slova. Můžete zadat jednotlivá klíčová slova `Vertex` , například, jak je znázorněno na předchozím obrázku, nebo více klíčových slov pomocí seznamu středníkem oddělených `Draw;Primitive` , který odpovídá událostem, které mají buď `Draw` nebo `Primitive` v jejich názvech. Vyhledávání jsou citlivá na prázdné znaky, například, `VSSet` a `VS Set` jsou různá hledání, takže se ujistěte, že poběží hledání pečlivě.

### <a name="moving-between-draw-calls"></a>Přesun mezi voláními vykreslování
 Vzhledem k tomu, že zkoumání `Draw` volání je obzvláště důležité, můžete použít příkaz **Přejít na další volání remíz** a **Přejít na předchozí tlačítka pro volání remíz** – v levém horním rohu okna **seznam událostí grafiky** – k rychlému vyhledání a přesunutí mezi voláními kreslení.

### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty
 Abyste pochopili určité události grafiky, možná budete potřebovat další informace o aktuálním stavu rozhraní Direct3D nebo o objektech Direct3D, na které se odkazuje v události. Mnoho událostí obsahuje odkazy na tyto informace, které můžete použít pro další podrobnosti.

## <a name="kinds-of-events-and-event-markers"></a>Typy událostí a značek událostí
 Události, které jsou zobrazeny v seznamu událostí, jsou uspořádány do čtyř kategorií: Obecné události, nakreslit události, uživatelsky definované skupiny událostí a uživatelsky definované značky událostí. S výjimkou obecných událostí se každá událost zobrazuje spolu s ikonou, která označuje kategorii, do které patří.

|Ikona|Popis události|
|----------|-----------------------|
|(bez ikony)|Obecná událost<br /> Jakákoli událost, která není uživatelem definovaná událost, uživatelem definovaná skupina událostí nebo událost Draw.|
|![Ikona události Draw](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Událost Draw<br /> Označuje událost Draw, ke které došlo během zachyceného snímku.|
|![Ikona značky události definované uživatelem&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Uživatelem definovaná skupina událostí<br /> Seskupuje události související s aplikací.|
|![Ikona značky události definované uživatelem&#45;](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Uživatelsky definovaná značka události<br /> Označí konkrétní umístění definované aplikací.|

## <a name="marking-user-defined-events-in-your-app"></a>Označení uživatelem definovaných událostí v aplikaci
 Uživatelsky definované události jsou specifické pro vaši aplikaci. Můžete je použít ke korelaci významných událostí, ke kterým dochází ve vaší aplikaci, s událostmi v seznamu událostí grafiky. Můžete například vytvořit uživatelsky definované skupiny událostí pro uspořádání souvisejících událostí, jako jsou například ty, které vykreslují vaše uživatelské rozhraní – do skupin nebo hierarchií, aby bylo možné procházet seznam událostí snadněji, nebo můžete vytvořit značky, když se vykreslí konkrétní druhy objektů, abyste mohli snadno najít své grafické události v seznamu událostí.

 Pokud chcete ve své aplikaci vytvořit skupiny a značky, použijte stejná rozhraní API, která technologie Direct3D poskytuje pro použití v jiných ladicích nástrojích Direct3D. Tato rozhraní API se někdy mění mezi verzemi rozhraní Direct3D, ale základní funkce jsou stejné.

### <a name="user-defined-events-in-direct3d-12"></a>Uživatelem definované události v Direct3D 12
 Chcete-li vytvořit skupiny a značky v Direct3D 12, použijte rozhraní API popsaná v této části. Následující tabulka shrnuje rozhraní API, která můžete použít v závislosti na tom, jestli označíte události ve frontě příkazů nebo seznamu příkazů.

|Popis rozhraní API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Ověřit dostupnost události definované uživatelem|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Zahájení skupiny událostí|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Ukončení skupiny událostí|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Vytvoření značky události|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Uživatelem definované události v Direct3D 11 a starších verzích
 Chcete-li vytvořit skupiny a značky v Direct3D 11 nebo starších, použijte rozhraní API popsaná v této části. Následující tabulka shrnuje rozhraní API, která můžete použít pro různé verze Direct3D 11 a starších verzí rozhraní Direct3D.

|Popis rozhraní API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11,1)|D3DPerf_ rodina rozhraní API (Direct3D 11,0 a starší)|
|---------------------| - | - | - |
|Zahájení skupiny událostí|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Ukončení skupiny událostí|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Vytvoření značky události|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Můžete použít kterékoli z těchto rozhraní API, které podporuje vaše verze technologie Direct3D – například pokud cílíte na rozhraní Direct3D 11,1 API, můžete použít buď `SetMarker` nebo `D3DPerf_SetMarker` k vytvoření značky události, ale ne, protože je `SetMarkerInt` dostupná jenom v Direct3D 11.2ch, a můžete dokonce i kombinovat ty, které podporují různé verze Direct3D společně ve stejné aplikaci.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historie prostředků
Visual Studio 2017 a vyšší obsahuje okno **historie prostředků** .  Když vyberete ikonu kukátka ![ kukátka ](media/gfx_watch.png) vedle položky v okně **seznam událostí** , zobrazí se okno **historie prostředků** zobrazené níže:

![Historie prostředků](media/gfx_diag_resource_history.png)

Toto okno umožňuje zobrazit historii vybrané položky v seznamu událostí.  Rozevírací seznam v horní části lze použít k výběru dalších položek k zobrazení historie.  Horní polovina okna obsahuje **události nastavení snímků**.  Jedná se o události, které spadají do kategorie *Create* Type a jsou volání, která obvykle inicializují a vytvoří prostředek.  Dolní polovina okna obsahuje část **události rámce** .  Jedná se o normální události čtení a zápisu, ke kterým dochází při používání prostředku.

| Sloupec | Popis |
|-----------| - |
| **Typ** | Zobrazuje typ položky, obvykle *vytvořit*, *číst* a *zapisovat*. |
| **Zobrazení** | Zobrazuje miniaturu prostředku v daném časovém okamžiku.  Dvojitým kliknutím na miniaturu otevřete v daném čase zobrazení podrobností o prostředku. |
| **Událost** | Zobrazuje volání metody, ke kterým došlo, která vygenerovala událost.  Jakoukoli další historii jednotlivých položek si můžete zobrazit tak, že ![ na příslušném řádku vyberete ikonu kukátka ikona kukátka ](media/gfx_watch.png) .  Pro další podrobnosti je také možné vybrat jakoukoli položku, která je vykreslena modře text, například `m_commandList` na snímku obrazovky výše. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Viz také
- [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)