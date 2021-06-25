---
title: Rozložení pro Visual Studio | Microsoft Docs
description: Seznamte se s rozložením Visual Studio dialogových oknech, včetně netvarovaných dialogů a nových dialogů s vzhledem s tematií.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e52b7b3fd620080b73e8d3de80672003ecb8fcf7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900523"
---
# <a name="layout-for-visual-studio"></a>Rozložení pro Visual Studio
Většina dialogových Visual Studio jsou Rozložení dialogových oken nástroje [,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)což jsou netemovaná dialogová okna, která dodržují standardní principy rozložení [desktopových dialogů Windows.](/windows/desktop/uxguide/win-dialog-box) Jak Visual Studio k aktualizaci uživatelského rozhraní, některé z význačnějších dialogů mají nový návrh, který je stanovuje jako prostředí definující produkty. Toto [rozložení s themed dialog](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) má vzhled s těmito styly.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Rozložení dialogového okna nástroje

- Všechny ovládací prvky v dialogovém okně nástroje by se měly spustit v levém horním rohu a měly by proudit dolů.

- Nikdy nezadáte ovládací prvky na střed v dialogovém okně, aby vyplnily velkou oblast.

- Pro veškerý text dialogového okna použijte písmo prostředí. Při psaní specifikace vizuálu místo výběru konkrétního písma a velikosti zadejte písmo prostředí. Viz [Písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Použijte konzistentní rozmístění a rozmístění ovládacích panelů, abyste podpořili cíl kvality v oblasti řízení.

- Dialogy mohou být složitější z většího počtu ovládacích prvků, jedinečné juxtapozice ovládacích prvků nebo obojího. V takových složitých situacích umožnte dostatečné místo mezi seskupeními ovládacích prostředků, aby uživatel mohl analyzovat logický tok.

### <a name="utility-dialog-layout-examples"></a>Příklady rozložení dialogových oknů nástrojů
 Všechny rozměry jsou vyjádřeny v pixelech.

 ![Mezery v dialogových oknech pro popisky nad ovládacími prvky](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 – a_UtilitySpacingAbove")

 **Obrázek 08.01-a: Pokyny pro mezery v dialogových oknech nástrojů s popisky nad ovládacími prvky**

 ![Mezery v dialogových oknech pro popisky nalevo od ovládacích prvků](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 – b_UtilitySpacingLeft")

 **Obrázek 08.01-b: Pokyny pro mezery v dialogových oknech nástrojů s popisky nalevo od ovládacích prvků**

### <a name="layout-details"></a>Podrobnosti o rozložení

#### <a name="margins"></a>Okraje

- Všechna dialogová okna by měla mít kolem všech okrajů ohraničení o 12 pixelech.

- Okraje v rámci skupinového rámce by měly být 9 pixelů od okraje rámu.

- Okraje v ovládacím prvku karta by měly být 6 pixelů od okraje ovládacího prvku karta.

#### <a name="command-buttons"></a>Příkazová tlačítka

- Příkazová tlačítka pracují s rámečkem dialogového okna, nikoli s obsahem. Měly by být umístěné v pravém dolním rohu a měly by mít dostatek místa nad proměnnou, aby byla tlačítka oddělená od jednotlivých tlačítek.

- Pokud dialogové okno používá vodorovná tlačítka, alternativní konfigurace příkazového tlačítka je vertikální zásobník v pravém horním rohu. Viz [vnitřní příkazová tlačítka](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) níže.

- Mezera nalevo od příkazových tlačítek (vlevo níž nebo uprostřed dialogového okna) se považuje za součást "pásma" ovládacích prvků operace dialogového okna. Jediné, co by v tomto prostoru mělo být, je odkaz Nápovědy, který je relevantní pro celkový úkol nebo dialogové okno.

- Příkazová tlačítka by měla mít velikost 75 × 23 pixelů.

- Command buttons should be 6 pixels apart.

  ![Základní zarovnání tlačítek](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 – c_ButtonAlign")

  **Obrázek 08,01-c: Základní zarovnání tlačítek**

#### <a name="labels"></a>Popisky

- Všechny popisky zarovnejte doleva.

- U popisků, které se nachází nad ovládacím prvku, by měly být přesně zarovnané doleva s ovládacím panelem pod ním a dolní část popisku by měla být 5 pixelů nad horním okrajem druhého ovládacího prvku (například pole se seznamem).

- U popisků, které jsou nalevo od ovládacích prvků, je minimální šířka mezi popiskem a ovládacím prvku vstupu 10 pixelů. Měl by být vytvořen implicitní druhý sloupec pro zarovnání textových polí, polí se seznamem nebo jiných ovládacích prvků.

- Popisky jsou velká a malá písmena, za kterých následuje dvojtečka. Viz [Styl textu.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Vzdálenost mezi ovládacími prvky
 Přiměřeně hromadíte ovládací prvky zásobníku. Pro mezery mezi skládané ovládací prvky neexistuje žádné absolutní vodítko. Těsnost mezi ovládacími prvky se může mezi dialogy mírně lišit. Doporučené mezery jsou 20 pixelů pro páry svislých ovládacích a popisků a 9 pixelů pro páry vodorovného ovládacího prvku a popisku. Minimální mezery mezi ovládacími panely u vodorovných párů jsou 6 pixelů.

 ![Doporučená vzdálenost mezi ovládacími prvky](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 – d_ControlDistance")

 **Obrázek 08.01-d: Doporučení pro vzdálenost mezi ovládacími prvky**

#### <a name="control-indentation"></a>Odsazení ovládacího prvku
 Když jsou ovládací prvky vnořené, zarovnejte vnitřní ovládací prvky vodorovně s levým okrajem výše uvedeného ovládacího prvku, obvykle s popiskem.

 ![Zarovnání vnořených ovládacích prvků](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 – e_ControlAlign")

 **Obrázek 08.01-e: Zarovnání vnořených ovládacích prvků**

#### <a name="control-width"></a>Šířka ovládacího prvku
 Šířka textového pole nebo jiných podobných ovládacích prvků by neměla být delší než průměrný vstup pole. Průměrné anglické slovo je pět znaků. Například textové pole, které vyžaduje dlouhý název cesty, by mělo být tak dlouhé, jak to umožňuje vodorovné rozložení, zatímco rozevírací seznam pro názvy platforem by měl mít délku, která umožňuje nejdelší zadání.

#### <a name="helper-text"></a>Text pomocné pomoci

- V dialogovém okně se může zobrazit pomocná text, který poskytuje další informace o účelu dialogového okna. Obvykle se nachází nahoře a může to být 1–2 věty.

- Délka čáry by měla mít pohodlnou šířku, aby ji uživatel parsovat a číst. Střední dialog by neměl být větší než 550 pixelů na šířku.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Vnitřní příkazová tlačítka
 Ve složitějších dialogových oknech může mít interní ovládací prvek vlastní související tlačítka, která můžou mít vliv na to, kde jsou umístěna tlačítka potvrzení dialogového okna.

- Pokud jsou tlačítka **OK** Cancel vodorovně orientovaná v pravém dolním rohu, použijte svislé zarovnání /  (sloupec) vnitřních tlačítek.

- Pokud jsou tlačítka **OK** Cancel svisle orientovaná v pravém horním rohu, použijte vodorovné zarovnání /  (řádek) vnitřních tlačítek. Tato situace je méně běžná.

- Vnitřní velikost tlačítka by měla cílit na standardní velikost tlačítka 75 × 23 pixelů, pokud je to možné, podle velikosti tlačítek **OK** /  Zrušit. Pokud popisek tlačítka zajistí, že tlačítko překročí standardní velikost tlačítka, ostatní tlačítka v této sadě by měla být zarovnána s širší velikostí.

  ![Vodorovná tlačítka OK a Zrušit](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 – f_HorizOKCan")

  **Obrázek 08.01-f: Svislá vnitřní tlačítka s vodorovným okem nebo rušit**

  ![Svislá tlačítka OK a Zrušit](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 – g_VertOKCan")

  **Obrázek 08,01 g: Vnitřní vodorovná tlačítka se svislou možností OK/Zrušit**

#### <a name="browse-button"></a>[Procházet...] Tlačítko
 **[Procházet...]** u tlačítek, která následují po textovém poli, by se měla zobrazit text "Procházet...". včetně tří tlipek. Pokud je místo příliš úzké nebo je na obrazovce **více tlačítek [Procházet...],** můžete tlačítko zmenšovat jenom na tři tečky.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Rozložení s themed dialog
 Dialogy s Visual Studio mají světlejší vzhled a nabízejí více prázdného místa. Typografie nabízí větší důraz a zájem a nabízí více otevřených mezer řádků a variaci velikostí a váze písma. Tam, kde je to možné, se chrome a záhlaví zmenšuje nebo odebraly. Rozložení těchto dialogových oknů by mělo postupovat podle tohoto základního vzoru:

1. Pozadí dialogového okna je bílé.

2. Uprostřed šedé hodnoty je ohraničení pravidla o pixelů 1 pixel.

3. Název dialogového okna už není v záhlaví, ale poskytuje vizuální význam a důraz na větší velikost bodu. (Viz část velikost písma ve [stylu textu.)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Popisky v kombinaci s dalším textem, jako je například popis, by měly být **Písmo prostředí + Tučné**.

5. Vnitřní sloupce jsou odděleny pravidlem o 1 pixelu světle šedě.

6. Výchozí odkazy nemají podtržítko. Stavy po najetí myší a stisknutí mají změnu barvy plus podtržítko.

7. Tlačítka potvrzení (například **OK** / **Zrušit)** se nachází v pravém dolním rohu.

### <a name="themed-dialog-layout-examples"></a>Příklady rozložení s themed dialog
 ![Rozložení s themed dialog](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 – h_ThemedDialog")

 **Obrázek 08.01-h: Dialogové okno s themed**

 ![Dimenze dialogových oknů s themed](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 – i_ThemedDialogDimensions")

 **Obrázek 08.01-i: Themed dialog - Dimensions**

 ![Písma dialogových dialogů s themed](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 – j_ThemedDialogFonts")

 **Obrázek 08.01-j: Dialogové okno s themed (s themed) – písma**

 ![Barvy dialogových oken s motivem](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 – k_ThemedDialogColors")

 **Obrázek 08,01-k: dialogové okno s motivem – barvy**

## <a name="see-also"></a>Viz také
- [Vzory aplikací pro Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Ovládací prvky (Windows)](/windows/desktop/uxguide/controls)
- [Dialogová okna (Windows)](/windows/desktop/uxguide/win-dialog-box)
