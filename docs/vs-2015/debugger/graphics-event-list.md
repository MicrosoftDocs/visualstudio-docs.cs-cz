---
title: Seznam událostí grafiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 497ee3fe1c588c84195a544179d0d2955b1932b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766217"
---
# <a name="graphics-event-list"></a>Seznam událostí grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijte seznam událostí grafiky v analyzátoru grafiky sady Visual Studio zkoumat události rozhraní Direct3D, které byly zaznamenány při vykreslování rámce hru nebo aplikaci.  
  
 Toto je seznam událostí:  
  
 ![Seznam událostí, které mají v názvu "Index". ](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Pomocí seznamu událostí  
 Když vyberete událost v případě, že seznam, se projeví v informace, které se zobrazí v jiných nástrojích pro analýzu grafiky; Pomocí seznamu událostí ve vzájemné součinnosti pomocí těchto nástrojů můžete zkoumat podrobně zjistit jeho příčinu problému vykreslování. Další informace o tom, jak můžete vyřešit problémů s vykreslováním použitím seznamu událostí společně s další nástroje pro analýzu grafiky, naleznete v tématu [příklady](../debugger/graphics-diagnostics-examples.md).  
  
 Efektivně díky funkcím, které jsou události v seznamu je důležité pro navigace komplexní rámce, které mohou obsahovat tisíce událostí. Chcete-li efektivně používat seznam událostí, zvolte že zobrazení vám nejvíce vyhovuje, můžete filtrovat seznam událostí, postupujte podle odkazy na další informace o objektech rozhraní Direct3D, která jsou přidružena k události pomocí vyhledávání a použijte šipku tlačítka pro přesun mezi nakreslit volání rychle.  
  
### <a name="color-coded-events-in-direct3d-12"></a>Barevně rozlišená události v Direct3D 12  
 Direct3D 12 poskytuje více front, které odpovídají funkci jiný hardware. K identifikaci fronty, který je spojen s konkrétním grafiky událostí v Direct3D 12, události jsou barevně v seznamu událostí podle jejich fronty, při práci s zachycení aplikace Direct3D 12.  
  
|Direct3D 12 fronty|Barva|  
|-----------------------|-----------|  
|Vykreslení fronty|Zelená|  
|COMPUTE fronty|Žlutá|  
|Fronta kopírování|Oranžová|  
  
 Direct3D 11 nebude vystavit více front, tak události nejsou barevně v seznamu událostí při práci s zachycení aplikace Direct3D 11.  
  
### <a name="event-list-views"></a>Zobrazení seznamu událostí  
 Seznam událostí podporuje dvě různá zobrazení, které umožňují uspořádat událostí grafiky na podporu vašeho pracovního postupu a předvolby různými způsoby. První zobrazení je *volání příkazu pro vykreslení zobrazení* který slouží k uspořádání událostí a jeho přidruženého stavu hierarchicky. Druhý zobrazení je *zobrazení časové osy* který slouží k uspořádání událostí chronologicky, v plochém seznamu.  
  
 **Volání vykreslování,** zobrazení  
 Ukazuje zachycené události a jejich stav v hierarchii. Nejvyšší úroveň hierarchie se skládá z události, například volání draw, vymaže, k dispozici a ztěžovat se zobrazeními. Události seznamu, můžete rozbalit volání vykreslování můžete zobrazit stav zařízení, který byl aktuální v okamžiku volání draw; a je možné dalším rozbalením jednotlivých stavů můžete zobrazit události, které nastavily jejich hodnoty. Na této úrovni také uvidíte, jestli v předchozí snímek byl nastaven určitého stavu, nebo pokud byla nastavena více než jednou od poslední nakreslit volání.  
  
 **Časová osa** zobrazení  
 Zobrazí všechny zachycené události v chronologickém pořadí. Tento způsob uspořádání seznamu událostí je stejné jako v předchozích verzích sady Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>Chcete-li změnit režim zobrazení seznamu událostí  
  
-   V **seznam událostí grafiky** okno nad seznam událostí, vyhledejte **zobrazení** rozevírací seznam a vyberte buď **časová osa** zobrazení nebo **nakreslit volání** zobrazení.  
  
### <a name="filtering-events"></a>Filtrování událostí  
 Můžete použít vyhledávací pole – nachází v pravém horním rohu **seznam událostí grafiky** okno – k filtrování seznamu událostí zahrnout pouze události, jejichž názvy obsahují určitá klíčová slova. Můžete zadat jeden klíčová slova, jako jsou `Vertex`– jak je znázorněno na předchozím obrázku – nebo více klíčových slov s využitím středníkem oddělený seznam podobný `Draw;Primitive`– což odpovídá události, které mají buď `Draw` nebo `Primitive` v jejich názvy. Hledání jsou citlivé na prázdné znaky, například `VSSet` a `VS Set` jsou různé hledání – proto ujistěte se, že do formuláře hledání pečlivě.  
  
### <a name="moving-between-draw-calls"></a>Přesouvání mezi voláními výkresu  
 Protože zkoumání `Draw` volání je obzvláště důležité, můžete použít **nakreslit přejít na další volání** a **nakreslit přejít na předchozí volání** tlačítka – nachází v levém horním rohu **Seznam událostí grafiky** okno – Najít a rychle přesouvat mezi voláními výkresu.  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafických objektů  
 Informace o tom určitých událostí grafiky, může být nutné další informace o aktuálním stavu Direct3D nebo objekty Direct3D, na které odkazuje událost. Mnoho událostí obsahují odkazy na tyto informace, které můžete použít pro více podrobností.  
  
## <a name="kinds-of-events-and-event-markers"></a>Typy událostí a události značek  
 Události, které se zobrazí v případě, že seznam jsou uspořádány do čtyř kategorií: nakreslete obecné události, události, uživatelem definované události skupiny a značky uživatelem definovanou událost. S výjimkou obecné události zobrazí se společně s ikonou, která určuje kategorii, která patří do každé události.  
  
|Ikona|Popis události|  
|----------|-----------------------|  
|(žádná ikona)|Obecné události<br /> Žádné událost, která není uživatelem definované události, uživatelem definované události skupiny nebo nakreslit události.|  
|![Ikona události draw](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Události Draw<br /> Označí událostí draw, ke které došlo během zachyceného snímku.|  
|![Uživatel&#45;definované ikona značky události](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Uživatelem definované události skupiny<br /> Seskupuje související události, jak je definováno aplikací.|  
|![Uživatel&#45;definované ikona značky události](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Značka události definované uživatelem<br /> Označuje konkrétní umístění, jak je definováno aplikací.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Označování událostí definovaných uživatelem ve vaší aplikaci  
 Uživatelem definované události jsou specifické pro vaši aplikaci. Můžete je použít ke korelaci s událostmi v seznamu událostí grafiky významné události, ke kterým dochází ve vaší aplikaci. Můžete například vytvořit uživatelem definované události skupiny pro uspořádání souvisejících událostí, jako jsou ty, které vykreslují uživatelského rozhraní – do skupiny nebo hierarchie tak, aby seznam událostí můžete procházet snadněji, nebo můžete vytvořit značky při určité druhy objektů jsou vykreslit, takže můžete snadno zjistíte, že jejich událostí grafiky v seznamu událostí.  
  
 Chcete-li vytvořit skupiny a značky ve vaší aplikaci, použijte stejná rozhraní API, která rozhraní Direct3D poskytuje pro použití u jiných rozhraní Direct3D, nástroje pro ladění. Tato rozhraní API někdy změnit mezi jednotlivými verzemi rozhraní Direct3D, ale základní funkce jsou stejné.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Uživatelem definované události v Direct3D 12  
 Chcete-li vytvořit skupiny a značky v Direct3D 12, pomocí rozhraní API popsané v této části. Následující tabulka shrnuje rozhraní API, které můžete použít v závislosti na tom, jestli jsou označení událostí ve frontě příkazu nebo příkazu seznamu.  
  
|Popis rozhraní API|[ID3D12CommandQueue](https://msdn.microsoft.com/library/dn788627.aspx)|[ID3D12GraphicsCommandList](https://msdn.microsoft.com/library/dn903537.aspx)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Zkontrolovat dostupnost uživatelem definovanou událost|[PIXGetStatus](http://msdn.microsoft.com/en-us/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/en-us/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Začít skupinu událostí|[PIXBeginEvent](http://msdn.microsoft.com/en-us/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/en-us/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Ukončit skupinu událostí|[PIXEndEvent](http://msdn.microsoft.com/en-us/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/en-us/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Vytvoření značky události|[PIXSetMarker](http://msdn.microsoft.com/en-us/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/en-us/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Uživatelem definované události v Direct3D 11 a starší  
 Pokud chcete vytvořit skupiny a značky v Direct3D 11 nebo starší, pomocí rozhraní API popsané v této části. Následující tabulka shrnuje rozhraní API, která můžete použít pro různé verze rozhraní Direct3D 11 a dřívějších verzích rozhraní Direct3D.  
  
|Popis rozhraní API|[ID3D11DeviceContext2](http://msdn.microsoft.com/library/windows/desktop/dn280498.aspx) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Rozhraní API D3DPerf_ řady (Direct3D 11.0 a starší)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Začít skupinu událostí|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Ukončit skupinu událostí|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Vytvoření značky události|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Můžete použít některý z těchto rozhraní API, které podporuje vaše verze rozhraní Direct3D – například pokud se zaměřujete na rozhraní API Direct3D 11.1, můžete použít buď `SetMarker` nebo `D3DPerf_SetMarker` vytvořit značku události, ale ne `SetMarkerInt` protože jeho k dispozici pouze v Direct3D 11.2 – a dokonce i těch, které společně podporují různé verze rozhraní Direct3D ve stejné aplikaci můžete kombinovat.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu stavu zařízení](../debugger/walkthrough-missing-objects-due-to-device-state.md)



