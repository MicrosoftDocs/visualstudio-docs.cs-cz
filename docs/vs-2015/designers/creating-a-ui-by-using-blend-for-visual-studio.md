---
title: Vytvoření uživatelského rozhraní pomocí Blendu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a65f42dafca696bfa638964b825410b576d4845
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544284"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Blend pro Visual Studio vám pomůže navrhovat aplikace Windows Desktop, web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)a [Windows Store](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) založené na jazyce XAML. Poskytuje stejné základní prostředí pro návrh XAML jako Visual Studio a přidává vizuální návrháře pro pokročilé úlohy, jako jsou například animace a chování.

 Protože Blend pro Visual Studio je součástí sady Visual Studio, nemusíte si ho stahovat. Je však nutné jej vybrat v instalačním programu sady Visual Studio, aby jej bylo možné nainstalovat do systému.

 Pokud s Blend pro Visual Studio začínáte, měli byste se seznámit s jedinečnými funkcemi pracovního prostoru. Toto téma vás provede rychlou prohlídku.

> [!NOTE]
> Chcete-li prohlídku funkcí sdíleného návrhu, jako je například návrhová plocha, okno Osnova dokumentu a okno zařízení, přečtěte si téma [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **V tomto tématu**:

- [Prohlídka panelu nástrojů](#Tools)

- [Prohlídka panelu aktiva](#Assets)

- [Prohlídka panelu Objekty a časová osa](#Objects)

- [Prohlídka panelu vlastností](#Properties)

## <a name="tour-of-the-tools-panel"></a><a name="Tools"></a>Prohlídka panelu nástrojů
 Pomocí panelu **nástroje** v Blend pro Visual Studio můžete vytvářet a upravovat objekty v aplikaci. Objekty vytvoříte tak, že vyberete nástroj a nakreslíte na návrhovou plochu pomocí myši.

 ![Panel Nástroje](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|Image|Typ nástroje|Image|Typ nástroje|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Nástroje pro výběr** Vyberte možnost objekty a cesty.<br /><br /> Pomocí nástroje **přímý výběr** vyberte vnořené objekty a segmenty cest.|![Popisek A](../designers/media/b5-label-a.png "b5_label_A")|**Nástroje přechodu a štětce**|
|![](../designers/media/b1-2.png "B1_2")|**Zobrazit nástroje** Upravte zobrazení návrhové plochy, například pro posouvání a zvětšování.|![Popisek B](../designers/media/b5-label-b.png "b5_label_B")|**Nástroje cest**|
|![](../designers/media/b1-3.png "B1_3")|**Nástroje štětce** Pracujte s vizuálními atributy objektu, jako je například transformace štětce, malování objektu nebo výběr atributů jednoho objektu, aby byly použity pro jiný objekt.|![Popisek jazyka C](../designers/media/b5-label-c.png "b5_label_C")|**Nástroje tvarů**|
|![](../designers/media/b1-4.png "B1_4")|**Nástroje objektů** Nakreslete nejběžnější objekty na návrhové ploše, například cesty, tvary, panely rozložení, text a ovládací prvky.|![Popisek D](../designers/media/b5-label-d.png "b5_label_D")|**Panely rozložení**|
|![](../designers/media/b1-5.png "B1_5")|**Nástroje assetu** Přístup k panelu **aktiva** a zobrazení naposledy použitého prostředku z knihovny.|![Popisek E](../designers/media/b5-label-e.png "b5_label_E")|**Textové ovládací prvky**|
|||![Popisek F](../designers/media/b5-label-f.png "b5_label_F")|**Běžné ovládací prvky**|

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [na panelu nástrojů](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a><a name="Assets"></a>Prohlídka panelu aktiva
 Všechny ovládací prvky můžete najít na panelu **aktiva** , podobně jako **panel nástrojů v sadě** Visual Studio. Kromě ovládacích prvků najdete všechno, co můžete přidat na návrhovou plochu na panelu **aktiva** , včetně stylů, médií, chování a efektů.

 ![Panel prostředků](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|Image|Popis|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Vyhledávací pole** Chcete-li filtrovat seznam assetů, zadejte do **vyhledávacího** pole.|
|![](../designers/media/b1-2.png "B1_2")|**Režim mřížky a režim seznamu** Přepínání mezi zobrazením **režimu mřížky** a zobrazením **režimu seznamu** prostředků|
|![](../designers/media/b1-3.png "B1_3")|**Kategorie prostředků** Kliknutím na kategorii nebo podkategorii zobrazíte seznam assetů v této kategorii.|
|![](../designers/media/b1-4.png "B1_4")|**Styly** Zobrazit všechny styly, které jsou obsaženy ve slovníku prostředků.|
|![](../designers/media/b1-5.png "B1_5")|**Popis** Zobrazí popis vybrané kategorie assetů nebo podkategorie.|

## <a name="tour-of-the-objects-and-timeline-panel"></a><a name="Objects"></a>Prohlídka panelu Objekty a časová osa
 Tento panel slouží k uspořádání objektů na návrhové ploše a v případě, že je chcete animovat.

 ![Panel objekt a časová osa v režimu animace](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|Image|Popis|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Zobrazení objektů** Zobrazení vizuálního stromu dokumentu Můžete přejít k podrobnostem na různé úrovně podrobností. Můžete také přidat vrstvy pro další uspořádání objektů na návrhové ploše. Tímto způsobem je můžete uzamknout a skrýt jako skupinu.|
|![](../designers/media/b1-2.png "B1_2")|**Indikátor režimu záznamu** Podívejte se, jestli se na časové ose zaznamenávají změny vlastností.|
|![](../designers/media/b1-3.png "B1_3")|**Výběr scénářů** Zobrazit seznam scénářů, které jste vytvořili.|
|![](../designers/media/b1-4.png "B1_4")|**Zavřít scénář** Zavře aktuální scénář.|
|![](../designers/media/b1-5.png "B1_5")|**Možnosti scénáře** Vytvoření, duplikování, vrácení, odstranění, přejmenování nebo zavření scénáře.|
|![](../designers/media/b1-6.png "B1_6")|**Ovládací prvky přehrávání** Procházejte časovou osou. Můžete také přetáhnout přehrávací hlavu a procházet časovou osu *(nebo ji*z ní opustit).|
|![](../designers/media/b1-7.png "B1_7")|**Vrátit rozsah do** Rozsah zobrazení objektů vraťte se k předchozímu kořenovému objektu nebo předchozímu oboru. To lze provést pouze v případě, že upravujete styl nebo šablonu.|
|![](../designers/media/b1-8.png "B1_8")|**Záznam klíčového snímku** Zaznamená snímek vlastností vybraného objektu v aktuálním bodu v čase.|
|![](../designers/media/b1-9.png "B1_9")|**Možnosti přichycení** Nastaví přichycení k časové ose, rozlišení přichycení a vypnutí přichycení k časové ose.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Zobrazit/skrýt**, **Uzamknout/Odemknout** zobrazit nebo skrýt možnosti viditelnosti a zamykání pro zobrazení objektů.|
|![](../designers/media/b1-11.png "B1_11")|**Pozice přehrávací pozice na časové ose** Zobrazí aktuální čas v milisekundách. Rovněž lze pro přechod na konkrétní místo v čase zadat přímo do tohoto pole časovou hodnotu. Přesnost závisí na rozlišení nastaveném v **možnostech přichycení**.|
|![](../designers/media/b1-12.png "B1_12")|**Přehrávací hlava** Určete, jaký bod v čase je animace zapnuta. Ukazatel pozice lze přetahovat po časové ose a zobrazovat tak náhled animace.|
|![](../designers/media/b1-13.png "B1_13")|**Klíčové snímky nastavené na časových osách** Změna hodnoty vlastnosti v určitém časovém okamžiku.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Změna pořadí objektů** Nastavte pořadí zobrazení objektů. Klikněte na toto tlačítko, chcete-li uspořádat objekty v zobrazení struktury podle pořadí Z (front-end) nebo podle pořadí značek (pořadí, ve kterém se zobrazují v zobrazení **XAML** ).|
|![](../designers/media/b1-15.png "B1_15")|**Přiblížení časové osy** Nastavte rozlišení přiblížení časové osy. Přiblížení umožňuje upravovat animaci s více detaily a oddálení zobrazení ukáže větší přehled o tom, co se děje během delšího časového období. Pokud přiblížíte, ale nemůžete nastavit klíčový snímek na pozici v čase, který chcete, ověřte, zda je hodnota rozlišení intervalu klíčových snímků dostatečně vysoká.|
|![Popisek 16](../designers/media/b5-label-16.png "b5_label_16")|**Oblast kompozice časové osy** Zobrazte časovou osu a přesuňte klíčové snímky kolem jejich přetažením nebo pomocí místních nabídek.|

## <a name="tour-of-the-properties-panel"></a><a name="Properties"></a>Prohlídka panelu vlastností
 Pomocí tohoto panelu můžete zobrazit a upravit vlastnosti objektu. Můžete je také nastavit přímo na návrhové ploše. Pokud to uděláte, změny vlastností se projeví na panelu **vlastnosti** .

 ![Panel vlastností](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategorie** Rozbalí a sbalí kategorie vlastností. Kliknutím na **Rozbalit** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") a **sbalit** ![sbalit](../designers/media/b5-collapse-button.png "b5_collapse_button") zobrazíte nebo skryjete podrobnosti kategorie.

|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Název a typ** Zobrazí ikonu, název a typ vybraného objektu.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Uspořádat podle** Uspořádejte vlastnosti abecedně podle názvu, zdroje nebo kategorie.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Vlastnosti štětce** Nastavte vlastnosti vizuálu pro štětce, jako je výplň štětce, štětec tahu a štětec popředí.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Editor barev** Používá se pro jednobarevné barvy a štětce přechodu.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Výběr barvy** Vyberte barvu.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Čipy barev** Zobrazení počáteční barvy, aktuální barvy a poslední barvy                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Kapátka** Použijte barvu libovolného prvku na obrazovce. **Kapátko barvy** je k dispozici, když je vybrána možnost **plná barva štětce** . **Kapátko přechodu** je k dispozici při výběru **štětce přechodu** . |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Vlastnosti a události** Nastavte vlastnosti nebo vyberte události pro vybraný element.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Vyhledávací pole** Vyhledejte vlastnosti. Filtrovat vlastnosti, které se zobrazí, zadáním do **vyhledávacího** pole.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Karty editoru štětce** Slouží k výběru editoru štětce. Můžete zvolit možnost **bez štětce**, **plných barev štětců**, **barevného štětce**, **štětce dlaždic**nebo **prostředku štětce**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Prostředky barev** Použijte stejnou barvu u různých vlastností. Karta **barvy prostředků** zahrnuje **místní prostředky** a **systémové prostředky**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **Barevný prostor RGB** Upravte barvu úpravou hodnot pro editory **R**, **G**nebo **B** (červené, zelené, modré) čísel.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Kanál alfa** Upravte hodnotu alfa pomocí editoru čísel **vedle.**                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Převést barvu na prostředek** Převést vybranou barvu na barevný zdroj. Prostředky barev jsou k dispozici po kliknutí na kartu barvy prostředků.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Šestnáctková hodnota** Zobrazení hexadecimální hodnoty zobrazené barvy.                                                                                 |
|                     ![Popisek 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Posuvník přechodu** Zobrazí se pouze v případě, že je vybrán štětec přechodu.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Zobrazit upřesňující vlastnosti** Umožňuje zobrazit kategorie vlastností, které se používají méně často.                                                                      |

 **Podívejte se na krátké video:** ![Konfigurace nainstalovaných vlastností funkcí](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [panel](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Viz také
 [Vložení ovládacích prvků a změna jejich chování](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [animace objekty](../designers/animate-objects-in-xaml-designer.md) [kreslení tvarů a cest](../designers/draw-shapes-and-paths.md) [návrh XAML v aplikaci Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md)
