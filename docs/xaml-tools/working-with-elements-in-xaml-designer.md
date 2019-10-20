---
title: Práce s elementy v Návrháři XAML
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bae8f676a009ef9e5b3560feff15b74410cc52ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668621"
---
# <a name="work-with-elements-in-xaml-designer"></a>Práce s elementy v Návrháři XAML

Můžete přidat prvky – ovládací prvky, rozložení a tvary – do aplikace v jazyce XAML, v kódu nebo pomocí Návrhář XAML. Toto téma popisuje, jak pracovat s prvky v Návrhář XAML v aplikaci Visual Studio nebo Blend pro Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Přidání elementu do rozložení

*Rozložení* je proces změny velikosti a umístění prvků v uživatelském rozhraní. Chcete-li umístit vizuální prvky, je nutné je umístit do [panelu](xref:Windows.UI.Xaml.Controls.Panel)rozložení. @No__t_0 má podřízenou vlastnost, která je kolekcí typů [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement) . Můžete použít různé podřízené prvky `Panel`, jako je [plátno](xref:Windows.UI.Xaml.Controls.Canvas), [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel)a [Grid](xref:Windows.UI.Xaml.Controls.Grid), a sloužit tak jako kontejnery rozložení a k umístění a uspořádání prvků na stránce.

Ve výchozím nastavení se jako kontejner rozložení nejvyšší úrovně v rámci stránky nebo formuláře používá panel `Grid`. Můžete přidat panely rozložení, ovládací prvky nebo jiné prvky v rozložení stránky nejvyšší úrovně.

Chcete-li přidat prvek do rozložení v Návrhář XAML, proveďte jednu z následujících akcí:

- Dvakrát klikněte na prvek v **sadě nástrojů** (nebo vyberte element v sadě nástrojů a stiskněte klávesu **ENTER**).

- Přetáhněte element ze **sady nástrojů** na návrhovou plochu.

- V **sadě nástrojů**vyberte jeden z nástrojů pro kreslení (například [elipsa](xref:Windows.UI.Xaml.Shapes.Ellipse) nebo [obdélník](xref:Windows.UI.Xaml.Shapes.Rectangle)) a potom nakreslete prvek na aktivním panelu.

## <a name="change-the-layering-order-of-elements"></a>Změna pořadí vrstvení prvků

Pokud jsou na návrhové ploše dva prvky v Návrhář XAML, jeden prvek se zobrazí před druhým v pořadí vrstev. V dolní části seznamu prvků je v okně Osnova dokumentu přední prvek (kromě případu, kdy je nastavena vlastnost **ZIndex** elementu). Při vložení elementu do kontejneru stránky, formuláře nebo rozložení, je prvek automaticky umístěn před další prvky v rámci aktivního prvku kontejneru. Chcete-li změnit pořadí prvků, lze použít příkazy **Order** nebo přetáhnout prvky ve stromové struktuře objektů v okně Osnova dokumentu.

Chcete-li změnit pořadí vrstvení, proveďte jednu z následujících akcí:

- V okně **Osnova dokumentu** přetáhněte prvky nahoru nebo dolů a vytvořte požadované pořadí vrstev.

- Klikněte pravým tlačítkem myši na prvek v okně Osnova dokumentu nebo na návrhové ploše, pro kterou chcete změnit pořadí vrstev, přejděte na příkaz **pořadí**a potom klikněte na jednu z následujících možností:

  - **Přeneste dopředu** pro převedení prvku na začátek objednávky.

  - **Přenést** nahoru, aby prvek předali jednu úroveň v pořadí.

  - **Přenést dozadu** pro odeslání elementu zpět o jednu úroveň v pořadí.

  - **Přenést do back** pro odeslání elementu všem způsobem na zadní stranu objednávky.

- Změňte vlastnost **ZIndex** v části **rozložení** v okno Vlastnosti. U překrývajících se prvků má vlastnost **ZIndex** přednost před pořadím prvků zobrazených v okně Osnova dokumentu. Prvek, který má vyšší hodnotu **ZIndex** , se zobrazí v popředí při překrytí prvků.

## <a name="change-the-alignment-of-an-element"></a>Změna zarovnání elementu

Prvky můžete zarovnat na návrhové ploše pomocí příkazů nabídky nebo přetažením prvků do zarovnávacím čárám.

*Snapline* je vizuální znázornění, které vám pomůže zarovnat prvek relativně k ostatním prvkům v aplikaci.

Zarovnání dvou nebo více prvků pomocí příkazů nabídky:

1. Vyberte prvky, které chcete zarovnat. Stisknutím a podržením klávesy **CTRL** můžete vybrat více než jeden prvek a zároveň vybrat prvky.

2. Vyberte jednu z následujících vlastností v části **HorizontalAlignment** v části **rozložení** okno Vlastnosti: **Left**, **Center**, **Right**nebo **Stretch**.

3. Vyberte jednu z následujících vlastností v části **VerticalAlignment** v části **rozložení** okno Vlastnosti: **nahoře**, **uprostřed**, **dole**nebo **Stretch**.

Chcete-li zarovnat dva nebo více prvků pomocí zarovnávacím čárám, v Návrhář XAML v rozložení, které obsahuje alespoň dva prvky, přetáhněte nebo změňte velikost jednoho z prvků tak, aby byl okraj zarovnán s jiným prvkem.

