---
title: Práce s elementy v Návrháři XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 47f6a975488adacbeffbdf0f04771131cd9a0ff9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926940"
---
# <a name="working-with-elements-in-xaml-designer"></a>Práce s elementy v Návrháři XAML
Můžete přidat prvky – ovládací prvky, rozložení a tvary – do vaší aplikace v XAML, v kódu nebo s použitím návrháře XAML. Toto téma popisuje, jak pracovat s elementy v Návrháři XAML v sadě Visual Studio nebo nástroje Blend for Visual Studio.

## <a name="adding-an-element-to-a-layout"></a>Přidat element do rozložení
 *Rozložení* je proces pro změnu velikosti a rozmístění prvků v uživatelském rozhraní. Pokud chcete umístit vizuálních prvků, je nutné umístit je v rozložení [Panel](/uwp/api/Windows.UI.Xaml.Controls.Panel). A `Panel` má vlastnost podřízené, což je kolekce z [FrameworkElement](/uwp/api/Windows.UI.Xaml.FrameworkElement) typy. Můžete použít různé `Panel` podřízené prvky, jako například [plátna](/uwp/api/Windows.UI.Xaml.Controls.Canvas), [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel), a [mřížky](/uwp/api/Windows.UI.Xaml.Controls.Grid), která bude sloužit jako kontejnery rozložení a do pozice a uspořádání prvků na stránce.

 Ve výchozím nastavení `Grid` panel slouží jako kontejner rozložení nejvyšší úrovně v rámci stránky nebo formuláře. Můžete přidat panely rozložení, ovládacích prvků nebo jiných prvků v rámci rozložení stránky nejvyšší úrovně.

#### <a name="to-add-an-element-to-a-layout"></a>Chcete-li přidat element do rozložení

-   V Návrháři XAML proveďte jednu z následujících akcí:

    -   Klikněte dvakrát na prvek v **nástrojů** (nebo vybrat prvek v panelu nástrojů a stisknutím klávesy **Enter**).

    -   Přetáhněte element z **nástrojů** na návrhovou plochu.

    -   V **nástrojů**, vyberte jeden z kreslících nástrojů (například [Elipsa](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) nebo [obdélník](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)) a následně nakreslete prvek v panelu aktivní.

## <a name="changing-the-layering-order-of-elements"></a>Změna pořadí vrstev elementů
 Pokud existují dva prvky na návrhovou plochu v Návrháři XAML, jeden prvek se zobrazí před jiným v pořadí vrstev. V dolní části Seznam prvků, osnovy dokumentu okna je nejvíce vpředu prvek (s výjimkou, kdy **ZIndex** je nastavena vlastnost pro daný element). Při vkládání elementů do stránky, formuláře nebo kontejner rozložení, element automaticky umístěn před další prvky v elementu aktivní kontejner. Chcete-li změnit pořadí prvků, můžete použít **pořadí** příkazy nebo přetáhnout prvky v rámci stromů objektů v okně osnovy dokumentu.

#### <a name="to-change-the-layering-order"></a>Chcete-li změnit pořadí vrstev

- Proveďte jednu z těchto akcí:

  - V **Osnova dokumentu** okně elementy přetáhnout nebo dolů lze vytvořit požadované pořadí vrstev.

  - Klikněte pravým tlačítkem myši na prvek v okně Osnova dokumentu nebo na návrhovou plochu, pro kterou chcete změnit pořadí vrstev, přejděte na **pořadí**a pak klikněte na jednu z následujících akcí:

    -   **Přenést do popředí** elementu uvést úplně přenést do popředí pořadí.

    -   **Přenést blíž** vám elementu vpřed o jednu úroveň v pořadí.

    -   **Přenést dál** odeslat zpět o jednu úroveň element v pořadí.

    -   **Přenést do pozadí** odesílat elementu úplně přenést do pozadí pořadí.

    Změnit **ZIndex** vlastnost **rozložení** oddíl v okně Vlastnosti. Pro překrývající se prvky, **ZIndex** vlastnost má přednost před pořadí prvků, které jsou zobrazeny v okně Osnova dokumentu. Element, který má vyšší **ZIndex** hodnota se zobrazí v popředí při prvky překrývat.

## <a name="changing-the-alignment-of-an-element"></a>Změna zarovnání prvku
 Pomocí příkazů nabídky nebo přetažením prvky k zarovnávacím čárám je možné zarovnat elementy v návrhové ploše.

 A *snapline –* je vizuální upozornění, která pomáhá zarovnat element vzhledem k další prvky v aplikaci.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Chcete-li zarovnat nejmíň dva elementy pomocí příkazů nabídky

1.  Vyberte prvky, které chcete, aby bylo v souladu. Můžete vybrat více než jeden element stisknutím a podržením **Ctrl** klávesu vybrat elementy.

2.  Vyberte jednu z následujících vlastností v rámci **HorizontalAlignment** v **rozložení** části okna vlastnosti: **vlevo**, **Center**, **Vpravo**, nebo **Stretch**.

3.  Vyberte jednu z následujících vlastností v rámci **VerticalAlignment** v **rozložení** části okna vlastnosti: **horní**, **Center**, **Dolní**, nebo **Stretch**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Chcete-li zarovnat dva nebo více prvků pomocí zarovnávacích čar

