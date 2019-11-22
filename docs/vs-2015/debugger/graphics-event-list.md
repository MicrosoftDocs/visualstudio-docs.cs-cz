---
title: Seznam událostí grafiky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b1d8bdeb4497af57c385e73ff0dcd34041a2097
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297326"
---
# <a name="graphics-event-list"></a>Seznam událostí grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí seznamu událostí grafiky v Analyzátor grafiky sady Visual Studio můžete prozkoumat události Direct3D, které byly zaznamenány při vykreslování snímku vaší hry nebo aplikace.  
  
 Toto je seznam událostí:  
  
 ![Seznam událostí, které mají v názvu "index".](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Použití seznamu událostí  
 Když v seznamu událostí vyberete událost, projeví se v informacích zobrazených jinými nástroji pro analýzu grafiky. pomocí seznamu událostí ve vzájemné součinnosti s těmito dalšími nástroji můžete zjistit příčinu problému s vykreslováním podrobněji. Další informace o řešení problémů s vykreslováním pomocí seznamu událostí spolu s dalšími nástroji pro analýzu grafiky najdete v tématu [Příklady](../debugger/graphics-diagnostics-examples.md).  
  
 Efektivní použití funkcí seznamu událostí je důležité pro získání složitých rámců, které mohou obsahovat tisíce událostí. Chcete-li používat seznam událostí efektivně, vyberte zobrazení, které je pro vás nejvhodnější, pomocí funkce Search vyfiltrujte seznam událostí, Sledujte odkazy na Další informace o objektech Direct3D, které jsou přidruženy k události, a pomocí tlačítek se šipkami můžete rychle přecházet mezi voláními remíz.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Barevně kódované události v Direct3D 12  
 Direct3D 12 zveřejňuje více front, které odpovídají různým hardwarovým funkcím. Aby bylo možné identifikovat frontu, která je přidružená k určité události grafiky v Direct3D 12, jsou události v seznamu událostí podle jejich fronty barevně kódované, když pracujete se zachycením aplikace Direct3D 12.  
  
|Fronta Direct3D 12|Barva|  
|-----------------------|-----------|  
|Fronta vykreslování|Šetrn|  
|Výpočetní fronta|Opatřen|  
|Kopírovat frontu|Oranžová|  
  
 Direct3D 11 nevystavuje více front, takže při práci se zachytáváním aplikace Direct3D 11 nejsou události v seznamu událostí zakódované barevně.  
  
### <a name="event-list-views"></a>Zobrazení seznamu událostí  
 Seznam událostí podporuje dvě různá zobrazení, která uspořádávají události grafiky různými způsoby, jak podporovat pracovní postup a předvolby. První zobrazení je *zobrazení volání vykreslování* , které organizuje události a jejich přidružený stav hierarchicky. Druhým zobrazením je *zobrazení časové osy* , které organizuje události chronologicky v nestrukturovaném seznamu.  
  
 Zobrazení **volání vykreslování**  
 Zobrazuje zachycené události a jejich stav v hierarchii. Nejvyšší úroveň hierarchie je tvořena událostmi, jako jsou volání draw, vymazání, přítomné a ty, které se týkají zobrazení. V seznamu událostí můžete rozbalit volání vykreslování a zobrazit tak stav zařízení, který byl aktuální v okamžiku volání metody Draw; a dalším rozbalením jednotlivých stavů můžete zobrazit události, které nastavily jejich hodnoty. Na této úrovni můžete také zjistit, zda určitý stav byl nastaven v předchozím snímku nebo zda byl nastaven více než jednou od posledního volání metody Draw.  
  
 Zobrazení **Časová osa**  
 Zobrazí každou zachycenou událost v chronologickém pořadí. Tento způsob uspořádání seznamu událostí je stejný jako v předchozích verzích sady Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Změna režimu zobrazení seznamu událostí  
  
- V okně **seznam událostí grafiky** , nad seznamem událostí, najděte rozevírací seznam **zobrazení** a zvolte buď zobrazení **Časová osa** , nebo zobrazení **volání vykreslování** .  
  
### <a name="filtering-events"></a>Filtrování událostí  
 Pomocí vyhledávacího pole, které je umístěné v pravém horním rohu okna **seznam událostí grafiky** , můžete filtrovat seznam událostí tak, aby zahrnoval jenom události, jejichž názvy obsahují konkrétní klíčová slova. Můžete zadat jednotlivá klíčová slova, jako je například `Vertex`, jak je znázorněno na předchozím obrázku, nebo více klíčových slov pomocí seznamu středníkem oddělených názvů, jako je například `Draw;Primitive`, který odpovídá událostem, které mají v názvech buď `Draw` nebo `Primitive`. Vyhledávání jsou citlivá na prázdné znaky, například `VSSet` a `VS Set` jsou různá hledání, takže se ujistěte, že se vyhledají pečlivě.  
  
### <a name="moving-between-draw-calls"></a>Přesun mezi voláními vykreslování  
 Vzhledem k tomu, že zkoumání `Draw` volání je obzvláště důležité, můžete použít příkaz **Přejít na další volání remíz** a **Přejít na předchozí tlačítka pro volání kreslení** – v levém horním rohu okna **seznam událostí grafiky** – k rychlému vyhledání a přesunutí mezi voláními vykreslování.  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty  
 Abyste pochopili určité události grafiky, možná budete potřebovat další informace o aktuálním stavu rozhraní Direct3D nebo o objektech Direct3D, na které se odkazuje v události. Mnoho událostí obsahuje odkazy na tyto informace, které můžete použít pro další podrobnosti.  
  
## <a name="kinds-of-events-and-event-markers"></a>Typy událostí a značek událostí  
 Události, které jsou zobrazeny v seznamu událostí, jsou uspořádány do čtyř kategorií: Obecné události, nakreslit události, uživatelsky definované skupiny událostí a uživatelsky definované značky událostí. S výjimkou obecných událostí se každá událost zobrazuje spolu s ikonou, která označuje kategorii, do které patří.  
  
|Ikona|Popis události|  
|----------|-----------------------|  
|(bez ikony)|Obecná událost<br /> Jakákoli událost, která není uživatelem definovaná událost, uživatelem definovaná skupina událostí nebo událost Draw.|  
|![Ikona události Draw](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Událost Draw<br /> Označuje událost Draw, ke které došlo během zachyceného snímku.|  
|![Ikona uživatelsky&#45;definované značky události](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Uživatelem definovaná skupina událostí<br /> Seskupuje události související s aplikací.|  
|![Ikona uživatelsky&#45;definované značky události](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Uživatelsky definovaná značka události<br /> Označí konkrétní umístění definované aplikací.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Označení uživatelem definovaných událostí v aplikaci  
 Uživatelsky definované události jsou specifické pro vaši aplikaci. Můžete je použít ke korelaci významných událostí, ke kterým dochází ve vaší aplikaci, s událostmi v seznamu událostí grafiky. Můžete například vytvořit uživatelsky definované skupiny událostí pro uspořádání souvisejících událostí, jako jsou například ty, které vykreslují vaše uživatelské rozhraní – do skupin nebo hierarchií, aby bylo možné procházet seznam událostí snadněji, nebo můžete vytvořit značky, pokud jsou určité typy objektů vykresleno, abyste mohli snadno najít své grafické události v seznamu událostí.  
  
 Pokud chcete ve své aplikaci vytvořit skupiny a značky, použijte stejná rozhraní API, která technologie Direct3D poskytuje pro použití v jiných ladicích nástrojích Direct3D. Tato rozhraní API se někdy mění mezi verzemi rozhraní Direct3D, ale základní funkce jsou stejné.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Uživatelem definované události v Direct3D 12  
 Chcete-li vytvořit skupiny a značky v Direct3D 12, použijte rozhraní API popsaná v této části. Následující tabulka shrnuje rozhraní API, která můžete použít v závislosti na tom, jestli označíte události ve frontě příkazů nebo seznamu příkazů.  
  
|Popis rozhraní API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Ověřit dostupnost události definované uživatelem|[PIXGetStatus](https://msdn.microsoft.com/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Zahájení skupiny událostí|[PIXBeginEvent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Ukončení skupiny událostí|[PIXEndEvent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Vytvoření značky události|[PIXSetMarker](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Uživatelem definované události v Direct3D 11 a starších verzích  
 Chcete-li vytvořit skupiny a značky v Direct3D 11 nebo starších, použijte rozhraní API popsaná v této části. Následující tabulka shrnuje rozhraní API, která můžete použít pro různé verze Direct3D 11 a starších verzí rozhraní Direct3D.  
  
|Popis rozhraní API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11,2)|[ID3DUserDefinedAnnotation](https://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11,1)|D3DPerf_ rodina rozhraní API (Direct3D 11,0 a starší)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Zahájení skupiny událostí|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Ukončení skupiny událostí|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Vytvoření značky události|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Můžete použít kterékoli z těchto rozhraní API, které podporuje vaše verze technologie Direct3D – například pokud cílíte na rozhraní Direct3D 11,1 API, můžete k vytvoření značky události použít buď `SetMarker`, nebo `D3DPerf_SetMarker`, ale ne `SetMarkerInt`, protože jsou dostupné jenom v Direct3D 11.2 – a můžete dokonce kombinovat ty, které podporují různé verze Direct3D společně ve stejné aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu stavu zařízení](../debugger/walkthrough-missing-objects-due-to-device-state.md)
