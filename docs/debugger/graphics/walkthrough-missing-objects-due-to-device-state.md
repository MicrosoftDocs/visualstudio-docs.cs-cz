---
title: 'Návod: chybějící objekty z důvodu stavu zařízení | Microsoft Docs'
description: Postupujte podle šetření, které najde nesprávně nakonfigurovaný stav zařízení. Zobrazuje použití seznamu událostí grafiky, fází zřetězení grafiky a Historie pixelů grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8eff8a088823bc46363d2e5ea7b40b3e2b8478e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890432"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Návod: Chybějící objekty z důvodu stavu zařízení
Tento návod ukazuje, jak použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafiky k prozkoumání objektu, který chybí kvůli nesprávně nakonfigurovanému stavu zařízení.

 Tento návod ukazuje, jak:

- K vyhledání potenciálních zdrojů problému použijte **seznam událostí grafiky** .

- Pomocí okna **fáze zřetězení grafiky** můžete kontrolovat účinek `DrawIndexed` volání rozhraní Direct3D API.

- Pomocí okna **Historie pixelů grafiky** můžete najít problém přesněji.

- Zkontrolujte stav zařízení a vyhledejte možné problémy nebo chyby konfigurace.

## <a name="scenario"></a>Scenario
 Jeden z důvodů, proč se objekty nemusí zobrazit tam, kde jsou očekávány v 3D aplikaci, je chybná konfigurace grafického zařízení, které způsobuje, že objekty budou vyloučeny z vykreslování – například v případě, že pořadí vinutí způsobuje odstranění trojúhelníků v chybě nebo když funkce hloubkového testu způsobí, že všechny pixely v objektu budou odmítnuty.

 Ve scénáři, který je popsaný v tomto návodu, jste právě dosáhli prvního milníku ve vývoji vaší 3D aplikace a jste připraveni ho otestovat poprvé. Při spuštění aplikace se ale na obrazovku vykresluje jenom uživatelské rozhraní. Pomocí Diagnostika grafiky zachytíte problém do souboru protokolu grafiky, abyste mohli aplikaci ladit. Problém v této aplikaci vypadá následovně:

 ![Aplikace před tímto problémem se opravila.](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")

 Informace o tom, jak zachytit problémy s grafikou v protokolu grafiky, najdete v tématu [zachycení grafických informací](capturing-graphics-information.md).

## <a name="investigation"></a>Šetření
 Pomocí nástrojů Diagnostika grafiky můžete načíst soubor protokolu grafiky a zkontrolovat rámce, které byly zachyceny během testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Prohlédnutí snímku v protokolu grafiky

1. V nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtěte protokol grafiky, který obsahuje rámeček, který vykazuje chybějící model. V nástroji se zobrazí nová karta Diagnostika grafiky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . V horní části této karty je výstup cíle vykreslování vybraného snímku. V dolní části je **seznam rámců**, který zobrazuje jednotlivé zachycené rámce jako obrázek miniatury.

2. V **seznamu snímků** vyberte rámec, který ukazuje, že model není zobrazen. Cíl vykreslování se aktualizuje tak, aby odrážel vybraný snímek. V tomto scénáři vypadá karta protokol grafiky takto:

    ![Karta. vsglog framebuffer náhled a seznam snímků](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")

   Po výběru rámce, který demonstruje problém, můžete k jeho diagnostice použít **seznam událostí grafiky** . **Seznam událostí grafiky** obsahuje každé volání rozhraní Direct3D API, které bylo provedeno pro vykreslení aktivního rámce, například volání rozhraní API pro nastavení stavu zařízení, pro vytváření a aktualizaci vyrovnávacích pamětí a pro kreslení objektů, které se zobrazí v rámci rámečku. Mnoho druhů volání je zajímavé, protože často (ale ne vždy) odpovídající změna v cíli vykreslování, když aplikace funguje podle očekávání, například kreslení, odesílání, kopírování nebo vymazání volání. Volání remíz jsou obzvláště zajímavá, protože každá z nich představuje geometrii, kterou vygenerovala aplikace (volání expedice může také vykreslovat geometrii).

#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Aby bylo zajištěno, že budou vyvolána volání draw

1. Otevřete okno **seznam událostí grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **seznam událostí**.

2. Zkontrolujte **seznam událostí grafiky** pro volání draw. To lze usnadnit zadáním příkazu "Draw" do **vyhledávacího** pole v pravém horním rohu okna **seznam událostí grafiky** . Tím se seznam vyfiltruje tak, aby obsahoval jenom události, které mají v názvech "Draw". V tomto scénáři zjistíte, že bylo provedeno několik volání remíz:

    ![Seznam událostí grafiky znázorňující zachycené události](media/vsg_walkthru1_.png "vsg_walkthru1_")

   Po potvrzení, že jsou vytvářena volání vykreslování, můžete určit, která z nich odpovídá chybějící geometrii. Protože víte, že chybějící geometrie není vykreslována do cíle vykreslování (v tomto případě), můžete použít okno **fáze zřetězení grafiky** k určení, které volání vykreslování odpovídá chybějící geometrii. Okno **fáze zřetězení grafiky** zobrazuje geometrii, která byla odeslána každému volání vykreslení bez ohledu na jeho vliv na cíl vykreslování. Při procházení volání vykreslování jsou fáze zřetězení aktualizovány tak, aby zobrazovaly geometrii, která je přidružena k tomuto volání, a výstup cíle vykreslování je aktualizován tak, aby zobrazoval stav cíle vykreslování po dokončení volání.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Vyhledání volání remíz pro chybějící geometrii

1. Otevřete okno **fáze zřetězení grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte **fáze zřetězení**.

2. Procházejte každým voláním remíz při sledování okna **fáze zřetězení grafiky** pro chybějící model. **Vstupní fáze assembleru** zobrazuje nezpracovaná data modelu. Fáze **vertex shader** zobrazuje transformovaná data modelu. Fáze **pixel shaderu** zobrazuje výstup pixel shaderu. Fáze **Výstup-fúze** zobrazuje sloučený cíl vykreslování tohoto volání vykreslování a všechna předchozí volání vykreslování.

3. Zastavit, pokud jste dosáhli volání vykreslování, které odpovídá chybějícímu modelu. V tomto scénáři okno **fáze zřetězení grafiky** indikuje, že geometrie byla vykreslena, ale nebyla zobrazena v cíli vykreslování:

    ![Prohlížeč kanálů zobrazující chybějící objekt](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")

   Po potvrzení, že aplikace vygenerovala chybějící geometrii a vyhledáte odpovídající volání metody Draw, můžete vybrat část výstupu cíle vykreslování, která by měla zobrazovat chybějící geometrii, a pak pomocí okna **Historie pixelů grafiky** zjistit, proč byly pixely vyloučeny. Historie pixelů obsahuje seznam všech volání remíz, která by mohla mít vliv na určitý pixel. Každé volání remízy v okně **Historie pixelů grafiky** je určeno číslem, které je také zobrazeno v okně **seznam událostí grafiky** . To vám pomůže potvrdit, že pixel by měl zobrazovat chybějící geometrii a zjistit, proč byl pixel vyloučený.

#### <a name="to-determine-why-the-pixel-was-excluded"></a>Určení důvodu vyloučení pixelu

1. Otevřete okno **Historie pixelů grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte položku **Historie pixelů**.

2. Na základě miniatury funkce **pixel shader** vyberte pixel ve výstupu framebuffer, který by měl obsahovat část chybějící geometrie. V tomto scénáři by výstup pixel shaderu měl pokrývat většinu cílů vykreslování; Po výběru pixelu okno **Historie pixelů grafiky** vypadá takto:

    ![Okno Historie pixelů zobrazující související volání vykreslování](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")

3. Potvrďte, že vybraný cílový pixel vykreslování obsahuje část geometrie, a to tak, že odpovídá počtu volání remíz, které kontrolujete (z okna **seznam událostí grafiky** ) k jednomu z volání vykreslování v okně **Historie pixelů grafiky** . Pokud se žádné volání v okně **Historie pixelů grafiky** neshoduje s voláním vykreslování, které jste prohlédli, opakujte tento postup (s výjimkou kroku 1), dokud nenajdete shodu. V tomto scénáři vypadá vyhovující volání draw takto:

    ![Okno Historie pixelů zobrazující informace o fragmentaci](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")

4. Po nalezení shody rozbalte odpovídající volání vykreslování v okně **Historie pixelů grafiky** a ověřte, zda byl pixel vyloučen. Každé volání remízy v okně **Historie pixelů grafiky** odpovídá jednomu nebo více geometrickým primitivním prvkům (body, řádky nebo trojúhelníky), které se protínají jako výsledek geometrie odpovídajícího objektu. Každé takové průsečíky může přispívat k konečné barvě pixelu. Primitivum, které se vyloučilo, protože došlo k selhání testu hloubky, je reprezentované ikonou, která zobrazuje písmeno Z na šipku, která se šikmo dolů od levého pravé strany.

5. Rozbalení vyloučené primitivy k dalšímu zjištění stavu, který způsobil, že bude vyloučen. Ve **výstupní skupině fúze** přesuňte ukazatel na **výsledek**. Popisek indikuje, proč se primitivum vyloučilo. V tomto scénáři zkoumání odhalí, že primitivní byla vyloučena, protože neprošel testem hloubky, a proto nepřispěla k konečné barvě pixelu.

   Až zjistíte, že se geometrie nezobrazí, protože její primitivní prvky selhaly při testování hloubky, možná budete mít podezření, že tento problém souvisí s chybně konfigurovaným stavem zařízení. Data o stavu zařízení a dalších objektech Direct3D lze prozkoumat pomocí **tabulky objekt grafiky**.

#### <a name="to-examine-device-state"></a>Kontrola stavu zařízení

1. Otevřete okno **tabulka objektů grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte **tabulka objektů**.

2. Vyhledejte objekt **zařízení d3d10** v **tabulce objekt grafiky** a pak otevřete objekt **zařízení d3d10** . Otevře se nová karta **zařízení d3d10** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Chcete-li to usnadnit, můžete seřadit **tabulku objektu grafiky** podle **typu**:

    ![Tabulka grafických objektů a související stav zařízení](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")

3. Projděte si stav zařízení, který se zobrazí na kartě **zařízení d3d10** , kde bude možné problémy vyřešit. Vzhledem k tomu, že se geometrie nezobrazí, protože její primitivní prvky selhaly při testování hloubky, můžete se zaměřit na stav zařízení, jako je například vzorník hloubky, který má vliv na test hloubky. V tomto scénáři obsahuje **Popis vzorníku hloubky** (ve **stavu fúze výstupu**) neobvyklou hodnotu člena **funkce hloubky** `D3D10_COMPARISON_GREATER` :

    ![Okno zařízení D3D10 zobrazující informace o vzorníku hloubky](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")

   Jakmile zjistíte, že příčinou potíží s vykreslováním může být chybná nakonfigurovaná hloubka, můžete tyto informace použít spolu s vaším vědomím kódu a vyhledat tak, kde byla funkce hloubky nastavena nesprávně, a pak problém vyřešit. Pokud nejste obeznámeni s kódem, mohli byste vyhledat problém pomocí označení, které jste shromáždili během ladění – například v závislosti na **popisu vzorníku hloubky** v tomto scénáři můžete hledat v kódu slova jako "Hloubka" nebo "větší". Po opravě kódu ho znovu sestavte a znovu spusťte aplikaci, abyste zjistili, že problém vykreslování je vyřešen:

   ![Aplikace po vyřešení problému](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")