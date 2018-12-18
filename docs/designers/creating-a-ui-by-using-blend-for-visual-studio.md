---
title: Vytvoření uživatelského rozhraní – Blend for Visual Studio
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76743674ef4e92f2ad52be108c1dafb8d942676c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059857"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Vytvoření uživatelského rozhraní pomocí nástroje Blend for Visual Studio

Blend for Visual Studio vám pomůže návrhu na základě XAML Windows a webových aplikací. Nabízí stejné základní XAML návrhové prostředí jako sady Visual Studio a přidá vizuální návrhářské nástroje pro pokročilé úlohy, jako je například animace a chování. Porovnání mezi Blendem a sadou Visual Studio najdete v tématu [návrh XAML v sadě Visual Studio a nástroje Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend for Visual Studio je součástí sady Visual Studio. Instalace v programu Blend, **instalační program sady Visual Studio** zvolit buď **vývoj pro univerzální platformu Windows** nebo **vývoj desktopových aplikací .NET** pracovního vytížení. Obě tyto úlohy zahrnují Blend pro komponentu sady Visual Studio.

![Součásti UPW pracovního vytížení](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Součásti úlohy vývoj desktopových aplikací .NET](media/installer-dotnet-desktop.png)

Pokud začínáte blendu pro Visual Studio, věnujte chvíli seznámení s jedinečné funkce pracovního prostoru. Toto téma přejdete na stručný přehled.

> [!NOTE]
> Prohlídka funkce sdílené návrh například návrhové ploše **Osnova dokumentu** okně a **zařízení** okna, naleznete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Přehled panelu nástrojů

Můžete použít **nástroje** panelu v Blendu pro Visual Studio k vytvoření a úprava objektů ve vaší aplikaci. Vytvoření objektů výběrem nástroj a vykreslení na návrhovou plochu pomocí myši.

![Panel Nástroje](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![Nástroje pro výběr](../designers/media/b1_1.png)|**Nástroje pro výběr** vyberte objekty a cesty.<br /><br /> Použití **přímý výběr** nástroj pro výběr vnořené objekty a segmenty cesty.|![Popisek A](../designers/media/b5_label_a.png)|**Nástroje pro barevný přechod a štětce**|
|![Zobrazení nástroje](../designers/media/b1_2.png)|**Zobrazení nástroje** upravit zobrazení návrhové plochy, například pro posouvání a zvětšování.|![Popisek B](../designers/media/b5_label_b.png)|**Cesta nástroje**|
|![Štětec](../designers/media/b1_3.png)|**Štětec nástroje** pracovat vizuální atributy objektu, například transformace štětce, vykreslování objektu nebo výběrem atributy jednoho objektu a aplikovat je na jiný objekt.|![Popisek C](../designers/media/b5_label_c.png)|**Nástroje pro kreslení tvarů**|
|![Objekt nástroje](../designers/media/b1_4.png)|**Objekt nástroje** nakreslit nejčastěji používané objekty na návrhové ploše, jako je například cesty, tvary, panely rozložení, text a ovládací prvky.|![Popisek D](../designers/media/b5_label_d.png)|**Panely rozložení**|
|![Nástroje pro prostředek](../designers/media/b1_5.png)|**Asset nástroje** přístup **prostředky** panelu a chcete-li zobrazit naposledy použít prostředek z knihovny.|![Popisek E](../designers/media/b5_label_e.png)|**Textových ovládacích prvků**|
|||![Popisek F](../designers/media/b5_label_f.png)|**Běžné ovládací prvky**|

**Podívejte se na krátké video:** ![konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.png) [The nástrojů](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Přehled panelu aktiva

Můžete najít všechny ovládací prvky v **prostředky** panelu, podobně jako **nástrojů** v sadě Visual Studio. Kromě ovládací prvky, najdete všechno, co můžete přidat do vaší návrhovou plochu v **prostředky** panelu, včetně styly, média, chování a efekty.

![Panel prostředků](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Vyhledávací pole** zadejte **hledání** pole filtrovat seznam prostředků.|
|![Režimy mřížka a seznam](../designers/media/b1_2.png)|**Režimy mřížka a seznam** přepínání **režim mřížky** zobrazení a **režim seznamu** zobrazení prostředků.|
|![Kategorie prostředků](../designers/media/b1_3.png)|**Kategorie prostředků** klikněte na tlačítko kategorie nebo podkategorie, chcete-li zobrazit seznam prostředků v dané kategorii.|
|![Styly](../designers/media/b1_4.png)|**Styly** zobrazit všechny styly, které jsou obsaženy ve slovníku prostředků.|
|![Popis](../designers/media/b1_5.png)|**Popis** zobrazení popisu vybrané kategorie nebo podkategorie prostředků.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Prohlídka objekty a časová osa panel

Pomocí tohoto panelu uspořádání objektů na kreslicí ploše a, pokud chcete, animovat je.

![Objekt a časová osa panel v režimu animace](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Zobrazení objektů](../designers/media/b1_1.png)|**Zobrazení objektů** prohlédnout vizuální strom dokumentu. Můžete procházení různými úrovněmi podrobností. Můžete také přidat vrstvy v rámci pokročilejší organizace objektů na návrhové ploše. Tímto způsobem můžete zamknout a skrýt jako skupinu.|
|![Indikátor režimu záznamu](../designers/media/b1_2.png)|**Indikátor režimu záznamu** naleznete v tématu, zda nahráváte změny vlastností na časové ose.|
|![Výběr scénáře](../designers/media/b1_3.png)|**Výběr scénáře** zobrazit seznam scénáře, které jste vytvořili.|
|![Zavřít scénář](../designers/media/b1_4.png)|**Zavřít scénář** zavřete tento scénář, aktuální.|
|![Možnosti scénáře](../designers/media/b1_5.png)|**Možnosti scénáře** opačný duplicitní, vytvoření, odstranění, přejmenování nebo zavření scénáře.|
|![Ovládací prvky přehrávání](../designers/media/b1_6.png)|**Ovládací prvky přehrávání** Navigovat prostřednictvím na časové ose. Můžete také přetahovat ukazatel pozice Procházet (nebo *procházení*) na časové ose.|
|![Vrátit rozsah do](../designers/media/b1_7.png)|**Vrátit rozsah do** oboru zobrazení objektů zpět do předchozího kořenového objektu nebo předchozího oboru. To můžete provést pouze v případě, že jste upravován styl nebo šablonu.|
|![Záznam klíčového snímku](../designers/media/b1_8.png)|**Záznam klíčového snímku** zaznamenat snímek vlastností vybraného objektu v aktuálním okamžiku v čase.|
|![Možnosti přichycení](../designers/media/b1_9.png)|**Možnosti přichycení** nastavení přichycení k časové ose a klíčových snímků, vypněte přichycení k časové ose.|
|![Odemknout uzamčení skrýt zobrazení](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Zobrazit/skrýt**, **Zamknout/odemknout** zobrazit nebo skrýt viditelnosti a zamykání možnosti pro zobrazení objektů.|
|![Poloha ukazatele pozice na časové ose](../designers/media/b1_11.png)|**Poloha ukazatele pozice na časové ose** zobrazit aktuální čas v milisekundách. Rovněž lze pro přechod na konkrétní místo v čase zadat přímo do tohoto pole časovou hodnotu. Přesnost závisí na rozlišení přichycení, nastavte **možnosti přichycení**.|
|![Ukazatel pozice](../designers/media/b1_12.png)|**Ukazatel pozice** určit, ve kterém bodě v čase se animace nachází. Ukazatel pozice lze přetahovat po časové ose a zobrazovat tak náhled animace.|
|![Klíčové snímky nastavené na časové ose](../designers/media/b1_13.png)|**Klíčové snímky nastavené na časové ose** změnit hodnotu vlastnosti v konkrétním bodě v čase.|
|![Změna pořadí objektů](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Změna pořadí objektů** nastavit pořadí zobrazení objektů. Kliknutím na toto tlačítko Uspořádat objekty ve strukturovaném zobrazení podle pořadí vykreslování (zepředu dozadu) nebo podle pořadí kódu (pořadí, v jakém jsou uvedeny v **XAML** zobrazení).|
|![Zvětšení časové osy](../designers/media/b1_15.png)|**Osy** nastavit rozlišení rozsahu časové osy. Přiblížení umožňuje upravovat animaci s více detaily a oddálení zobrazení ukáže větší přehled o tom, co se děje během delšího časového období. Pokud přiblížíte, ale nemůžete nastavit klíčový snímek na pozici v čase, který chcete, ověřte, zda je hodnota rozlišení intervalu klíčových snímků dostatečně vysoká.|
|![Popisek 16](../designers/media/b5_label_16.png)|**Oblast kompozice časové osy** zobrazit časovou osu a přesouvat klíčové snímky nebo pomocí jejich místní nabídky.|

## <a name="tour-of-the-properties-panel"></a>Průvodce panelu Vlastnosti

Pomocí tohoto panelu zobrazení a úprav vlastností objektu. Můžete je také nastavit přímo na návrhové ploše. Pokud tak učiníte, vlastnost změny se projeví v **vlastnosti** panelu.

![Panel vlastností](../designers/media/blend5_properties_panel.png)

**Kategorie** rozbalení a sbalení kategorie vlastnosti. Klikněte na tlačítko **Rozbalit** ![Rozbalit](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) a **sbalit** ![sbalit](../designers/media/b5_collapse_button.png) zobrazíte nebo skryjete kategorie Podrobnosti.

|||
|-|-|
|![Název a typ](../designers/media/b1_1.png)|**Název a typ** zobrazit ikonu, název a typ vybraného objektu.|
|![Uspořádat podle](../designers/media/b1_2.png)|**Uspořádat podle** seřadit vlastnosti abecedně podle názvu, zdrojového nebo kategorie.|
|![Vlastnosti štětce](../designers/media/b1_3.png)|**Vlastnosti štětce** nastavit vizuální vlastnosti pro štětce, jako je například výplňové štětce, Stroke štětce a popředí štětce.|
|![Editor barev](../designers/media/b1_4.png)|**Editor barev** plnou barvu a štětce přechodu.|
|![Výběr barvy](../designers/media/b1_5.png)|**Výběr barvy** výběr barvy.|
|![Barva čipy](../designers/media/b1_6.png)|**Barva čipy** zobrazit počáteční barvu, aktuální barvu a poslední barva|
|![Kapátka](../designers/media/b1_7.png)|**Kapátka** použít barvu libovolného elementu na obrazovce. **Barevné kapátko** je k dispozici, když **štětec jednotné barvy** zaškrtnuto. **Kapátko přechodu** je k dispozici, když **štětce přechodu** zaškrtnuto.|
|![Vlastnosti a události](../designers/media/b1_8.png)|**Vlastnosti a události** nastavit vlastnosti, nebo zvolte události pro vybraný element.|
|![Vyhledávací pole](../designers/media/b1_9.png)|**Vyhledávací pole** hledání vlastnosti. Filtrovat vlastnosti, které jsou zobrazeny tak, že zadáte **hledání** pole.|
|![Editor karty štětce](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Štětec editor karty** vyberte editor štětců. Můžete zvolit **žádný štětec**, **štětec jednotné barvy**, **štětce přechodu**, **dlaždicového štětce**, nebo **štětce prostředků**.|
|![Barvy](../designers/media/b1_11.png)|**Barva prostředky** platí přesně stejnou barvu pro různé vlastnosti. **Prostředky barev** karta obsahuje **místní prostředky** a **systémové prostředky**.|
|![RGB barevný prostor](../designers/media/b1_12.png)|**RGB barevný prostor** změnit barvu nastavením hodnoty **R**, **G**, nebo **B** editory (červená, zelená, modrá) čísla.|
|![Alfa kanál](../designers/media/b1_13.png)|**Alfa kanál** upravte hodnotu alfa pomocí editoru číslo vedle položky **A**.|
|![Převést barvu na prostředek](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Převést barvu na prostředek** převést vybranou barvu na prostředek barvy. Prostředky barev jsou k dispozici, když kliknete na kartě prostředky barev.|
|![](../designers/media/b1_15.png)|**Šestnáctková hodnota** zobrazení šestnáctkové hodnoty barev zobrazí.|
|![Popisek 16](../designers/media/b5_label_16.png)|**Jezdcem přechodu** nabídnuta jen v případě, že je vybraná štětce přechodu.|
|![Zobrazit upřesňující vlastnosti](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Zobrazit upřesňující vlastnosti** zobrazení kategorií vlastností, které jsou méně často používány.|

**Podívejte se na krátké video:** ![konfigurovat nainstalované funkce](../designers/media/bldadminconsoleinitialconfigicon.png) [panel vlastnosti](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Viz také:

- [Vložení ovládacích prvků a změna jejich chování](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animace objektů](../designers/animate-objects-in-xaml-designer.md)
- [Kreslení tvarů a cest](../designers/draw-shapes-and-paths.md)
- [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md)
