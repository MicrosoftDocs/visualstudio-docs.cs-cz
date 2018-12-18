---
title: 'Návod: Chybějící objekty z důvodu nesprávné konfigurace zřetězení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd28886695e3234240de5675e5e2b19972b105fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782009"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Návod: Chybějící objekty z důvodu nesprávné konfigurace zřetězení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů diagnostiky grafiky k prozkoumání objekt, který nebyl nalezen kvůli nenastavené pixel shader.  
  
 Tento návod ilustruje tyto úkoly:  
  
-   Použití **seznam událostí grafiky** k vyhledání potenciálních zdrojů problému.  
  
-   Použití **fáze zřetězení grafiky** okno prozkoumat účinek `DrawIndexed` volání rozhraní API Direct3D.  
  
-   Kontroluje se kontext zařízení potvrďte, že nebyla nastavena fázi shaderu.  
  
-   Použití **fáze zřetězení grafiky** okno spolu s **zásobník volání událostí grafiky** vám pomohou najít zdroje nenastavené pixel shader.  
  
## <a name="scenario"></a>Scénář  
 Pokud objekt chybí v 3D aplikaci, je to někdy protože jeden z těchto fází shaderu není nastaven před vykreslením objektu. V aplikacích, které mají jednoduchý vykreslování potřebám příčiny této chyby je obvykle někde umístěn v zásobníku volání objektu volání draw. Ale rámci Optimalizace aplikací batch společně objekty, které jsou programy shaderu, textury a další data v běžných, chcete-li minimalizovat – změnu stavu režie. V těchto aplikacích zdroje chyby může být schovaný v systému dávkování, spíše než umístěný v zásobníku volání daného volání vykreslování. Scénář v tomto návodu ukazuje aplikace, který má jednoduchý vykreslování potřebám a proto zdroje chyby najdete v zásobníku volání.  
  
 V tomto scénáři při spuštění aplikace a otestovat ho pozadí se vykresluje podle očekávání, ale jeden z objektů se nezobrazí. Pomocí diagnostiky grafiky můžete zaznamenat problém do protokolu grafiky, tak, že ladíte aplikaci. Problém je v aplikace vypadá například takto:  
  
 ![Objekt je nemohou vidět](../debugger/media/gfx-diag-demo-misconfigured-pipeline-problem.png "gfx_diag_demo_misconfigured_pipeline_problem")  
  
## <a name="investigation"></a>Šetření  
 Pomocí nástrojů diagnostiky grafiky můžete načíst dokument grafických protokolů ke kontrole snímků, které byly zachyceny během testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Přezkoumání snímku v protokolu grafiky  
  
1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], načíst dokument grafických protokolů, který obsahuje rámec vykazující chybí objekt. Zobrazí se nová karta protokolu grafiky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V horní části této karty je výstup cíle vykreslení vybraného snímku. V dolní části je **seznam snímků**, který zobrazuje jako obrázek miniatury každého zachyceného snímku.  
  