Když jsou okraje zarovnány, zobrazí se *hranice zarovnání* označující zarovnání. Hranice zarovnání je červená přerušovaná čára. Hranice zarovnání se zobrazí jenom v případě, že je povolený **přichycení k zarovnávacím čárám** . Ilustraci návrhové plochy, která zobrazuje hranici zarovnání, najdete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Změna okrajů prvku

Okraje v Návrhář XAML určují velikost prázdného místa, které je okolo prvku na návrhové ploše. Například okraje určují velikost prostoru mezi vnějšími okraji prvku a hranicemi panelu `Grid`, který obsahuje prvek. Okraje také určují velikost prostoru mezi prvky, které jsou obsaženy v `StackPanel`.

Změna okrajů prvku v okno Vlastnosti:

1. Vyberte prvek, jehož okraje chcete změnit.

2. V části **rozložení** v okno Vlastnosti změňte hodnotu (v pixelech nebo jednotkách nezávislých na zařízení, které jsou přibližně 1/96 palce) pro kteroukoli vlastnost **okraje** (**nahoře**, **vlevo**, **vpravo**nebo **dole**).

Chcete-li změnit okraje prvku vzhledem k kontejneru rozložení prvku, klikněte na tlačítko *Doplňky okrajů* , které se zobrazí kolem prvku, když je vybrán prvek a je uvnitř kontejneru rozložení. Ilustrace znázorňující doplňky okrajů naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Je-li doplněk pro úpravy okrajů otevřený, svisle nebo vodorovně, tato marže není nastavena. Je-li doplněk pro úpravy okrajů uzavřen, je tento okraj nastaven.

Když otevřete doplněk pro úpravy okrajů a opačná marže není nastavena, je opačná marže nastavena na správnou hodnotu podle umístění prvku na návrhové ploše. Pro opačné okraje, jako jsou **levý** a **pravý** okraj, je vždy nastavena alespoň jedna vlastnost.

> [!IMPORTANT]
> Prvky umístěné uvnitř některých kontejnerů rozložení, jako je [plátno](xref:Windows.UI.Xaml.Controls.Canvas), nemají doplňky pro okraje. Prvky umístěné uvnitř [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) mají doplňky pro okraje pro levý a pravý okraj nebo horní a dolní okraj v závislosti na orientaci `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Seskupit a zrušit seskupení prvků

Seskupení dvou nebo více prvků v Návrhář XAML vytvoří nový kontejner rozložení a umístí tyto prvky do tohoto kontejneru. Umístění dvou nebo více prvků dohromady do kontejneru rozložení umožňuje snadno vybrat, přesunout a transformovat skupinu, jako kdyby byly elementy v dané skupině jedním prvkem. Seskupení je také užitečné pro identifikaci prvků, které jsou vzájemně propojené, například tlačítek, která tvoří prvek navigace. Při zrušení seskupení prvků je jednoduše odstraněn kontejner rozložení, který obsahuje prvky.

Seskupení prvků do nového kontejneru rozložení:

1. Vyberte prvky, které chcete seskupit. (Chcete-li vybrat více prvků, stiskněte a podržte stisknutou **klávesu CTRL** a klikněte na ně.)

2. Klikněte pravým tlačítkem myši na vybrané prvky, přejděte na položku **Seskupit na**a potom klikněte na typ kontejneru rozložení, ve kterém chcete skupinu umístit.

    > [!TIP]
    > Pokud vyberete možnost [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [border](xref:Windows.UI.Xaml.Controls.Border)nebo [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) k seskupení prvků, prvky jsou umístěny na novém panelu [mřížky](xref:Windows.UI.Xaml.Controls.Grid) v rámci [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [ohraničení](xref:Windows.UI.Xaml.Controls.Border)nebo [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer). Pokud zrušíte seskupení prvků v jednom z těchto kontejnerů rozložení, odstraní se pouze [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [border](xref:Windows.UI.Xaml.Controls.Border)nebo [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) a panel [mřížky](xref:Windows.UI.Xaml.Controls.Grid) zůstane. Chcete-li odstranit panel `Grid`, odseskupte prvky znovu.

Chcete-li zrušit seskupení prvků a odstranit rozložení, klikněte pravým tlačítkem myši na skupinu, kterou chcete zrušit seskupení, a klikněte na příkaz **Zrušit seskupení**. Prvky můžete také seskupit nebo zrušit seskupení kliknutím pravým tlačítkem myši na vybrané položky v okně Osnova dokumentu a kliknutím na **seskupit do** nebo **oddělit**.

## <a name="reset-the-element-layout"></a>Resetovat rozložení elementu

Můžete obnovit výchozí hodnoty pro konkrétní vlastnosti rozložení prvku pomocí příkazů pro obnovení rozložení. Pomocí tohoto příkazu můžete obnovit okraj, zarovnání, šířku, výšku a velikost elementu, a to buď jednotlivě, nebo souhrnně.

Chcete-li obnovit rozložení prvku, klikněte pravým tlačítkem myši na prvek v okně Osnova dokumentu nebo na návrhové ploše a pak zvolte **rozložení** > **obnovit** *PropertyName*, kde *PropertyName* je vlastnost, kterou chcete obnovit (nebo zvolte **Rozložení** > **Obnovit vše** pro resetování všech vlastností rozložení elementu).

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
