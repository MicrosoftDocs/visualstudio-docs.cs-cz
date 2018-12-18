---
title: Rozložení
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce6d1a39f568986dfd77ed47fc2da18bf3da7ee4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063677"
---
# <a name="layout-for-visual-studio"></a>Rozložení pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Většina dialogová okna Visual Studio je [rozložení dialogového okna nástroje](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), které jsou unthemed dialogů tento standard postupujte [Principy rozložení dialogového okna Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx). Visual Studio přesune na aktualizovat jeho uživatelské rozhraní, některé z nejvážnějších dialogová okna mít nový návrh, který vytváří je jako produkt definování prostředí. Tyto [rozložení dialogového okna s motivem](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) s motivem vzhled.

##  <a name="BKMK_UtilityDialogLayout"></a> Rozložení dialogového okna nástroje

-   Všechny ovládací prvky v dialogovém okně nástroje by měla začít od levého nebo horního a tok směrem dolů.

-   Nikdy center ovládacích prvků v dialogovém okně tak, aby vyplnil velké oblasti.

-   Použijte prostředí písmo veškerého textu dialogového okna. Při zápisu visual specifikace, zadejte místo výběru konkrétního písma a velikost písma prostředí. Zobrazit [písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

-   Použití mezery konzistentní řízení a umístění na podporu cílem kvality v řemeslné ruční práce.

-   Dialogová okna se může stát složitější z větší počet ovládacích prvků a jedinečný srovnáním ovládacích prvků. Pro tyto komplexní situace povolte dostatečný prostor mezi seskupení řízení uživateli přidělit logický tok analyzovat.

### <a name="utility-dialog-layout-examples"></a>Příklady rozložení dialogového okna nástroje
 Všechny dimenze jsou vyjádřeny v pixelech.

 ![Dialogové okno mezery pro popisky nad ovládací prvky](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801 a_UtilitySpacingAbove")

 **Obrázek 08.01-a: Mezery pokyny pro dialogová okna nástroje s popisky nad ovládací prvky**

 ![Dialogové okno mezery pro popisky nalevo od ovládacích prvků](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801 b_UtilitySpacingLeft")

 **Obrázek 08.01-b: Mezery pokyny pro dialogová okna nástroje s popisky nalevo od ovládacích prvků**

### <a name="layout-details"></a>Podrobnosti o rozložení

#### <a name="margins"></a>Okraje

-   Všechna dialogová okna by měl mít 12 pixel ohraničení všech okrajů.

-   Okraje v rámci skupiny musí mít 9 pixelů od levého okraje rámce.

-   Okraje v rámci ovládacího prvku karta by měla být 6 pixelů od levého okraje ovládacího prvku karta.

#### <a name="command-buttons"></a>Příkazová tlačítka

- Příkazová tlačítka pracovat v rámci dialogového okna, ne na obsah. Jsou třeba umístit na dolní pravé a musí mít dostatek variabilní mezerou výše uvedených nastavení odděleně samostatné tlačítka.

- Pokud existují vodorovná tlačítka, který provoz v rámci dialogového okna, konfigurace tlačítko alternativní příkaz je svislý zásobník v pravém horním rohu. Zobrazit [vnitřní příkazová tlačítka](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) níže.

- Místo nalevo od příkazová tlačítka (nižší vlevo/na střed dialogového okna) je považováno za součást "vzdálené" operace ovládací prvky dialogového okna. Jediné, co by měl pronikat na toto místo je odkaz nápovědy, které se týkají jedné úlohy nebo dialogového okna.

- Příkazová tlačítka by měla být 75 × 23 pixelů.

- Příkazová tlačítka by měla být 6 pixelů od sebe.

  ![Tlačítko základní zarovnání](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801 c_ButtonAlign")

  **Obrázek 08.01-c: Tlačítko základní zarovnání**

#### <a name="labels"></a>Popisky

-   Zarovnat vlevo všechny popisky.

-   Popisky, které se nacházejí nad ovládací prvek by měl vlevo – zařízení vyhovují přesně ovládacího prvku pod ní a dolní popisek by měla být vyšší než ten druhý ovládací prvek (například pole se seznamem) 5 pixelů.

-   Minimální šířka mezi popiskem a vstupní ovládací prvek pro popisky, které se nacházejí na levé straně ovládacích prvků, je 10 pixelů. Implicitní druhý sloupec stanovit pro zarovnání textová pole, pole se seznamem nebo jiných ovládacích prvků.

-   Popisky jsou věty a následuje dvojtečka. Zobrazit [styl textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Vzdálenost mezi ovládacími prvky
 Ovládací prvky zásobníku přiměřeným způsobem. Neexistuje žádné absolutní pokyny k vytvoření mezer mezi ovládacími prvky skládaný. Těsnost mezi ovládacími prvky mohou mírně lišit dialogová okna. Doporučené mezery je 20 pixelů pro dvojice svislé/popisek ovládacího prvku a 9 pixelů pro dvojice Vodorovný/popisek ovládacího prvku. Mezery minimální ovládací prvek pro vodorovné dvojice je 6 pixelů.

 ![Doporučené vzdálenost mezi ovládacími prvky](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801 d_ControlDistance")

 **Obrázek 08.01-d: Doporučení pro vzdálenost mezi ovládacími prvky**

#### <a name="control-indentation"></a>Ovládací prvek odsazení
 Když jsou vnořené ovládací prvky, Zarovnat vnitřní ovládací prvky vodorovně s levým okrajem ovládacího prvku výše, obvykle popisek.

 ![Vnořené řízení zarovnání](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801 e_ControlAlign")

 **Obrázek 08.01 – e: Zarovnání ovládacího prvku vnořené**

#### <a name="control-width"></a>Šířku ovládacího prvku
 Šířka textového pole nebo další podobné prvky musí být delší než průměrná vstupní pole. Průměrná anglického slova je pět znaků. Například textové pole, která vyžaduje dlouhého názvu cesty by měl být libovolně dlouhý umožňuje vodorovné rozložení, přestože rozevírací seznam pro platformu názvy by měly být pouze délkou, která umožňuje nejdelší položce.

#### <a name="helper-text"></a>Pomocné rutiny, textu

-   Text pomocné rutiny, s dalšími informacemi o účelu dialogového okna můžete zobrazit dialogové okno. To obvykle nachází v horní části a může být 1 až 2 věty.

-   Délka řádku by měla být pohodlné šířku pro uživatele k analýze a číst. Střední dialogového okna by měl být více než 550 pixelů na šířku.

####  <a name="BKMK_InteriorCommandButtons"></a> Vnitřní příkazová tlačítka
 V dialogových oknech složitější vnitřní ovládací prvek může mít svůj vlastní související tlačítka, což může ovlivnit, kde se nachází tlačítka dialogového okna potvrzení.

- Svislé zarovnání (sloupec) vnitřní tlačítka při použití **OK**/**zrušit** jsou orientovaný vodorovně v pravém dolním rohu.

- Vodorovné zarovnání (řádků) vnitřní tlačítka při použití **OK**/**zrušit** jsou orientovány svisle v pravém horním rohu. Tato situace je méně častý.

- Velikost vnitřní tlačítka zaměřit standardní tlačítko velikost 75 × 23 pixelech odpovídající velikost **OK**/**zrušit** tlačítka, pokud je to možné. Pokud popisek tlačítka tlačítko přesáhla velikost standardní tlačítko, by mělo odpovídat tato velikost rozšířit další tlačítka v dané sadě.

  ![Tlačítka OK vodorovné a zrušit](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801 f_HorizOKCan")

  **Obrázek 08.01-f: Svislé vnitřní tlačítka s vodorovné OK/zrušit**

  ![Tlačítka OK svislé a zrušit](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801 g_VertOKCan")

  **Obrázek 08.01-g: Vodorovné vnitřní tlačítka s svislé OK/zrušit**

#### <a name="browse-button"></a>[Procházet...] tlačítko
 **[Procházet...]**  tlačítka, které následují textové pole by si "Procházet..." pravopisu v plném rozsahu, včetně na tři tečky. Pokud je na úzkou místa nebo je více **[Procházet...]**  tlačítka na obrazovce, na tlačítko můžete omezit na právě na tři tečky.

##  <a name="BKMK_ThemedDialogLayout"></a> Rozložení s motivem dialogového okna
 S motivem dialogová okna v sadě Visual Studio světlejší vzhled a nabízí další prázdné znaky. Typografie poskytuje další důraz a oblastí zájmu, nabízí otevřenější řádkování a změnu velikosti písma a váhy. Tam, kde je to možné, byly pruhy chrome a názvu nižší nebo odebrán. Rozložení těchto dialozích postupujte podle tohoto základního modelu:

1.  Je bílé pozadí dialogového okna.

2.  Je střední hodnota šedě hranici pravidlo 1 pixelu.

3.  Název dialogového okna už umístěn v záhlaví okna, ale poskytuje vizuální přitažlivost a zvýraznit větší bod. (Viz část velikost písma v [styl textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4.  Popisky spolu se další text, například popis, musí být **písmo prostředí + tučné**.

5.  Vnitřní sloupce jsou odděleny pravidlo 1 pixelu ve světle šedá.

6.  Výchozí odkazy mít žádná podtržení. Při najetí myší a stavy při stisknutí mít změna barvy a podtržítka.

7.  Potvrdit tlačítka (například **OK**/**zrušit**) nacházejí v pravém dolním rohu.

### <a name="themed-dialog-layout-examples"></a>Příklady s motivem dialogu rozložení
 ![Rozložení dialogového okna s motivem](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801 h_ThemedDialog")

 **Obrázek 08.01v: Dialogové okno s motivem**

 ![Dialogové okno s motivem dimenze](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801 i_ThemedDialogDimensions")

 **Obrázek 08.01-i: s motivem dialogové okno – dimenze**

 ![Písma dialogového okna s motivem](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801 j_ThemedDialogFonts")

 **Obrázek 08.01-j: s motivem dialogové okno – písma**

 ![Dialogové okno motivy barev](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801 k_ThemedDialogColors")

 **Obrázek 08.01-k: s motivem dialogové okno – barvy**

## <a name="see-also"></a>Viz také
 [Modely aplikací pro sadu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md) [ovládacích prvků (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) [dialogových oken (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)
