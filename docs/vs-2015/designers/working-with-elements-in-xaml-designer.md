---
title: Práce s prvky v Návrhář XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 483023fbd28da26d9967dd2d88bc37748d00f088
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663990"
---
# <a name="working-with-elements-in-xaml-designer"></a>Práce s elementy v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přidat prvky – ovládací prvky, rozložení a tvary – do aplikace v jazyce XAML, v kódu nebo pomocí Návrhář XAML. Toto téma popisuje, jak pracovat s prvky v Návrhář XAML v aplikaci Visual Studio nebo Blend pro Visual Studio.

## <a name="adding-an-element-to-a-layout"></a>Přidání elementu do rozložení
 *Rozložení* je proces změny velikosti a umístění prvků v uživatelském rozhraní. Chcete-li umístit vizuální prvky, je nutné je umístit do [panelu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx)rozložení. `Panel`Má podřízenou vlastnost, která je kolekcí typů [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706.aspx) . Můžete použít různé  `Panel` podřízené prvky, jako je [plátno](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx)a [Grid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), k obsluze jako kontejnerů rozložení a k umístění a uspořádání prvků na stránce.

 Ve výchozím nastavení `Grid` je panel použit jako kontejner rozložení nejvyšší úrovně v rámci stránky nebo formuláře. Můžete přidat panely rozložení, ovládací prvky nebo jiné prvky v rozložení stránky nejvyšší úrovně.

#### <a name="to-add-an-element-to-a-layout"></a>Přidání elementu do rozložení

- V Návrhář XAML proveďte jednu z následujících akcí:

  - Dvakrát klikněte na prvek v **sadě nástrojů** (nebo vyberte element v sadě nástrojů a stiskněte klávesu ENTER).

  - Přetáhněte element ze **sady nástrojů** na návrhovou plochu.

  - V **sadě nástrojů**vyberte jeden z nástrojů pro kreslení (například [elipsa](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) nebo [obdélník](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)) a potom nakreslete prvek na aktivním panelu.

## <a name="changing-the-layering-order-of-elements"></a>Změna pořadí vrstvení prvků
 Pokud jsou na návrhové ploše dva prvky v Návrhář XAML, jeden prvek se zobrazí před druhým v pořadí vrstev. V dolní části seznamu prvků v okně Osnova dokumentu je přední prvek elementu (kromě případu, kdy je nastavena vlastnost **ZIndex** elementu). Při vložení elementu do kontejneru stránky, formuláře nebo rozložení, je prvek automaticky umístěn před další prvky v rámci aktivního prvku kontejneru. Chcete-li změnit pořadí prvků, lze použít příkazy **Order** nebo přetáhnout prvky ve stromové struktuře objektů v okně Osnova dokumentu.

#### <a name="to-change-the-layering-order"></a>Změna pořadí vrstvení

- Proveďte jednu z následujících akcí:

  - V okně **Osnova dokumentu** přetáhněte prvky nahoru nebo dolů a vytvořte požadované pořadí vrstev.

  - Klikněte pravým tlačítkem myši na prvek v okně Osnova dokumentu nebo na návrhové ploše, pro kterou chcete změnit pořadí vrstev, přejděte na příkaz **pořadí**a potom klikněte na jednu z následujících možností:

    - **Přeneste dopředu** pro převedení prvku na začátek objednávky.

    - **Přenést** nahoru, aby prvek předali jednu úroveň v pořadí.

    - **Přenést dozadu** pro odeslání elementu zpět o jednu úroveň v pořadí.

    - **Přenést do back** pro odeslání elementu všem způsobem na zadní stranu objednávky.

    Změňte vlastnost **ZIndex** v části **rozložení** v okno Vlastnosti. U překrývajících se prvků má vlastnost **ZIndex** přednost před pořadím prvků zobrazených v okně Osnova dokumentu. Prvek, který má nižší hodnotu **ZIndex** , se zobrazí v popředí při překrytí prvků.

## <a name="changing-the-alignment-of-an-element"></a>Změna zarovnání elementu
 Prvky můžete zarovnat na návrhové ploše pomocí příkazů nabídky nebo přetažením prvků do zarovnávacím čárám.

 *Snapline* je vizuální znázornění, které vám pomůže zarovnat prvek relativně k ostatním prvkům v aplikaci.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Zarovnání dvou nebo více prvků pomocí příkazů nabídky

1. Vyberte prvky, které chcete zarovnat. Stisknutím a podržením klávesy CTRL můžete vybrat více než jeden prvek a zároveň vybrat prvky.

2. Vyberte jednu z následujících vlastností v části **HorizontalAlignment** v části **rozložení** okno Vlastnosti: **Left**, **Center**, **Right**nebo **Stretch**.

3. Vyberte jednu z následujících vlastností v části **VerticalAlignment** v části **rozložení** okno Vlastnosti: **nahoře**, **uprostřed**, **dole**nebo **Stretch**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Zarovnání dvou nebo více prvků pomocí zarovnávacím čárám

- V Návrhář XAML v rozložení, které obsahuje alespoň dva prvky, přetáhněte nebo změňte velikost jednoho prvku tak, aby byl okraj zarovnán s jiným prvkem.

     Když jsou okraje zarovnány, zobrazí se *hranice zarovnání* označující zarovnání. Hranice zarovnání je červená přerušovaná čára. Hranice zarovnání se zobrazí jenom v případě, že je povolený **přichycení k zarovnávacím čárám** . Ilustraci návrhové plochy, která zobrazuje hranici zarovnání, najdete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-the-an-elements-margins"></a>Změna okrajů elementu
 Okraje v Návrhář XAML určují velikost prázdného místa, které je okolo prvku na návrhové ploše. Například okraje určují velikost prostoru mezi vnějšími okraji prvku a hranicemi  `Grid` panelu, který obsahuje prvek. Okraje také určují velikost prostoru mezi prvky, které jsou obsaženy v `StackPanel` .

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Změna okrajů prvku v okno Vlastnosti

