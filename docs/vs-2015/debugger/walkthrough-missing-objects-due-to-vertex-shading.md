---
title: 'Návod: Chybějící objekty z důvodu použití funkce Vertex Shading | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ecff22d99eb995f0dbe70e93783460f4343d74f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745942"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Návod: Chybějící objekty z důvodu použití funkce vertex shading
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů diagnostiky grafiky k prozkoumání objekt, který nebyl nalezen z důvodu chyby, ke které dojde během fáze vertex shader.  
  
 Tento návod ilustruje tyto úkoly:  
  
-   Použití **seznam událostí grafiky** k vyhledání potenciálních zdrojů problému.  
  
-   Použití **fáze zřetězení grafiky** okna zkontrolovat dopad `DrawIndexed` volání rozhraní API Direct3D.  
  
-   Použití **ladicí program HLSL** prozkoumat vertex shader.  
  
-   Použití **zásobník volání událostí grafiky** vám pomohou najít zdroje nesprávné konstanty HLSL.  
  
## <a name="scenario"></a>Scénář  
 Jednou z běžných příčin chybí objekt v 3D aplikaci nastane vertex shader vrcholů objektu transformuje nesprávné nebo neočekávaným způsobem, například objekt může být škálovat velmi malé velikosti, nebo transformovat tak, aby se zobrazí za fotoaparátu/kamery , spíše než před tímto prvkem.  
  
 V tomto scénáři při spuštění aplikace a otestovat ho pozadí se vykresluje podle očekávání, ale jeden z objektů se nezobrazí. Pomocí diagnostiky grafiky můžete zaznamenat problém do protokolu grafiky, tak, že ladíte aplikaci. Problém je v aplikace vypadá například takto:  
  
 ![Objekt nelze zobrazit. ](../debugger/media/gfx-diag-demo-missing-object-shader-problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Šetření  
 Pomocí nástrojů diagnostiky grafiky můžete načíst soubor protokolu grafiky kontrolovat rámce, které se zaznamenalo během testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Přezkoumání snímku v protokolu grafiky  
  
1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], načtěte protokol grafiky, který obsahuje rámec vykazující chybějícím objektu. Zobrazí se nová karta protokolu grafiky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V horní části této karty je výstup cíle vykreslení vybraného snímku. V dolní části je **seznam snímků**, který zobrazuje jako obrázek miniatury každého zachyceného snímku.  
  