2. V **seznam snímků**, vyberte snímek, který ukazuje, že objekt se nezobrazuje. Cíl vykreslování se aktualizuje tak, aby odrážely vybraného snímku. V tomto scénáři vypadá karta protokolu grafiky:  
  
    ![Dokumentu protokolu grafiky v aplikaci Visual Studio](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-1.png "gfx_diag_demo_misconfigured_pipeline_step_1")  
  
   Po vybrání rámce, který znázorňuje problém, můžete začít pro diagnostiku pomocí **seznam událostí grafiky**. **Seznam událostí grafiky** obsahuje každé volání rozhraní API Direct3D, která byla vytvořena pro vykreslení aktivní rámec – například k nastavení stavu zařízení můžete taky vytvářet a aktualizovat vyrovnávací paměti a chcete-li nakreslit objekty, které se zobrazují v rámci. Různé druhy volání – například kreslení, odesílání, kopírování nebo vymazat volání – jsou zajímavé, protože je často (ale ne vždy) odpovídající změnu cíle vykreslování, pokud aplikace funguje podle očekávání. Volání příkazu pro vykreslení jsou zvlášť zajímavý, protože každé z nich představuje geometrii, která vykresluje aplikace.  
  
   Protože víte, že cíl vykreslování nebude obsahovat chybějící objektu ale také, že existuje pravděpodobně jiné chyby, můžete použít **seznam událostí grafiky** spolu s **fáze zřetězení grafiky**nástroje k určení, které nakreslit volání odpovídá chybějícím objektu geometry. **Fáze zřetězení grafiky** okno zobrazuje geometrii, která byla odeslána pro každé volání draw, bez ohledu na jeho dopad na cíl vykreslování. Při procházení volání draw, fáze zřetězení se aktualizuje a zobrazí geometrie, který je spojen s každé volání procházejících každé fázi povolená a výstup cíle vykreslení se aktualizuje a zobrazí stav cíle vykreslování po dokončení volání.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>K vyhledání volání draw pro chybějící geometrie  
  
1. Otevřít **seznam událostí grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **seznam událostí**.  
  
2. Otevřít **fáze zřetězení grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **fáze zřetězení**.  
  
3. Při přesunu jednotlivými kreslete volání **seznam událostí grafiky** okna, podívejte **fáze zřetězení grafiky** okně chybějícím objektu. Abychom to usnadnili, zadejte "Draw" **hledání** pole v pravém horním rohu **seznam událostí grafiky** okna. Vyfiltruje seznam tak, aby obsahoval pouze události, které mají "Draw" v názvech.  
  
    V **fáze zřetězení grafiky** okně **vstupní Assembler** fáze ukazuje geometrie objektu ve předtím, než se transformuje a **Vertex Shader** fáze zobrazuje stejné objekt po je transformaci. V tomto scénáři, Všimněte si, že **fáze zřetězení grafiky** okno zobrazuje **vstupní Assembler** a **Vertex Shader** zpracování, ale ne **Pixel Shader**  fáze pro jeden z volání vykreslování.  
  
   > [!NOTE]
   >  Pokud jiné zřetězení – například, shader trupu, shader domény nebo geometry shader fáze, proces objektu, některý z nich může být příčinou problému. Obvykle problém souvisí s první fáze, ve kterém se nezobrazuje výsledek, nebo se zobrazí neočekávaným způsobem.  
  
4. Zastavte při dosažení volání draw, která odpovídá chybějícím objektu. V tomto scénáři **fáze zřetězení grafiky** okno znamená, že byl vydán geometrii do GPU (indikován přítomnost **vstupní Assembler** fázi) a transformovaná (indikován  **Vertex Shader** fázi), ale nezobrazí v cíle vykreslování, protože není nejspíš aktivní pixel shader (indikován absenci **Pixel Shader** fáze). V tomto scénáři můžete dokonce vidět obrysem chybí objekt v **slučovací modul výstupu** fáze:  
  
    ![Událost DrawIndexed a její vliv na kanálu](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-2.png "gfx_diag_demo_misconfigured_pipeline_step_2")  
  
   Po potvrzení, že aplikace vydala volání draw pro geometrii chybějícím objektu a zjistit aktivní fázi pixel shaderu nebyl, můžete zkontrolovat stav zařízení potvrďte svá zjištění. Můžete použít **Graphics Object Table** k prozkoumání kontextu zařízení a další data objektu rozhraní Direct3D.  
  
#### <a name="to-examine-device-context"></a>K prozkoumání kontextu zařízení  
  
1. Otevřít **kontextu zařízení d3d11**. V **fáze zřetězení grafiky** okna, vyberte **ID3D11DeviceContext** odkaz, který je součástí `DrawIndexed` volání, které se zobrazí v horní části okna.  
  
