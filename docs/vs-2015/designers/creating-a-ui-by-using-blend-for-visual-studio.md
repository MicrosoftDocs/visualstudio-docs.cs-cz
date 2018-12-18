---
title: Vytvoření uživatelského rozhraní pomocí nástroje Blend
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f77fba9ed184d5def85aa7ca260b7c552dddbfd1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054538"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Blend for Visual Studio vám pomůže navrhnout založené na XAML Windows desktopových, webových, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx), a [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) aplikace. Nabízí stejné základní XAML návrhové prostředí jako sady Visual Studio a přidá vizuální návrhářské nástroje pro pokročilé úlohy, jako je například animace a chování.

 Blend for Visual Studio je zahrnutý jako součást sady Visual Studio, nemusíte si ho stáhnout. Musíte však vybrat v instalačním programu sady Visual Studio pro něj chcete nainstalovat do vašeho systému.

 Pokud začínáte blendu pro Visual Studio, věnujte chvíli seznámení s jedinečné funkce pracovního prostoru. Toto téma přejdete na stručný přehled.

> [!NOTE]
>  Prohlédnete si funkce sdílené návrh například návrhovou plochu, Osnova dokumentu – okno a okno zařízení, najdete v článku [vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **V tomto tématu**:

-   [Přehled panelu nástrojů](#Tools)

-   [Přehled panelu aktiva](#Assets)

-   [Prohlídka objekty a časová osa panel](#Objects)

-   [Průvodce panelu Vlastnosti](#Properties)

##  <a name="Tools"></a> Přehled panelu nástrojů
 Můžete použít **nástroje** panelu v Blendu pro Visual Studio k vytvoření a úprava objektů ve vaší aplikaci. Vytvoření objektů výběrem nástroj a vykreslení na návrhovou plochu pomocí myši.

 ![Panel nástrojů](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Nástroje pro výběr** vyberte objekty a cesty.<br /><br /> Použití **přímý výběr** nástroj pro výběr vnořené objekty a segmenty cesty.|![Popisek A](../designers/media/b5-label-a.png "b5_label_A")|**Nástroje pro barevný přechod a štětce**|
|![](../designers/media/b1-2.png "B1_2")|**Zobrazení nástroje** upravit zobrazení návrhové plochy, například pro posouvání a zvětšování.|![Callout B](../designers/media/b5-label-b.png "b5_label_B")|**Cesta nástroje**|
|![](../designers/media/b1-3.png "B1_3")|**Štětec nástroje** pracovat vizuální atributy objektu, například transformace štětce, vykreslování objektu nebo výběrem atributy jednoho objektu a aplikovat je na jiný objekt.|![Callout C](../designers/media/b5-label-c.png "b5_label_C")|**Nástroje pro kreslení tvarů**|
|![](../designers/media/b1-4.png "B1_4")|**Objekt nástroje** nakreslit nejčastěji používané objekty na návrhové ploše, jako je například cesty, tvary, panely rozložení, text a ovládací prvky.|![Popisek D](../designers/media/b5-label-d.png "b5_label_D")|**Panely rozložení**|
|![](../designers/media/b1-5.png "B1_5")|**Asset nástroje** přístup **prostředky** panelu a chcete-li zobrazit naposledy použít prostředek z knihovny.|![Popisek E](../designers/media/b5-label-e.png "b5_label_E")|**Textových ovládacích prvků**|
|||![Callout F](../designers/media/b5-label-f.png "b5_label_F")|**Běžné ovládací prvky**|

 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [The nástrojů](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

##  <a name="Assets"></a> Přehled panelu aktiva
 Můžete najít všechny ovládací prvky v **prostředky** panelu, podobně jako **nástrojů** v sadě Visual Studio. Kromě ovládací prvky, najdete všechno, co můžete přidat do vaší návrhovou plochu v **prostředky** panelu, včetně styly, média, chování a efekty.

 ![Panel aktiva](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Vyhledávací pole** zadejte **hledání** pole filtrovat seznam prostředků.|
|![](../designers/media/b1-2.png "B1_2")|**Režimy mřížka a seznam** přepínání **režim mřížky** zobrazení a **režim seznamu** zobrazení prostředků.|
|![](../designers/media/b1-3.png "B1_3")|**Kategorie prostředků** klikněte na tlačítko kategorie nebo podkategorie, chcete-li zobrazit seznam prostředků v dané kategorii.|
|![](../designers/media/b1-4.png "B1_4")|**Styly** zobrazit všechny styly, které jsou obsaženy ve slovníku prostředků.|
|![](../designers/media/b1-5.png "B1_5")|**Popis** zobrazení popisu vybrané kategorie nebo podkategorie prostředků.|

##  <a name="Objects"></a> Prohlídka objekty a časová osa panel
 Pomocí tohoto panelu uspořádání objektů na kreslicí ploše a, pokud chcete, animovat je.

 ![Objekt a časová osa panel v režimu animace](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Zobrazení objektů** prohlédnout vizuální strom dokumentu. Můžete procházení různými úrovněmi podrobností. Můžete také přidat vrstvy v rámci pokročilejší organizace objektů na návrhové ploše. Tímto způsobem můžete zamknout a skrýt jako skupinu.|
|![](../designers/media/b1-2.png "B1_2")|**Indikátor režimu záznamu** naleznete v tématu, zda nahráváte změny vlastností na časové ose.|
|![](../designers/media/b1-3.png "B1_3")|**Výběr scénáře** zobrazit seznam scénáře, které jste vytvořili.|
|![](../designers/media/b1-4.png "B1_4")|**Zavřít scénář** zavřete tento scénář, aktuální.|
|![](../designers/media/b1-5.png "B1_5")|**Možnosti scénáře** opačný duplicitní, vytvoření, odstranění, přejmenování nebo zavření scénáře.|
|![](../designers/media/b1-6.png "B1_6")|**Ovládací prvky přehrávání** Navigovat prostřednictvím na časové ose. Můžete také přetahovat ukazatel pozice Procházet (nebo *procházení*) na časové ose.|
|![](../designers/media/b1-7.png "B1_7")|**Vrátit rozsah do** oboru zobrazení objektů zpět do předchozího kořenového objektu nebo předchozího oboru. To můžete provést pouze v případě, že jste upravován styl nebo šablonu.|
|![](../designers/media/b1-8.png "B1_8")|**Záznam klíčového snímku** zaznamenat snímek vlastností vybraného objektu v aktuálním okamžiku v čase.|
|![](../designers/media/b1-9.png "B1_9")|**Možnosti přichycení** nastavení přichycení k časové ose a klíčových snímků, vypněte přichycení k časové ose.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Zobrazit/skrýt**, **Zamknout/odemknout** zobrazit nebo skrýt viditelnosti a zamykání možnosti pro zobrazení objektů.|
|![](../designers/media/b1-11.png "B1_11")|**Poloha ukazatele pozice na časové ose** zobrazit aktuální čas v milisekundách. Rovněž lze pro přechod na konkrétní místo v čase zadat přímo do tohoto pole časovou hodnotu. Přesnost závisí na rozlišení přichycení, nastavte **možnosti přichycení**.|
|![](../designers/media/b1-12.png "B1_12")|**Ukazatel pozice** určit, ve kterém bodě v čase se animace nachází. Ukazatel pozice lze přetahovat po časové ose a zobrazovat tak náhled animace.|
|![](../designers/media/b1-13.png "B1_13")|**Klíčové snímky nastavené na časové ose** změnit hodnotu vlastnosti v konkrétním bodě v čase.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Změna pořadí objektů** nastavit pořadí zobrazení objektů. Kliknutím na toto tlačítko Uspořádat objekty ve strukturovaném zobrazení podle pořadí vykreslování (zepředu dozadu) nebo podle pořadí kódu (pořadí, v jakém jsou uvedeny v **XAML** zobrazení).|
|![](../designers/media/b1-15.png "B1_15")|**Osy** nastavit rozlišení rozsahu časové osy. Přiblížení umožňuje upravovat animaci s více detaily a oddálení zobrazení ukáže větší přehled o tom, co se děje během delšího časového období. Pokud přiblížíte, ale nemůžete nastavit klíčový snímek na pozici v čase, který chcete, ověřte, zda je hodnota rozlišení intervalu klíčových snímků dostatečně vysoká.|
|![Popisek 16](../designers/media/b5-label-16.png "b5_label_16")|**Oblast kompozice časové osy** zobrazit časovou osu a přesouvat klíčové snímky nebo pomocí jejich místní nabídky.|

##  <a name="Properties"></a> Průvodce panelu Vlastnosti
 Pomocí tohoto panelu zobrazení a úprav vlastností objektu. Můžete je také nastavit přímo na návrhové ploše. Pokud tak učiníte, vlastnost změny se projeví v **vlastnosti** panelu.

 ![Panel vlastnosti](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategorie** rozbalení a sbalení kategorie vlastnosti. Klikněte na tlačítko **rozbalte** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") a **sbalit** ![sbalit](../designers/media/b5-collapse-button.png "b5_collapse_button") zobrazíte nebo skryjete kategorie Podrobnosti.


|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Název a typ** zobrazit ikonu, název a typ vybraného objektu.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Uspořádat podle** seřadit vlastnosti abecedně podle názvu, zdrojového nebo kategorie.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Vlastnosti štětce** nastavit vizuální vlastnosti pro štětce, jako je například výplňové štětce, Stroke štětce a popředí štětce.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Editor barev** plnou barvu a štětce přechodu.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Výběr barvy** výběr barvy.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Barva čipy** zobrazit počáteční barvu, aktuální barvu a poslední barva                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Kapátka** použít barvu libovolného elementu na obrazovce. **Barevné kapátko** je k dispozici, když **štětec jednotné barvy** zaškrtnuto. **Kapátko přechodu** je k dispozici, když **štětce přechodu** zaškrtnuto. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Vlastnosti a události** nastavit vlastnosti, nebo zvolte události pro vybraný element.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Vyhledávací pole** hledání vlastnosti. Filtrovat vlastnosti, které jsou zobrazeny tak, že zadáte **hledání** pole.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Štětec editor karty** vyberte editor štětců. Můžete zvolit **žádný štětec**, **štětec jednotné barvy**, **štětce přechodu**, **dlaždicového štětce**, nebo **štětce prostředků**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Barva prostředky** platí přesně stejnou barvu pro různé vlastnosti. **Prostředky barev** karta obsahuje **místní prostředky** a **systémové prostředky**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **RGB barevný prostor** změnit barvu nastavením hodnoty **R**, **G**, nebo **B** editory (červená, zelená, modrá) čísla.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Alfa kanál** upravte hodnotu alfa pomocí editoru číslo vedle položky **A**.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Převést barvu na prostředek** převést vybranou barvu na prostředek barvy. Prostředky barev jsou k dispozici, když kliknete na kartě prostředky barev.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Šestnáctková hodnota** zobrazení šestnáctkové hodnoty barev zobrazí.                                                                                 |
|                     ![Popisek 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Jezdcem přechodu** nabídnuta jen v případě, že je vybraná štětce přechodu.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Zobrazit upřesňující vlastnosti** zobrazení kategorií vlastností, které jsou méně často používány.                                                                      |

 **Podívejte se na krátké video:** ![nakonfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [panel vlastnosti](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Viz také
 [Vložení ovládacích prvků a změna jejich chování](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [animace objektů](../designers/animate-objects-in-xaml-designer.md) [kreslení tvarů a cest](../designers/draw-shapes-and-paths.md) [návrh XAML v sadě Visual Studio a nástroje Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
