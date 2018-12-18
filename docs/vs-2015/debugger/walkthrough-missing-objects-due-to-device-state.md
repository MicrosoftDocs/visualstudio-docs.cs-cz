---
title: 'Návod: Chybějící objekty z důvodu stavu zařízení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c0ad6017dd6ff660dfbd47977e1a53346cf6c55
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773727"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Návod: Chybějící objekty z důvodu stavu zařízení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostiky grafiky k prozkoumání objekt, který je z důvodu chybějící správně nakonfigurovaný. stav zařízení.  
  
 Tento návod ukazuje, jak:  
  
-   Použití **seznam událostí grafiky** k vyhledání potenciálních zdrojů problému.  
  
-   Použití **fáze zřetězení grafiky** okna zkontrolovat dopad `DrawIndexed` volání rozhraní API Direct3D.  
  
-   Použití **historie pixelů grafiky** okno přesněji řečeno nalezení problému.  
  
-   Kontrolovat stav zařízení pro potenciální problémy nebo chyby v konfiguraci.  
  
## <a name="scenario"></a>Scénář  
 Jedním z důvodů, že objekty neobjeví, kde se očekává v 3D aplikaci je chybná konfigurace zařízení grafiky, která způsobí, že objekty, které chcete vyloučit z vykreslování – například když pořadí vinutí způsobí, že trojúhelníky vyřazeny chybu , nebo když hloubky testovací funkce způsobí, že všechny obrazové body v objekt, který má být odmítnut.  
  
 Ve scénáři, který je popsaný v tomto podrobném návodu stačí dosáhli prvního milníku při vývoji aplikace pro 3D a jsou připraveny k testování poprvé. Při spuštění aplikace uživatelského rozhraní vykreslen na obrazovku. Pomocí diagnostiky grafiky můžete zaznamenat problém do soubor protokolu grafiky, tak, že ladíte aplikaci. Problém je v aplikace vypadá například takto:  
  
 ![Aplikace předtím, než se problém nevyřeší](../debugger/media/vsg-walkthru1-firstview.png "vsg_walkthru1_firstview")  
  
 Informace o tom, jak zachytit problémy s grafikou v protokolu grafiky, naleznete v tématu [Capturing Graphics Information](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Šetření  
 Pomocí nástrojů diagnostiky grafiky můžete načíst soubor protokolu grafiky kontrolovat rámce, které se zaznamenalo během testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Přezkoumání snímku v protokolu grafiky  
  
1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], načtěte protokol grafiky, který obsahuje rámec vykazující chybí model. Nová karta Diagnostika grafiky se zobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V horní části této karty je výstup cíle vykreslení vybraného snímku. V dolní části je **seznam snímků**, který zobrazuje jako obrázek miniatury každého zachyceného snímku.  
  
2. V **seznam snímků**, vyberte snímek, který ukazuje, že se model zobrazen. Cíl vykreslování se aktualizuje tak, aby odrážely vybraného snímku. V tomto scénáři vypadá karta protokolu grafiky:  
  
    ![.Vsglog kartu framebuffer ve verzi preview a rámce seznamu](../debugger/media/vsg-walkthru1-experiment.png "vsg_walkthru1_experiment")  
  
   Po vybrání rámce, který znázorňuje problém, můžete použít **seznam událostí grafiky** k její diagnostice. **Seznam událostí grafiky** obsahuje každé volání API rozhraní Direct3D, která byla vytvořená pro vykreslení aktivního rámce, například volání rozhraní API k nastavení stavu zařízení můžete taky vytvářet a aktualizovat vyrovnávací paměti a chcete-li nakreslit objekty, které se zobrazují v rámci. Různé druhy volání je zajímavé, protože není často (ale ne vždy) odpovídající změnu cíle vykreslování, pokud aplikace funguje podle očekávání, například kreslení, odesílání, kopírování nebo vymazat volání. Volání příkazu pro vykreslení jsou zvlášť zajímavý, protože každé z nich představuje geometrii, která vykresluje aplikace (odeslání volání může také vykreslit geometrii).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>K zajištění, které kreslí uskutečněných volání  
  
