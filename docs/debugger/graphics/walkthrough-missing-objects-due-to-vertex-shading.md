---
title: 'Návod: chybějící objekty z důvodu stínování vrcholu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc3bd288044c9fea1da648b64cabc87148b8463a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825521"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Návod: Chybějící objekty z důvodu použití vertex shaderu
Tento návod ukazuje, jak použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nástroje Diagnostika grafiky k prozkoumání objektu, který chybí z důvodu chyby, ke které dojde během fáze vertex shader.

 Tento návod ilustruje tyto úlohy:

- K vyhledání potenciálních zdrojů problému použijte **seznam událostí grafiky** .

- Pomocí okna **fáze zřetězení grafiky** můžete kontrolovat účinek `DrawIndexed` volání rozhraní Direct3D API.

- Použití **ladicího programu HLSL** k prohlédnutí vrcholu shaderu.

- Použití **zásobníku volání událostí grafiky** k získání zdroje nesprávné HLSL konstanty.

## <a name="scenario"></a>Scénář
 Jeden z běžných příčin chybějícího objektu v 3D aplikaci nastává, když clona vrcholu transformuje vrcholy objektu nesprávnému nebo neočekávanému způsobu, například objekt může být zvětšen na velmi malou velikost nebo transformovat tak, aby se zobrazil za fotoaparátem, nikoli před ním.

 V tomto scénáři se při spuštění aplikace pro otestování pozadí vykreslí podle očekávání, ale jeden z objektů se nezobrazí. Pomocí Diagnostika grafiky zachytíte problém do protokolu grafiky, abyste mohli aplikaci ladit. Problém v této aplikaci vypadá následovně:

 ![Objekt nelze zobrazit.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Šetření
 Pomocí nástrojů Diagnostika grafiky můžete načíst soubor protokolu grafiky a zkontrolovat rámce, které byly zachyceny během testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Prohlédnutí snímku v protokolu grafiky

1. V nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtěte protokol grafiky, který obsahuje rámeček, který vykazuje chybějící objekt. V nástroji se zobrazí nová karta protokol grafiky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . V horní části této karty je výstup cíle vykreslování vybraného snímku. V dolní části je **seznam rámců**, který zobrazuje jednotlivé zachycené rámce jako obrázek miniatury.

2. V **seznamu snímků**vyberte rámec, který ukazuje, že se objekt nezobrazuje. Cíl vykreslování se aktualizuje tak, aby odrážel vybraný snímek. V tomto scénáři vypadá karta protokol grafiky takto:

    ![Dokument protokolu grafiky v aplikaci Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Po výběru rámce, který demonstruje daný problém, můžete začít diagnostikovat pomocí **seznamu událostí grafiky**. **Seznam událostí grafiky** obsahuje každé volání rozhraní Direct3D API, které bylo provedeno pro vykreslení aktivního rámce, například volání rozhraní API pro nastavení stavu zařízení, pro vytváření a aktualizaci vyrovnávacích pamětí a pro kreslení objektů, které se zobrazí v rámci rámečku. Mnoho druhů volání je zajímavé, protože často (ale ne vždy) odpovídající změna v cíli vykreslování, když aplikace funguje podle očekávání, například kreslení, odesílání, kopírování nebo vymazání volání. Volání remíz jsou obzvláště zajímavá, protože každá z nich představuje geometrii, kterou vygenerovala aplikace (volání expedice může také vykreslovat geometrii).

   Vzhledem k tomu, že víte, že chybějící objekt není vykreslen do cíle vykreslování (v tomto případě), ale zbývající část scény je vykreslena podle očekávání, můžete použít **seznam událostí grafiky** spolu s nástrojem **fáze zřetězení grafiky** a určit, které volání vykreslování odpovídá geometrii chybějícího objektu. Okno **fáze zřetězení grafiky** zobrazuje geometrii, která byla odeslána každému volání vykreslení bez ohledu na jeho vliv na cíl vykreslování. Při procházení volání vykreslování jsou fáze zřetězení aktualizovány tak, aby zobrazovaly geometrii, která je přidružena k tomuto volání, a výstup cíle vykreslování je aktualizován tak, aby zobrazoval stav cíle vykreslování po dokončení volání.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Vyhledání volání remíz pro chybějící geometrii

1. Otevřete okno **seznam událostí grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **seznam událostí**.

2. Otevřete okno **fáze zřetězení grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte **fáze zřetězení**.

3. Při procházení každého volání remízy v okně **seznam událostí grafiky** sledujte okno **fáze zřetězení grafiky** pro chybějící objekt. To lze usnadnit zadáním příkazu "Draw" do **vyhledávacího** pole v pravém horním rohu okna **seznam událostí grafiky** . Tím se seznam vyfiltruje tak, aby obsahoval jenom události, které mají v názvech "Draw".

    V okně **fáze zřetězení grafiky** zobrazuje fáze **vstupního assembleru** geometrii objektu před jeho transformací a fáze **vertex shader** po transformaci zobrazuje stejný objekt. V tomto scénáři zjistíte, že jste našli chybějící objekt, když se zobrazí ve **vstupní fázi assembleru** , a ve fázi **vertex shader** se nic nezobrazuje.

   > [!NOTE]
   > Pokud jiné fáze geometrie – například shader trupu, shader domény nebo fáze geometrie shaderu – zpracuje objekt, mohou být příčinou problému. Obvykle se problém týká nejbližší fáze, ve které se výsledek nezobrazuje nebo se zobrazuje neočekávaným způsobem.

4. Zastaví se při dosažení volání metody Draw, která odpovídá chybějícímu objektu. V tomto scénáři okno **fáze zřetězení grafiky** indikuje, že se geometrie vystavila pro GPU (označená vstupní miniaturou assembleru), ale nezobrazuje se v cíli vykreslování, protože došlo k chybě během fáze vertex shader (označená miniaturou vertex shaderu):

    ![Událost DrawIndexed a její vliv na kanál](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Po potvrzení, že aplikace vystavila volání draw pro geometrii chybějícího objektu a zjistíte, že k problému dojde během fáze vertex shader, můžete použít ladicí program HLSL a zjistit, co se stalo s geometrií objektu. Můžete použít ladicí program HLSL k prohlédnutí stavu proměnných HLSL během provádění, krokovat kód HLSL a nastavit zarážky, které vám pomohou diagnostikovat problém.

#### <a name="to-examine-the-vertex-shader"></a>Kontrola vrcholu shaderu

1. Spustí ladění fáze vertex shader. V okně **fáze zřetězení grafiky** pod fází **vertex shader** vyberte tlačítko **Spustit ladění** .

2. Vzhledem k tomu, že se **vstupní fáze assembleru** zobrazuje pro vertex shader dobrá data a fáze **vertex shader** se zdá, že nevytváří žádný výstup, chcete prošetřit výstupní strukturu shaderu vrcholu, `output` . Při procházení kódu HLSL se podíváte na další vzhled, když `output` se upraví.

3. Při prvním změně se `output` člen `worldPos` zapíše do.

    ![Hodnota možnosti Output. worldPos se jeví jako přiměřená.](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Vzhledem k tomu, že se jeho hodnota jeví jako rozumná, budete pokračovat v procházení kódu až do dalšího řádku, který se upraví `output` .

4. Až se příště `output` změní, člen `pos` se zapíše do.

    ![Hodnota "Output. POS" byla vypočítána od nuly.](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Tentokrát se hodnota `pos` člena – všechny nuly – jeví jako podezřelé. V dalším kroku chcete určit, jak má `output.pos` mít hodnotu se všemi nulami.

5. Všimněte si, že `output.pos` převezme jeho hodnotu z proměnné s názvem `temp` . Na předchozím řádku vidíte, že hodnota `temp` je výsledkem vynásobení předchozí hodnoty konstantou, která je pojmenována `projection` . Máte podezření, že `temp` je výsledkem tohoto násobení podezřelá hodnota. Když umístíte ukazatel myši na `projection` , všimnete si, že jeho hodnota je také nula.

    ![Matice projekce obsahuje chybnou transformaci.](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    V tomto scénáři zkoumání odhalí, že `temp` podezřelá hodnota je pravděpodobně způsobena jejím násobení `projection` , a vzhledem k tomu, že `projection` je konstanta, která je určena k tomu, aby obsahovala matrici projekce, víte, že by neměla obsahovat všechny nuly.

   Až zjistíte, že je HLSL konstanta, která `projection` je předána do shaderu vaší aplikací – je pravděpodobným zdrojem problému, je dalším krokem hledání umístění ve zdrojovém kódu vaší aplikace, kde je vyplněna konstantní vyrovnávací paměť. K vyhledání tohoto umístění můžete použít **zásobník volání událostí grafiky** .

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Pokud chcete zjistit, kde je ve zdrojovém kódu vaší aplikace nastavená konstanta.

1. Otevřete okno **zásobník volání událostí grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **zásobník volání událostí grafiky**.

2. Přejděte do zásobníku volání do zdrojového kódu vaší aplikace. V okně **zásobník volání událostí grafiky** vyberte volání nejvyšší úrovně, abyste viděli, zda je vložena konstantní vyrovnávací paměť. Pokud není, pokračujte v zásobníku volání, dokud nezjistíte, kde je vyplněna. V tomto scénáři zjistíte, že je vyplněna konstantní vyrovnávací paměť – pomocí `UpdateSubresource` rozhraní Direct3D API – dále v zásobníku volání ve funkci s názvem `MarbleMaze::Render` a zda její hodnota pochází z objektu konstanty buffer s názvem `m_marbleConstantBufferData` :

    ![Kód, který nastavuje konstantní vyrovnávací paměť objektu](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > Pokud současně ladíte aplikaci, můžete nastavit zarážku v tomto umístění a bude dosaženo při vykreslení dalšího snímku. Potom můžete zkontrolovat členy `m_marbleConstantBufferData` , abyste potvrdili, že hodnota `projection` člena je nastavena na hodnotu všechny nuly při vyplňování konstantní vyrovnávací paměti.

   Po nalezení umístění, kde je vyplněna vyrovnávací paměť konstanty a zjištění, že hodnoty pocházejí z proměnné `m_marbleConstantBufferData` , je dalším krokem zjištění, kde `m_marbleConstantBufferData.projection` je člen nastaven na všechny nuly. Pomocí funkce **Najít všechny odkazy** můžete rychle vyhledat kód, který změní hodnotu `m_marbleConstantBufferData.projection` .

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Chcete-li zjistit, kde je nastaven člen projekce ve zdrojovém kódu vaší aplikace

1. Vyhledejte odkazy na `m_marbleConstantBufferData.projection` . Otevřete místní nabídku pro proměnnou `m_marbleConstantBufferData` a zvolte možnost **Najít všechny odkazy**.

2. Pokud chcete přejít do umístění řádku ve zdrojovém kódu vaší aplikace `projection` , kde je člen upravený, vyberte tento řádek v okně **výsledky hledání symbolu** . Vzhledem k tomu, že první výsledek, který mění člen projekce, nemusí být příčinou problému, možná budete muset prostudovat několik oblastí zdrojového kódu vaší aplikace.

   Po nalezení umístění `m_marbleConstantBufferData.projection` , kde je nastaveno, můžete prostudovat zdrojový kód, abyste určili původ nesprávné hodnoty. V tomto scénáři zjistíte, že hodnota `m_marbleConstantBufferData.projection` je nastavena na místní proměnnou, která je pojmenována `projection` předtím, než byla inicializována na hodnotu, která je uvedena v kódu `m_camera->GetProjection(&projection);` na dalším řádku.

   ![Projekce pro mramor je nastavená před inicializací.](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Chcete-li problém vyřešit, přesuňte řádek kódu, který nastaví hodnotu `m_marbleConstantBufferData.projection` po řádku, který inicializuje hodnotu místní proměnné `projection` .

   ![Opravený zdrojový kód jazyka C&#43;&#43; ](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Po opravě kódu jej můžete znovu sestavit a znovu spustit aplikaci, abyste zjistili, zda je problém vykreslování vyřešen:

   ![Aktuálně zobrazený objekt.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")