2. V **seznam snímků**, vyberte snímek, který ukazuje, že objekt se nezobrazuje. Cíl vykreslování se aktualizuje tak, aby odrážely vybraného snímku. V tomto scénáři vypadá karta protokolu grafiky:  
  
    ![Dokumentu protokolu grafiky v aplikaci Visual Studio](../debugger/media/gfx-diag-demo-missing-object-shader-step-1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
   Po výběru rámce, který znázorňuje problém, můžete začít pro diagnostiku pomocí **seznam událostí grafiky**. **Seznam událostí grafiky** obsahuje každé volání API rozhraní Direct3D, která byla vytvořená pro vykreslení aktivního rámce, například volání rozhraní API k nastavení stavu zařízení můžete taky vytvářet a aktualizovat vyrovnávací paměti a chcete-li nakreslit objekty, které se zobrazují v rámci. Různé druhy volání je zajímavé, protože není často (ale ne vždy) odpovídající změnu cíle vykreslování, pokud aplikace funguje podle očekávání, například kreslení, odesílání, kopírování nebo vymazat volání. Volání příkazu pro vykreslení jsou zvlášť zajímavý, protože každé z nich představuje geometrii, která vykresluje aplikace (odeslání volání může také vykreslit geometrii).  
  
   Protože víte, že chybí objekt není nakreslena na cíl vykreslování (v tomto případě) – ale, že zbývající části scény je vykreslena podle očekávání, můžete použít **seznam událostí grafiky** spolu s **zřetězení grafiky Fáze** nástroje k určení, které nakreslit volání odpovídá chybějícím objektu geometry. **Fáze zřetězení grafiky** okno zobrazuje geometrii, která byla odeslána pro každé volání draw, bez ohledu na jeho dopad na cíl vykreslování. Při procházení volání draw, fáze zřetězení se aktualizuje a zobrazí geometrii, která souvisí s voláním a výstup cíle vykreslení se aktualizuje a zobrazí stav cíle vykreslování po volání bylo dokončeno.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>K vyhledání volání draw pro chybějící geometrie  
  
1. Otevřít **seznam událostí grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **seznam událostí**.  
  
2. Otevřít **fáze zřetězení grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **fáze zřetězení**.  
  
3. Při přesunu jednotlivými kreslete volání **seznam událostí grafiky** okna, podívejte **fáze zřetězení grafiky** okně chybějícím objektu. Abychom to usnadnili, zadejte "Draw" **hledání** pole v pravém horním rohu **seznam událostí grafiky** okna. Vyfiltruje seznam tak, aby obsahoval pouze události, které mají "Draw" v názvech.  
  
    V **fáze zřetězení grafiky** okně **vstupní Assembler** fáze ukazuje geometrie objektu před jeho transformovaný a **Vertex Shader** fáze zobrazuje stejné objekt po je transformaci. V tomto scénáři, víte, že jakmile se zobrazí v nenajdete chybějícím objektu **vstupní Assembler** fáze, ale nic se zobrazí v **Vertex Shader** fázi.  
  
   > [!NOTE]
   >  Pokud jiných geometrie fází – například, Shader trupu, Shader domény a Shader geometrie fází – proces objektu, mohou být příčinou problému. Obvykle problém souvisí s první fáze, ve kterém se nezobrazuje výsledek, nebo se zobrazí neočekávaným způsobem.  
  
4. Zastavte při dosažení volání draw, která odpovídá chybějícím objektu. V tomto scénáři **fáze zřetězení grafiky** okno znamená, že byl vydán geometrii GPU (označená miniaturu vstupní Assembler), ale nezobrazí v cíle vykreslování, protože došlo k chybě během fáze shader vrcholu (označená miniaturu Vertex Shader):  
  
    ![Událost DrawIndexed a její vliv na kanálu](../debugger/media/gfx-diag-demo-missing-object-shader-step-2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
   Po potvrzení, že aplikace vydala volání draw pro geometrii chybějícím objektu a zjistit, že tento problém nastává během fáze shader vrcholu, můžete použít ladicí program HLSL sloužící ke zkoumání vertex shader a zjistěte, co se stalo s geometrie objektu. Můžete použít ladicí program HLSL a kontrolu stavu proměnných HLSL během provádění, krokovat kód HLSL a nastavit zarážky, které vám pomohou diagnostikovat problém.  
  
#### <a name="to-examine-the-vertex-shader"></a>Prozkoumat vertex shader  
  
1. Spusťte ladění vrcholu fázi shaderu. V **fáze zřetězení grafiky** okně v části **Vertex Shader** fáze, zvolte **spustit ladění** tlačítko.  
  
2. Protože **vstupní Assembler** fázi se zobrazí k poskytování dobré data do vertex shaderu a **Vertex Shader** fáze se žádný výstup, které chcete prověřit výstup vertex shaderu strukturu, `output`. Krocích kódu HLSL je provést blíže podívat při `output` se mění.  
  
3. Prvním `output` se změní, člen `worldPos` se zapisují do.  
  
    ![Zobrazí se hodnota "output.worldPos" přiměřené](../debugger/media/gfx-diag-demo-missing-object-shader-step-4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
    Zdá se, že její hodnota být přijatelný, můžete pokračovat, protože krokování kódu až do další řádek, který upravuje `output`.  
  
4. Při příštím `output` se změní, člen `pos` se zapisují do.  
  
    ![Hodnota "output.pos" byly vynulován](../debugger/media/gfx-diag-demo-missing-object-shader-step-5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
    Tentokrát, hodnota `pos` člen – samými nulami – zdá podezřelá. Dále byste měli určit, jak `output.pos` přišel s hodnotou samými nulami.  
  
5. Všimněte si, že `output.pos` trvá svou hodnotu z proměnné s názvem `temp`. Na předchozím řádku, můžete vidět, že hodnota `temp` je výsledek násobení původní hodnotu konstantu, která má název `projection`. Máte podezření, že `temp`společnosti podezřelá hodnota je výsledek této násobení. Při přesunutí ukazatele myši na `projection`, Všimněte si, že její hodnota je také samými nulami.  
  
    ![Projekce matice obsahuje chybný transformace](../debugger/media/gfx-diag-demo-missing-object-shader-step-6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
    V tomto scénáři zkoumání zjistí, že `temp`společnosti podezřelá hodnota je s největší pravděpodobností způsobené jeho násobení hodnotou `projection`a protože `projection` je konstanta, která je určená obsahovat projekce matice, víte, že by neměla obsahují samými nulami.  
  
   Až zjistíte, že – konstanta HLSL `projection`– předán shaderu aplikací pro – je pravděpodobně zdroj problému, dalším krokem je najít umístění ve zdrojovém kódu vaší aplikace ve kterém se naplní vyrovnávací paměť konstant. Můžete použít **zásobník volání událostí grafiky** k vyhledání tohoto umístění.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Chcete-li najít, kde je konstanta nastavena ve zdrojovém kódu vaší aplikace  
  
1. Otevřít **zásobník volání událostí grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **zásobník volání událostí grafiky**.  
  
2. Procházet nahoru o zásobníku volání do zdrojového kódu vaší aplikace. V **zásobník volání událostí grafiky** okně zvolte volání nejvrchnější zobrazíte, pokud existuje se naplní vyrovnávací paměť konstant. Pokud není, dokud nenajdete, kde se naplní pokračujte v zásobníku volání. V tomto scénáři zjistíte, že se naplní vyrovnávací paměť konstant – s použitím `UpdateSubresource` rozhraní Direct3D API – další nahoru v zásobníku volání ve funkci s názvem `MarbleMaze::Render`, a že jeho hodnota pochází z objektu vyrovnávací paměť konstant, který je pojmenován `m_marbleConstantBufferData` :  
  
    ![Kód, který nastaví konstantní vyrovnávací paměti objektu](../debugger/media/gfx-diag-demo-missing-object-shader-step-7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
   > [!TIP]
   >  Pokud jsou současně ladění vaší aplikace, můžete nastavit zarážku na tomto místě a při vykreslení dalšího snímku se dostanou. Pak si můžete prohlédnout členy `m_marbleConstantBufferData` potvrdit, že hodnota `projection` člen je nastavený na samými nulami, když se naplní vyrovnávací paměť konstant.  
  
   Po vyhledání umístění, kde se naplní vyrovnávací paměť konstant a zjistit, že jeho hodnoty pocházejí z proměnné `m_marbleConstantBufferData`, dalším krokem je zjistit, kde `m_marbleConstantBufferData.projection` člen je nastavený na samými nulami. Můžete použít **najít všechny odkazy** rychle vyhledávat kód, který změní hodnotu `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Chcete-li najít, kde je nastaven člen projekce ve zdrojovém kódu vaší aplikace  
  
1. Najít odkazy na `m_marbleConstantBufferData.projection`. Otevřete místní nabídku pro proměnnou `m_marbleConstantBufferData`a klikněte na tlačítko **najít všechny odkazy**.  
  
2. Přejděte do umístění na řádku ve zdrojovém kódu vaší aplikace ve kterém `projection` člen je upravit, vyberte tento řádek v **výsledky hledáni symbolu** okno. Protože první výsledek, který upraví člen projekce nemusí být příčinou problému, budete muset zkontrolovat několik oblastí zdrojovém kódu vaší aplikace.  
  
   Po nalezení umístění kde `m_marbleConstantBufferData.projection` je nastaven, můžete prozkoumat okolního zdrojový kód k určení původu nesprávnou hodnotu. V tomto scénáři zjistíte, že hodnota `m_marbleConstantBufferData.projection` je nastavena na místní proměnnou s názvem `projection` předtím, než byl inicializován na hodnotu, která je přidělena kódem `m_camera->GetProjection(&projection);` na dalším řádku.  
  
   ![Marble projekce nastaven před inicializací](../debugger/media/gfx-diag-demo-missing-object-shader-step-9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
   Chcete-li problém vyřešit, je přesunout řádek kódu, který nastaví hodnotu `m_marbleConstantBufferData.projection` po řádek, který inicializuje hodnotu místní proměnné `projection`.  
  
   ![Opravené C&#43; &#43; zdrojový kód](../debugger/media/gfx-diag-demo-missing-object-shader-step-10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
   Po opravě kód, můžete její opětovné sestavení a spuštění aplikace znovu a zjistit, že je vyřešen problém vykreslování:  
  
   ![Objekt v nyní zobrazen. ](../debugger/media/gfx-diag-demo-missing-object-shader-resolution.png "gfx_diag_demo_missing_object_shader_resolution")