1. Otevřít **seznam událostí grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **seznam událostí**.  
  
2. Zkontrolujte **seznam událostí grafiky** pro kreslení volání. Abychom to usnadnili, zadejte "Draw" **hledání** pole v pravém horním rohu **seznam událostí grafiky** okna. Vyfiltruje seznam tak, aby obsahoval pouze události, které mají "Draw" v názvech. V tomto scénáři zjistíte, že byly provedeny několik volání draw:  
  
    ![Seznam událostí grafiky zobrazující zachycené události](../debugger/media/vsg-walkthru1.png "vsg_walkthru1_")  
  
   Jakmile potvrdíte, které kreslí uskutečněných volání, můžete určit, která z nich odpovídá chybějící geometry. Protože víte, že není právě chybějící geometrie vykreslovány cíl vykreslování (v tomto případě), můžete použít **fáze zřetězení grafiky** okna můžete určit, které nakreslit volání odpovídá chybějící geometry. **Fáze zřetězení grafiky** okno zobrazuje geometrii, která byla odeslána pro každé volání draw, bez ohledu na jeho dopad na cíl vykreslování. Při procházení volání draw, fáze zřetězení se aktualizuje a zobrazí geometrii, která souvisí s voláním a výstup cíle vykreslení se aktualizuje a zobrazí stav cíle vykreslování po volání bylo dokončeno.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>K vyhledání volání draw pro chybějící geometrie  
  
1. Otevřít **fáze zřetězení grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **fáze zřetězení**.  
  
2. Pohyb v každé volání draw při sledování **fáze zřetězení grafiky** okně chybí model. **Vstupní Assembler** fázi zobrazí data o nezpracovanou modelu. **Vertex Shader** fázi zobrazí data o transformovaných modelu. **Pixel Shader** fáze zobrazuje výstup pixel shaderu. **Slučovací modul výstupu** fáze ukazuje cíle vykreslování sloučené toto volání draw a všech předchozích volání draw.  
  
3. Zastavte, když jste dosáhli volání draw, která odpovídá chybí model. V tomto scénáři **fáze zřetězení grafiky** okno označuje, že geometrii vykreslil ale nebyla součástí cíle vykreslování:  
  
    ![Prohlížeč zřetězení zobrazující chybí objekt](../debugger/media/vsg-walkthru1-pipeline.png "vsg_walkthru1_pipeline")  
  
   Jakmile potvrdíte, že aplikace vykreslí chybějící geometrie a vyhledejte odpovídající volání draw, můžete vybrat část výstup cíle vykreslení, který by měl zobrazit chybějící geometrie a pak použít **historie pixelů grafiky** okno a zjistěte, proč byly vyloučeny pixely. Historie pixelů obsahuje seznam každé volání draw, která by mohla obsahovat vliv na jeden konkrétní bod. Každý draw volání v **historie pixelů grafiky** okna je identifikován číslo, které se zobrazí také ve **seznam událostí grafiky** okna. Díky tomu můžete potvrdit, že je pixel by měl zobrazit chybějící geometrie a chcete zjistit, proč byl vyloučen, je pixel  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Chcete-li zjistit, proč byl vyloučen, je pixel  
  
1. Otevřít **historie pixelů grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **historie pixelů**.  
  
2. Na základě **Pixel Shader** miniaturu, vyberte pixel v framebuffer výstup, který by měl obsahovat část chybí geometry. V tomto scénáři by výstup pixel shaderu pokrýval většinu cíle vykreslování; Po výběru pixel **historie pixelů grafiky** okno vypadá takto:  
  
    ![Okno historie pixelů zobrazující související nakreslit volání](../debugger/media/vsg-walkthru1-hist1.png "vsg_walkthru1_hist1")  
  
