---
title: Rozložení pro Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698397"
---
# <a name="layout-for-visual-studio"></a>Rozložení pro Visual Studio
Většina dialogových oken sady Visual Studio jsou [rozložení dialogového okna nástroj ,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)což jsou netemitová dialogová okna, která se řídí [standardními principy rozložení dialogového okna Plochy systému Windows](/windows/desktop/uxguide/win-dialog-box). Jako Visual Studio přesune aktualizovat své rozhraní, některé z výraznější dialogy mají nový návrh, který je stanoví jako prostředí definující produkt. Tyto [tematou rozvržení dialogu](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) mají tematou vzhled.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Rozložení dialogového okna nástroje

- Všechny ovládací prvky v rámci dialogu nástroje by měly začínat v horní části/vlevo a stékat dolů.

- Nikdy nevystředňujte ovládací prvky v dialogovém okně, abyste vyplnili velkou plochu.

- Pro veškerý text dialogu použijte písmo prostředí. Při psaní vizuální specifikace určete písmo prostředí namísto výběru konkrétního písma a velikosti. Viz [Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Používejte konzistentní rozestupy ovládacích tlačítek a umístění, abyste podpořili cíl kvality v řemeslném zpracování.

- Dialogová okna mohou být složitější z většího počtu ovládacích prvků, jedinečné hojné umístění ovládacích prvků nebo obojí. Pro tyto složité situace povolte dostatečný prostor mezi seskupeními ovládacích prvku, aby uživatel logický tok analyzovat.

### <a name="utility-dialog-layout-examples"></a>Příklady rozložení dialogového okna nástroje
 Všechny kóty jsou vyjádřeny jako obrazové body.

 ![Rozteč dialogů pro popisky nad ovládacími prvky](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Obrázek 08.01-a: Pokyny pro mezery pro dialogová okna nástrojů s popisky nad ovládacími prvky**

 ![Rozteč dialogů pro popisky vlevo od ovládacích prvků](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Obrázek 08.01-b: Pokyny pro mezery pro dialogová okna nástrojů s popisky nalevo od ovládacích prvků**

### <a name="layout-details"></a>Podrobnosti rozložení

#### <a name="margins"></a>Okraje

- Všechna dialogová okna by měla mít kolem všech okrajů ohraničení o 12 obrazových bodech.

- Okraje v rámci skupinového rámečku by měly být 9 obrazových bodů od okraje rámečku.

- Okraje v ovládacím prvku tabulátoru by měly být 6 pixelů od okraje ovládacího prvku tabulátoru.

#### <a name="command-buttons"></a>Příkazová tlačítka

- Příkazová tlačítka pracují na dialogu, nikoli na obsahu. Měly by být umístěny v pravém dolním rohu a měly by mít dostatek variabilního prostoru výše pro nastavení tlačítek zřetelně oddělených.

- Pokud existují vodorovná tlačítka, která pracují v dialogovém okně, alternativní konfigurace příkazového tlačítka je svislý zásobník v pravém horním bodě. Viz [vnitřní příkazová tlačítka](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) níže.

- Mezera vlevo od příkazových tlačítek (vlevo dole/uprostřed dialogu) je považována za součást "pásma" ovládacích prvků pro ovládání dialogu. Jediná věc, která by měla zasahovat do tohoto prostoru, je odkaz nápovědy, který je relevantní pro celkový úkol nebo dialog.

- Příkazová tlačítka by měla mít rozměry 75 x 23 pixelů.

- Příkazová tlačítka by měla být od sebe vzdálena 6 pixelů.

  ![Základní zarovnání tlačítek](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Obrázek 08.01-c: Základní zarovnání tlačítka**

#### <a name="labels"></a>Popisky

- Všechny popisky zarovnávají doleva.

- Pro popisky, které sedí nad ovládacím prvkem, by měly být přesně zarovnány doleva s ovládacím prvkem pod ním a spodní část popisku by měla být 5 pixelů nad horní částí druhého ovládacího prvku (například pole se seznamem).

- Pro popisky, které jsou nalevo od ovládacích prvků, je minimální šířka mezi popiskem a vstupním ovládacím prvkem 10 pixelů. Implicitní druhý sloupec by měl být vytvořen pro zarovnání textových polí, polí se seznamem nebo jiných ovládacích prvků.

- Popisky jsou velká písmena a následuje dvojtečka. Viz [Styl textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Vzdálenost mezi ovládacími prvky
 Stack ovládá rozumně. Neexistuje žádné absolutní vodítko pro mezery mezi skládanýovládací prvky. Těsnost mezi ovládacími prvky se může mezi dialogy mírně lišit. Doporučené mezery jsou 20 pixelů pro svislé dvojice ovládacích prvk/popisků a 9 pixelů pro dvojice vodorovného ovládání/popisku. Minimální rozteč ovládacích míst pro vodorovné páry je 6 pixelů.

 ![Doporučená vzdálenost mezi ovládacími prvky](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Obrázek 08.01-d: Doporučení pro vzdálenost mezi ovládacími prvky**

#### <a name="control-indentation"></a>Odsazení ovládacího prvku
 Když jsou ovládací prvky vnořené, zarovnejte vnitřní ovládací prvky vodorovně s levým okrajem ovládacího prvku výše, obvykle popisku.

 ![Vnořené zarovnání ovládacího prvku](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Obrázek 08.01-e: Vnořené zarovnání ovládacího prvku**

#### <a name="control-width"></a>Šířka ovládacího prvku
 Šířka textového pole nebo jiných podobných ovládacích prvků by neměla být delší než průměrný vstup pro pole. Průměrné anglické slovo je pět znaků. Například textové pole, které vyžaduje dlouhý název cesty by měla být tak dlouho, jak umožňuje vodorovné rozložení, zatímco rozevírací plán pro názvy platformy by měla být pouze délka, která umožňuje nejdelší položku.

#### <a name="helper-text"></a>Pomocné texty

- V dialogovém okně lze zobrazit pomocný text, který poskytuje další informace o účelu dialogového okna. To obvykle sedí v horní části a může být 1-2 věty.

- Délka řádku by měla být pohodlná šířka pro uživatele analyzovat a číst. Střední dialog by neměl být širší než 550 pixelů.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Vnitřní příkazová tlačítka
 Ve složitějších dialogových oknech může mít vnitřní ovládací prvek vlastní související tlačítka, která mohou ovlivnit umístění tlačítek potvrzení dialogového okna.

- Použijte svislé zarovnání (sloupec) vnitřních tlačítek, když je **ok**/**storno** vodorovně orientováno v pravém dolním rohu.

- Použijte vodorovné zarovnání (řádek) vnitřních tlačítek, když je **funkce OK**/**Cancel** v pravém horním rohu svisle orientována. Tato situace je méně častá.

- Velikost vnitřního tlačítka by měla cílit na standardní velikost tlačítka 75 x 23 pixelů, pokud je to možné, odpovídající velikosti tlačítek **OK**/**Cancel.** Pokud popisek tlačítka způsobí, že tlačítko překročí standardní velikost tlačítka, ostatní tlačítka v této sadě by měla být zarovnána s tou širší velikostí.

  ![Vodorovná tlačítka OK a Storno](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Obrázek 08.01-f: Svislá vnitřní tlačítka s vodorovným OK/Cancel**

  ![Svislá tlačítka OK a Storno](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Obrázek 08.01-g: Vodorovná vnitřní tlačítka se svislým OK/Cancel**

#### <a name="browse-button"></a>[Procházet...] Tlačítko
 **[Procházet...]** Tlačítka, která následují za textovým polem, by měla hláskovat "Procházet..." včetně tři tečky. Pokud je na obrazovce málo míst nebo je na obrazovce více tlačítek **[Procházet...],** lze tlačítko zredukovat pouze na tři tečky.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Rozložení tematého dialogu
 Tématické dialogy v sadě Visual Studio mají světlejší vzhled a nabízejí více prázdného místa. Typografie poskytuje větší důraz a zájem, nabízí otevřenější řádkování a variace velikostí a hmotností písma. Pokud je to možné, byly chromové a titulní pruhy zmenšeny nebo odstraněny. Rozložení těchto dialogových oken by mělo následovat tento základní vzor:

1. Pozadí dialogu je bílé.

2. V šedé mši střední hodnoty je ohraničení pravidla o 1 obrazovém bodu.

3. Název dialogového okna již není v záhlaví, ale poskytuje vizuální zájem a důraz ve větší velikosti bodu. (Viz část velikost písma ve [stylu Textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Popisky spojené s dalším textem, například popisem, by měly být **písmo prostředí + tučné písmo**.

5. Vnitřní sloupce jsou odděleny pravidlem 1 obrazového bodu světle šedě.

6. Výchozí odkazy nemají podtržítko. Najetí a stisknuté stavy mají změnu barvy plus podtržítko.

7. Tlačítka potvrzení (například **OK**/**Cancel)** sedí v pravém dolním rohu.

### <a name="themed-dialog-layout-examples"></a>Příklady rozložení dialogových oken s tématiky
 ![Rozložení tematého dialogu](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Obrázek 08.01-h: Dialog s tématy**

 ![Tematou mise dialogových dimenzí](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Obrázek 08.01-i: Dialog s tématy – rozměry**

 ![Tématová dialogová písma](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Obrázek 08.01-j: Dialogové okno s tématy – písma**

 ![Temamotivní dialogové okno barvy](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Obrázek 08.01-k: Dialog s tématy – barvy**

## <a name="see-also"></a>Viz také
- [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Ovládací prvky (Windows)](/windows/desktop/uxguide/controls)
- [Dialogová okna (Windows)](/windows/desktop/uxguide/win-dialog-box)