1. Vyberte prvek, jehož okraje chcete změnit.

2. V části **rozložení** v okno Vlastnosti změňte hodnotu (v pixelech nebo jednotkách nezávislých na zařízení, které jsou přibližně 1/96 palce) pro kteroukoli vlastnost **okraje** (**nahoře**, **vlevo**, **vpravo**nebo **dole**).

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Změna okrajů prvku na návrhové ploše

- Chcete-li změnit okraje elementu relativně vzhledem k jeho kontejneru rozložení, klikněte na *Doplňky okrajů* , které se zobrazí kolem prvku na návrhové ploše, když je vybrán prvek a je uvnitř kontejneru rozložení. Ilustrace znázorňující doplňky okrajů naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Je-li doplněk pro úpravy okrajů otevřený, svisle nebo vodorovně, tato marže není nastavena. Je-li doplněk pro úpravy okrajů uzavřen, je tento okraj nastaven.

     Když otevřete doplněk pro úpravy okrajů a opačná marže není nastavena, je opačná marže nastavena na správnou hodnotu podle umístění prvku na návrhové ploše. Pro opačné okraje, jako jsou **levý** a **pravý** okraj, je vždy nastavena alespoň jedna vlastnost.

    > [!IMPORTANT]
    > Prvky umístěné uvnitř některých kontejnerů rozložení, například a <xref:Windows.UI.Xaml.Controls.Canvas> , nemají doplňky pro okraje. Prvky umístěné uvnitř prvku <xref:Windows.UI.Xaml.Controls.StackPanel> mají doplňky pro okraje pro levý a pravý okraj nebo horní a dolní okraj v závislosti na orientaci `StackPanel` .

## <a name="grouping-and-ungrouping-elements"></a>Seskupení a rozseskupení prvků
 Seskupení dvou nebo více prvků v Návrhář XAML vytvoří nový kontejner rozložení a umístí tyto prvky do tohoto kontejneru. Umístění dvou nebo více prvků dohromady do kontejneru rozložení umožňuje snadno vybrat, přesunout a transformovat skupinu, jako kdyby byly elementy v dané skupině jedním prvkem. Seskupení je také užitečné pro identifikaci prvků, které jsou vzájemně propojené, například tlačítek, která tvoří prvek navigace. Při zrušení seskupení prvků je jednoduše odstraněn kontejner rozložení, který obsahuje prvky.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Seskupení prvků do nového kontejneru rozložení

1. Vyberte prvky, které chcete seskupit. (Chcete-li vybrat více prvků, stiskněte a podržte stisknutou klávesu CTRL a klikněte na ně.)

2. Klikněte pravým tlačítkem myši na vybrané prvky, přejděte na položku **Seskupit na**a potom klikněte na typ kontejneru rozložení, ve kterém chcete skupinu umístit.

    > [!TIP]
    > Pokud vyberete <xref:Windows.UI.Xaml.Controls.Viewbox> , <xref:Windows.UI.Xaml.Controls.Border> nebo <xref:Windows.UI.Xaml.Controls.ScrollViewer> Chcete-li seskupit prvky, prvky jsou umístěny na novém <xref:Windows.UI.Xaml.Controls.Grid> panelu v rámci <xref:Windows.UI.Xaml.Controls.Viewbox> , <xref:Windows.UI.Xaml.Controls.Border> nebo <xref:Windows.UI.Xaml.Controls.ScrollViewer> . Pokud zrušíte seskupení prvků v jednom z těchto kontejnerů rozložení, bude <xref:Windows.UI.Xaml.Controls.Viewbox> <xref:Windows.UI.Xaml.Controls.Border> odstraněno pouze, nebo, <xref:Windows.UI.Xaml.Controls.ScrollViewer> a <xref:Windows.UI.Xaml.Controls.Grid> panel zůstane. Chcete-li `Grid` panel odstranit, oddělit prvky znovu.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Oddělit prvky a odstranit rozložení

- Klikněte pravým tlačítkem na skupinu, kterou chcete zrušit seskupení, a klikněte na zrušit **seskupení**.

  Prvky můžete také seskupit nebo zrušit seskupení kliknutím pravým tlačítkem myši na vybrané položky v okně Osnova dokumentu a kliknutím na **seskupit do** nebo **oddělit**.

## <a name="resetting-the-element-layout"></a>Resetování rozložení prvku
 Můžete obnovit výchozí hodnoty pro konkrétní vlastnosti rozložení prvku pomocí příkazů pro obnovení rozložení. Pomocí tohoto příkazu můžete obnovit okraj, zarovnání, šířku, výšku a velikost elementu, a to buď jednotlivě, nebo souhrnně.

#### <a name="to-reset-the-element-layout"></a>Resetování rozložení prvku

- V okně Osnova dokumentu nebo na návrhové ploše klikněte pravým tlačítkem myši na prvek, vyberte možnost **rozložení**, **resetovat** hodnotu *PropertyName*, kde *PropertyName* je vlastnost, kterou chcete obnovit (nebo vyberte možnost **rozložení**, **Obnovit vše** pro resetování všech vlastností rozložení elementu).

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
