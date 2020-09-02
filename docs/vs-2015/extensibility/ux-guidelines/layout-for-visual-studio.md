---
title: Layout
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09656b9afac82eec8981f8573af87391c99a3688
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179757"
---
# <a name="layout-for-visual-studio"></a>Rozložení pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Většina dialogových oken sady Visual Studio je [rozložení dialogového okna nástrojů](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), což jsou nezobrazená dialogová okna, která následují standardní [zásady rozložení dialogového okna Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx). Když se Visual Studio přesune k aktualizaci uživatelského rozhraní, některé z výraznějších dialogových oken mají nový návrh, který je sestavil jako prostředí s definicí produktu. Toto [rozložení dialogového okna s motivem](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) má vzhled motivu.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Rozložení dialogového okna nástrojů

- Všechny ovládací prvky v dialogovém okně nástroje by měly začínat nahoře nebo vlevo a přesměrovat směrem dolů.

- Nikdy necentruje ovládací prvky v dialogovém okně pro vyplňování velké oblasti.

- Použijte písmo prostředí pro veškerý text dialogového okna. Při psaní vizuální specifikace místo výběru konkrétního písma a velikosti zadejte písmo prostředí. Podívejte [se na písmo prostředí](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Pro podporu cíle kvality v craftsmanship používejte konzistentní mezery a umístění ovládacích prvků.

- Dialogy mohou být složitější z většího počtu ovládacích prvků, jedinečných juxtaposition ovládacích prvků nebo obojího. V případě těchto složitých situací umožněte, aby uživatel měl k analýze logický tok dostatek místa mezi seskupeními ovládacích prvků.

### <a name="utility-dialog-layout-examples"></a>Příklady rozložení dialogového okna nástrojů
 Všechny dimenze jsou vyjádřeny v pixelech.

 ![Mezery v dialogovém okně pro popisky nad ovládacími prvky](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801 – a_UtilitySpacingAbove")

 **Obrázek 08,01-a: pokyny pro mezery pro dialogová okna s popisky nad ovládacími prvky**

 ![Mezery v dialogovém okně pro popisky nalevo od ovládacích prvků](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801 – b_UtilitySpacingLeft")

 **Obrázek 08,01-b: pokyny pro mezery pro dialogová okna s popisky nalevo od ovládacích prvků**

### <a name="layout-details"></a>Podrobnosti rozložení

#### <a name="margins"></a>Okraje

- Všechny dialogy by měly mít ohraničení 12 pixelů kolem všech hran.

- Okraje v rámci skupinového rámečku by měly být z okraje rámce 9 pixelů.

- Okraje v rámci ovládacího prvku karta by měly být 6 pixelů od okraje ovládacího prvku karta.

#### <a name="command-buttons"></a>Příkazová tlačítka

- Příkazová tlačítka fungují v rámci dialogového okna, nikoli na obsahu. Měly by být umístěny v pravém dolním rohu a měly by mít k dispozici dostatek místa na více proměnných pro nastavení samostatných tlačítek.

- Pokud existují horizontální tlačítka, která v dialogovém okně pracují, je alternativní tlačítko pro konfiguraci příkazového řádku svisle v pravém horním rohu. Viz níže uvedená [tlačítka pro vnitřní příkazy](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) .

- Mezera vlevo od příkazových tlačítek (dolní levý/střed dialogového okna) se považuje za součást "panelu" ovládacího prvku operace dialogu. Jediným aspektem, který by se měl v tomto prostoru intrude, je odkaz na odkaz, který je důležitý pro celou úlohu nebo dialog.

- Příkazová tlačítka by měla být 75x23 pixely.

- Příkazové tlačítko by mělo mít více než 6 pixelů od sebe.

  ![Základní zarovnání tlačítek](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801 – c_ButtonAlign")

  **Obrázek 08,01-c: základní zarovnání tlačítek**

#### <a name="labels"></a>Popisky

- Zarovnává všechny popisky vlevo.

- U popisků, které se nachází nad ovládacím prvkem, by měly být přesně zarovnány s ovládacím prvkem pod ním a dolní část popisku by měla být 5 pixelů nad horním okrajem druhého ovládacího prvku (například pole se seznamem).

- U popisků, které sedí nalevo od ovládacích prvků, je minimální šířka mezi popiskem a ovládacím prvkem vstupu 10 pixelů. Měl by být vytvořen implicitní druhý sloupec pro zarovnání textových polí, polí se seznamem nebo jiných ovládacích prvků.

- Popisky jsou velká a malá písmena a za nimi následuje dvojtečka. Zobrazit [styl textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Vzdálenost mezi ovládacími prvky
 Ovládací prvky zásobníku jsou odůvodněné. Pro mezery mezi skládanými ovládacími prvky neexistuje absolutní směrnice. Těsnost mezi ovládacími prvky se může mírně lišit mezi dialogovými dialogy. Doporučené řádkování je 20 pixelů pro svislé páry ovládacího prvku/popisku a 9 pixelů pro páry vodorovných ovládacích prvků nebo popisků. Minimální mezery mezi ovládacími prvky pro vodorovné páry jsou 6 pixelů.

 ![Doporučená vzdálenost mezi ovládacími prvky](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801 – d_ControlDistance")

 **Obrázek 08,01-d: doporučení pro vzdálenost mezi ovládacími prvky**

#### <a name="control-indentation"></a>Odsazení ovládacího prvku
 Když jsou ovládací prvky vnořené, zarovnejte vnitřní ovládací prvky vodorovně s levým okrajem ovládacího prvku, který je obvykle popisek.

 ![Zarovnání vnořeného ovládacího prvku](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801 – e_ControlAlign")

 **Obrázek 08,01-e: vnořené zarovnání ovládacího prvku**

#### <a name="control-width"></a>Šířka ovládacího prvku
 Šířka textového pole nebo jiných podobných ovládacích prvků by neměla být delší než průměrná hodnota vstupu pole. Průměrné slovo v angličtině je pět znaků. Například textové pole, které vyžaduje dlouhý název cesty, by mělo být, pokud umožňuje horizontální rozložení, zatímco rozevírací seznam pro názvy platforem by měl mít pouze délku, která umožňuje nejdelší položku.

#### <a name="helper-text"></a>Text nápovědy

- Dialogové okno může zobrazit pomocný text, který poskytuje další informace o účelu dialogového okna. Obvykle je umístěn v horní části a může být 1-2 vět.

- Délka řádku by měla být pohodlná, aby mohl uživatel analyzovat a číst. Střední dialog by neměl být větší než 550 pixelů na šířku.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Vnitřní příkazová tlačítka
 V složitějších dialogových oknech může interní ovládací prvek mít vlastní související tlačítka, která mohou ovlivnit, kde jsou umístěna tlačítka pro potvrzení dialogového okna.

- Použijte svislé zarovnání (sloupec) vnitřních tlačítek, pokud je tlačítko **OK** / **Zrušit** vodorovné orientace v pravém dolním rohu.

- Použijte vodorovné zarovnání (řádek) vnitřních tlačítek, když se **OK** / **Cancel** v pravém horním rohu orientují svisle. Tato situace je méně častá.

- Velikost vnitřního tlačítka by měla cílit na velikost standardního tlačítka v 75x23 pixelech, pokud je to možné, odpovídá velikost tlačítek **OK** / **Cancel** . Pokud jmenovka tlačítka změní tlačítko na standardní velikost tlačítka, ostatní tlačítka v této sadě by měla zarovnat s touto širší velikostí.

  ![Tlačítka pro horizontální tlačítko OK a Storno](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801 – f_HorizOKCan")

  **Obrázek 08,01-f: svislá vnitřní tlačítka s vodorovným kliknutím na tlačítko OK/Storno**

  ![Tlačítka pro svislé tlačítko OK a Storno](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801 – g_VertOKCan")

  **Obrázek 08,01-g: vodorovná vnitřní tlačítka se svislým kliknutím na tlačítko OK/Storno**

#### <a name="browse-button"></a>[Procházet...] tlačítko
 **[Procházet...]** tlačítka, která následují po textovém poli, by měla vyslovit "Procházet...". v plném rozsahu, včetně tří teček. Pokud je prostor těsné a na obrazovce je víc tlačítek **[Procházet...]** , může se tlačítko snížit jenom na tři tečky.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Rozložení dialogového okna s motivem
 Dialogová okna motivů v aplikaci Visual Studio mají světlejší vzhled a nabízejí více prázdných znaků. Typografie nabízí více zdůraznění a zájmu, nabízí další otevřené mezery mezi řádky a variace velikostí a vah písma. Pokud je to možné, aplikace Chrome a záhlaví se snížily nebo odeberou. Rozložení těchto dialogových oken by se mělo řídit tímto základním vzorem:

1. Pozadí dialogového okna je bílé.

2. Šedá hodnota je ohraničení pravidla o velikosti 1 pixelu.

3. Název dialogového okna už není umístěný v záhlaví, ale poskytuje vizuální zájem a důraz na velikost většího bodu. (Viz část velikost písma ve [stylu textu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Popisky s dalším textem, jako je například popis, by měly být **Písmo prostředí + tučné**.

5. Vnitřní sloupce jsou oddělené pravidlem o velikosti 1 pixelu ve světle šedé.

6. Výchozí odkazy nemají žádné podtržítko. Stavy najetí myší a stisknutí mají změnu barvy a podtržítko.

7. Tlačítka potvrzení (například **OK** / **Zrušit**) sedí v pravém dolním rohu.

### <a name="themed-dialog-layout-examples"></a>Příklady rozložení dialogových oken s motivy
 ![Rozložení dialogového okna s motivem](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801 – h_ThemedDialog")

 **Obrázek 08,01-h: dialogové okno s motivem**

 ![Rozměry dialogových oken s motivem](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801 – i_ThemedDialogDimensions")

 **Obrázek 08,01-i: dialog s motivem – dimenze**

 ![Písma dialogových oken s motivem](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801 – j_ThemedDialogFonts")

 **Obrázek 08,01-j: dialog s motivem – písma**

 ![Barvy dialogových oken s motivem](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801 – k_ThemedDialogColors")

 **Obrázek 08,01-k: dialogové okno s motivem – barvy**

## <a name="see-also"></a>Viz také
 [Vzory aplikací pro dialogová okna sady Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md) [(](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) Windows) [(Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)