-   V Návrháři XAML, v rozložení, který obsahuje alespoň dva prvky přetáhněte nebo jeden z elementů velikost tak, aby na hraničních zařízeních je v souladu s jiný element.

     Když jsou zarovnány okrajů, *hranicích zarovnání* se zobrazí k označení zarovnání. Hranicích zarovnání je red přerušovanou čáru. Hranice pro zarovnání se zobrazí pouze tehdy, když **přichycování k zarovnávacím čárám** je povolená. Pro ilustraci na návrhovou plochu, zobrazující hranici zarovnání, najdete v článku [vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-an-elements-margins"></a>Změna okrajů elementu
 Okraje v Návrháři XAML určují velikost volného místa okolo prvek na návrhovou plochu. Například mohou také určovat velikost místa mezi vnějšími hranami elementu a hranice `Grid` panel, který obsahuje element. Mohou také také určovat velikost místa mezi prvky, které jsou součástí `StackPanel`.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Chcete-li změnit okrajů elementu v okně Vlastnosti

1.  Vyberte prvek, jehož okraje, kterou chcete změnit.

2.  V části **rozložení** v okně Vlastnosti změňte hodnotu (v pixelech nebo jednotkách nezávislých na zařízení, které jsou přibližně 1/96 palce) pro některý z **okraj** vlastnosti (**horní**, **Vlevo**, **vpravo**, nebo **dolní**).

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Chcete-li změnit okrajů elementu v návrhové ploše

-   Změna okrajů elementu vzhledem k jeho kontejner rozložení, klikněte na tlačítko *doplňků pro úpravy okrajů* , který se kolem elementu v návrhové ploše, když elementu je vybraná a není kontejner rozložení. Obrázek, na kterém doplňků pro úpravy rozpětí, naleznete v tématu [vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Pokud je okrajů otevřen, svisle nebo vodorovně, není tento okraj nastaven. Pokud okrajů zavřen, je okraj nastaven.

     Když otevřete okrajů a není nastavená na opačnou okraj, je opačné okraj nastaven na správnou hodnotu podle umístění prvku v návrhové ploše. Opačné okrajů, jako **vlevo** a **vpravo** okrajů, alespoň jednu vlastnost je vždycky nastavený.

    > [!IMPORTANT]
    >  Prvky umístit do některé kontejnery rozložení, jako například <xref:Windows.UI.Xaml.Controls.Canvas>, nemají doplňků pro úpravy rozpětí. Umístí prvky uvnitř <xref:Windows.UI.Xaml.Controls.StackPanel> mají doplňků pro úpravy rozpětí pro buď levého a pravého okraje nebo horní a dolní okraj, v závislosti na orientaci ovládacího prvku `StackPanel`.

## <a name="grouping-and-ungrouping-elements"></a>Seskupování a oddělování elementů
 Seskupení dvou nebo více prvků v Návrháři XAML vytvoří nový kontejner rozložení a umístí tyto prvky v rámci tohoto kontejneru. Umístěním dvou nebo více prvků společně v kontejneru rozložení umožňuje snadno vybrat, přesun a transformaci skupiny, jako kdyby byly prvky v dané skupině jeden element. Seskupení je také užitečné pro identifikaci prvků, které se vztahují k sobě navzájem nějakým způsobem, jako je například tlačítka, která tvoří prvek navigace. Když oddělíte prvků, je jednoduše provedeno odstranění kontejner rozložení, který obsahoval prvky.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Které prvky do nového kontejneru rozložení

1.  Vyberte prvky, které chcete seskupit. (Pokud chcete vybrat více prvků, stiskněte a podržte **Ctrl** klávesu klikněte na ně.)

2.  Klikněte pravým tlačítkem na vybrané elementy, přejděte na **seskupit do**a potom klikněte na typ kontejner rozložení, ve kterém chcete bude skupina nacházet.

    > [!TIP]
    >  Pokud vyberete <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, nebo <xref:Windows.UI.Xaml.Controls.ScrollViewer> k seskupení elementů, prvky jsou umístěny v novém <xref:Windows.UI.Xaml.Controls.Grid> panelu v rámci <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, nebo <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Pokud oddělíte prvky v jednom z těchto kontejnerů rozložení, pouze <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, nebo <xref:Windows.UI.Xaml.Controls.ScrollViewer> se odstraní a <xref:Windows.UI.Xaml.Controls.Grid> panelu zůstane. Chcete-li odstranit `Grid` panelu, znovu zrušit seskupení elementů.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Zrušit seskupení elementů a odstranit rozložení

- Klikněte pravým tlačítkem na skupinu, kterou chcete oddělit a klikněte na tlačítko **oddělit**.

  Můžete taky seskupit nebo oddělit prvků tak, že pravým tlačítkem myši na vybrané položky v okně Osnova dokumentu a kliknutím na **seskupit do** nebo **oddělit**.

## <a name="resetting-the-element-layout"></a>Resetování rozložení elementu
 Pomocí příkazů resetovat rozložení můžete obnovit výchozí hodnoty pro specifické rozložení vlastností elementu. Pomocí tohoto příkazu můžete obnovit okraj, zarovnání, šířku, výšku a velikost elementu, samostatně nebo společně.

#### <a name="to-reset-the-element-layout"></a>Chcete-li obnovit rozložení elementu

-   V okně Osnova dokumentu nebo návrhové ploše, klikněte pravým tlačítkem na elementu, zvolte **rozložení** > **resetování** *PropertyName*, kde  *Vlastnost PropertyName* je vlastnost, kterou chcete obnovit (nebo zvolte **rozložení** > **Obnovit vše** resetovat všechny vlastnosti rozložení pro element).

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
