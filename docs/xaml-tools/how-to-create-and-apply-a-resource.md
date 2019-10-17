---
title: Postup vytvoření a použití prostředku
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acbd1641a8ac16376ead04bfb37782e523f090c6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450781"
---
# <a name="how-to-create-and-apply-a-resource"></a>Postup vytvoření a použití prostředku

Styly a šablony pro prvky v Návrhář XAML jsou uloženy v opakovaně použitelných entitách nazývaných prostředky. Styly umožňují nastavit vlastnosti elementu a znovu použít tato nastavení pro konzistentní vzhled napříč více prvky. [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) definuje vzhled ovládacího prvku a lze jej také použít jako prostředek. Další informace naleznete v tématu [styly XAML](/windows/uwp/design/controls-and-patterns/xaml-styles) a [šablony ovládacích prvků](/windows/uwp/design/controls-and-patterns/control-templates).

Při každém vytvoření nového prostředku z existující vlastnosti, [stylu](xref:Windows.UI.Xaml.Style)nebo [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate)vám dialogové okno **vytvořit prostředek** umožňuje definovat prostředek na úrovni aplikace, na úrovni dokumentu nebo na úrovni prvku. Tyto úrovně určují, kde můžete prostředek použít. Například pokud definujete prostředek na úrovni prvku, prostředek lze použít pouze pro prvek, na kterém jste jej vytvořili. Můžete také zvolit uložení prostředku do [slovníku prostředků](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references), což je samostatný soubor, který můžete použít znovu v jiném projektu.

## <a name="create-a-new-resource"></a>Vytvořit nový prostředek

1. Se souborem XAML otevřeným v Návrhář XAML vytvořte prvek nebo vyberte prvek v okně Osnova dokumentu.

2. V okně **vlastnosti** zvolte značku vlastnosti, která se zobrazí jako symbol pole napravo od hodnoty vlastnosti, a pak zvolte **převést na nový prostředek**. Symbol bílého pole označuje výchozí hodnotu a symbol černého pole obvykle indikuje, že byl použit místní prostředek.

     Zobrazí se příslušné dialogové okno pro tvorbu prostředku. Toto dialogové okno se zobrazí při vytvoření prostředku z štětce:

     ![Vytvořit prostředek – dialogové okno](../designers/media/xaml_create_resource.png)

3. Do pole **název (klíč)** zadejte název klíče. Toto je název, který lze použít, pokud chcete, aby na prostředek odkazovaly jiné prvky.

4. V části **definovat v**vyberte možnost, která určuje, kde se má prostředek definovat:

    - Chcete-li prostředek zpřístupnit pro libovolný dokument v aplikaci, vyberte možnost **aplikace**.

    - Chcete-li prostředek zpřístupnit pouze pro aktuální dokument, vyberte **Tento dokument**.

    - Chcete-li prostředek zpřístupnit pouze pro prvek, ze kterého jste vytvořili prostředek, nebo na jeho podřízené prvky, zvolte **Tento dokument**a v rozevíracím seznamu vyberte **element**: **název**.

    - Chcete-li definovat prostředek v souboru [slovníku prostředků](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) , který lze znovu použít v jiných projektech, klikněte na možnost **slovník prostředků**. Pak v rozevíracím seznamu vyberte existující soubor slovníku prostředků, například **StandardStyles. XAML**.

5. Klikněte na tlačítko **OK** a vytvořte prostředek a použijte ho pro element, ze kterého jste ho vytvořili.

## <a name="apply-a-resource-to-an-element-or-property"></a>Použít prostředek pro element nebo vlastnost

1. V okně Osnova dokumentu vyberte prvek, pro který chcete použít prostředek.

2. Proveďte jednu z těchto akcí:

   - Použijte prostředek pro vlastnost. V okně **vlastnosti** zvolte značku vlastnosti vedle hodnoty vlastnosti, zvolte **místní prostředek** nebo **systémové prostředky**a pak zvolte dostupný prostředek ze seznamu, který se zobrazí.

      Pokud nevidíte prostředek, který byste očekávali, může to být způsobeno tím, že typ prostředku neodpovídá typu vlastnosti.

   - Použití prostředku stylu nebo šablony ovládacího prvku k ovládacímu prvku. Otevřete nabídku klikněte pravým tlačítkem myši (kontextová nabídka) pro ovládací prvek v okně Osnova dokumentu, zvolte možnost **Upravit šablonu** nebo **upravte další šablony**, zvolte možnost **použít prostředek**a potom zvolte název šablony ovládacího prvku ze seznamu uvedeny.

     > [!NOTE]
     > **Úprava šablony** aplikuje šablony ovládacích prvků. **Úprava dalších šablon** aplikuje další typy šablon.

     Můžete použít prostředky bez ohledu na to, kde jsou kompatibilní. Například můžete použít prostředek štětce na vlastnost **popředí** ovládacího prvku [TextBox](xref:Windows.UI.Xaml.Controls.TextBox) .

## <a name="edit-a-resource"></a>Úprava prostředku

1. Vyberte prvek na návrhové ploše nebo v okně Osnova dokumentu.

2. Zvolte výchozí nebo místní značku vlastnosti napravo od vlastnosti v okně **vlastnosti** a pak zvolte **Upravit prostředek** . otevře se dialogové okno **Upravit prostředek** .

3. Upravte možnosti prostředku.

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