3. Potvrďte, že pixel cíl vykreslování vybrané obsahuje část geometrii to provede spárováním odpovídajících počet volání draw při kontrole (z **seznam událostí grafiky** okno) do jednoho volání draw v **grafiky Historie pixelů** okna. Pokud žádná volání v **historie pixelů grafiky** okno Shoda volání draw, že zkontrolujete, opakujte tyto kroky (s výjimkou kroku 1) dokud najít shoda. V tomto scénáři odpovídající volání draw vypadá například takto:  
  
    ![Okno historie pixelů informace o fragmentu](../debugger/media/vsg-walkthru1-hist2.png "vsg_walkthru1_hist2")  
  
4. Můžete najít shodu, rozbalte položku odpovídající volání příkazu pro vykreslení v **historie pixelů grafiky** okno a potvrďte, že je pixel byl vyloučen. Každý draw volání v **historie pixelů grafiky** okna odpovídá jedné nebo více geometrické primitivních elementů (body, čáry nebo trojúhelníky), které prolínají obrazového bodu v důsledku geometrie odpovídajícího objektu. Každý takový průnik může přispět k konečnou barvu pixelu. Jednoduchého typu, která je vyloučená, protože se má neprošel testem hloubky je reprezentován ikonou, která zobrazuje písmeno Z za šipkou dolů svažuje zleva doprava.  
  
5. Rozbalte vyloučené primitivem a další kontrolu stavu, který způsobil, že mají být vyloučeny. V **slučovací modul výstupu** skupině, přesuňte ukazatel myši **výsledek**. Popisek označuje, proč byl vyloučen, primitivní vlastnost. V tomto scénáři zkoumání odhalí, že primitivní vlastnost byl vyloučen, protože se neprošel testem hloubky a proto nepřispěl k konečnou barvu pixelu.  
  
   Pokud zjistíte, že geometrie se nezobrazí, protože jste jeho primitivy neprošel testem hloubky, může být máte podezření, jestli problém souvisí s stavu nesprávné konfigurace zařízení. Stav zařízení a jiných rozhraní Direct3D objekt pomocí se dají prozkoumat data **Graphics Object Table**.  
  
#### <a name="to-examine-device-state"></a>Pro zjištění stavu zařízení  
  
1. Otevřít **Graphics Object Table** okna. Na **diagnostiky grafiky** nástrojů, zvolte **tabulky objektů**.  
  
2. Vyhledejte **zařízením D3D10** objekt **Graphics Object Table**a pak otevřete **zařízením D3D10** objektu. Nový **zařízením d3d10** kartě se otevře v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Abychom to usnadnili, můžete seřadit **Graphics Object Table** podle **typ**:  
  
    ![Tabulka grafických objektů a související zařízení stavu](../debugger/media/vsg-walkthru1-objtable.png "vsg_walkthru1_objtable")  
  
3. Zkontrolovat stav zařízení, která se zobrazí **zařízením d3d10** kartu pro potenciální problémy. Protože geometrii nezobrazí, protože jeho primitivy mají neprošel testem hloubky, můžete se zaměřit na stavu zařízení, jako je například hloubky, která ovlivňuje testem hloubky. V tomto scénáři **popis vzorníku hloubky** (v části **výstup stavu fúze**) obsahuje běžné hodnotu pro **hloubka funkce** člena, `D3D10_COMPARISON_GREATER`:  
  
    ![Okno zařízení D3D10 informace vzorníku hloubky](../debugger/media/vsg-walkthru1-devicestate.png "vsg_walkthru1_devicestate")  
  
   Pokud zjistíte, že příčinu problému vykreslování může být nesprávně nakonfigurované hloubka funkce, můžete tyto informace slouží společně s svoje znalosti v oblasti kódu najít, kde byl nesprávně nastaveny hloubka funkce a pak tento problém vyřešit. Pokud nejste obeznámeni s kódem, můžete pro problém vyhledat pomocí příčiny, které jste shromáždili během kdybyste ladili – například na základě **popis vzorníku hloubky** v tomto scénáři můžete vyhledat kód slova například "hloubky" nebo "Vyšší". Po opravě kód její opětovné sestavení a spuštění aplikace znovu a zjistit, že je vyřešen problém vykreslování:  
  
   ![Aplikace, po vyřešení problému](../debugger/media/vsg-walkthru1-finalview.png "vsg_walkthru1_finalview")