2. Zkontrolujte stav zařízení, která se zobrazí v **kontextu zařízení d3d11** tab potvrďte, že žádné pixel shader byl aktivní během volání draw. V tomto scénáři **obecné informace shaderu**– zobrazí v části **pixel shader stavu**– označuje, že shader je **NULL**:  
  
    ![Kontext zařízení D3D 11 zobrazuje stav pixel shader](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-4.png "gfx_diag_demo_misconfigured_pipeline_step_4")  
  
   Jakmile potvrdíte, že pixel shader byl nastaven na hodnotu null jako aplikace, dalším krokem je najít umístění ve zdrojovém kódu vaší aplikace, kde je nastaven shader. Můžete použít **seznam událostí grafiky** spolu s **zásobník volání událostí grafiky** k vyhledání tohoto umístění.  
  
#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Chcete-li najít, kde je nastaven pixel shader ve zdrojovém kódu vaší aplikace  
  
1. Najít `PSSetShader` volání, které odpovídá chybějícím objektu. V **seznam událostí grafiky** okno, zadejte "Draw; PSSetShader"v **hledání** pole v pravém horním rohu **seznam událostí grafiky** okna. Vyfiltruje seznam tak, aby pouze obsahoval "PSSetShader" události a události, které mají "Draw" v názvech. Zvolte první `PSSetShader` volání, které se zobrazí před volání draw chybějící objektu.  
  
   > [!NOTE]
   >  `PSSetShader` nebude zobrazovat **seznam událostí grafiky** okno, pokud nebyla nastavena během tohoto rámce. Obvykle k tomu dochází pouze v případě, že právě jeden pixel shaderu se používá pro všechny objekty, nebo pokud `PSSetShader` volání přeskočila neúmyslně během tohoto rámce. V obou případech doporučujeme hledání zdrojový kód aplikace `PSSetShader` volání a použijte tradiční techniky ladění ke kontrole chování těchto volání.  
  
2. Otevřít **zásobník volání událostí grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **zásobník volání událostí grafiky**.  
  
3. Použití zásobníku volání vyhledejte `PSSetShader` volání ve zdrojovém kódu vaší aplikace. V **zásobník volání událostí grafiky** okno, zvolte volání úplně nahoře a který pixel shader je nastavena na hodnotu. Pixel shader může být nastaveno přímo na hodnotu null nebo hodnotu null. hodnota může dojít z důvodu argument, který byl předán do funkce nebo jiného stavu. Pokud není nastavena přímo, je možné vyhledat zdroj někde výše v zásobníku volání hodnotu null. V tomto scénáři zjistíte, že pixel shader je nastavena přímo na `nullptr` ve funkci zcela nahoře, který se nazývá `CubeRenderer::Render`:  
  
    ![Kód, který nelze inicializovat pixel shader](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-5.png "gfx_diag_demo_misconfigured_pipeline_step_5")  
  
   > [!NOTE]
   >  Pokud nemůžete najít zdrojové hodnoty null stačí zkoumání zásobníku volání, doporučujeme nastavit podmíněné zarážky na `PSSetShader` volání, tak, že pokud se nastaví pixel shader, přestane fungovat provádění programu na hodnotu null. Potom restartujte aplikaci v režimu ladění a využijte tradiční techniky ladění vyhledat zdroj hodnotu null.  
  
   Chcete-li vyřešit tento problém, přiřaďte správné pixel shader pomocí první parametr `ID3D11DeviceContext::PSSetShader` volání rozhraní API.  
  
   ![Opravené C&#43; &#43; zdrojový kód](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-6.png "gfx_diag_demo_misconfigured_pipeline_step_6")  
  
   Po opravě kód, můžete její opětovné sestavení a spuštění aplikace znovu k ověření, že je vyřešen problém vykreslování:  
  
   ![Objekt se nyní zobrazí](../debugger/media/gfx-diag-demo-misconfigured-pipeline-resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")



