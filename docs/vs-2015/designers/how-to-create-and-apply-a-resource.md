---
title: Vytvoření a použití prostředku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d1fba3b956a492740171bf2ad747e980b41df29
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851969"
---
# <a name="how-to-create-and-apply-a-resource"></a>Postup vytvoření a použití prostředku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Styly a šablony pro prvky v Návrhář XAML jsou uloženy v opakovaně použitelných entitách nazývaných prostředky. Styly umožňují nastavit vlastnosti elementu a znovu použít tato nastavení pro konzistentní vzhled napříč více prvky. [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) definuje vzhled ovládacího prvku a lze jej také použít jako prostředek. Další informace naleznete v tématu [rychlý Start: ovládací prvky pro stylování](https://msdn.microsoft.com/library/windows/apps/xaml/hh465381.aspx) a [rychlé zprovoznění: šablony ovládacích](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374.aspx)prvků.

 Kdykoli vytvoříte nový prostředek z existující vlastnosti, [stylu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx)nebo `ControlTemplate`, dialogové okno **vytvořit prostředek** umožňuje definovat prostředek na úrovni aplikace, na úrovni dokumentu nebo na úrovni prvku. Tyto úrovně určují, kde můžete prostředek použít. Například pokud definujete prostředek na úrovni prvku, prostředek lze použít pouze pro prvek, na kterém jste jej vytvořili. Také lze zvolit uložení prostředku do adresáře zdrojů, což je oddělený soubor, který lze znovu použít v jiném projektu.

### <a name="to-create-a-new-resource"></a>Vytvoření nového prostředku

1. Se souborem XAML otevřeným v Návrhář XAML vytvořte prvek nebo vyberte prvek v okně Osnova dokumentu.

2. V okno Vlastnosti zvolte značku vlastnosti, která se zobrazí jako symbol pole napravo od hodnoty vlastnosti, a pak zvolte **převést na nový prostředek**. Symbol bílého pole označuje výchozí hodnotu a symbol černého pole obvykle indikuje, že byl použit místní prostředek.

     Zobrazí se příslušné dialogové okno pro tvorbu prostředku. Toto dialogové okno se zobrazí při vytvoření prostředku z štětce:

     ![Vytvořit prostředek – dialogové okno](../designers/media/xaml-create-resource.png "xaml_create_resource")

3. Do pole **název (klíč)** zadejte název klíče. Toto je název, který lze použít, pokud chcete, aby na prostředek odkazovaly jiné prvky.

4. V části **definovat v**vyberte možnost, která určuje, kde se má prostředek definovat:

    - Chcete-li prostředek zpřístupnit pro libovolný dokument v aplikaci, vyberte možnost **aplikace**.

    - Chcete-li prostředek zpřístupnit pouze pro aktuální dokument, vyberte **Tento dokument**.

    - Chcete-li prostředek zpřístupnit pouze pro prvek, ze kterého jste vytvořili prostředek, nebo na jeho podřízené prvky, zvolte **Tento dokument**a v rozevíracím seznamu vyberte *element*: *název*.

    - Chcete-li definovat prostředek v souboru slovníku prostředků, který lze znovu použít v jiných projektech, klikněte na možnost **slovník prostředků**a potom v rozevíracím seznamu vyberte existující soubor slovníku prostředků, například **StandardStyles. XAML**.

5. Klikněte na tlačítko **OK** a vytvořte prostředek a použijte ho pro element, ze kterého jste ho vytvořili.

### <a name="to-apply-a-resource-to-an-element-or-property"></a>Použití prostředku pro element nebo vlastnost

1. V okně Osnova dokumentu vyberte prvek, na který chcete prostředek použít.

2. Proveďte jednu z těchto akcí:

   - Použijte prostředek pro vlastnost. V okno Vlastnosti zvolte značku vlastnosti vedle hodnoty vlastnosti, zvolte **místní prostředek** nebo **systémové prostředky**a pak zvolte dostupný prostředek ze seznamu, který se zobrazí.

      Pokud nevidíte prostředek, který byste očekávali, může to být způsobeno tím, že typ prostředku neodpovídá typu vlastnosti.

   - Použití prostředku stylu nebo šablony ovládacího prvku k ovládacímu prvku. Otevřete kontextovou nabídku pro ovládací prvek v okně Osnova dokumentu, zvolte možnost **Upravit šablonu** nebo **Upravit další šablony**, zvolte možnost **použít prostředek**a potom zvolte název šablony ovládacího prvku ze seznamu, který se zobrazí.

     > [!NOTE]
     > **Úprava šablony** se používá pro použití šablon ovládacích prvků. **Úprava dalších šablon** se používá k aplikování dalších typů šablon.

     Prostředky je možné použít bez ohledu na to, kde jsou kompatibilní. Například prostředek štětce lze použít na vlastnost **popředí** ovládacího prvku <xref:Windows.UI.Xaml.Controls.TextBox>.

### <a name="to-edit-a-resource"></a>Úprava prostředku

1. Vyberte prvek na návrhové ploše nebo v okně Osnova dokumentu.

2. Zvolte výchozí nebo místní značku vlastnosti napravo od vlastnosti v okno Vlastnosti a pak zvolte **Upravit prostředek** . otevře se dialogové okno **Upravit prostředek** .

3. Upravte možnosti prostředku.

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
