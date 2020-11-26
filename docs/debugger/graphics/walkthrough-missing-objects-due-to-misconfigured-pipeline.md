---
title: Chybějící objekty z důvodu chybně nakonfigurovaného kanálu
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64c00c10b8b7207e1162aa0041145000126fde87
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189846"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Návod: Chybějící objekty z důvodu nesprávné konfigurace kanálu
Tento návod ukazuje, jak použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nástroje Diagnostika grafiky k prozkoumání objektu, který chybí z důvodu nenastavené funkce pixel shader.

 Tento návod ilustruje tyto úlohy:

- K vyhledání potenciálních zdrojů problému použijte **seznam událostí grafiky** .

- Pomocí okna **fáze zřetězení grafiky** můžete vyzkoušet efekt `DrawIndexed` volání rozhraní Direct3D API.

- Kontrola kontextu zařízení pro potvrzení, že nebyla nastavena fáze shaderu.

- Pomocí okna **fáze zřetězení grafiky** spolu s **zásobníkem volání událostí grafiky** můžete najít zdroj nenastavené funkce pixel shader.

## <a name="scenario"></a>Scénář
 V případě, že v 3D aplikaci chybí objekt, je někdy v případě, že jedna z fází shaderu není nastavena před vykreslením objektu. V aplikacích, které mají jednoduché vykreslování, se zdrojem této chyby obvykle nachází někde v zásobníku volání volání vykreslování objektu. V rámci optimalizace ale některé aplikace dávkují objekty, které mají programy shaderů, textury nebo jiná data, společná pro minimalizaci nákladů na změnu stavu. V těchto aplikacích může být zdroj chyby ukryto v systému dávkování, nikoli v zásobníku volání volání metody Draw. Scénář v tomto návodu ukazuje aplikaci, která má jednoduché vykreslování, takže zdroj chyby lze nalézt v zásobníku volání.

 V tomto scénáři se při spuštění aplikace pro otestování pozadí vykreslí podle očekávání, ale jeden z objektů se nezobrazí. Pomocí Diagnostika grafiky zachytíte problém do protokolu grafiky, abyste mohli aplikaci ladit. Problém v této aplikaci vypadá následovně:

 ![Objekt se nedá zobrazit.](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Šetření
 Pomocí nástrojů Diagnostika grafiky můžete načíst dokument protokolu grafiky pro kontrolu rámců, které byly zachyceny během testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Prohlédnutí snímku v protokolu grafiky

1. V nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtěte dokument protokolu grafiky, který obsahuje rámeček, který vykazuje chybějící objekt. V nástroji se zobrazí nová karta protokol grafiky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . V horní části této karty je výstup cíle vykreslování vybraného snímku. V dolní části je **seznam rámců**, který zobrazuje jednotlivé zachycené rámce jako obrázek miniatury.

2. V **seznamu snímků** vyberte rámec, který ukazuje, že se objekt nezobrazuje. Cíl vykreslování se aktualizuje tak, aby odrážel vybraný snímek. V tomto scénáři vypadá karta protokol grafiky takto:

    ![Dokument protokolu grafiky v aplikaci Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Po výběru rámce, který demonstruje daný problém, můžete začít diagnostikovat pomocí **seznamu událostí grafiky**. **Seznam událostí grafiky** obsahuje každé volání rozhraní Direct3D API, které bylo provedeno pro vykreslení aktivního rámce – například pro nastavení stavu zařízení, pro vytváření a aktualizaci vyrovnávacích pamětí a pro kreslení objektů, které se zobrazí v rámci rámečku. Mnoho druhů volání – například kreslení, odesílání, kopírování nebo vymazání volání – je zajímavé, protože často (ale ne vždy) odpovídající změna v cíli vykreslování, když aplikace funguje podle očekávání. Volání remíz jsou obzvláště zajímavá, protože každá z nich představuje geometrii, kterou aplikace vykreslila.

   Vzhledem k tomu, že víte, že cíl vykreslování neobsahuje chybějící objekt, ale také že nedošlo k jiným chybám, můžete použít **seznam událostí grafiky** spolu s nástrojem **fáze zřetězení grafiky** , abyste určili, které volání vykreslování odpovídá geometrii chybějícího objektu. Okno **fáze zřetězení grafiky** zobrazuje geometrii, která byla odeslána každému volání vykreslení bez ohledu na jeho vliv na cíl vykreslování. Při procházení volání vykreslování jsou fáze zřetězení aktualizovány tak, aby zobrazovaly geometrii, která je spojena s každým voláním při průchodu všemi povolenými fázemi, a výstup cíle vykreslování se aktualizuje tak, aby po dokončení volání zobrazil stav cíle vykreslování.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Vyhledání volání remíz pro chybějící geometrii

1. Otevřete okno **seznam událostí grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **seznam událostí**.

2. Otevřete okno **fáze zřetězení grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte **fáze zřetězení**.

3. Při procházení každého volání remízy v okně **seznam událostí grafiky** sledujte okno **fáze zřetězení grafiky** pro chybějící objekt. To lze usnadnit zadáním příkazu "Draw" do **vyhledávacího** pole v pravém horním rohu okna **seznam událostí grafiky** . Tím se seznam vyfiltruje tak, aby obsahoval jenom události, které mají v názvech "Draw".

    V okně **fáze zřetězení grafiky** zobrazuje fáze **vstupního assembleru** geometrii objektu před transformací a fáze **vertex shader** po transformaci zobrazuje stejný objekt. V tomto scénáři si všimněte, že okno **fáze zřetězení grafiky** zobrazuje **vstupní fáze assembleru** a  **vrcholu shaderu** , ale ne fázi **shaderu pixel** pro jedno z volání vykreslování.

   > [!NOTE]
   > Pokud další fáze zřetězení – například fáze trupu, shader domény nebo fáze geometrie shaderu – zpracuje objekt, kterákoli z nich může být příčinou problému. Obvykle se problém týká nejbližší fáze, ve které se výsledek nezobrazuje nebo se zobrazuje neočekávaným způsobem.

4. Zastaví se při dosažení volání metody Draw, která odpovídá chybějícímu objektu. V tomto scénáři okno **fáze zřetězení grafiky** indikuje, že se geometrie vystavila pro GPU (označená přítomností vstupní fáze **assembleru** ) a transformovaná (označená fází **vertex shader** ), ale v cíli vykreslování se nezobrazuje, protože se nejeví jako aktivní pixel shader (indikuje se neexistence fáze **pixel shaderu** ). V tomto scénáři můžete dokonce zobrazit Silhouette chybějícího objektu ve fázi **výstupní fúze** :

    ![Událost DrawIndexed a její vliv na kanál](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Po potvrzení, že aplikace vystavila volání draw pro geometrii chybějícího objektu a zjistíte, že fáze pixel shaderu byla neaktivní, můžete prozkoumat stav zařízení a potvrdit si vaše závěry. Pomocí **tabulky objekt grafiky** můžete prozkoumávat kontext zařízení a jiná data objektu Direct3D.

#### <a name="to-examine-device-context"></a>Kontrola kontextu zařízení

1. Otevřete **kontext zařízení d3d11**. V okně **fáze zřetězení grafiky** vyberte odkaz **ID3D11DeviceContext** , který je součástí `DrawIndexed` volání zobrazeného v horní části okna.

2. Zkontrolujte stav zařízení, který se zobrazí na kartě **D3D11 (kontext zařízení** ), a ověřte, že během volání vykreslení není aktivní žádný pixel shader. V tomto scénáři jsou **Obecné informace shaderu**– zobrazené v části **stav funkce pixel shader**– označuje, že shader má **hodnotu null**:

    ![Kontext zařízení D3D 11 zobrazuje stav funkce pixel shader.](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Po potvrzení, že je pixel shader nastavený na hodnotu null vaší aplikací, je dalším krokem hledání umístění ve zdrojovém kódu vaší aplikace, kde je shader nastavený. K vyhledání tohoto umístění můžete použít **seznam událostí grafiky** spolu se **zásobníkem volání událostí grafiky** .

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Chcete-li zjistit, kde je pixel shader nastaven ve zdrojovém kódu vaší aplikace

1. Vyhledejte `PSSetShader` volání, které odpovídá chybějícímu objektu. V okně **seznam událostí grafiky** zadejte "Draw; PSSetShader "do **vyhledávacího** pole v pravém horním rohu okna **seznam událostí grafiky** . Tím se seznam vyfiltruje tak, aby obsahoval jenom události "PSSetShader" a události, které mají v názvech "Draw". Vyberte první `PSSetShader` volání, které se zobrazí před voláním metody Draw objektu Missing.

   > [!NOTE]
   > `PSSetShader` se nezobrazí v okně **seznam událostí grafiky** , pokud nebylo nastaveno během tohoto snímku. K tomu obvykle dochází pouze v případě, že je pro všechny objekty použit pouze jeden pixel shader nebo pokud `PSSetShader` volání bylo během tohoto rámce neúmyslně vynecháno. V obou případech doporučujeme vyhledat ve zdrojovém kódu aplikace `PSSetShader` volání a použít tradiční techniky ladění k prozkoumání chování těchto volání.

2. Otevřete okno **zásobník volání událostí grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **zásobník volání událostí grafiky**.

3. Použijte zásobník volání k vyhledání `PSSetShader` volání ve zdrojovém kódu vaší aplikace. V okně **zásobník volání událostí grafiky** vyberte volání nejvyšší úrovně a prověřte hodnotu, na kterou je pixel shader nastaven. Pixel shader může být nastaven přímo na hodnotu null nebo hodnota null může být způsobena argumentem, který byl předán do funkce nebo do jiného stavu. Pokud není přímo nastaveno, může být možné najít zdroj hodnoty null v zásobníku volání. V tomto scénáři zjistíte, že je funkce pixel shader nastavena přímo na `nullptr` funkci nejvyšší úrovně, která má název `CubeRenderer::Render` :

    ![Kód, který neinicializuje pixel shader](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Pokud nemůžete najít zdroj hodnoty null pouhým prozkoumáním zásobníku volání, doporučujeme, abyste pro volání nastavili podmíněný zarážku `PSSetShader` , což je spuštění programu při přerušení v případě, kdy je pixel shader nastaven na hodnotu null. Pak aplikaci restartujte v režimu ladění a použijte tradiční techniky ladění pro vyhledání zdroje hodnoty null.

   Chcete-li tento problém vyřešit, přiřaďte správnou funkci pixel shader pomocí prvního parametru `ID3D11DeviceContext::PSSetShader` volání rozhraní API.

   ![Opravený zdrojový kód jazyka C&#43;&#43; ](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Po opravě kódu jej můžete znovu sestavit a znovu spustit aplikaci, abyste ověřili, zda je problém vykreslování vyřešen:

   ![Objekt je nyní zobrazen](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")